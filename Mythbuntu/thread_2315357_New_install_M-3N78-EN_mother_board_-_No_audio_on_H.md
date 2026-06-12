---
title: "New install M-3N78-EN mother board - No audio on HDMI Mythbuntu 12.04"
date: 2016-02-28
forum: Mythbuntu
---

### Post by frank116 on 2016-02-28
I spent quite a while researching the solution to this problem.  I finally got it solved so I thought I might be able to save others some time by posting the solution that worked for me.

First of all I started with Mythbuntu 14.04 and had the same audio problem plus some other major issues on my setup.  There was a stability issue that caused the system to crash on playback, so having heard that others found 12.04 to be stable, I decided to downgrade with a fresh install of 12.04.

This install seemed to work except for the audio.  Here are the steps that I found necessary to get the problem resolved.  I gathered this information through many different posts, each dealing with a particular aspect of the problems I encountered.

On installation I selected to use the nVidia driver for the board.  The installed driver was version 304.  However I found that although installed, this driver is not set up.  You can see this by going to the control centre, clicking the graphics driver icon and noticing that the installed driver is activated, but not in use. To correct this, open the nVidia X Server Settings tool (found in settings) and confirm your display is shown.  Click the save to X configuration file button.  You can now reboot to put the driver in use.

The next thing I did was to get some audio flowing.  I loaded a DVD and brought up VLC to play it.  While it was playing (silently) I made the audio changes.

Many posts on this forum say to click the sound icon on the top panel to bring up the sound settings tool.  However on my setup there was no sound icon and I could not find an option to display one.  So the fix is to install pavucontrol.  

Open a terminal window.

```
sudo apt-get install pavucontrol
```

Run it.

```
pavucontrol
```

Go to the configuration tab and select HDMI/DisplayPort.  Go to output devices tab and select the HDMI/DisplayPort as the port

I was able to see that the output level was fluctuating, so sound was apparently being processed.  But still no sound out...

Close the pavucontrol.

Run the alsamixer to see the settings.

```
alsamixer
```

Use the right arrow key to move to the S/PDIF channels and verify that none are muted.  In my case S/PDIF1 was muted.   Muting is designated by "MM".  Click the "m" key to unmute as necessary.  When I did this, the sound came through.

Close the mixer and hopefully you now have HDMI sound output! 

All the best!

---

