---
title: "jerky video - $20 paypal reward"
date: 2008-12-13
forum: Mythbuntu
---

### Post by davidstoll on 2008-12-13
If anyone can help me with my jerky/stuttery video problem.  I'll send them $20 via paypal.

Here is my hardware:
2.6 GHz Quad core Intel
Gigabyte GA-EP35-DS3L LGA 775 Intel P35 ATX Intel mobo
8400 Nvidia (DVI & HDMI)
4GB 1066Mhz Corsair Dominator ram
1 SATA 3.0MB/s 7200 drive for 64bit OS
1 SATA 3.0MB/s 7200 drive for recordings
1 IDE DVD rom
Silicon Dust HD Homerun (over the air antenna)
Hauppauge WinTV-PVR-500MCE PCI (SD cable)

The video is jerky and stutters.  It also seems to go fast, slow, fast, slow when there is extra movement on the screen.  Not a huge speed change (fast, slow, fast, slow), but it is annoying.  I am not re-encoding the video and I do not want to.  I have tried different playback profiles CPU+, CPU++, High Quality, etc...

The problem is more noticeable on HD content than on SD, but it happens on SD also.  This happens on Live or recorded content.  I was also having problems playing videos on optical disks, but "sort of" solved it by making mplayer the default video playback device.  DVD playback within MythTV is also jettery...slow, fast, slow, fast.

The solution I'm looking for is a "setting"...not using mplayer as a work-around.  I don't want to buy a better video card or something else.  I want to use the hardware that I have.  I'm looking to tweak the settings.

The giving of the reward is left up to my discretion, but I will absolutely pay it if someone can help me fix it (with no extra hardware cost).  I am a linux noob, so speak slowly.  ;)

Thanks!

---

### Post by 2hot6ft2 on 2008-12-13
You can keep the $20. Try vlc and when the video is playing try clicking on video at the top and deinterlace>Blend if there are any artifacts you may have to pause and restart it or skip forward and back after setting it to straighten the pic out.

vlc works better for me mplayer always does what you're describing.

---

### Post by linuxguymarshall on 2008-12-13
Try VLC 


BTW Ill take his $20 ^

---

### Post by blackened on 2008-12-13
Which video drivers are you using? Do you have DMA enabled on your drives? Do you have all applicable restricted codecs installed?

My first bet would be on your video drivers. Make sure you've enabled the restricted nvidia driver under System->Administration->Hardware Drivers.

---

### Post by 2hot6ft2 on 2008-12-13
Hey linuxguymarshall. I like the part of your sig "I void warranties"
:lolflag: Like I tell them every time I buy a new pc and they offer me the extended warranty. "Why would I do that? I'll be voiding the warranty as soon as I get it home".

---

### Post by davidstoll on 2008-12-14
> **blackened said:**
> Which video drivers are you using? Do you have DMA enabled on your drives? Do you have all applicable restricted codecs installed?

My first bet would be on your video drivers. Make sure you've enabled the restricted nvidia driver under System->Administration->Hardware Drivers.

My drivers are Nvidia 177.80 (restricted).
From my understanding, DMA is only valid under IDE.  My HD's are SATA.
All drivers in the Myth Control Center are installed except the one for 32 bit systems (which is greyed out).

---

### Post by davidstoll on 2008-12-14
> **2hot6ft2 said:**
> You can keep the $20. Try vlc and when the video is playing try clicking on video at the top and deinterlace>Blend if there are any artifacts you may have to pause and restart it or skip forward and back after setting it to straighten the pic out.

vlc works better for me mplayer always does what you're describing.


How is it that the built-in media player is so bad?  mplayer, vlc, xine each seem to play ok....it's whatever the built in player is that's giving me the problem.  There must be a setting somewhere...?

---

### Post by KingArthur10 on 2008-12-14
I had jerky playback when I first installed everything.  I added -cache 65536 to the mplayer command in the video options.  Everything worked smoothly from there on.

---

### Post by davidstoll on 2008-12-14
> **KingArthur10 said:**
> I had jerky playback when I first installed everything.  I added -cache 65536 to the mplayer command in the video options.  Everything worked smoothly from there on.

My main problem is with the internal Live TV and recorded TV player...the built-in myth player.

---

### Post by tgalati4 on 2008-12-14
P35 mobo has some bottlenecks.  Even a Quad Core won't help.  You can donate your $20 in my name.

---

### Post by davidstoll on 2008-12-15
> **tgalati4 said:**
> P35 mobo has some bottlenecks.  Even a Quad Core won't help.  You can donate your $20 in my name.

If I take those same recorded videos and play them outside of mythtv (on the same machine) with VLC or mplayer, they play fine.

Not a bottleneck...it's a setting....or buffer...maybe it's an audio thing?  I've increased the audio buffer and it makes a little bit of a difference.

Basically if 1X is regular full speed video.  Live TV and recorded tv go like this...

1.2X (for 0.5 sec), 0.8X (for 0.5 sec), 1.2X, 0.8X, 1.2X, 0.8X...

And then skips every 5-10 seconds (or so).  If I rewind the video and play back where the skip happened, it doesn't skip again, so it's not the actual video or the recording engine.

---

### Post by utar on 2008-12-15
Have you tried toggling the "use open-gl sync" setting?  May be worth tring the aggresive sound buffer setting as well.

Can you also monitor the CPU usage (using top or something similar) to see if for any reason Myth is eating all your CPU cycles.

If those don't work can you check you mythfrontend log to see if that gives any clues.

---

### Post by davidstoll on 2008-12-16
> **utar said:**
> Have you tried toggling the "use open-gl sync" setting?  May be worth tring the aggresive sound buffer setting as well.

Can you also monitor the CPU usage (using top or something similar) to see if for any reason Myth is eating all your CPU cycles.

If those don't work can you check you mythfrontend log to see if that gives any clues.

The open-gl sync doesn't seem to make a difference one way or the other.


Here is an example of my CPU usage.

top - 08:42:34 up 13:48,  4 users,  load average: 0.86, 0.39, 0.14
Tasks: 172 total,   2 running, 170 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.6%us,  1.0%sy,  0.0%ni, 81.0%id,  0.2%wa,  0.1%hi,  0.2%si,  0.0%st
Mem:   4054416k total,  4024628k used,    29788k free,    44220k buffers
Swap:  7807580k total,     5536k used,  7802044k free,  2951612k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6109 root      20   0  253m 147m  71m R   42  3.7  59:17.42 Xorg               
 6692 login     20   0  814m 276m  99m S   16  7.0  68:30.26 mythfrontend.re    
 6969 login     20   0 86068  20m  10m S   10  0.5  49:02.26 npviewer.bin

a couple other entries at 1-2%.  Nothing significant.

---

### Post by newlinux on 2008-12-16
If you really want help you should post your frontend logs and what settings you were using with that log. You may need to turn up the verbosity of your logs (-v playback) for more information. This is usually the first place you look for playback problems. I recommend starting with the basic profile of CPU++ to start troubleshooting. It also may be that none of the stock playback profiles will work for you and you need to create your own. Your problems sound like playback profile issues. I've had those same symptoms before on some channels.


