---
title: "Sound Blaster AWE64 Gold in Intrepid Ibex"
date: 2008-12-14
forum: Multimedia Software
---

### Post by scott_selberg on 2008-12-14
Hi,

  I have a rather old PC with a Creative Labs AWE64 Gold ISA sound card and I managed to get it to work by a lot of trial and error.  I just wanted to drop my recipe so that it may benefit others who are as foolish as I.  I think this recipe will also work for ISA SoundBlaster 16 cards.

  As a starter, I spent several days getting this card to work and I'm not a novice to Linux or Ubuntu.  I might highly recommend buying a cheap PCI sound card rather than trying to get an ISA card working.  But if you got the hardware, here are some hints.

First, I needed to reserve IRQ5 for my sound card in the computer BIOS.

Second, I needed to manually add the sound card drivers to the /etc/modprobe.d/alsa-base and reboot the computer (or re-load the module if you are comfortable with how to do it.)

```

options snd-sbawe isapnp=0 port=0x220 mpu_port=0x300 awe_port=0x640 irq=5 dma8=1 dma16=5
#options snd-sb16  isapnp=0 port=0x220 irq=5 dma8=0 dma16=5 mpu_port=0x300

```

I commented out the snd-sb16 which should be used for SoundBlaster 16 cards.  If you enable it, comment out the snd-sbawe line by adding a '#' in front of it.

Third, I needed to add myself to the group "audio".  I tried to fire up "alsamixer" and got an error, but root could do it.

At this point, you should be able to get some sound by entering "aplay -Dhw /usr/share/sound/question.wav"

The trick at this point is to get pulse to pick it up.  I think Ubuntu wants hal (hardware abstraction layer) to figure out what hardware is present and load the right drivers.  I'm not sure HAL can deal with old ISA cards, so I think it needs to be loaded manually by adding the following lines into: /etc/pulse/default.pa
```

load-module module-alsa-sink device=hw:0
load-module module-alsa-source device=hw:0

``` 

While working on all this stuff, here are some useful tips for seeing if sound stuff is present or not:

[LIST]
[*]lspnp  (list pnp devices such as ISA cards)
[*]lspci  (list pci devices)
[*]cat /proc/interrupts
[*]cat /proc/asound
[*]cat /dev/sndstat
[*]aplay -l (list sound devices)
[*]amixer
[*]speaker-test -wav -c2
[/LIST]

---

### Post by matt.matolcsi on 2009-01-02
Big thanks for this post! I had the same problem myself and I doubt I would've had the patience to figure it all out. 

Sound works pretty well for me after following these tips. That is, system sounds work through both Pulse Audio and ALSA, but it seems that I can't record sounds through Pulse. However, in Skype it's possible to directly select the sound recording device, and that's all I needed. 

I want to add that I was getting a pcm_write:1394 error (or something very similar) for the longest time when trying to play any sounds -- this was before I even got around to sorting out ALSA or PA issues. To fix this, I had to go into the BIOS and simply reset the PCI and ACPI configuration to the defaults. No idea what the problem was, but seeing as this BIOS is from 1998, I'd guess it's some ancient stupid thing that's not worth looking into. 

With that done, I added snd-sbawe to /etc/modules, rebooted, and ALSA picked it up from there. It was *not* necessary for me to specify IO ports and DMA channels. I did, however, have to specifically add the devices to the Pulse Audio config as above.

---

### Post by jis on 2009-01-16
I used Xubuntu 8.04 before and there I had to only add snd-sbawe to /etc/modules, and reboot (like instructed at [Community Documentation]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs"). But in 8.10 (Intrepid Ibex) I had to additionally add a group named "audio" and add user to it and reboot to have sound for the user. What does that change come from? I haven't used Pulseaudio.

scott_selberg, thanks for tips, but note that
cat: /proc/asound: Is a directory

---

### Post by jis on 2009-01-21
Somebody asked for more detailed instructions.

/etc/modules is a text file you can edit as superuser. You just add
line "snd-sbawe" there (without quotes). If you use a graphical editor,
you should start it in terminal by command "gksudo
editorname /etc/modules" to be able to save the file.

Then start program called users-admin. (You may find it by similar name under System menu.) Make sure users have "Use audio devices" checked in Properties.

The device should work after restarting system.

---

### Post by jis on 2009-04-01
Anybody else tried to use the sound card in Jaunty? I tried in alpha release and it did not work even if I added current user x to group audio by ```
sudo adduser x audio
``` and rebooted. I could not use the gui way, because trying to unlock users-admin produced an unexpected error. Is the hardware support gone along with Jaunty?

---

### Post by jis on 2009-04-02
Some correction to my previous message: yes, it works in jaunty. You have to adjust volume by e.g. qamix in addition to the previous instructions. Btw. The bug report about users-admin is [here]("https://bugs.launchpad.net/bugs/353652").

---

### Post by jis on 2009-04-02
If you play sound by one application, sounds of other applications do not work; the system can not mix sounds from several apps. I wonder why this is and is it common for all ISA cards in Linux?

---

