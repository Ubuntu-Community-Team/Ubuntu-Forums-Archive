---
title: "Sound cards nothing but trouble in 8.04"
date: 2009-10-15
forum: Multimedia Software
---

### Post by mysticofjesus on 2009-10-15
After failing to get Nvidia drivers working under Ubuntu 9.04, I've successfully installed 8.04 x64 on my desktop. Everything works great, except for the sound. Now, I have two sound cards: the built in Nvidia ALC882, and a M-Audio Fast Track USB, which is what I'd prefer to use.

The Fast Track works great for playing music, but system sounds and network streaming are silent.

The ALC882 does *something* any time a sound ought to be played, but it's garbled and glitchy every time.

I normally use the Fast Track as my main sound card, since I use a USB keyboard with Windows quite a bit and need low latency. If I can't get that working with Linux, it's no big deal, I can just switch the cords around when needed.

Any ideas?

---

### Post by duanedesign on 2009-10-15
Does your M-Audio Fast Track show up when you type 'lsusb' into the Terminal (Application > Accesories > Terminal). If it does you are close it is a matter of probably finding a setting or two.

Go to System/Preferences/Sound and switch everything except Default Mixer Tracks to ALSA or Pulse Audio. if you see ...HDMI... in Default Mixer Tracks, change it to your sound card/chip, Realtecxxxx or Emuxxx or ATI SB or HDA INTEL or something like that.

Right click on the speaker icon on the top panel and choose Open Volume Control. Click File/Change Device and make sure you have the correct device chosen. Close that window, right click on the icon again and choose Preferences. Make sure the device listed in the box is your sound card and select Master. Close the window. Now left click on the speaker icon and move the slider all the way up.

If you have a new Nvidia HDA sound chip and it sounds scratchy, this is a known problem and is fixed in the 2.6.27 kernel( It is part of Intrepid so you may want to consider upgrading, or trying a newer kernel) First maybe try some of the settings below.

Try turning up the PCM slider in the volume control. If PCM is set to 0 it makes the sound scratchy for some of those devices.

also in the Terminal (Applications > Accesories > Terminal) type the command:

```
alsamixer
```

make sure these are turned up at least 2/3 to 3/4 of the way. Also make sure none of the channels are muted (don't worry about the IEC958 channels, unmuting these can cause some cards to not work). You should see '00' at the bottom of each channel instead of 'MM'. You can mute/unmute by hitting the m-key.

If that didnt help continue.
Now in the Terminal run the command:

```
sudo gedit /etc/pulse/daemon.conf
```

Change these lines to look like this:
[B]default-fragments = 5
default-fragment-size =25[/B]

Additional Resources:
**Multiple Sound Solution (ALSA w Pulseaudio)**
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
**Multiple Sound Solutions**
[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by mysticofjesus on 2009-10-15
Alright, nevermind. This is now beyond the point where getting sound to work is the biggest of my problems. I tried upgrading to 8.10, and it broke the X server again. It also broke Windows Vista, which was on a separate hard drive. ](*,)

---