do you have openGL vsync enabled in your nvidia driver settings (check nvidia-settings)

if you run mythfrontend from the menu your logs will be in /var/log/mythtv

---

### Post by davidstoll on 2008-12-16
> **newlinux said:**
> If you really want help you should post your frontend logs and what settings you were using with that log. You may need to turn up the verbosity of your logs (-v playback) for more information. This is usually the first place you look for playback problems. I recommend starting with the basic profile of CPU++ to start troubleshooting. It also may be that none of the stock playback profiles will work for you and you need to create your own. Your problems sound like playback profile issues. I've had those same symptoms before on some channels.


do you have openGL vsync enabled in your nvidia driver settings (check nvidia-settings)

if you run mythfrontend from the menu your logs will be in /var/log/mythtv

Yes, currently openGL vsync is enabled, but I have disabled it at times when troubleshooting and I don't see any difference.

CPU++ is my current profile and I've tried to make my own, but I don't know much about the different settings and I was not able to make my problem go away.

Attached are my frontend and backend files.  I appreciate any help you guys can provide.

Thanks you!

---

### Post by newlinux on 2008-12-16
I've only had a chance to glance at it, but this:

```

2008-12-16 08:40:40.813 Video sync method can't support double framerate (refresh rate too low for bob deint)
2008-12-16 08:40:40.821 Video timing method: SGI OpenGL
2008-12-16 08:40:40.863 AO: dropping back audio_buffer_unused
2008-12-16 08:40:40.909 AO: dropping back audio_buffer_unused
2008-12-16 08:40:40.960 AO: dropping back audio_buffer_unused
2008-12-16 08:40:40.990 AO: dropping back audio_buffer_unused
<snip>

```
appears to be the issue. without thinking about it much, you might want to change deinterlacers to one that doesn't double the frame rate. Another approach is to change your refresh rate, whether or not you want to do that depends on your monitor and your current refresh rate.

What type of display are you using? 

What happens when you use timestretch when watching problem channels? Try watching at 1.05x speed. This would disable the bob deinterlacer (*I think, at least it used to*), and I bet your picture would look a lot better.

If so, change your deinterlacer to one field or something simple and see how it looks.

---

### Post by newlinux on 2008-12-16
just out of curiousity, are you using spdif out? If so and you are watching video with dolby digital passthrough enabled and you timestretch your audio will sound strange, but it is nothing to worry about. I'm more interested in what happens to the video when you switch deinterlacers.

---

### Post by novellahub on 2008-12-16
> **davidstoll said:**
> If anyone can help me with my jerky/stuttery video problem.  I'll send them $20 via paypal.

Here is my hardware:
2.6 GHz Quad core Intel
Gigabyte GA-EP35-DS3L LGA 775 Intel P35 ATX Intel mobo
8400 Nvidia (DVI & HDMI)
4GB 1066Mhz Corsair Dominator ram
1 SATA 3.0MB/s 7200 drive for 64bit OS
1 SATA 3.0MB/s 7200 drive for recordings
1 IDE DVD rom
Silicon Dust HD Homerun (over the air antenna)
Hauppauge WinTV-PVR-500MCE PCI (SD cable)

The video is jerky and stutters.  It also seems to go fast, slow, fast, slow when there is extra movement on the screen.  Not a huge speed change (fast, slow, fast, slow), but it is annoying.  I am not re-encoding the video and I do not want to.  I have tried different playback profiles CPU+, CPU++, High Quality, etc...

The problem is more noticeable on HD content than on SD, but it happens on SD also.  This happens on Live or recorded content.  I was also having problems playing videos on optical disks, but "sort of" solved it by making mplayer the default video playback device.  DVD playback within MythTV is also jettery...slow, fast, slow, fast.

The solution I'm looking for is a "setting"...not using mplayer as a work-around.  I don't want to buy a better video card or something else.  I want to use the hardware that I have.  I'm looking to tweak the settings.

The giving of the reward is left up to my discretion, but I will absolutely pay it if someone can help me fix it (with no extra hardware cost).  I am a linux noob, so speak slowly.  ;)

Thanks!

Edit your /etc/X11/xorg.conf file.  Does it have the following in the device section?

```

Option  "UseEvents" "True"

```


This is usually in the "Device" section.  If it is not there, try adding this line, reboot, and try playing with the internal player again.  I can provide you more detailed instructions if needed.

---

### Post by davidstoll on 2008-12-16
> **newlinux said:**
> I've only had a chance to glance at it, but this:

```

2008-12-16 08:40:40.813 Video sync method can't support double framerate (refresh rate too low for bob deint)
2008-12-16 08:40:40.821 Video timing method: SGI OpenGL
2008-12-16 08:40:40.863 AO: dropping back audio_buffer_unused
2008-12-16 08:40:40.909 AO: dropping back audio_buffer_unused
2008-12-16 08:40:40.960 AO: dropping back audio_buffer_unused
2008-12-16 08:40:40.990 AO: dropping back audio_buffer_unused
<snip>

```
appears to be the issue. without thinking about it much, you might want to change deinterlacers to one that doesn't double the frame rate. Another approach is to change your refresh rate, whether or not you want to do that depends on your monitor and your current refresh rate.

What type of display are you using? 

What happens when you use timestretch when watching problem channels? Try watching at 1.05x speed. This would disable the bob deinterlacer (*I think, at least it used to*), and I bet your picture would look a lot better.

If so, change your deinterlacer to one field or something simple and see how it looks.


My display is a Samsung 750 42" LCD TV.

I tried all the different deinterlacers, nothing fixed the issue...not even one filed.

---

### Post by davidstoll on 2008-12-16
> **newlinux said:**
> just out of curiousity, are you using spdif out? If so and you are watching video with dolby digital passthrough enabled and you timestretch your audio will sound strange, but it is nothing to worry about. I'm more interested in what happens to the video when you switch deinterlacers.

SPDIF - Yes and no.

Yes, I want to.  Yes, it is connected.  Yes, I know it works because I had Windows installed on this before I formatted it and install MythBuntu.

But, no, it's not working...that's another issue.

---

### Post by davidstoll on 2008-12-16
> **novellahub said:**
> Edit your /etc/X11/xorg.conf file.  Does it have the following in the device section?

```

Option  "UseEvents" "True"

```


This is usually in the "Device" section.  If it is not there, try adding this line, reboot, and try playing with the internal player again.  I can provide you more detailed instructions if needed.

I'll give that a try, but one little issue...I have 2 "device" sections...


**********************
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection
*******************

Should I combine and then add your line or just add it to one of them?

Thanks

---

### Post by newlinux on 2008-12-16
did to try turning off deinterlacing or see what happens when you time stretching? did you look at the logs after changing to each deinterlacer?  Just trying to narrow down the problem...

So you are getting sound via analog right now? 
Another possibility is that it could be that you've set the wrong audio device. what do you have your audio device set as in myth? You could try ALSA:default to start with... 

