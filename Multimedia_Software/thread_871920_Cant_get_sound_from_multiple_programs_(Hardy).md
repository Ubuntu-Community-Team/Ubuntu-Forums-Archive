---
title: "Cant get sound from multiple programs (Hardy)"
date: 2008-07-27
forum: Multimedia Software
---

### Post by Striken on 2008-07-27
I've already tried every guide I can find on these forums.
 
I've ran the command:

```
sudo apt-get install alsa-oss
```
 
and added "aoss" to my program launchers, according to the Sticky in this section, but it had no effect whatsoever.
 
I've followed the guide for using PulseAudio on Hardy found here:

[http://ubuntuforums.org/showthread.php?t=776739]("http://ubuntuforums.org/showthread.php?t=776739")
 
but that only resulted in my losing sound altogether.
 
Most guides contain instructions for what appear to be much worse problems then what I have (no sound at all, bad quality sound, etc). My sound works perfectly fine in all my programs individually, including Games (Wine), Flash (Firefox), Movies, and MP3's. I can even use Ventrilo through Wine without any problems. The only problem is that no combination of any two programs allows me to hear sound from both.
 
At the moment, this is what I have in my /etc/asound.conf file in order for my USB Headset to work:

```
pcm.!default {
type hw
card 1
}
ctl.!default {
type hw
card 1
}
```
 
In Preferences>Sound, everything is set to ALSA, and my default mixer is set to Logitech USB Headset (ALSA mixer). When I run the command:

```
alsamixer
```

It opens up pre-set to my USB Headset, with controls for both the speakers and microphone working fine.
 
I'm pretty new to Ubuntu, but it seems that if my sound is already working perfectly, it should be a fairly easy fix to get sound from more then one application, but none of the tips or guides I've seen have worked. Is there anyone out there with any info that I haven't found yet?

---

### Post by markbuntu on 2008-07-27
The problem here is that pulse audio and alsa are fighting for control of the sound device(s). To get them to work together you need to make oss apps use alsa and alsa apps use pulse and pulse go through the alsa drivers.

Anyway, read this through and maybe you can figure some stuff out just from the info below.

First, make alsa the default sound manager. 

Edit etc/libao.conf
```

default_driver=alsa

```

If you have an etc/asoundrc file, put it in the trash. If you previously edited your ~/.asound.conf or ~/.asound.rc file then replace them with the backups you made before you edited them.

Check if you have these packages installed:


AlSA Packages (search alsa)

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

PulseAudio Packages (search pulseaudio)

audacious-plugins-extra
gstreamer0.10-pulseaudio
libpulse0
libpulse-browser0
libpulsecore5
libpulse-mainloop-glib0
padevchooser
paman
paprefs
pavucontrol
pavumeter
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-hal
pulseadio-module-x11
pulseaudio-module-zeroconf
pulseaudio-utils

You should find most of the stuff you need in Applications/Sound and Video but some stuff ends up in System/Preferences.


Open System/Preferences/Default Sound Card and choose pulseaudio. Open System/Preferences/Sound and set all the defaults to ALSA. Default Mixer Tracks to your sound card. You may want to change this a little for your usb stuff.

Open System/Preferences/Multimedia Selector/Audio and set Plugin to ALSA and Device to Default for both Input and Output.

Open the Volume Control and set it to the same as in Sound.

Reboot.

Open the Gnome-alsamixer and you should see sections for your sound card and usb headset. adjust the sliders, check the boxes for mix, etc.

Try to run a few things at once, ie rythmbox and vlc or totem. This does nto work with flash9 but does work with flash10b (not flash10b2). It will work also with oss apps. I have not tried it with jack.

Open Pulse Audio Manager and you should see the Default Source and Default Sink as ALSA......

In the Devices section you can see your individual streams as #1, #2, #28, etc and click on properties to see which plugin is being used and adjust the individual volumes etc.

Try the sound recorder to test the mike and capture, etc.

---

### Post by Striken on 2008-07-28
Thanks for the tips. I already know ALSA is set as my default sound manager, because I changed it back after the PulseAudio guide failed me.
 
I will try the rest of it to see if it helps.

---

### Post by Torgas Prim on 2008-07-30
I am having the same issues with getting multiple progs using sound at the same time.
Be nice to see what comes up after Striken gets his working.
:)

---

### Post by GotNoLife on 2008-12-10
[SIZE="3"]Thank you! ):P[/SIZE]

I had the same problem.
Ubuntu 8.04 Hardy Heron on a IBM/Lenovo laptop.

I had to close what ever program that _had_ played sounds (FF, music programs, VirtualBox, etc) to get sounds working in an other.. Dont know how many things I've tried or how many forums i've been through and banged my head in whatever closest cause it didnt work.. ](*,)

I had no idea it would be so darn simple.. :)

---

### Post by frogotronic on 2009-01-07
I followed the instructions and I have no discovered sound servers via the Pulse audio applet, BUT multiple programs and multiple sounds now work.

Thanks

--------------------

whoops, my mistake - ALSA shows up 


MANY THANKS

---

### Post by frogotronic on 2009-01-07
One more issue, can't get sound back after suspend...any thoughts?

Was working before...

---

### Post by markbuntu on 2009-01-07
I wrote that a long time ago. I have more up to date guides for both Hardy and Intrepid here

The quick guide:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

The totally comprehensive guide.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The no sound after suspend is a long running headache that I have yet to see a comprehensive solution to. If I ever do, I will put it in the guides. If you come across one let me know by posting in either thread above.

---

