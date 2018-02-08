# Streamlabs OBS Issues and Solutions

- Roadmap > [found on Trello](https://trello.com/b/oTl4KiBW/streamlabs-obs-roadmap)
- Report Issues > Please submit all issues on the tracker http://tracker.streamlabs.com
- Backups > Always make backups during beta testing! Settings > Overlays > Export

## Game optimized encoder settings

The game optmized encoder settings is currently only available when using **software (x264)** encoding and using **Twitch** as streaming service. If you use both, you can enable the optmized encoder settings by clicking *Go Live* and in the pop-up you see to set your Game and Title, you can now also enable optimized encoder settings.

- Medium profile; CPU usage equivalent to x264 profile **veryfast** but optimized for gameplay.
- Low profile; CPU usage equivalent to x264 profile **ultrafast** but opttmized for gameplay.

If you do not see the pop-up to set the game or title, make sure that **Confirm stream title and game before going live** is set found in the General Settings.

## Streamlabs OBS crashes during startup

1. Try starting Streamlabs OBS as administrator.
2. Update your graphic card driver if needed and try again.
3. Delete `C:\Program Files\Streamlabs OBS\resources\app\node_modules\obs-studio-node\distribute\obs-plugins\frontend-tools.dll`
4. Try disabling your **Anti-Virus Software** and/or allow Streamlabs OBS in the **firewall**.
5. Reinstall with the latest installer from [the website](http://streamlabs.com/slobs)

## Streamlabs OBS randomly crashes during streaming

1. Update your video drivers.
    - For NVIDIA: 390.77
    - For AMD/ATI: 18.2.1

If the above did not work or already installed

2. Try a clean install of the video driver.

If this did not work, please `Upload Cache to Developers` (found in General Settings) and with the filename, that got copied to your clipboard by doing so, add a note to the [following issue](http://tracker.streamlabs.com/view.php?id=678) on our SLOBS Tracker. Describe what video driver version you have and include your Discord handle so developers can contact you.

## Streamlabs OBS is stuck on rainbow-colored Streamlabs logo

1. Try logging out of Streamlabs OBS, restart application, and log back in.

If the above did not work, or recovered your scenes do the following, it will be tricky.

2. Close Streamlabs OBS
3. Navigate (or winlogo + r) in Windows to `%appdata%\slobs-client\SceneCollections`
4. Open up `manifest.json` in a text editor.
5. Change any `false` you see to `true` and save the file.
6. Delete any other file in `SceneCollections` **except** `manifest.json`
7. Start Streamlabs OBS

To recover your scenes from before version 0.8.9

8. Close Streamlabs OBS
9. Navigate (or winlogo + r) in Windows to `%appdata%\slobs-client`
10. Delete `SceneCollections`
11. Start Streamlabs OBS again.

If step 7-8 did not work, reimport your scenes from an exported .overlay file or start anew by clearing cache and restart (found in settings) to reimport overlays from OBS Studio. In the latter case you have to redo your settings as well.

## Lost my scenes after updating to 0.8.9

Do the same steps as **Streamlabs OBS is stuck on rainbow-colored Streamlabs logo**

## Not capturing desktop audio

The developers are currently aware of the issue for some users unable to capture desktop audio. Some audio management software, like `Nahimic 2` or motherboard audio software like `Realtek HD Audio Manager` or `Sound Blaster Recon` are known to cause issues. Try closing that kind of software, and also check Windows taskmanager if any processes with a similiar name are running to be closed.

You can also try first to select manually the desktop audio device (audio settings), you use as default device in Windows Sound, not setting it to default. Alternatively you can set it to disabled and add in the scene you want desktop audio an `Audio Output Capture` and select the device that is set as default device in Windows Sound.

As last resort, you can temporary use an alternative program to capture audio like `VoiceMeeter Banana`. This program allows you to set it as default device, and then use a *virtual audio cable* into Streamlabs OBS to capture the desktop audio. You can find various guides on the internet (like [this one](http://www.ocgineer.com/audio.html)) or Youtube.

## Not going live on the service

Developers are currently aware of the issue. You can try the following;

1. Go to `Stream` in settings and select a **different** service than you want to use.
2. Restart Streamlabs OBS.
3. Go to `Stream` in settings and select the service again you want to use.
4. Select a different server, and then the server you want to use (**do not use auto**)
5. Restart Streamlabs OBS once more.
6. Try going live.

If this did not work, please upload your cache to the developers (found in General Settings) and with the filename, that got copied to your clipboard by doing so, create an issue on the [SLOBS Tracker](http://tracker.streamlabs.com). Describe the nature of the issue and post the filename of your cache as well.

## Recording is not working or saved

Developers are currently aware of the issue. You can try the following;

1. Go to `Output` in settings and change all values for recording you see to something else.
2. Restart Streamlabs OBS.
3. Go to `Output` in settings and change all values for recording you want to use or default.
4. Restart STreamlabs OBS.
5. Try recording.

If the above does not work try the following.

6. Change to *Advanced Output Mode* or *Simple Output Mode* depending on what you were using.
7. Restart Streamlabs OBS
8. Try recording.
9. Perhaps repeat step 1-5.

If this did not work, please upload your cache to the developers (found in General Settings) and with the filename, that got copied to your clipboard by doing so, create an issue on the [SLOBS Tracker](http://tracker.streamlabs.com). Describe the nature of the issue and post the filename of your cache as well.

## Hotkeys set in Streamlabs OBS do not work in other applications

This is a known issue, and nothing you can do about this. The hotkey system is currently being rewritten to allow modifier keys (alt, shift, control) and mouse buttons (4 and 5) as hotkey **and** allow other applications to use the same hotkeys. No ETA for when this will be available.

## Hotkeys are not working in Streamlabs OBS

Currently there is a known issue in Streamlabs OBS version 0.8.9 where hotkeys are not activated on startup.

1. Open up `Hotkeys` in settings and close it.

`This issue is fixed in the next version`

## My Elgato HD60 is not capturing audio

1. Make sure your Video Capture Device is set to `Elgato Game Capture HD` and **not** `Game Capture HD60 S (Video) (#01)`

2) If the above option doesn't work for you, try running a 3.5mm audio cable from your monitor (headphones, if available) to your line-in on your PC. Then use an `Audio Input Capture Source` in a scene you want to have the Elgato audio, and select the line-input. You might want to add a small "Render Delay" `Filter` to the Elgato Video Capture Device to resync with the audio.

## High CPU usage in Idle

- Make sure all drivers are up-to-date and are matching 64-bit versions of your system.
- Almost every source you use, uses CPU to be functioning properly. The more you have the higher the total CPU usage would be.
- Downloaded animated overlays can cause high CPU usage due to the webm video files used as overlays.
- Using many different browser sources can cause high CPU usage, try limiting them or create references.
- You can delete Streamlabs OBS browser source cache that can cause high CPU usage;
    1. Navigate (or winlogo + r) in Windows to `%appdata%\slobs-client\plugin_config\obs-browser`
    2. Delete `Cache`
    3. Start Streamlabs OBS again

## Twitch Chat is not loading

Apparently, having another streamers channel open, in your own normal browser, while you have Streamlabs OBS open will cause your the chat window to not work properly. Only solution as of right now is to just simply not have another Twitch Chat open in your normal browser while you are using Streamlabs OBS.

## Discord does not go into 'Streamer Mode'

This is something Discord has to add on their side. You can up-vote at https://feedback.discordapp.com/forums/326712-discord-dream-land/suggestions/32823340-add-streamlabs-obs-to-streamermode-app-detection to push the process along and get it in faster! In the meantime, you can manually enable Streamer Mode in your Discord Settings, or you can set it up as a hotkey to enable or disable Streamer Mode.

## Game or Stream is stuttering or having FPS drops.

These is most likely caused by overloading either the GPU and CPU. At all times keep and eye out for both the total CPU and GPU usage in Windows task manager (if you do not have GPU in Windows 10, update to the latest major update). Some games are known to be broken and like to use all available CPU or GPU resources and cause issues for streaming software.

If you are using software (x264) encoding and are running into high CPU usage issues, causing **skipped frames**, consider using a faster preset or start using hardware encoding (NVENC/AMD) as that wont load the CPU extra to encode the stream.

Having high GPU usage? Lower the graphics quality in game so streaming software gets more breathing room to compose the frames for the encoder. Regardless of software or hardware encoding, streaming software requires shared GPU to compose the frames (combine sources) for the encoder to encode. Having overloaded GPU will cause **lagged frames**.

If you are having **dropped frames** this is most likely the network/internet connection to the selected server. Try selecting the closest Twitch server manually (not auto), and if already done so, try another (like 2nd closest) server. You can also try to restart your local network gear (modem, router, and switches) and see if that helps. Ultimately you can test different connections to the Twitch server with [this tool](https://r1ch.net/projects/twitchtest), as your ISP routing can be messed up as well.

In addition to the **dropped frames**, make also sure the video + audio bitrate is not exceeding or is getting close to your internet upload speed. Having other users on same network using upload (like cloud storage) will lower the throughput of the upload.

summary;
- Lagged Frames; Compositor overloaded, commonly high GPU usage.
- Skipped Frames; Encoder overloaded, commonly high CPU usage on x264.
- Dropped Frames; Network issues, try other servers or restart equipment.
{% include anchor.html %}