what does 

aplay -l 

return?

Have you tinkered with any other audio settings on your install?

---

### Post by novellahub on 2008-12-17
> **davidstoll said:**
> I'll give that a try, but on little issue...I have 2 "device" sections...


**********************
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection
*******************

Should I combine and then add your line or just add it to one of them?

Thanks

Do not combine them.  Add the line to both of them to look like this:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    Option         "UseEvents" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    Option         "UseEvents" "True"
EndSection

```

---

### Post by davidstoll on 2008-12-18
> **newlinux said:**
> did to try turning off deinterlacing or see what happens when you time stretching? did you look at the logs after changing to each deinterlacer?  Just trying to narrow down the problem...

So you are getting sound via analog right now? 
Another possibility is that it could be that you've set the wrong audio device. what do you have your audio device set as in myth? You could try ALSA:default to start with... 

what does 

aplay -l 

return?

Have you tinkered with any other audio settings on your install?


aplay -l
# gives me....
*****************************
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
*****************************

Yes, I do get analog stereo out.  I do use ALSA:default, and have tried the other settings (SPDIF out, surround5.1, etc) and none of them seem to work, but it's probably likely that I don't have the correct combination of settings on that page.  I also ran the alsamixer and un-muted the digital out...but that didn't help.  It's at 00 and I can't up the volume, but I'm guessing digital out doesn't have volume control.

When I have AC3 passthrough enabled, I sometimes get really loud static (depending on what I'm playing and other settings)...but sometimes it does pass through.  DTS never passes through.  I had windows installed and both the optical out, coax out and HDMI delivered digital audio.  I would be happy with any digital coming out of any ouput.  Although, my preference would be to pass the audio over the HDMI and then use the optical out on the TV to go to the receiver.  That way, if I don't need the surround sound and only want to use analog, I don't have to turn on my receiver to get video.

I'm not sure how to time stretch, but I did try "none" as the primary and backup deinterlacer and it got all interlacy (is that even a word?) as expected ;)

Thank you so much, I appreciate all the feedback!

---

### Post by davidstoll on 2008-12-18
> **novellahub said:**
> Do not combine them.  Add the line to both of them to look like this:

```

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    Option         "UseEvents" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    Option         "UseEvents" "True"
EndSection

```


I'll add those tonight when I get home.  By the way, what does it do?   And just out of curiosity can it be added through the Nvidia GUI or other windowed interface?

Thank you for your suggestions!

---

### Post by novellahub on 2008-12-18
> **davidstoll said:**
> I'll add those tonight when I get home.  By the way, what does it do?   And just out of curiosity can it be added through the Nvidia GUI or other windowed interface?

Thank you for your suggestions!

See these threads on the Knoppmyth forum for more info:

[http://knoppmyth.net/phpBB2/viewtopic.php?t=13550](http://knoppmyth.net/phpBB2/viewtopic.php?t=13550)

[http://knoppmyth.net/phpBB2/viewtopic.php?t=18119](http://knoppmyth.net/phpBB2/viewtopic.php?t=18119)

There is no gui way to enter it. I used nano to edit and change the xorg.conf file.

---

### Post by davidstoll on 2008-12-19
> **novellahub said:**
> See these threads on the Knoppmyth forum for more info:

[http://knoppmyth.net/phpBB2/viewtopic.php?t=13550](http://knoppmyth.net/phpBB2/viewtopic.php?t=13550)

[http://knoppmyth.net/phpBB2/viewtopic.php?t=18119](http://knoppmyth.net/phpBB2/viewtopic.php?t=18119)

There is no gui way to enter it. I used nano to edit and change the xorg.conf file.

It doesn't look like it's making any difference.  Although the CPU usage may be a bit lower.

---

### Post by newlinux on 2008-12-19
> **davidstoll said:**
> 

I'm not sure how to time stretch, but I did try "none" as the primary and backup deinterlacer and it got all interlacy (is that even a word?) as expected ;)

Thank you so much, I appreciate all the feedback!

Time stretch is in the OSD while playing video back (audio stretch or something) press m to get to the OSD during playback. I didn't expect turning off interlacing to make the picture look good, what I wanted to find out is if the when you turned off deinterlacing did the original problem still exist? 

And examining the logs after each change is very useful for others to help you debug. We only need to parts when you are playing back video. There are a lot of possible variables, especially if you have been tinkering.

Also, while continuing to use your analog for sound, try changing you output device to ALSA:hw:0,0 and disabling dolby digital and DTS pass through.

We can troubleshoot your passthrough problems separately.

Also you can turn bob deint back on, but make sure the second deinterlacer is something simple to fall back to (like kernel, or one field)

---

### Post by davidstoll on 2008-12-20
> **newlinux said:**
> Time stretch is in the OSD while playing video back (audio stretch or something) press m to get to the OSD during playback. I didn't expect turning off interlacing to make the picture look good, what I wanted to find out is if the when you turned off deinterlacing did the original problem still exist? 

And examining the logs after each change is very useful for others to help you debug. We only need to parts when you are playing back video. There are a lot of possible variables, especially if you have been tinkering.

Also, while continuing to use your analog for sound, try changing you output device to ALSA:hw:0,0 and disabling dolby digital and DTS pass through.

We can troubleshoot your passthrough problems separately.

Also you can turn bob deint back on, but make sure the second deinterlacer is something simple to fall back to (like kernel, or one field)

When playing the video time-stretched, it does seem to be better.

ALSA:hw:0,0 does work!  I tried 0,2 because I read it somewhere...why didn't I try 0,0?  Anyway, I'm getting audio on the TV through HDMI and (whatever audio format) is passing through to the receiver through the optical out (on the TV), so, it is passing something, I just don't know if it's DTS.  My mobo has optical and coax out and they don't seem to be outputting anything right now, but it's definitely a step in the right direction!

I've also attached the latest log files for anyone's enjoyment to see how things are looking.

---

### Post by SyvanX on 2008-12-20
Alright, I read through the posts and I didn't see any mention of XvMC.  That offloads much of the mpeg2 video processing to your video card.  My hardware is much worse than yours and I'm running at 1024x768 right now.  My Xorg process uses about 4% CPU and my Mythfrontend about 20%.

[http://www.mythtv.org/wiki/index.php/XvMC#NVIDIA_2](http://www.mythtv.org/wiki/index.php/XvMC#NVIDIA_2)

You already have the proprietary driver installed, you just need a few edits with nano.  You'll need to modify the actual xorg.conf file directly, the nvidia settings manager won't add the correct options.  Make sure to save a backup!

Best of luck

Here's the relevant parts of my xorg.conf

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 LE"
    Option "UseEvents" "true"
    Option "XvmcUsesTextures" "false"  # necessary for color Chromakey OSD)
    Option "NVAGP" "1"                 # some users report 2 or 3 works better
EndSection
```
```

Section "Extensions"
      Option "Composite" "Disabled"
 EndSection
```

---

