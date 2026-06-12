---
title: "VLC: Error messages"
date: 2009-09-05
forum: Multimedia Software
---

### Post by abhilash82 on 2009-09-05
I get the following messages when I run VLC via terminal.

```
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[COLOR="Red"][00000428] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)[/COLOR]
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
[COLOR="#ff0000"][00000428] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)[/COLOR]
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
[COLOR="#ff0000"][00003355] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)[/COLOR]
[????????] x11 video output error: X11 request 42.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
```

Is there something that can be done to prevent this?

---

### Post by cronholio on 2009-09-05
Well, does it seem to play the video correctly or not?

---

### Post by abhilash82 on 2009-09-06
> **cronholio said:**
> Well, does it seem to play the video correctly or not?

The video opens in a separate window and plays correctly but I notice that there are some frames that get skipped sometimes.

---

### Post by cronholio on 2009-09-07
I guess your computer is really too slow to decode the video in time.

---

### Post by abhilash82 on 2009-09-07
The error message clearly states that .. but I am not sure about it.

I am able to run other process in the same machine and I haven't encountered any problems.

Maybe this has to do with the X11 problems in Jaunty.

---

### Post by abhilash82 on 2009-09-07
My system spec is as given in my signature.. Will I have to downgrade from Ubuntu 9.04 to Xubuntu?

---

### Post by abhilash82 on 2009-09-09
I tried deactivating compiz and still I don't get any marked performance improvement.

Upgrading my RAM from 512MB to 1GB help?

---

### Post by rob-ward on 2009-09-09
Upgrading you ram may help but it could also be your HDD that is too slow, what type of HDD have you got?

What is the output of this command?
```
sudo hdparm -tT /dev/yourdrive
```
What type of file are you playing? how long is it? what size is it?

If it is smaller than 250meg then you could try placing it in /dev/shm (ramdrive) and play it from there which would rule out your HDD

---

### Post by Yellow Pasque on 2009-09-09
So you have an Intel 865G IGP? The first thing I would try is allocating more RAM to the video in your BIOS if you have such an option.

> Upgrading my RAM from 512MB to 1GB help?
If you have an AGP slot, you'd probably get more value by adding a video card with its own dedicated memory. It would be a good idea to add system RAM if you can do it without spending too much money. If you have RDRAM, forget about it.

> Will I have to downgrade from Ubuntu 9.04 to Xubuntu?
Xubuntu often doesn't use significantly less resources, because it uses a bunch of GNOME stuff by default. There are better low-resource distros you should search for.

---

### Post by XanTrax on 2009-09-25
I also have this issue and noticed it more in Jaunty using the newest VLC from the repositories.

System Specs:

- AMD 64 x2 Athlon 4000 (2.2 ghz)
- 4 Gigs of RAM (though using 32 bit Ubuntu so only 3.3gb is being used)
- nVidia GeForce 8500 GT (using the recommended restricted drivers)


Any ideas?  Like I said, only noticed this since upgraded Jaunty.  I have tried switching it to X11 output only and it doesnt seem to have much of a difference.

---

### Post by markharding557 on 2009-09-25
do any of you get this in any other software?
this will tell you if it is vlc specific or not.

---

### Post by XanTrax on 2009-09-25
Personally, I havent tried it yet (silly me).  But, dont they all use the same codecs?  In this instance, the "avcodec" decoder so that means, technically speaking, it would encounter the same late video and drop the frames in other applications?

I'll give it a try and let ya know.  Thank you.

---

### Post by ATSystems on 2010-05-14
[FONT=Arial]Hey folks!

Sorry to bump an old thread but I am hitting the same issue, which has frustratingly only appeared since I reinstalled jaunty, there were no issues prior (formatted/reinstalled because I broke my last install and didn't know how to fix it)

I'm a very recent convert from windows and first time Linux user, running a first Gen Mac Mini[/FONT] Core Duo ([specs]("http://www.everymac.com/systems/apple/mac_mini/stats/mac_mini_cd_1.66.html")[FONT=Arial]-everymac.com; note my machine has an Intel 945GM GPU, not a [/FONT]GMA950[FONT=Arial]) with 9.04, and cannot play AVI's in anything but VLC (Mplayer and Movie Player both crash on start unless opened from the CLI). VLC seems to lose the plot and start frame dropping/going choppy in window resolutions greater than ~800x600 and fullscreen. I have also attempted to change output modes in VLC, trying openGL and x11 to no avail. I believe my problem lies with my video drivers. the error I see is as per OP's..
[I]
x11 video output error: X11 request 42.0 failed with error code 8:

[/I]..with the accompanying choppy video, but I have also seen..[/FONT]
[I]
x11 video output error: X11 request 134.19 failed with error code 11:[/I]*[I][FONT=Arial] BadAlloc (insufficient resources for operation)[/FONT]*[/I] 


MPlayer (when opened from the CLI with *mplayer path/to/file.avi)* will start playback, but also shows a continual stream of similar errors..
[I]
X11 error: BadAlloc (insufficient resources for operation)2.2% 2 0 [/I]
[FONT=Arial]
..when running from the CLI. I don't think this problem is codec or player specific. 

I have been trying to find a way to verify that I have the correct drivers installed for the Intel 945GM this thing uses, [/FONT][FONT=Arial]though appears that this chipset may not supported by Jaunty. Having said this, this worked flawlessly before I destroyed my install last week. Additionally, [/FONT][FONT=Arial]the fact I cannot activate visual effects from System > Prefs > Appearance anymore, whereas I could before the rebuild, also leads me to believe it may be a fundamental driver issue. It is not a resource thing, the machine has a gig of memory in it, and no hardware changes have been made between the installs. This thing was breezing along with all visual effects active, no issue with hardware performance here IMO. 

Some other research has also shown me xorg.conf should have entries specific to my GPU, however all I see in the device section is..

[I]Section "Device"
    Identifier    "Configured Video Device"
EndSection[/I]

..and my google-fu is failing to find an answer on what should be here.


**TL;DR**, VLC and other media players are misbehaving after a reinstall of jaunty, I suspect the problem is video drivers due to consistent errors between my media players and other errors seen with the machine, and a potential misconfig in xorg.conf. how can I verify I have the correct drivers installed for this chipset? ([/FONT][FONT=Arial]Intel 945GM), and is there there some sort of lookup table anywhere that tells you how to configure xorg.conf?

TIA guys!
[/FONT]

---

### Post by wayward4now on 2011-03-15
BUMP! Running an Athlon64-3200, 2 Gigs of ram, and I get that same error message with cvlc... using 10.4 Ubuntu, completely updated.

---

### Post by cotcot on 2011-03-22
Confirm the problem with hardware specs in signature. Other players run the HD Xvid clips fine.

---

### Post by emanuel.landeholm on 2011-07-10
Bump!

I also have this problem... There is a stream from a volcano webcam at:
mms://3.efstaleiti.rs.ruv.is/katla

I have problems accessing it from all my ubuntu computers, using vlc or the vlc browser plugin. Same with totem. These are installed or have been installed with Lucid, Maverick, Natty. These computers all have different graphics cards, Xorg version etc.

Symptoms: As soon as a new frame is rendered it quickly gets covered with a black rectangle so you get the barest minimum of a glimpse of the image (quite frustrating!). If I move the window around I can make the tearing less severe but the stream is more or less unwatchable.

---

