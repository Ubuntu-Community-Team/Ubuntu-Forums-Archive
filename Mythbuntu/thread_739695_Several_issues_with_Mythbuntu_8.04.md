---
title: "Several issues with Mythbuntu 8.04"
date: 2008-03-30
forum: Mythbuntu
---

### Post by dafreak on 2008-03-30
Welll folks I have a few issues with Mythbuntu some major (no sound!!) and some minor (not high enough resolution) so hopefully we can work together and figure them out.

First let me give my system specs

P4 1.4Ghz
768MB RAM
Matrox G450MAX (DVI to HDMI on TV)
Hercules Fortissimo
ATi TV Wonder (two of them)
WD 40GB HDD
Seagate 320GB HDD
Lite ON DVD ROM

External components

Samsung HLS-4266W DLP TV (720p native)
Harmon Kardon AVR-230 receiver


Issues:

1) I get absolutely no sound no matter which application in mythbuntu I'm using while having the sound hooked up via SPDIF output. I know that the card will work in Linux with optical out because I was able to get it work very easily in Linux Media Center when I set it up. I abandoned that distribution because I disliked its interface and for some reason it didn't detect my remote. In any case it looks like it was installed fine from an aplay -l prompt I get:

```

**** List of PLAYBACK Hardware Devices ****
card 0: YMF744 [Yamaha DS-1S (YMF744)], device 0: YMFPCI [YMFPCI]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: YMF744 [Yamaha DS-1S (YMF744)], device 1: YMFPCI - IEC958 [YMFPCI - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: YMF744 [Yamaha DS-1S (YMF744)], device 2: YMFPCI - Rear [YMFPCI - Rear PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have the passthrough enabled in the general settings so I'm not sure what else to do. I have tried setting the device in the general settings for audio to several different ones including /dev/dsp1 and ALSA:default none of which work. I have also followed the instructions in the sound troubleshooting thread including completely removing & re-installing the audio software packages.

2) My TV viewing is dog slow. For some reason I go to TV and it brings up the picture (which looks pretty poor, but I guess that's analog cable on an HDTV) but it goes on an almost frame by frame basis. Now if I was trying to play high def video on this system I could understand as it definitely would not be up to task. However this is just SD which even my old PIII 700 could run quite fine so an even faster processor shouldn't have a single issue. My signal is quite strong as the strength is around 95.

3) I can not view DVDs at all. I go to the option to watch a DVD after I pop it in and it starts playing. I get the first few warning screens and it drops right back to the screen where I select play video from. Not sure what the heck that is about.

4) I can't seem to get my TV to run at its native resolution. Mythbuntu detects it as a plug and play monitor capable of only 640x480. However I know that this monitor is capable of more & higher resolutions. The complete manual for my TV is located [here (PDF file)]("http://downloadcenter.samsung.com/content/UM/200603/20060329093509921_BP68-00586D-01Eng.pdf")and it shows the resolutions that are supported. My TV is hooked up to my video card by way of DVI to HDMI cable btw.

Thanks for all the help folks.

Oh and on a side note should I bother trying to hook up my Comcast Motorola 3412 to my MythTV box or it not worth my time?

---

### Post by laga on 2008-03-30
For items 2 and 3: can you please provide log files? Check the link in my signature for information how to find them.

---

### Post by dafreak on 2008-03-30
I have attached my logfiles and there are several lines that indicate problems to me, problem is that I'm not sure how to fix them. Here are the  ones that I think are causing the problems with the slow video:

```

2008-03-29 20:17:47.886 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-03-29 20:17:47.887 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-03-29 20:17:47.900 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x82d4b10) visual(0x83cb6a0) 
                        XJ_depth(24) WxH(1280x768) bpl(3840)	
2008-03-29 20:17:47.901 VideoOutputXv Error: Failed to create X buffers.
2008-03-29 20:17:48.807 Couldn't load deinterlace filter 
```

And this one indicates the problem with the audio:

```