### Post by davidstoll on 2008-12-20
> **SyvanX said:**
> Alright, I read through the posts and I didn't see any mention of XvMC.  That offloads much of the mpeg2 video processing to your video card.  My hardware is much worse than yours and I'm running at 1024x768 right now.  My Xorg process uses about 4% CPU and my Mythfrontend about 20%.

[http://www.mythtv.org/wiki/index.php/XvMC#NVIDIA_2](http://www.mythtv.org/wiki/index.php/XvMC#NVIDIA_2)

You already have the proprietary driver installed, you just need a few edits with nano.  You'll need to modify the actual xorg.conf file directly, the nvidia settings manager won't add the correct options.  Make sure to save a backup!

Best of luck

Here's the relevant parts of my xorg.conf

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 LE"
    Option "UseEvents" "true"
    Option "XvmcUsesTextures" "false"  # necessary for color Chromakey OSD)
    Option "NVAGP" "1"                 # some users report 2 or 3 works better
EndSection
```
```

Section "Extensions"
      Option "Composite" "Disabled"
 EndSection
```

I'll give this a try, but I have two "Device" sections in my xorg.conf file.  Do I add it to both?  I was told previously that it would not be a good idea to combine them...but maybe I should make a third "Device" section?  What do you guys think?  Also, I don't have the "Extensions" section, so I assume it will be ok to just add it.

---

### Post by SyvanX on 2008-12-20
I only added it to Device0.  Also, make sure you select a playback profile that uses XvMC (Setup > TV Settings > Playback > page 3 of 9).  CPU-- will do it, but I  made a new Playback profile with only 1 entry (Add New) so I could tweak the settings:

> Match Criteria >= W: 0 H: 0

Decoder: Standard XvMC     Max CPUs: 1     Loop (unchecked)
Video Renderer: xvmc-opengl     OSD Renderer: chromakey

I'm not using a deinterlacer, but you can give a few a try.

I wouldn't merge the Devices in your xorg.conf.  Only work with the one that names your video card, mine specifically references a GeForce 6200.  If both do, try to figure out which Screen section controls the TV, and see what device that section references.  I've broken my X config enough times to know not to try anything unnessary.  Again, don't forget to make a quick copy of the file in case you can't restart gdm.

Once you have XvMC configured, you can restart the window manager with:

```
sudo /etc/init.d/gdm restart
```

If it worked correctly you should see an nvidia logo at the moment gdm restarts and it's also likely your OSD popups will be grayscale.  You can change this, but chromakey gives the best performance.

Let me know if anything doesn't work quite right.

---

### Post by davidstoll on 2008-12-20
> **SyvanX said:**
> Alright, I read through the posts and I didn't see any mention of XvMC.  That offloads much of the mpeg2 video processing to your video card.  My hardware is much worse than yours and I'm running at 1024x768 right now.  My Xorg process uses about 4% CPU and my Mythfrontend about 20%.

[http://www.mythtv.org/wiki/index.php/XvMC#NVIDIA_2](http://www.mythtv.org/wiki/index.php/XvMC#NVIDIA_2)

You already have the proprietary driver installed, you just need a few edits with nano.  You'll need to modify the actual xorg.conf file directly, the nvidia settings manager won't add the correct options.  Make sure to save a backup!

Best of luck

Here's the relevant parts of my xorg.conf

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 LE"
    Option "UseEvents" "true"
    Option "XvmcUsesTextures" "false"  # necessary for color Chromakey OSD)
    Option "NVAGP" "1"                 # some users report 2 or 3 works better
EndSection
```
```

Section "Extensions"
      Option "Composite" "Disabled"
 EndSection
```


Well, I must say, it made a HUGE difference in the CPU usage.  Unfortunately, I am still having that same issue.

One thing I noticed in doing all this testing.  Currently all 4 major channels are showing in HD.
CBS - 1080i
NBC - 1080i
FOX - 720p
ABC - 720p

I'm only having the problem on the ABC station at this moment.  I'm going to keep an eye out on that.

The Fox show does not appear to have the same bandwidth coming through as the ABC station.  (Does that make sense?).

Is it possible it is the recording engine?  Realistically, when I am watching live tv, it's actually recorded because it is buffered a few seconds.  I'm wondering if the recording engine or something relating to that is causing the....fast, slow, fast slow....problem.

I'm going to try to find out if there is a way I can reduce the bitrate of the recording...or something along those lines.

---

### Post by SyvanX on 2008-12-20
That could definitely be another problem.  You can reduce the bitrate in Setup > TV Settings > Recording Profiles.  

Mine says MPEG-2 Encoders since I'm on a couple PVR-150s, but I'm not sure how the HD-homerun options work.  I'm sure MythTV can set them though.
For me, the third page in the recording profile has a bitrate and max-bitrate slider you can adjust.

By the way, how do you like the HD homerun?  Other than the stuttering ;)  I've been thinking about getting one.

---

### Post by SyvanX on 2008-12-20
I was also thinking, if your CPU usage is lower (less than 100% total?), you might want to go back to the frontend logs to see why the video is still stuttering.  You might want to check that you still have some of the audio buffering and video syncing options enabled.  I have OpenGL vertical sync checked but not extra audio buffering or video as timebase.

I was also having a weird problem with stuttering when I changed the MythTV volume that only went away when I got the right combination of XvMC settings.

---

### Post by davidstoll on 2008-12-20
> **SyvanX said:**
> That could definitely be another problem.  You can reduce the bitrate in Setup > TV Settings > Recording Profiles.  

Mine says MPEG-2 Encoders since I'm on a couple PVR-150s, but I'm not sure how the HD-homerun options work.  I'm sure MythTV can set them though.
For me, the third page in the recording profile has a bitrate and max-bitrate slider you can adjust.

By the way, how do you like the HD homerun?  Other than the stuttering ;)  I've been thinking about getting one.

Actually, I just used mplayer to play a recording that has that stuttering and mplayer played it perfectly smooth.  So, I guess it's not the recording engine/bitrate.

Maybe I should just have mplayer playback the live tv recordings or live tv...is that even an option?  That would probably totally fix my problem.  I already gave up on the internal DVD player and set it to use mplayer and haven't had the stuttering on on DVD's any more.

The HD Homerun is really great.  It saves space inside my machine rather than buying two HD cards.  I love it.  In fact, I may buy another one.  I have another machine and I would like to watch live tv, but I don't want it to fight with my Myth box.  I also don't really need 2 more tuners, but 1 more would be great.  So I can get one more HD Homerun and assign one to Myth (so it has 3) and one to my other PC so I can just watch TV while I work.

My HDHomerun profile doesn't have a slider for quality...not that I can see.  It's just the name of the profile,  My PVR-500 does have a slider, but that's for analog cable, so that won't help me for this issue, but it's good to know that it's there.

---

### Post by davidstoll on 2008-12-20
> **SyvanX said:**
> I was also thinking, if your CPU usage is lower (less than 100% total?), you might want to go back to the frontend logs to see why the video is still stuttering.  You might want to check that you still have some of the audio buffering and video syncing options enabled.  I have OpenGL vertical sync checked but not extra audio buffering or video as timebase.

