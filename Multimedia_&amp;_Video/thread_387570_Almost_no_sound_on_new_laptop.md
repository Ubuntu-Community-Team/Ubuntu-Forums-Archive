---
title: "Almost no sound on new laptop"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by tph on 2007-03-18
I recently got myself a new laptop, an Acer Aspire 5114WLMi.
The first thing I did after getting it was installing ubuntu, as I've got experience with it from before and I didn't want to run Windows.
Everything works just fine, but when I try to play some music there's no sound, and even worse, no errors.
Another thing I find wierd is that when I open nautilus and place the mouse-pointer on a sound-file it plays just fine, but I don't want to do that every time I want to listen to music.

aplay -l outputs ```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and alsamixer just gives me a ```
alsamixer: function snd_mixer_load failed: Invalid argument
```

I'm running 64bit btw, but I thought that this wasn't too related to that.

---

### Post by eggdeng on 2007-03-18
That sound files play when the mouse cursor is over them is down to a preview feature in Nautilus, you can turn it off in Edit -> Preferences->Preview. As for the rest, try adding the line ```
options snd-hda-intel model=ACER 
``` to /etc/modprobe.d/alsa-base. Reboot for changes to take effect. More info at [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383).

---

### Post by tuque on 2007-03-18
I have an Acer laptop and had difficulties with the sound. I tried various fixes but this was the only one to work for me.  

The chip for your sound device is made by Realtek. Realtek have produced a linux driver. 
The Realtek package will compile the driver into your kernel. To do this you will need the build-essential package to be installed on your computer. Open a terminal and enter the following;

sudo apt-get update
sudo apt-get install build-essential

Download the linux driver

[ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.05f.tar.bz2](ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.05f.tar.bz2)

The install instructions should be in the download package.

---

### Post by tph on 2007-03-19
Well, there is sound, but nautilus is the only program I've heard sound from so far.
Adding the line to /etc/modprobe.d/alsa-base didn't help much, but I assume I can try to compile that driver later on and check if it helps.

Edit: compiling my own driver did help

---