2008-03-29 20:17:42.479 Opening audio device 'default'. ch 6(2) sr 44100
2008-03-29 20:17:42.479 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-03-29 20:17:42.603 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'

```

And finally here are some lines from DVD playback:

```

WatchingPreRecorded
libdvdread: Encrypted DVD support unavailable.
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdnav: DVD Title: ALIEN2
libdvdnav: DVD Serial Number: 26A4338D
libdvdnav: DVD Title (Alternative): ALIEN2
libdvdnav: Unable to find map file '/home/cpatricca/.dvdnav/ALIEN2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
2008-03-29 22:05:46.118 Opened DVD device at //dev/scd0
	
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1518 ***
*** for info_length % sizeof(uint32_t) == 0 ***

```

That one should be fixable, I just to enable encrypted DVD support. However its kindof silly to do until I get at least the audio issue fixed. Thanks for the help.

Just a quick update. I changed the default mixer from /dev/mixer to ALSA:default. It can open it now but its still having problems, here is what I see in my logfiles now if I try and do something with audio:

```

2008-03-30 13:09:47.114 Opening ALSA audio device 'default'.
2008-03-30 13:09:47.219 Mixer unable to find control Master 2
2008-03-30 13:09:47.220 Mixer unable to find control Master 3
2008-03-30 13:09:47.220 Mixer unable to find control Master 4

```

---

### Post by jbman on 2008-03-30
could be the mixed settings for your sound card. I used to use the ymf744 with no troubles at all

run alsamixer

make sure the ice958 is not muted

---

### Post by dafreak on 2008-03-30
> **jbman said:**
> could be the mixed settings for your sound card. I used to use the ymf744 with no troubles at all

run alsamixer

make sure the ice958 is not muted

Yeah that was the first thing that occured to me. I have run alsamixer and made sure that ice958 is not muted though. I should note though 
that there are three IEC958 settings in alsamixer though for some odd reason. There's an IEC958 (labeled Item IECE958) and an IEC958_A (labeled IECE958 AC97) and finally an IECE958_A (labeled IEC958 AC97 1). The first one is not muted but does not have a volume bar, the second one is not muted and does have a volume bar (at about 80%) and the third one is not muted, has a volume bar but no volume adjustment.

---

### Post by jbman on 2008-03-31
maybe give alsaconf a try and see if it resinstalls the card

---

### Post by dafreak on 2008-03-31
Well it seems that alsaconf is no longer a part of the ubuntu distribution. Its not in any of the alsa packages. I tried compiling it manually but its complaining about a new enough version of libasound not being present. Any other utilities that could be used for the same purpose?

---

### Post by jbman on 2008-03-31
i think its part of alsa-tools, just apt-get that

---

### Post by laga on 2008-03-31
Wrt your video display issue: your video driver doesn't support Xv (or it's not enabled), you need to fix that.

---

### Post by dafreak on 2008-04-01
The problem is that I can't seem to install the drivers. Every time I select my card (Matrox G450) and then restart it comes up with a warning box that I can't even read and goes back to the default vesa driver. I'm also not having much luck finding modelines for my Samsung DLP. Pointers to posts on how to do this would be great as the third party drivers just don't seem to be working.

---

### Post by dafreak on 2008-04-01
Hopefully this information will be useful to other people but I'm still trying to get this all working properly. I still don't have audio however the video is MUCH smoother now. Not quite at the image quality that I want it at but that's improved a good bit as well. What would be the best de-interlacing method to use for image quality? So I haven't found anything additional to do with the sound card, hopefully with some more searching I will but so far no joy. If anybody knows how the Linux Media Center edition goes about setting up a sound card and if its possible to use this tool in Ubuntu it would be great. That was about the only thing I liked about that distribution, how quickly it got my sound setup correctly. 

Here is what I now have for an xorg.conf file, this was constructed after doing some searching for the matrox g450 on these forums. 

```