I was also having a weird problem with stuttering when I changed the MythTV volume that only went away when I got the right combination of XvMC settings.

After your settings, I'm around 20%.  Whereas before, I was around 50%.

I've tried those other settings (extra audio buffering, video as timebase), but none of that made a difference.  Although, I might try again now that my CPU usage is lower.

---

### Post by davidstoll on 2008-12-22
> **davidstoll said:**
> After your settings, I'm around 20%.  Whereas before, I was around 50%.

I've tried those other settings (extra audio buffering, video as timebase), but none of that made a difference.  Although, I might try again now that my CPU usage is lower.

No luck, still jerky with the internal player.
Mplayer, xine, VLC all play it fine.

---

### Post by whosmatt on 2008-12-22
> **davidstoll said:**
> If anyone can help me with my jerky/stuttery video problem.  I'll send them $20 via paypal.

Here is my hardware:
2.6 GHz Quad core Intel
Gigabyte GA-EP35-DS3L LGA 775 Intel P35 ATX Intel mobo
8400 Nvidia (DVI & HDMI)
4GB 1066Mhz Corsair Dominator ram
1 SATA 3.0MB/s 7200 drive for 64bit OS
1 SATA 3.0MB/s 7200 drive for recordings
1 IDE DVD rom
Silicon Dust HD Homerun (over the air antenna)
Hauppauge WinTV-PVR-500MCE PCI (SD cable)

The video is jerky and stutters.  It also seems to go fast, slow, fast, slow when there is extra movement on the screen.  Not a huge speed change (fast, slow, fast, slow), but it is annoying.  I am not re-encoding the video and I do not want to.  I have tried different playback profiles CPU+, CPU++, High Quality, etc...

The problem is more noticeable on HD content than on SD, but it happens on SD also.  This happens on Live or recorded content.  I was also having problems playing videos on optical disks, but "sort of" solved it by making mplayer the default video playback device.  DVD playback within MythTV is also jettery...slow, fast, slow, fast.

The solution I'm looking for is a "setting"...not using mplayer as a work-around.  I don't want to buy a better video card or something else.  I want to use the hardware that I have.  I'm looking to tweak the settings.

The giving of the reward is left up to my discretion, but I will absolutely pay it if someone can help me fix it (with no extra hardware cost).  I am a linux noob, so speak slowly.  ;)

Thanks!

Is it always jerky?  I have what i think might be a similar problem that happens more often during commercials on digital channels but also affects certain recordings from my digital tuner.  It seems like the audio and video get terribly out of sync, and the video speeds up or slows down to catch up, but never really does.

It's not a CPU thing; the CPU never tops about 50%.  I have found CPU++ profile to be the best but still not perfect; other profiles are generally unusable as the audio and video stutter make it impossible to watch.

system is 8.10 x64, Prescott 3.0 GHz, 1.25GB RAM, Nvidia Geforce 7300LE with newest drivers available via 'restricted drivers' connected to 720p LCD via VGA cable
PCHDTV 5500 digital tuner and Hauppauge PVR-150 analog tuner. I should note that the analog content has no problems whatsoever.

I am watching this thread closely.

---

### Post by newlinux on 2008-12-22
if it only happens with live tv and not recordings it could be a disk speed problem. what filesystem are you using? have you run some disk speed tests? Again, always posting your frontend logs after each change you make can help when others aren't at the computer to troubleshoot with you. I've had similar problems and that is how i narrowed it down on each of my frontends, which all have different playback settings even though they are viewing the same files...

---

### Post by whosmatt on 2008-12-22
> **davidstoll said:**
> 

My HDHomerun profile doesn't have a slider for quality...not that I can see.  It's just the name of the profile,  My PVR-500 does have a slider, but that's for analog cable, so that won't help me for this issue, but it's good to know that it's there.


Digital tuners aren't actually encoding anything; since the content is already digital, all it has to do is tune it and stream it to disk.  Hence no quality settings.

-M

---

### Post by davidstoll on 2008-12-23
> **newlinux said:**
> if it only happens with live tv and not recordings it could be a disk speed problem. what filesystem are you using? have you run some disk speed tests? Again, always posting your frontend logs after each change you make can help when others aren't at the computer to troubleshoot with you. I've had similar problems and that is how i narrowed it down on each of my frontends, which all have different playback settings even though they are viewing the same files...

My HDD's are new SATA 3.0 MB/s, although, if there is a problem, it could be the bus.  I've never run a speed test on the drives, but what would you suggest?

However, I don't think it's a throughput or HDD problem because mplayer, xine & vlc can play the mpg file without stuttering, while the internal player stutters on the same file.

---

### Post by newlinux on 2008-12-23
Yes, but if it is live tv, the internal player is reading while it is writing whereas the other players aren't, hence my question if it only happens with livetv.

you can use hdparm to do some simple tests.
```

sudo hdparm -tT /dev/<device>

```
where <device> is the disk you are testing... which you can find out with:
```

df -h

```

---

### Post by newlinux on 2008-12-23
and what filesystem are you using? speed of reading/writing to disk has a lot more variables than  the rated speed of your drive. Just something to rule out...

---

### Post by davidstoll on 2008-12-23
> **newlinux said:**
> Yes, but if it is live tv, the internal player is reading while it is writing whereas the other players aren't, hence my question if it only happens with livetv.

you can use hdparm to do some simple tests.
```

sudo hdparm -tT /dev/<device>

```
where <device> is the disk you are testing... which you can find out with:
```

df -h

```

I apologize, I thought I was clear when I said mplayer, xine & vlc play recorded files just fine when the internal player does not.  So, no it's not just with live TV.  I had the problem with DVD's, but gave up and just changed to mplayer for playing DVD's.

I also set a show to record and it was stuttering as I played it.  So, I escaped out of watching it, but I let it keep recording in the background, ATL-TAB'ed out and played the mpg file (that is actively being recorded to) with mplayer...no problem...played perfectly.

/dev/sdb1:
 Timing cached reads:   9254 MB in  2.00 seconds = 4632.09 MB/sec
 Timing buffered disk reads:  320 MB in  3.01 seconds = 106.49 MB/sec

/dev/sda2:
 Timing cached reads:   8994 MB in  2.00 seconds = 4501.59 MB/sec
 Timing buffered disk reads:  274 MB in  3.00 seconds =  91.25 MB/sec

sda2 is my os drive and sdb1 is my drive for recordings only.

I did try to move live tv to the os drive, but it didn't help.

---

### Post by newlinux on 2008-12-23
No these are plenty fast read times... That's not it. Well, at least we eliminated that variable...

---

### Post by davidstoll on 2008-12-23
> **newlinux said:**
> No these are plenty fast read times... That's not it. Well, at least we eliminated that variable...

So, I take it that it's not even possible to use mplayer (or some other player) to play live tv or recorded tv through myth?

---

### Post by newlinux on 2008-12-24
> **davidstoll said:**
> So, I take it that it's not even possible to use mplayer (or some other player) to play live tv or recorded tv through myth?

