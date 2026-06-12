---
title: "MP4 video poor playback...is there a fix?"
date: 2011-03-09
forum: Multimedia Software
---

### Post by tweezak on 2011-03-09
I just bought a Flip Ultra HD. I didn't see a lot of gripes about it on the Ubuntu forums so I thought it probably worked. Well, it connects and transfers files just fine but so far the demo video that comes on the device will not play properly (meerkat). Some players will not recognize it at all and others (Gnome Mplayer, VLC) play it but stall every few seconds and won't recover without intervention.

I made a half-attempt at converting it to an OGG which sort of worked. I don't recall which app I used but more could probably be done to improve the output. As it was the quality was severely degraded and the video still played haltingly.

Just to make sure it wasn't my computer I booted into winduhsXP and tried the video there. It plays fine even with my old copy of Media Player Classic - Home Cinema. That player gave me this information about the file:

General
Complete name                    : C:\DEM00602.MP4
Format                           : MPEG-4
Format profile                   : Sony PSP
Codec ID                         : MSNV
File size                        : 56.2 MiB
Duration                         : 52s 66ms
Overall bit rate                 : 9 048 Kbps
Encoded date                     : UTC 2010-08-16 23:47:54
Tagged date                      : UTC 2010-08-16 23:47:54

Video
ID                               : 1
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 1 frame
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 52s 66ms
Bit rate mode                    : Variable
Bit rate                         : 8 782 Kbps
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16:9
Frame rate mode                  : Constant
Frame rate                       : 30.000 fps
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.318
Stream size                      : 54.5 MiB (97%)
Language                         : English
Encoded date                     : UTC 2010-08-16 23:47:54
Tagged date                      : UTC 2010-08-16 23:47:54

Audio
ID                               : 2
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Codec ID                         : 40
Duration                         : 52s 64ms
Bit rate mode                    : Constant
Bit rate                         : 256 Kbps
Nominal bit rate                 : 64.0 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 44.1 KHz
Resolution                       : 16 bits
Stream size                      : 1.59 MiB (3%)
Language                         : English
Encoded date                     : UTC 2010-08-16 23:47:54
Tagged date                      : UTC 2010-08-16 23:47:54



Any ideas? I'm kinda stuck. If I can't get this sorted in a week I'm shipping this back to Amazon.

Thanks!

Oh, by the way...before giving up I did go to the "comprehensive multimedia guide" sticky in this forum and followed all the instructions for installing codecs, players, and so forth. No errors.

---

### Post by nomko on 2011-03-09
Have you installed all the necessary multimedia packages? Especially ubuntu-restricted and libdvdcss2.

---

### Post by tweezak on 2011-03-10
> **nomko said:**
> Have you installed all the necessary multimedia packages? Especially ubuntu-restricted and libdvdcss2.

Thanks for the reply.

I have installed libdvdcss2 but I don't really have a way of knowing what is "necessary." Is there a recommended list somewhere I can start with?

Also, I saw a thread in the Ubuntu forums that suggested that the player may be using the CPU rather than the GPU for playing video. I changed the settings according to the instructions specifying X11 instead of xv. In fact, I tried every setting and nothing made any difference.

Thanks again.

---

### Post by johntaylor1887 on 2011-03-11
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tweezak on 2011-03-12
> **johntaylor1887 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

Already installed:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Thanks, though. Any other ideas? 

Maybe it's just player settings that I can tweak. I tried switching to xv, X11, etc. with no perceptible change.

I guess it isn't the end of the world because I'm going to need to keep an XP install around for running Google Sketchup anyway. It's just really annoying and kind of inconvenient. After all, I was trying to make life easier by going to the Flip and getting away from a camcorder which required special software and lots of time to render the appropriate file.

Thanks again for helping.

---

### Post by zcartist on 2011-03-12
Maybe try file conversion with winff or avidemux? It may be a funky encoding issue changing to say xvid avi or a plain oldly mpeg may do the trick

---

### Post by no2498 on 2011-03-13
the settings you need to change is in Gnome Mplayer
i forget what i changed to fix mine but its in the player

---

### Post by tweezak on 2011-03-13
> **zcartist said:**
> Maybe try file conversion with winff or avidemux? It may be a funky encoding issue changing to say xvid avi or a plain oldly mpeg may do the trick

We may be onto something. I had installed Avidemux but apparently had not tried it yet. When I open a short video I made I get this message:

"If the file is using B-frames as reference it can lead to a crash or stuttering.
Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY.
Do you want to use that mode?"

The options are "Cancel" and "Use Safe Mode." Whichever method I choose I get smooth playback but it's in slow motion. Also, the sound cuts in briefly about every second. What I suspect is happening is that the video is recorded at 60fps but the player wants to do 30fps.

Not having any experience with this player (and little experience with video/codecs overall) I would appreciate any suggestions. I'm going to start doing different conversions as you suggested to see what I end up with.