Section "Files"
   RgbPath "/usr/X11R6/lib/X11/rgb"
   FontPath "unix/:7100"
EndSection
Section "Module"
   Load "dbe"
   Load "extmod"
   Load "fbdevhw"
   Load "glx"
   Load "record"
   Load "freetype"
   Load "type1"
   Load "dri"
   Load "v4l"
EndSection
Section "InputDevice"
   Identifier "Keyboard0"
   Driver "kbd"
   Option "XkbModel" "pc105"
   Option "XkbLayout" "us"
EndSection
Section "InputDevice"
   Identifier "Mouse0"
   Driver "mouse"
   Option "Protocol" "IMPS/2"
   Option "Device" "/dev/input/mice"
   Option "ZAxisMapping" "4 5"
   Option "Emulate3Buttons" "yes"
EndSection
Section "Device"
   Identifier "MATROX G450MAX"
   Driver "fbdev"
   VendorName "Matrox"
   BoardName "G450"
   Driver "fbdev"
   BusID "PCI:1:0:0"
   Option "UseFBDev"
   Option "HWcursor" "no"
   Option "fbdev" "/dev/fb0"
EndSection
Section "Monitor"
   Identifier "Samsung HLS-4266W"
   Option "DPMS" "false"
   Option "UseEdidDpi" "FALSE"
   HorizSync 31.4 - 75.0
   VertRefresh 59.8 - 75.0
EndSection
Section "Screen"
   Identifier "Screen0"
   Device "MATROX G450MAX"
   Monitor "Samsung HLS-4266W"
   DefaultColorDepth 24
     SubSection "Display"
       Depth 16
       Modes "1280x720" "640x480"
     EndSubSection
     SubSection "Display"
     	Depth 24
	Modes "1280x720" "640x480"
     EndSubSection
     SubSection "Display"
     	Depth 32
	Modes "1280x720" "640x480"
     EndSubSection	
EndSection
Section "DRI"
   Mode 0666
EndSection

```

And I've attached my latest Xorg.conf logfile.

---

### Post by dafreak on 2008-04-01
Just a quick update, I have run asoundconf and set my Yamaha card as default. Still no luck in getting audio out of the optical port. Further ideas are appreciated.

---

### Post by jbman on 2008-04-02
create /etc/asound.conf with the following

```

pcm.!default { 
type hw 
card 0 
device 1 
} 

```

---

### Post by dafreak on 2008-04-02
Still not working although I'm going to keep trying different combinations of mixers and default output devices. Right now I have it set to ALSA:default with the passthrough iec958. The mixer is set to default (there's also the option for /dev/mixer, /dev/mixer1,/dev/mixer2) and I have the volume control set to PCM. If anybody has any idea what it should be set to let me know.

---

### Post by jbman on 2008-04-02
i used to have mine set to /dev/dsp

---

### Post by laga on 2008-04-02
Please do not use .doc to post log files. Normal text files work just fine.

Rgarding your issue with audio passthrough: have you tried searching the Ubuntu and the MythTV wikis for a solution?

---

### Post by dafreak on 2008-04-03
> **laga said:**
> Please do not use .doc to post log files. Normal text files work just fine.

Rgarding your issue with audio passthrough: have you tried searching the Ubuntu and the MythTV wikis for a solution?


Yep I have run through the wikis and hadn't found a solution. I did just complete running through the Complete Audio solution thread and this time I got my audio working. Had to find some other solutions posted in the thread and I think I had skipped a step previously but now my audio is working just fine. So the last part for me to get working properly is the resolution for my TV. So far the wikis I've found don't have xorg.conf information for my set. I'm going to continue searching but if anybody knows what the xorg.conf setup for a Samsung HLS-4266W is supposed to look like I'd appreciate some help. The manual on Samsung's website also lists all of the resolutions supported by the se and what the rates should be. I just can't seem to get those same rates to work in my xorg.conf.

---

### Post by jbman on 2008-04-03
my next suggestion is try a different pci slot

---

