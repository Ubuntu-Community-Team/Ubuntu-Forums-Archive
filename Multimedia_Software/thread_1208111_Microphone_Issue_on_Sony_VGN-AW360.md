---
title: "Microphone Issue on Sony VGN-AW360"
date: 2009-07-08
forum: Multimedia Software
---

### Post by lchoate on 2009-07-08
Hello.  First off, big thanks to the Ubuntu community for making such an awesome OS. 

**The issue:**
I have a new Sony Viao VGN-AW360j running Jaunty with ext4. Whoa! is it fast! Anyway, I have a strange Mic issue and my Sx soft keys aren't working yet. Everything else has been great.

My microphone audio channel seems to work, because when I run System->Prefs -> sound and test the mic audio, the level of static is increased with both mic boost and mic vol. Also, when using skype call testing, I can hear my own DTMF tones played back and the static volume changes when using the controls. Same if I try to record a wav. Here is the kicker, the very first time I used skype, it worked. No config needed. After reboots and alsa reloads, still no mic audio. 

I have attempted to upgrade alsa, but I get compile errors and I'm not skilled enought to understand what that is all about. I have read about 20 different threads and blog entries but this mic issue seems to be different than what they all describe. What is interesting is that in the "input" area of alsamixer, it shows two front microphones. I think this may be the problem but cant figure out how to remove the one I think doesn't do anything. Should I? Got any ideas?

So I've been playing with it and here is where I'm at: 

```

lucas@lucas-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```lspci -V says:
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Sony Corporation Device 9040
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at daa00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```Don't know if it helps:
```

lucas@lucas-laptop:~$ dmesg | grep -i dsdt
[    0.000000] ACPI: DSDT BDF09010, 5D9A (r1   Sony     VAIO 20090218 INTL 20051117)
[    0.019911] ACPI: Checking initramfs for custom DSDT
[    0.396831] ACPI: EC: Look up EC in DSDT

```I'm using a sony-laptop module, config is:
```

options snd-hda-intel model=vaio
options xrandr --output LVDS --set BACKLIGHT_CONTROL native
options hci-usb reset=1

```esd.conf looks like:
```
[esd]
# autospawning is not recommended, since it can't really be done
# right.  If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
# was spawn 0 -as =2
auto_spawn=1
spawn_options=-terminate -nobeeps -as 0
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```Some help on this would be fabulous. Thank you in advance,
Lucas

---

### Post by lchoate on 2009-07-29
Well, sadly, not much help from the community, but I was able to get sound properly working. The current community supported Alsa drivers apparently don't support the ALC889 card in the VGN-AW360. 

You will need to go all the way up to alsa 1.0.20, which as of July '09 doesn't have a binary install (no .deb) It took a manual install, here is what I did...

```


cd /usr/src/
mkdir alsa
cd alsa
#get alsa drivers
sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
sudo bunzip2 alsa-driver-1.0.20.tar.bz2 
sudo tar -xf alsa-driver-1.0.20.tar 
cd alsa-driver-1.0.20/
sudo ./configure --with-cards=hda-intel --with-sequencer=yes
sudo make
sudo make install
# this next command was recommended by the ALSA folks, I didn't have a /dev/midi, so
# i cut it out... but I do have a sequencer2, might want to check yours.
# sudo chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi 
sudo chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/sequencer2
cd ..
#get libs...
sudo wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2
sudo bunzip2 alsa-lib-1.0.20.tar.bz2 
sudo tar -xf alsa-lib-1.0.20.tar 
cd alsa-lib-1.0.20/
sudo ./configure ; sudo make ;sudo make install
cd ..
#get utils
sudo wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2
sudo bunzip2 alsa-utils-1.0.20.tar.bz2 
sudo tar -xf alsa-utils-1.0.20.tar 
cd alsa-utils-1.0.20/
sudo ./configure ; sudo make ;sudo make install
#all of these next modules should be on the same line....
sudo modprobe snd-hda-intel ; sudo modprobe snd-pcm-oss ; sudo modprobe snd-mixer-oss ; sudo modprobe snd-seq-oss

```And reboot. 
When I did, my "generic oss mixer" was gone, and replaced with a NvidiaMCP78 HDMI (OSS mixer). The microphone is working now, don't forget to turn up your levels as they are muted by default. The volume is nice and loud now too.

Good luck. I'll be playing with the s-keys soon, so I'll let you know how I fare.

---

