---
title: "Ubuntu 9.10 no sound for Xbox360 connection"
date: 2010-04-06
forum: Multimedia Software
---

### Post by andyvy on 2010-04-06
Hi,

I'm running Asus M2N32-D motherboard which has on-board sound.

I also have a 24' monitor which I connect the Xbox 360 to, and the PC. Xbox 360 takes up the VGA connector, and the PC runs through DVI connection.

The connection that goes from Xbox 360 has a splitter basically one end is VGA, other end is a sound output a White / Red splitter which connects into a regular 3.5mm audio jack which then plugs into the motherboard input sound device. Here's a pic of the wiring harness I use: 

[IMG]http://www.uk-consoles.co.uk/shop/images/official_xbox_360_vga_hd_av_cable_360.jpg[/IMG]

The white / red ends plug into the 3.5mm audio jack which then goes into the back of the PC in the Input jack.

In windows, I only have to turn on the xbox and switch the output on my monitor, and then use my PC speaker system to have xbox sound, and PC monitor to have the video come in.

In ubuntu, everything works the same except there is no sound coming in, so basically either I'm missing a driver somewhere, or the sound is turned down by default. (In windows, this option is turned down to 0 by default).

I really don't want to go back to windows just because of this, and I'm sorry if this is a repost but I had no idea how to search for it, browsed through thousands of links with no help.

Anyone running a similar setup that may have some input on this?

Thanks in advance!

---

### Post by andyvy on 2010-04-06
Here's the list of hardware playback devices;

andy@home:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andy@home:~$

---

### Post by andyvy on 2010-04-06
!!! 

Found a solution;

Open terminal, type: alsamixer

Left / Right to scroll through, push M to mute / unmute. Make sure to scroll all the way right since there are more options.

Like I figured the option for input audio was just muted and turned all the way down, now I have sound and everything works flawlessly.

Source of my solution: [http://ubuntuforums.org/showthread.php?t=1285957&highlight=M3N72-D]("http://ubuntuforums.org/showthread.php?t=1285957&highlight=M3N72-D")

Except this guy had no sound through HDMI, but same fix!

---