Nope...

---

### Post by davidstoll on 2008-12-26
Does anybody have any other ideas?

I'm desperate.  I can't be the only one out there with this issue.  My machine is very well powered and I know I can play the videos with other players and it works fine, so, in my mind, it has to be the internal myth player (i.e. a bug of some sort?) or a setting that I'm overlooking.

---

### Post by SyvanX on 2008-12-26
Did you post recent frontend logs?  I wasn't able to find them.

Are you still getting that same audio message?  Maybe there's something simpler at the heart of this problem.

---

### Post by newlinux on 2008-12-26
The only way I could troubleshoot this is if you post relevant sections of the logs after changes to pinpoint the problem. This shows how the system is reacting to different changes and helps. As I mentioned, I've had these types of problems on a couple different frontends, some were fixed by using a different filesystem, others by making custom playback profiles - which I could only pinpoint by trial and error and examining the logs after changes (small tests of change).

---

### Post by davidstoll on 2008-12-26
I searched through the log files and I don't see where I played a particular show that gives me problems (Polar Express).  I don't fully understand the log files and how/when certain things are captured.

But anyway, here are the latest.

---

### Post by ruminant1 on 2008-12-26
I am having the exact problem on an ATI (780g) based system.  I didn't see the problem in myth 8.04, but it showed up after a clean install of 8.10.  Playing HD recordings from the frontend shows intermittent freezes while playing the exact same video from a terminal with mplayer works fine.  

I've tried just about all the options in myth (vsync, deinterlacers, decoders) and they make no discernible difference.

I'm very frustrated by this problem.  It's pretty much a deal breaker on Intrepid;  I'm thinking about reinstalling Hardy.

---

### Post by SyvanX on 2008-12-27
> **davidstoll said:**
> I searched through the log files and I don't see where I played a particular show that gives me problems (Polar Express).  I don't fully understand the log files and how/when certain things are captured.

But anyway, here are the latest.

How often are your freezes?

I noticed some prebuffering pauses, which are what I see when my video has stuttered.  Do these times look at all familiar, or are you getting stuttering more often?

```

2008-12-26 11:04:55.143 NVP: prebuffering pause
2008-12-26 11:13:21.280 NVP: prebuffering pause
2008-12-26 11:14:52.432 NVP: prebuffering pause
2008-12-26 11:29:08.071 NVP: prebuffering pause
2008-12-26 11:42:20.125 NVP: prebuffering pause
2008-12-26 11:47:14.476 NVP: prebuffering pause
2008-12-26 12:11:20.668 NVP: prebuffering pause
2008-12-26 12:15:41.650 NVP: prebuffering pause
2008-12-26 12:15:41.701 NVP: prebuffering pause
2008-12-26 12:17:29.182 NVP: prebuffering pause
2008-12-26 12:17:29.227 NVP: prebuffering pause
2008-12-26 12:19:05.027 NVP: prebuffering pause
```

Below are some new other errors I noticed.  This seems to be a very common in your logs.  From what I read, these errors are related to poor signal quality of the stream.  

```

2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 40
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 41
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 42
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 43
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 44
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 34 38
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]invalid mb type in P Frame at 47 39
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 37 40
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 31 41
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 52 42
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 27 43
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 29 44
2008-12-26 13:42:41.056 [mpeg2video @ 0x7f6fa794de90]slice mismatch
2008-12-26 13:42:41.057 [mpeg2video @ 0x7f6fa794de90]mb incr damaged

```

Are you splitting the cable into the HDHomerun?

---

### Post by davidstoll on 2008-12-28
> **SyvanX said:**
> How often are your freezes?

I noticed some prebuffering pauses, which are what I see when my video has stuttered.  Do these times look at all familiar, or are you getting stuttering more often?

```

2008-12-26 11:04:55.143 NVP: prebuffering pause
2008-12-26 11:13:21.280 NVP: prebuffering pause
2008-12-26 11:14:52.432 NVP: prebuffering pause
2008-12-26 11:29:08.071 NVP: prebuffering pause
2008-12-26 11:42:20.125 NVP: prebuffering pause
2008-12-26 11:47:14.476 NVP: prebuffering pause
2008-12-26 12:11:20.668 NVP: prebuffering pause
2008-12-26 12:15:41.650 NVP: prebuffering pause
2008-12-26 12:15:41.701 NVP: prebuffering pause
2008-12-26 12:17:29.182 NVP: prebuffering pause
2008-12-26 12:17:29.227 NVP: prebuffering pause
2008-12-26 12:19:05.027 NVP: prebuffering pause
```

Below are some new other errors I noticed.  This seems to be a very common in your logs.  From what I read, these errors are related to poor signal quality of the stream.  

```

2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 40
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 41
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 42
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 43
2008-12-26 13:39:17.908 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 0 44
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 34 38
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]invalid mb type in P Frame at 47 39
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 37 40
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 31 41
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 52 42
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 27 43
2008-12-26 13:41:05.649 [mpeg2video @ 0x7f6fa794de90]ac-tex damaged at 29 44
2008-12-26 13:42:41.056 [mpeg2video @ 0x7f6fa794de90]slice mismatch
2008-12-26 13:42:41.057 [mpeg2video @ 0x7f6fa794de90]mb incr damaged

```

Are you splitting the cable into the HDHomerun?

You are probably seeing where I had some windy days and my "barely" strong enough signals were cutting in and out.  I've also been moving my antenna around to find the sweet spot for my channels.

I do get skipping (or cut outs) if my signal is weak.  But I'm talking about a good signal.  If normal playback is 1X, I get some shows to playback (live or recorded) like this...

1.1x (.5 seconds)
0.9x (.5 seconds)
1.1x (.5 seconds)
0.9x (.5 seconds)
repeat

fast, slow, fast, slow...
I don't get that problem if I play the file with mplayer, vlc or xine.  Only the internal player.  I usually only watch my HD channels, but it's safe to say it doesn't happen on my analog cable or non HD channels over the air.

---

### Post by SyvanX on 2008-12-30
I forgot about the other apps playing back just fine...

Ok, I have another idea for you to try.  I started noticing I was getting some prebuffering pauses watching recordings in progress, which should be analogous to live tv.  Anyway, after digging around google for a while, I stumbled upon a mailing list that suggested turning off "sync to vblank" in the driver settings.

So try going into the nvidia-settings app and un-selecting all of the options for syncing to vblank.  I think there are 3.  Anyway, hope it works for you.

---

### Post by davidstoll on 2008-12-30
> **SyvanX said:**
> I forgot about the other apps playing back just fine...

Ok, I have another idea for you to try.  I started noticing I was getting some prebuffering pauses watching recordings in progress, which should be analogous to live tv.  Anyway, after digging around google for a while, I stumbled upon a mailing list that suggested turning off "sync to vblank" in the driver settings.

So try going into the nvidia-settings app and un-selecting all of the options for syncing to vblank.  I think there are 3.  Anyway, hope it works for you.

