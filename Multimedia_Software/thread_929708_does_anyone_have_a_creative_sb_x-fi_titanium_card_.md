---
title: "does anyone have a creative sb x-fi titanium card working?"
date: 2008-09-25
forum: Multimedia Software
---

### Post by badperson on 2008-09-25
`do you use alsa or oss? Is there a how-to that you followed?
thanks, 
bp

---

### Post by Yellow Pasque on 2008-09-25
OSS has added support for PCI-e models recently:
[http://mercurial.opensound.com/?rev=X-fi](http://mercurial.opensound.com/?rev=X-fi)

Here is my guide to building OSS 4.1rc:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by badperson on 2008-09-25
excellent, will try that tonight!
thanks,
bp

---

### Post by badperson on 2008-09-25
I had gone throught that tutorial (thought you linked to something different)

and while my soundcard is detected, I get a red arrow in kmix. 
there is this note:

> kmix
kmix may work with OSS in KDE 3.5.x, but for KDE4, the issue is still unresolved. The bug has been reported. Subscribe to this report to stay abreast of developments. If you know how to build source, install the latest version(s) of the gstreamer plugin packages.

any ideas?
bp

---

### Post by markbuntu on 2008-09-26
You can try recompiling your kernel with a patched driver like in this link but I have seen a report that doing so may kludge your video driver and leave you with a choice of sound or video. Anyway, it is an extremely experimental bleeding edge sort of thing to try. 

Now that you have been properly warned:

[http://ubuntuforums.org/showpost.php...&postcount=675](http://ubuntuforums.org/showpost.php...&postcount=675)

---

### Post by badperson on 2008-09-28
mmmm....I think I may skip that...
I actually think I just need to read up on OSS more; have my soundcard associated with OSS or something. 

thanks,
bp

---

### Post by badperson on 2008-09-28
meant to mention, 
this is my output from the console looking for my soundcard:

```
jason@jason-kubuntu:~$ lspci | grep Audio
07:00.0 Audio device: Creative Labs Unknown device 000b (rev 03)

```

can I configure that in OSS somehow?
bp

---

### Post by PGHammer on 2008-09-28
> **badperson said:**
> mmmm....I think I may skip that...
I actually think I just need to read up on OSS more; have my soundcard associated with OSS or something. 

thanks,
bp

ossxmix is a better alternative to kmix, and works in GNOME as well.

The same tutorial works a treat for PCI-based X-Fi cards as well (I'm listening to "I Remember" in the background via RhythmBox as I type this, playing through my X-Fi XtremeGamer on Ubuntu 8.10/Intrepid Ibex alpha 6).

---

### Post by badperson on 2008-09-29
Does that work in KDE? The docs I saw for OSS say that there's a known bug...

I typed ossxmix on the console, and the gui came up, and it has my sound card listed in the tab title bar. 

this is my output for ossinfo:

```
jason@jason-kubuntu:~$ ossinfo
Version info: OSS 4.1 (b rc1/200809232338) (0x00040090)
Hg revision: changeset: 456:cae33709684b, tag: tip, date: Mon Sep 22 10:16:43 2008 +0300, summary: Make sure mixer names are NULL terminated. Minor changes to osstest
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 (jason-kubuntu)

Number of audio devices:        2
Number of audio engines:        6
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi interrupts=2054 (2054)
    PCI device 1102:000b, subdevice 1102:0043
 2: oss_usb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi output         /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi input          /dev/oss/oss_sbxfi0/pcmin0  (device index 1)
jason@jason-kubuntu:~$

```

In sound settings, for hardware I have Open Sound System selected. 
I still get no audio in amorak or kaffeine. 

thanks, 
bp

---

### Post by badperson on 2008-10-01
is there a media player that works better with oss and/or ossxmix?
bp

---

### Post by Yellow Pasque on 2008-10-01
> **badperson said:**
> is there a media player that works better with oss and/or ossxmix?
bp
Amarok should work (IIRC, you may need to switch it to a gstreamer backend instead of xine).
For testing, try Audacious (get audacious and audacious-plugins from repo). Be sure to go into its preferences (Audio subsection) and change to OSS output.
Are you getting any audio from anything? Does the osstest program work?

---

### Post by Yellow Pasque on 2008-10-01
Sorry for the info about amarok. It doesn't have a gstreamer engine anymore (I was thinking of Phonon). Anyway, I tested Amarok and found it worked just fine for me without configuration.

---

### Post by badperson on 2008-10-02
Hi,

here's what I get from osstest:

> jason@jason-kubuntu:~$ osstest
Sound subsystem and version: OSS 4.1 (b rc1/200809232338) (0x00040090)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/oss_sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi output
- Performing audio playback test...
  <left> Device returned error: Input/output error
/dev/oss/oss_sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi input
- Skipping input only device

*** Some errors were detected during the tests ***
jason@jason-kubuntu:~$                                    

ossmix:

> jason@jason-kubuntu:~$ ossmix
Selected mixer 0/Sound Blaster X-Fi
Known controls are:


play [<leftvol>:<rightvol>] (currently 14.4:14.4 dB)
rec [<leftvol>:<rightvol>] (currently 13.4:13.4 dB)
recsrc <mic|line|video|aux|none> (currently line)
jason@jason-kubuntu:~$


> jason@jason-kubuntu:~$ sudo ossdetect -v
Detected Creative SB X-Fi (PCI-e) *EARLY BETA*
USB support available in the system, adding USB driver
Detected Generic USB audio/MIDI device (BETA)
jason@jason-kubuntu:~$





bp

---