Thanks again and keep the ideas coming! I'd love to get this fixed as I don't know of anyone who has a viable solution for the Flip in Linux yet.

---

### Post by SeijiSensei on 2011-03-13
First thing I'd do is install smplayer from the repositories and see how well it works.  smplayer is a nice front-end to mplayer, which will be automatcally installed alongside smplayer.  mplayer shouldn't have a problem with the file you describe.  You shouldn't need any restricted extras either, I don't think, certainly not libdvdcss2 which is for DVD playback.

If you happen to already have mplayer installed, try running "mplayer /path/to/file.mp4" from the command line.

---

### Post by tweezak on 2011-03-13
> **no2498 said:**
> the settings you need to change is in Gnome Mplayer
i forget what i changed to fix mine but its in the player

There are only a couple of tabs in the preferences that could make a difference. I think I've tried about every setting but haven't seen it improve anything yet.

Is there any chance you could go to the Preferences>Player and Preferences>Mplayer tabs and tell me what options you have selected and what boxes are checked?

Pretty please? :D

---

### Post by tweezak on 2011-03-13
Before I go any further on this I'm going to try a different machine.

I have a newer netbook that may work better for this than my old tower. I also may need to change the Nvidia drivers I'm using.

Stay tuned.

---

### Post by tweezak on 2011-03-13
Ok...tried the laptop. Identical behavior.

When I first tried to run the video on the laptop with the default player I got a message that plugins were needed:

MPEG-4 AAC decoder
H.264 decoder

The app searched and found 

gstreamer0.10-ffmpeg
gstreamer0.10-plugins-bad

After installation I got this message:

"The selected packages were successfully installed but did not provide all requested plugins."

---

### Post by tweezak on 2011-03-13
Ok...I think I have a working solution. It's not perfect but it will get me by until I figure out a real fix.

Using PiTiVi I am able to render a 1280x720 video at 60fps (have to use custom settings) and it seems to work really well. It does take a long time (20 minutes for a 11sec video) but it's just something I'll have to live with for now I guess.

In a lot of cases I think I'll be able to reduce the video size or drop the frame rate and save rendering time. Also, most of my family uses winblows or mac so they won't have this problem with files I give them.

I'll keep checking back here to see if anyone posts up player settings that will allow me to play the recordings natively without converting them to something else first. For this reason, I'm not going to mark this thread solved.

Edit: I may have spoken too soon. 720x576 at 60fps plays great. 1280x720 at 30fps plays great. 1280x720 at 60fps plays in stops and starts. I'm re-rendering and trying again but at this point it doesn't look like I can yet have a video of the same quality as the original that I can play...in linux.

---

### Post by tweezak on 2011-03-13
It appears this is my problem:

[http://brainstorm.ubuntu.com/idea/12404/](http://brainstorm.ubuntu.com/idea/12404/)

In a nutshell, there's no GPU acceleration in Linux. The whole load is being dumped to my CPU and it's not capable of running "HD" video.

I'm going to try the VLC guide on implementing GPU acceleration:

[http://wiki.videolan.org/VLC_VAAPI](http://wiki.videolan.org/VLC_VAAPI)

---

### Post by rubylaser on 2011-03-13
You didn't mention your hardware at all.  What are you running? There's Hardware GPU decoding in Linux, for both VDPAU and VAAPI.  I haven't used VAAPI, as all my HTPC's are ION based (VDPAU), but VDPAU allows measily Atom processors to playback just about anything.

---

### Post by tweezak on 2011-03-14
> **rubylaser said:**
> You didn't mention your hardware at all.  What are you running? There's Hardware GPU decoding in Linux, for both VDPAU and VAAPI.  I haven't used VAAPI, as all my HTPC's are ION based (VDPAU), but VDPAU allows measily Atom processors to playback just about anything.

Sorry about that. Up to this point I didn't think hardware was the issue. I was under the impression it was a Linux limitation.

The laptop I'm on right now is an HP Mini 311 with ION (not LE) GPU and Atom CPU.

VDPAU and VAAPI are little more than cryptic acronyms to me. I know even less about how to enable video acceleration.

If you have a link to a guide on how to do it I could really use the assistance.

Thanks!!

---

### Post by rubylaser on 2011-03-14
Have you installed the NVIDIA driver for your card?
**32 bit**
[http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.44-driver.html)
**64 bit**
[http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html](http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html)

If you haven't you'll need to download the file from above, then open a terminal.
```
sudo apt-get install build-essential
```
```
sudo chmod +x NVIDIA-Linux-x86-260.19.run
sudo ./NVIDIA-Linux-x86-260.19.run
```
The version numbers above could be wrong, so you will need to change it to suit.  After it's done, you'll need to reboot.

If you have the NVIDIA driver installed already (or from the repositories), I'd personally use mplayer with the smplayer frontend as it supports VDPAU (what your ION uses) out of the box.

---

### Post by rubylaser on 2011-03-14
Here are some easier directions to follow if you're so inclined :)
[http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html](http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html)

---

### Post by tweezak on 2011-03-14
> **rubylaser said:**
> Here are some easier directions to follow if you're so inclined :)
[http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html](http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html)

I'll try it as soon as I get a chance.

Thanks a ton!

---

### Post by rubylaser on 2011-03-14
No problem.  Please report back if it works for you.  And mark the thread solved, so others can find the solution (if it does work of course :) )

---

### Post by tweezak on 2011-03-15
> **rubylaser said:**
> No problem.  Please report back if it works for you.  And mark the thread solved, so others can find the solution (if it does work of course :) )