I have tried to mess with those before, but decided to try again with a reboot....no luck.
I only saw 2 locations for vsync to black.

---

### Post by uncle hammy on 2008-12-31
Thre are 3...

2 in XServer XVideo Settings
1 in OpenGL Settings

---

### Post by davidstoll on 2009-01-01
> **uncle hammy said:**
> Thre are 3...

2 in XServer XVideo Settings
1 in OpenGL Settings

I only have one in each.

---

### Post by uncle hammy on 2009-01-02
IN XServer  XVideo Settings,  you don't have a "Sync To VBlank" under the "Video Texture Adapter" section, then a "Sync To VBlank for Display Device" unde the "Video Blitter Adapter Settings"?

---

### Post by davidstoll on 2009-01-02
> **uncle hammy said:**
> IN XServer  XVideo Settings,  you don't have a "Sync To VBlank" under the "Video Texture Adapter" section, then a "Sync To VBlank for Display Device" unde the "Video Blitter Adapter Settings"?

I have one under XServer Xvideo Settings and one under OpenGL Settings.

I only have those two as far as I can see.

---

### Post by mjc7373 on 2009-01-04
I just thought you'd like to know that you can purchase tech support for Ubuntu from Canonical, the commercial sponsor of Ubuntu project:

[http://www.canonical.com/services/support](http://www.canonical.com/services/support)

I noticed they have phone tech support for Ubuntu 9 to 5, or 24 hours a day. It's not cheap, but some folks might find this invaluable and the money helps support the Ubuntu project.

---

### Post by fenian on 2009-01-05
What happens if you take out the PVR 500 card and just use the HD Homerun?

---

### Post by davidstoll on 2009-01-05
> **mjc7373 said:**
> I just thought you'd like to know that you can purchase tech support for Ubuntu from Canonical, the commercial sponsor of Ubuntu project:

[http://www.canonical.com/services/support](http://www.canonical.com/services/support)

I noticed they have phone tech support for Ubuntu 9 to 5, or 24 hours a day. It's not cheap, but some folks might find this invaluable and the money helps support the Ubuntu project.

Thank you for that suggestion, but wow, that is really expensive.  Kind of defeats the purpose of going open source.  I could go out and buy a new computer...or at least a new video card...and hope it works better than what I've got.

I also doubt that they would be able to help solve this particular MythTV problem...as I suspect it is more of a Myth problem than it is Ubuntu.

---

### Post by davidstoll on 2009-01-05
> **fenian said:**
> What happens if you take out the PVR 500 card and just use the HD Homerun?

Well, I'm not sure, I guess I could try to pull out that card.  It's kind of a pain to pull it out of my home theater and pull it all apart.

What is your thinking on this?  Because, remember, the videos play fine in VLC, Xine, and mplayer.

---

### Post by fenian on 2009-01-05
My thinking is that maybe the two tuners are fighting each other in Myth,I know of this happening with other card combinations.
When you open a tuner in mplayer (outside of Myth) you are only accessing one tuner however when you start mythfrontend both tuner are made available maybe there is some conflict here.

---

### Post by davidstoll on 2009-01-05
> **fenian said:**
> My thinking is that maybe the two tuners are fighting each other in Myth,I know of this happening with other card combinations.
When you open a tuner in mplayer (outside of Myth) you are only accessing one tuner however when you start mythfrontend both tuner are made available maybe there is some conflict here.

Even during recorded playback?  ...when you are not watching live TV?

My HD Home Run is an external tuner, so do I just unplug it or do I have to go to the backend setup and actually remove it also?

---

### Post by davidstoll on 2009-01-07
> **fenian said:**
> My thinking is that maybe the two tuners are fighting each other in Myth,I know of this happening with other card combinations.
When you open a tuner in mplayer (outside of Myth) you are only accessing one tuner however when you start mythfrontend both tuner are made available maybe there is some conflict here.

No, luck removing the cards.

---

### Post by EasyRiderOnTheStorm on 2009-01-07
Just a stupid question: are you recording into MPEG2-PS or MPEG2-TS (settings->recording profiles)? Could you please try changing to the other option and see if it changes anything...?

---

### Post by newlinux on 2009-01-07
The fact that it doesn't happen at all with mplayer on the same recordings and it happens on liveTV and recordings with the internal player implies to me that it is a playbeck profile/audio setting issue (or a combination of the two). When I've had the stuttered playback that goes fast/slow it was always one of those two issues. your logs seem to indicate that as well. Unfortunately, there are a lot of variables between those two sets (and combinations of settings) so you have to go through them methodically with small tests of change.

> 
Just a stupid question: are you recording into MPEG2-PS or MPEG2-TS (settings->recording profiles)? Could you please try changing to the other option and see if it changes anything...?


Those recording profile settinsg only affect hardware analog encoders. Since he has this problem with digital recordings too, I doubt that's the problem

---

### Post by davidstoll on 2009-01-07
> **EasyRiderOnTheStorm said:**
> Just a stupid question: are you recording into MPEG2-PS or MPEG2-TS (settings->recording profiles)? Could you please try changing to the other option and see if it changes anything...?

I not sure of the location that you are referring to, but if you are talking about...

Utilities/Setup...Setup...TV Settings...Recording Profiles...

My HDHomeRun doesn't have that option...in fact, there are no options.  My understanding is that it just dumps the HD (over the air) signal right to a file.  I don't even see settings like that for my analog tuners.

---

### Post by newlinux on 2009-01-07
> **davidstoll said:**
> I not sure of the location that you are referring to, but if you are talking about...

Utilities/Setup...Setup...TV Settings...Recording Profiles...

My HDHomeRun doesn't have that option...in fact, there are no options.  My understanding is that it just dumps the HD (over the air) signal right to a file.  I don't even see settings like that for my analog tuners.

correct. Those codec options are only for analog hardware encoders. You don't get choices with digital recordings - they simply capture the stream as it comes...

---

### Post by EasyRiderOnTheStorm on 2009-01-07
> **newlinux said:**
> correct. Those codec options are only for analog hardware encoders. You don't get choices with digital recordings - they simply capture the stream as it comes...

Well, I warned you it might be a stupid question...

On the other hand, my understanding is that one of the tuners involved is a PVR500 card, which also has the problem, and others seemed to have a fairly similar problem with similar cards (a PVR150 and a PVR250) - see ["Choppy Video on Playback and LiveTV, not with mplayer"]("http://www.gossamer-threads.com/lists/mythtv/users/150926") - where changing said in-existent setting seemed to help. I wouldn't know, I'm using an analog P7131 framegrabber card...

---

### Post by davidstoll on 2009-01-07
> **EasyRiderOnTheStorm said:**
> Well, I warned you it might be a stupid question...

On the other hand, my understanding is that one of the tuners involved is a PVR500 card, which also has the problem, and others seemed to have a fairly similar problem with similar cards (a PVR150 and a PVR250) - see ["Choppy Video on Playback and LiveTV, not with mplayer"]("http://www.gossamer-threads.com/lists/mythtv/users/150926") - where changing said in-existent setting seemed to help. I wouldn't know, I'm using an analog P7131 framegrabber card...

The problem is only with HD.
By the way, my analog card is MPEG2-PS.

---

### Post by newlinux on 2009-01-07
> **EasyRiderOnTheStorm said:**
> Well, I warned you it might be a stupid question...

On the other hand, my understanding is that one of the tuners involved is a PVR500 card, which also has the problem, and others seemed to have a fairly similar problem with similar cards (a PVR150 and a PVR250) - see ["Choppy Video on Playback and LiveTV, not with mplayer"]("http://www.gossamer-threads.com/lists/mythtv/users/150926") - where changing said in-existent setting seemed to help. I wouldn't know, I'm using an analog P7131 framegrabber card...

Understood. It's just my opinion that tuners aren't the problem.

Since he is having the same playback problem with digital and analog recordings, changing recording settings for the hardware analog card won't affect the digital recordings.

In the thread you posted the situation is quite different, despite the title, if you read through it carefully. Thery weren't using any digital encoders. They were using ATI cards for playback, which myth often behaves very strangely with. Myth often behaves badly now with ATI cards, it was much worse back then. Not to mention Linux and myth have come a long way since 2005.

---

### Post by newlinux on 2009-01-07
davidstoll,

When playing back some of this jerky video, try pausing and going into the onscreen menu (press m on the keyboard) and go to video and  reselect the "Detect" deinterlacing mode. Just curious if that does something. If you are only having problems with 720p channels... You can also try the "reverse fields" (I'm doing this from memory, so the details of what to select may be a little different.

Just a shot in the dark...

Also, let me know what playback profile settings you are currently using... I've noticed that sometimes my playback profile changes don't "stick." It's really annoying when I am troubleshooting or tweaking...

---

### Post by newlinux on 2009-01-07
Also, does this only happen on stations while they are playing ac3 content?

[http://ubuntuforums.org/showthread.php?t=918086](http://ubuntuforums.org/showthread.php?t=918086)
or
[http://ubuntuforums.org/showthread.php?t=932926](http://ubuntuforums.org/showthread.php?t=932926)

seem relevant...

---

### Post by bone2006 on 2009-01-07
I'm having the same problem and for me it has something to do with the HDMI passing audio through it.  I researched and researched how to get audio out of audio out of my HDMI cable and after trying everything possible.  I was finally able to get audio out of my HDMI cable.

Today I tried playing an HD movie and I noticed it right away.  I thought it was something to do with my card, everything else under the hood.   Well I went back to an xvid that I played 3 days ago that played crystal clear and when I played it I could see the jerky or more of a line every now and then that came from the top to the bottom.

I'm not sure if you have the same problem or not, but my video was working perfect before I started to mess with things to get my audio settings working via HDMI.  I can't even remember everything I did to get the audio through the HDMI

---

### Post by newlinux on 2009-01-07
Cetainly sounds plausible. Audio issues cause these same symptoms. davidstoll, have you tried playing the videos without using HDMI audio?

---

### Post by davidstoll on 2009-01-08
> **newlinux said:**
> Cetainly sounds plausible. Audio issues cause these same symptoms. davidstoll, have you tried playing the videos without using HDMI audio?

I'm using VGA out with analog stereo out now and I have the same issue.
I also removed all the "passthrough" options and it didn't seem to help.

Remember, I had issues playing back DVD's.  Had the same issue, so I'm thinking it's not a recording card/profile.  Luckily, you can change to an external player.  So, I'm using mplayer to playback DVD's.

Why can't they have that option for live tv?  With Microsoft Winblows, you can play live tv with the HDHomerun tuner using VLC.

I'm almost to the point where I want to reformat and re-install to see what happens.  But I've made so many customizations, I'm not looking forward to all the re-work.

---

### Post by newlinux on 2009-01-08
> **davidstoll said:**
> I'm using VGA out with analog stereo out now and I have the same issue.
I also removed all the "passthrough" options and it didn't seem to help.

Remember, I had issues playing back DVD's.  Had the same issue, so I'm thinking it's not a recording card/profile.  Luckily, you can change to an external player.  So, I'm using mplayer to playback DVD's.

Why can't they have that option for live tv?  With Microsoft Winblows, you can play live tv with the HDHomerun tuner using VLC.

I'm almost to the point where I want to reformat and re-install to see what happens.  But I've made so many customizations, I'm not looking forward to all the re-work.


The internal player uses the playback profiles for dvds too, so that wouldn't rule out playback profiles or audio settings - but I agree it isn't anything to do with configuring the tuners.

 Did you try my previous couple of sugggestions and look at the other threads I posted?

I think the primary reason it forces you to use the internal player for liveTV/recordings is all the background stuff it does and it's use of the database and seektable to keep recordings in sync, commercial detection and skipping an etc. Not justifying, just explaining. It does a lot of different things. Of course in Linux you could use VLC (and mplayer and other apps) to playback liveTV too, you'd just have to do it outside of myth.

---

### Post by rhpot1991 on 2009-01-08
I didn't see this mentioned while I skimmed through the pages.  What version of MythTV are you running?  There was a bug long ago that caused the playback profiles for livetv to be detected incorrectly thus causing the the wrong profile to be used.  It sounds like this may be your issue, if not then forgive me for not reading every post here :)

---

### Post by davidstoll on 2009-01-08
> **rhpot1991 said:**
> I didn't see this mentioned while I skimmed through the pages.  What version of MythTV are you running?  There was a bug long ago that caused the playback profiles for livetv to be detected incorrectly thus causing the the wrong profile to be used.  It sounds like this may be your issue, if not then forgive me for not reading every post here :)

I'm using 64bit MythBuntu 8.10.

---

### Post by davidstoll on 2009-01-09
Ok, so I went back into the previous comments because so many other settings have changed...

Utilities/Setup -> Setup -> TV Setup -> Playback -> Enable OpenGL vertical sync for timing (page 1/9)

This was suggested way back at the beginning and it did not help at all at that time.  But now it does.  I suspect it is a combination of settings, but now the only way I can get it to work poorly is to turn that setting off.  If it's on, I can change the playback profiles and all sorts of other settings, and it plays fine.  Who knows, maybe the update that was installed just a couple of days ago helped too...?

That being said, on a scale of 1-10 (1 being my original problem, and 10 being a live TV feed) I would give it a 8 out of 10.  It's not 100%, but it's SO much better.  In fact, I'm not sure I would have noticed any problem if it had always been this good.

The down side is that now my remote stopped working...but I'll open another thread after I spend some time with it...but that was probably a result of one of the updates.

My problem is...who do I give the money to?  I'll even be willing to up it a little more and split it between a couple of people because they were so helpful.

You guys are the best.  I appreciate all the kind and patient help.

---

### Post by newlinux on 2009-01-09
I don't know if you were considering me for some of the paypal money - but If you were, no thank you. helping people is my way of giving back since I am long past my developer days...

Further playing with the profiles and driver settings might give you an even better picture. You can tweak forever. So many combinations.

---

