---
title: "Sound doesn't go through connected speakers"
date: 2009-01-06
forum: Multimedia Software
---

### Post by Sh4wn on 2009-01-06
Hi,

I have a Acer Aspire 7530 Laptop. I have installed ubuntu dual boot beside Vista.

The sound from he built in speakers is not really great, so, I have a nice extra pair of speakers which I connect to the 3.5mm jack. In vista, the sound stops coming from the built in speakers, and will start coming from my connected speakers.

But, in Ubuntu, when I connect my speakers, or any other device which I can connect to the 3.5mm jack, nothing happens. It just keeps playing from the built in speakers, and no sound from the connected one.

**Installation Info**
Ubuntu Version: 8.10
Kernel version: 2.6.27-9-generic

lsusb:
```

Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 064e:a103 Suyin Corp. 
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

If you need anymore info, tell me.


How can I fix this, so the sounds comes from my connected speakers?
Thanks in advance.

---

### Post by Sh4wn on 2009-01-07
*Bump*

---

### Post by Valygard84 on 2009-01-09
Hello, I own an Acer Aspire 7530G (I presume it's the same model as the one the original poster wrote about) and suffer the same problem.
I would be very grateful for getting help on this proplem, as it's the only real showstopper that keeps me from using Ubuntu full-time on this laptop.

As previously stated, it's not only that the headphone jack doesn't work, it's the headphone sensing, too. (Meaning that the front speakers won't go quiet when you plug in headphones.)
Also the Mic and Line in Jacks don't work. The build-in mic doesn't work, too.

_Things I've already tried:_

* Installing the Realtek audio drivers (as the build-in audio chip is
  reported by the the mixer as being ALC888)
* A fix metioned in another thread which sounded similar to my woes:
  install linux-backports-modules-intrepid-generic and add "options
  snd-hda-intel model=acer" (without quotes) to /etc/modprobe.d/alsa-base

Putting in **acer-aspire** as model option leads to all kind of weirdnes:
Now the Headphone Jack works, but is (even when setting ALL available Volume Sliders in both alsamixer and Gnome-Mixer to 100%) rather quiet.
Sadly thought the front speakers are totally quiet now and can't be bothered to work.

Trying out **3stack-dig** as model enabled the internal microphone, but Sound-Recorder Isn't able to record anything. 

Notes:
The Gnome Audio Mixer has a switch called "Headphone" which doesn't do anything, regardles of what model I put into /etc/modprobe.d/alsa-base.
Installing the Realtek drivers added an option called "IEC958" which seemingly doesn't do anything at all.

A workaround might be to write a shellscript that stops alsa and restarts it with the acer-aspire model parameter or revert to the default.
This would allow one to switch between headphones and the internal speakers but would be a huge inconvenience.

_I am using:_
Ubuntu Version: 8.10
Kernel Version: 2.6.27-9-generic
Version of installed alsa-base: 1.0.17.dfs

_System Info/Pastebin links:_
-dmesg: [http://pastebin.com/f7bb49fb2](http://pastebin.com/f7bb49fb2)
-Relevant section of lspci -nn -vv & regular lspci: [http://pastebin.com/m33a7dee0](http://pastebin.com/m33a7dee0)
-aplay -l: [http://pastebin.com/mad64b9e](http://pastebin.com/mad64b9e)

Ps.:

To **Sh4wn**: If you only want to get your external speakers to work, you can try using the above mentioned "no-fix":
Open the file /etc/modprobe.d/alsa-base as root (by doing sudo gedit /etc/modprobe.d/alsa-base in a terminal for example)
and add "option snd-hda-intel model=acer-aspire" (without the quotes) at the bottom. This should work well if your speakers have a build in amplifier.
Although you might get worse sound quality as with the internal speakers.
Removing the option snd... line resets your system to the old state.

If the above doesn't work, try installing the realtek drivers beforehand, but be warned that I don't know if that won't screw up anything further.
(you need to do "sudo aptitude install xmlto build-essential" beforehand)

---

### Post by Sh4wn on 2009-01-10
Well, I've got sound from my speakers :)

Here's how I did it:

1. Open Gnome Volume Control, and make sure HDA Nvidia (Alsa Mixer) is selected
2. Click the Preferences button, and check 'Surround'
3. Close the preferences window
4. Slide the surround volume up
5. And wh00p I've got sound

(I also added the option Valygard mentioned, don't know if that had anything to do with it.)

---

### Post by Valygard84 on 2009-01-11
Hello again!

After reading Sh4wn's post, I tried fiddling around with the Gnome Mixer once again. Pressing "Settings" unveiled a whole bunch of disabled volume sliders, just as stated, but without adding acer as model option, they won't do anything to the headphone volume.

Adding "options snd-hda-intel model=**acer**" (without quotes) to /etc/modprobe.d/alsa-base does the trick. :)

Now the headphones and front speakers work. 
They have seperate volume sliders (Surround for the headphones, Front for the front speakers.) which can be used as a workaround for headphone sensing.
The internal mic started working, too, which is a great bonus. :D

Now the only thing I'ld like to get working is the headphone sensing.

I would be very grateful if someone could offer some assistance or pointers.

Being able to set the volumes of the two channels via terminal to build a shell script around would be quite nice, too.

---

### Post by Valygard84 on 2009-10-31
Update:
Everything works out of the box now sound-wise with Karmic Koala.
Even headphone sensing and the internal mic.

Great work people! :D :KS

---

