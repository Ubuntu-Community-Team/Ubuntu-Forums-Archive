---
title: "Sound card not detecetd!"
date: 2006-01-03
forum: Multimedia &amp; Video
---

### Post by gravediggers on 2006-01-03
Hi,

I have installed breezy some months ago on and old PC, and at the time, sound was not an issue because there was no speakers. Now I have some extra speakes, but I have since found that my sound card does not get detected. I have absolutely no idea about sound, and auto detection in linux (Ubuntu in this case), and wouls be grateful for some help. I want to learn something, so if there are any "about" or "howto" links someone can give me then that is great. But also some specific things I can check would also help.

My system (for Ubuntu) is my old PII 350 with a Creative Sound Blaster AWE64 (ISA PnP).

I also used the liveCD in expert mode to check if it detects the soundcard (it doesn't)!

---

### Post by Lord Illidan on 2006-01-03
Take a look at this page : [http://programming.linux.com/howtos/Hardware-HOWTO/sound.shtml](http://programming.linux.com/howtos/Hardware-HOWTO/sound.shtml)

I think you have to change from alsa to oss. However, I am not sure how to go about it in GNOME (I use KDE)

---

### Post by Wyrm_1972 on 2006-01-03
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28sound%29](https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28sound%29)

ISA cards aren't autodetected. You'll have to manually load the driver.

I had problems with my old ISA card. In the end I bit the bullet and went and bought the cheapest PCI sound card I could from the local computer shop. Worked without a hitch.

---

### Post by gravediggers on 2006-01-03
Thanks, will take a look tomorrow!

---

### Post by Lord Illidan on 2006-01-03
[quote=Wyrm_1972][https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28sound%29]("https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28sound%29")

ISA cards aren't autodetected. You'll have to manually load the driver.

I had problems with my old ISA card. In the end I bit the bullet and went and bought the cheapest PCI sound card I could from the local computer shop. Worked without a hitch.[/quote]

Might as well... ISA is an old and failing technology.. You will have better sound in the end.

---

### Post by Wyrm_1972 on 2006-01-03
[QUOTE=Lord Illidan]You will have better sound in the end.[/QUOTE]

And I do :)

---

### Post by gravediggers on 2006-01-06
OK - finally figured it out and got it working!:D 

The links supplied by Lord Illidan and Wyrm_1972 both directly and indirectly helped -  Thanks guys!

First checked if soundcore installed (should be):

[I]$ modprobe soundcore
filename:       /lib/modules/2.6.12-9-386/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:
srcversion:     E11490DC3F523551C4C2A6D[/I]

good!

Now, are there any sound devices!
[I]$ cat /proc/devices
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 29 fb
116 alsa
128 ptm
136 pts
180 usb
216 rfcomm
254 devfs

Block devices:
  1 ramdisk
  2 fd
  3 ide0
  9 md
 22 ide1
253 device-mapper
254 mdp[/I]

OK - alsa there (good) but no snd.
My card should work with driver snd-sbawe so:
*$ modprobe snd-sbawe* then
[I]$ cat /proc/devices
Character devices:[/I]
  .........as before....
 *14 sound*

Great! Just to check:
[I]$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux wintermute 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Sound Blaster 16 at 0x220, irq 5, dma 1&5

Audio devices:
0: DSP v4.16 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: Sound Blaster 16 MIDI

Timers:
7: system timer

Mixers:
0: CTL1745[/I]

This almost looks promising! The IRQ and DMA even agree with what was on the screen during boot! Now for the acid test. Played a wave file. Silence (except for buzzing of speaker). Shit!!!:mad: 
Is sound muted? Opened Volume Control (Alsa mixer). No, not muted. Cranked up the volume. Buzzing increases but no sound! Speakers faulty? Tried headset, but still no sound.    ????:???: 
Oh well, might as well commit to the driver - that amount seems to be right.
*$ sudo gedit /etc/modules*
add
*snd-sbawe*
Time to reboot and check that the sound card drivers are pemanently loaded at boot.
........
SHIT!! That nearly blew my eardrums out!

I guess the only thing I forgot was that after loading the driver, I should have reinitialised alsa. Will remember that for next time!

Now, on to the next problem!

---

### Post by eigenman on 2006-02-06
I have the same card and the same problem.
I run modprobe soundcore, and that is installed without a problem.
But when I cat /proc/devices, I get a device called sound, instead of alsa. After that, when I try running modprobe snd-sbawe, I get an error saying the card is not installed.
Am I doing something wrong? 
I've tried using isapnp as well, with no luck. I've also tried giving the irq and ports as an option in the modprobe, but it always fails. 

Any help is greatly appreciated.
Thanks,
Eigenman

---

### Post by FarEast on 2006-02-06
Hi,
Enter BIOS setting on boot and reserve IRQ 5 and 11 for ISA-pnp devices.
I hope this helps.

Visit here for details.
[http://ubuntuforums.org/showthread.php?t=103180](http://ubuntuforums.org/showthread.php?t=103180)

---