Ok...now I feel really stupid. I guess the reason nobody has been posting problems with this camera is because this was so easy to fix.

Thanks for pointing me in the right direction.

Problem solved!\\:D/

---

### Post by rubylaser on 2011-03-15
Great, glad to hear it:)  Under Thread Tools at the top, you can mark the thread a [SOLVED].

---

### Post by tweezak on 2011-03-29
> **rubylaser said:**
> No problem.  Please report back if it works for you.  And mark the thread solved, so others can find the solution (if it does work of course :) )

So I just tried this on my desktop machine (also Nvidia) and I'm getting the following error:

Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory


I may have fouled something up in all my tweaking. I've tried reinstalling everything listed in synaptic that seems related to VDPAU with no change.

Any suggestions?

BTW...the card is a GeForce 6200 AGP

Thanks!

---

### Post by BicyclerBoy on 2011-03-29
Anything before 8xxx family has no VDPAU capability..

There is no AGP VDPAU video card (AFAIK).
AGP does not have the bandwidth for decoded HD playback.

There is a PCI 9500GT with VDPAU that works okay (feature set B).

The recommended are PCIe GT430, GT240, GT220 (feature set C). These don't have component out options (AFAIK).

BTW
My netbook atom HP mini plays SD (576i) H264 broadcast material okay/watchable with intel i915 driver..
I imagine your video is lower resolution & less compressed..

---

### Post by tweezak on 2011-03-30
> **BicyclerBoy said:**
> Anything before 8xxx family has no VDPAU capability..

There is no AGP VDPAU video card (AFAIK).
AGP does not have the bandwidth for decoded HD playback.

There is a PCI 9500GT with VDPAU that works okay (feature set B).

The recommended are PCIe GT430, GT240, GT220 (feature set C). These don't have component out options (AFAIK).

BTW
My netbook atom HP mini plays SD (576i) H264 broadcast material okay/watchable with intel i915 driver..
I imagine your video is lower resolution & less compressed..


Hmm...I'll have to boot into windows and see what it does.

As far as the HP...Your HP netbook has an intel GPU?
My mini 311 has the atom as the main cpu but the GPU is the Nvidia ION. Therefore I'm using an Nvidia driver with excellent results. I actually chose this netbook because it supports 1080p and has an HDMI port. I want to use it as a media PC. 

Thanks again. I'll let you know how the winduhs test goes.

---

### Post by BicyclerBoy on 2011-03-31
Good choice of netbook..

Mine was a favour-to-help-a-mate purchase , just the crappy intel GPU.
The whole atom (270 330) think is a bad joke. The chipset uses more power than the CPU & a discrete mobile nvidia GPU..

Can't use VDPAU playback for 6200 video card only XVideo OpenGL etc..

---

### Post by tweezak on 2011-04-09
Just by way of an update, I've more or less switched over to my netbook from my old tower. 

I used the HDMI port for video through a DVI adapter to my monitor. I'm extending the desktop which seems to work pretty well but sometimes I have trouble getting windows to go to the display I choose.

Other than that it seems fine.

Audio is handled by plugging my old powered computer speakers into the headphone jack on the netbook. I'm using ethernet instead of wireless while set up in this location. All of my peripherals (keyboard, mouse, ipod, flip camera, etc.) are plugged into a 7 port USB hub which I have plugged into my netbook.

So, 5 plugs total: power, HDMI, ethernet, usb and audio.

FWIW...I tried VGA but it was harder to plug in than HDMI and it didn't seem to produce as clear an image as the HDMI-DVI solution.

All I need now is a USB2 3.5" IDE enclosure to put my 320GB HDD from my old tower in. Does anyone have any recommendations?

Thanks!

---

### Post by BicyclerBoy on 2011-04-09
Funny that the netbook is more capable than the old tower PC..

Just use the tower as a HDD/optical drive enclosure & PSU box..

---

### Post by tweezak on 2011-04-17
> **BicyclerBoy said:**
> Funny that the netbook is more capable than the old tower PC..

Just use the tower as a HDD/optical drive enclosure & PSU box..

Well, we'll have to see if the netbook lasts as long as the tower. I think I built that about 8 years ago. Granted, I've upgraded a few things since then and that's one of the main reasons to go with a desktop...you can work on it yourself. My issue is that my needs are finally exceeding the capabilities of my old architecture (AGP and IDE specifically).

---

