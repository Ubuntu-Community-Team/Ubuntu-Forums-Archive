---
title: "MythTV does not work with HDMI"
date: 2010-05-30
forum: Multimedia Software
---

### Post by jlr4u on 2010-05-30
MythTV Records fine but will not play the recorded shows and I can not watch or open the TV.


Running Ubuntu 10.04 LTS lucid

Runing a pcHDTV HD-5500 Video card
Using on Board Video from an Asus M3A78-EM with onboard ATI Radeoon 3200

dmesg | grep DVB
[   14.461244] cx88[0]/2: cx2388x based DVB/ATSC card
[   14.771709] DVB: registering new adapter (cx88[0])
[   14.771711] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...

My symptoms are as follows:
I can do a manual scan
scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > channels.confvlc
Run VLC and TV channels with audio and video are fine.
After configuting MythTV, I can record a TV show with Mythtv, but can not play back or view TV.  After recording a show with MythTV, I can exit Myth and open the recorded show with VLC and it plays fine.


The mythfrontend log errors look like this:

2010-05-30 16:47:39.404 VideoOutputXv Error: Could not find suitable XvMC surface.
2010-05-30 16:47:39.404 VideoOutputXv Error: Failed to initialize buffers for codec MPEG2 IDCT
2010-05-30 16:47:39.408 VideoOutputXv Error: Could not find suitable XvMC surface.
2010-05-30 16:47:39.408 VideoOutputXv Error: Failed to initialize buffers for codec MPEG2 IDCT
2010-05-30 16:47:39.408 VideoOutputXv Error: Failed to get any video output Exiting playback.
2010-05-30 16:47:39.409 VideoOutputXv Error: InputChanged(): Failed to recreate buffers
2010-05-30 16:47:39.409 NVP(0), Error: Failed to Reinitialize Video. Exiting..
2010-05-30 16:47:39.410 AFD: Opened codec 0x7fac51220790, id(MPEG2VIDEO_XVMC) type(Video)
2010-05-30 16:47:39.410 AFD: codec AC3 has 6 channels
2010-05-30 16:47:39.411 AFD: Opened codec 0x7fac50044d60, id(AC3) type(Audio)
2010-05-30 16:47:39.411 AFD: codec AC3 has 1 channels
2010-05-30 16:47:39.412 AFD: Opened codec 0x7fac51efc150, id(AC3) type(Audio)
2010-05-30 16:47:39.444 NVP(0), Error: Serious error detected in Video Output
2010-05-30 16:47:39.454 Couldn't open decoder for: /var/lib/mythtv/livetv/1021_20100530164738.mpg
2010-05-30 16:47:39.454 NVP(0), Error: Error opening jump program file
2010-05-30 16:47:39.454 NVP(0), Error: JumpToProgram failed.
2010-05-30 16:47:39.454 NVP(0), Error: Unknown recorder error, exiting decoder
2010-05-30 16:47:39.478 NVP(0), Error: Serious error detected in Video Output
2010-05-30 16:47:39.479 VideoBuffers::DiscardFrames(): ERROR, A not in available, pause, or displayed         
2010-05-30 16:47:39.479 VideoBuffers::DiscardFrames(): ERROR, B not in available, pause, or displayed A       
2010-05-30 16:47:39.479 VideoBuffers::DiscardFrames(): ERROR, C not in available, pause, or displayed AA      
2010-05-30 16:47:39.479 VideoBuffers::DiscardFrames(): ERROR, D not in available, pause, or displayed AAA     
2010-05-30 16:47:39.479 VideoBuffers::DiscardFrames(): ERROR, E not in available, pause, or displayed AAAA 

What do I do to get MythTV working?

---

### Post by jlr4u on 2010-06-06
Audio and Video with MythTV resolved....

I never - ever get a response to my questions on the Ubuntu forms.
but since I resolved my issue, I will document how I resolved it so others can benefit.

First run the aplay -l command
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Notice that my HDMI is card 2, device 3.

Create a speaker test command using card 2, device 3 (2,3) and verify that sound works.
```
speaker-test -Dplughw:2,3 -c2
```

You may have to change your sound preferences -- System-Preferences-Sound to set up your HDMI sound card.
Under Hardware - I turned on "Digital Stereo (HDMI) Output
I also had to boot into the System Bios and set-up the audio for HDMI.
Once you get sound from the aplay -l command, then modify Mythtv front end as folllows:

Utilities/Setup- Setup-TV Settings- Playback 
(Hit Enter twice to go to the second screen):
Change "Current Video Playback Profile: To "High Quality"

Next under Utilities/Setup- Setup- General
(Hit Enter three times to go to the third screen):
Change "Audio Output Device" to:ALSA:plughw:2,3
[COLOR="Red"]Note[/COLOR]:You have to enter the field and manually change ALSA:plughw:0,3 to ALSA:plughw:2,3

That's it.  With only 2 MythTV front end settings, I was able to get HDMI both audio and video on an HDTV (LED)

---

### Post by TV Stands on 2010-06-06
My friend has the same problem, I will try your solution and let you know.

---

### Post by jlr4u on 2010-06-06
Thanks --  Please let me know if this helped

---

### Post by terminixer on 2010-07-14
Thanks jlr4u, your post was exactly what I needed.

Last weekend I installed mythtv on 10.4LTS on a Gigabyte AMD motherboard with 785G (Radeon 4200) graphics on a 1920x1200 monitor. With the restricted graphics driver enabled, the mythtv front end would show live tv only for over the air (OTA) channels broadcasting in 1280x720p. When I attempted to tune a station broadcasting in 1920x1080i (for example), I got the error "Failed to Reinitialize Video". I tried all sorts of things, and eventually found that disabling the restricted graphics driver resolved the problem (but, of course, that meant I had to accept the limitations of the nonrestricted driver).

Your post was the only hit that came up when  I googled (the web) "Failed to Reinitialize Video", and at first I didn't think it would apply (since I was not using HDMI and my sound was working fine), but following your advice:

>Utilities/Setup- Setup-TV Settings- Playback 
>(Hit Enter twice to go to the second screen):
>Change "Current Video Playback Profile: To "High Quality"

fixed my problem. I am now able to tune all my OTA channels regardless of broadcast format while using the restricted graphics driver.

So again, thanks a million.

---

### Post by tom purl on 2010-10-01
Thanks a million jlr4u!  This also worked for me, even though I wasn't using HDMI.  My symptoms were that some channels would show, and others would fail with the error messages that you described.

I had moved my mythtv server to a new computer, which had a much more powerful cpu and video card.  Changing the "Video Playback Profile" to "High Quality" made every single channel work.   

Also, I share your frustration when it comes to posting questions that no one answers.  Sometimes, we just have to admit that we have very difficult technical problems that very few people can solve.

Thanks again!

Tom Purl

---

### Post by J.H. on 2010-10-01
This fixed this annoying issue for me also! :KS

>Utilities/Setup- Setup-TV Settings- Playback
>(Hit Enter twice to go to the second screen):
>Change "Current Video Playback Profile: To "High Quality"

---

