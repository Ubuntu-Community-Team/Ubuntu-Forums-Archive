---
title: "MCP51 (Nvidia) Headphone Jack Support in Edgy (Sort of a HOWTO)"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by marinosr on 2006-12-21
Like a few of you, I've had major problems getting my headphone jack to work on my Compaq V6000 laptop. This problem was quite urgent for me, as I have a radio show for which I need music off of my computer. At one point, I managed to get ALSA working for my headphone jack,  but couldn't remember how. Then, it stopped working a few months later. In the interim, I upgraded to Edgy, hoping that would solve the problem, but it didn't. I finally got it to work again, although it required a fresh install of Edgy (not the uprgrade.) If I knew more about Linux, such drastic measures probably would not have been necessary, but this is what I did to get full sound support again...I'm guessing this will work for anyone with the MCP51 audio chipset, but no promises:

1. I did a fresh install of Edgy, using the alternate install CD, wiping my root partition.
2. I got a bunch of repos necessary for compiling ALSA. This included build-essential, linux-headers-2.6.17-10-386, libncurses5-dev, and maybe some others. You should be able to decipher from the ./configure error output if that list isn't exhaustive. 
3. From alsa-project.org, I snatched alsa-driver-1.0.12, alsa-lib-1.0.12, and alsa-utils-1.0.12.** NB: I tried to use 1.0.13 stable and 1.0.14rc2, and both of these DID NOT WORK.** 1.0.12 is a safe bet; it's documented to work for others, too, while the other versions cause problems. 
4. I applied [this patch]("http://xopen.dyndns.org/linux/v6024ea/hda-generic-hp-fix.diff") by copying it into my alsa-driver-1.0.12/alsa-kernel directory and running "patch -p1 < hda-generic-hp-fix.diff" on the command line in that directory. (THANK YOU xopen for making [this tutorial]("http://xopen.dyndns.org/linux/v6024ea/#sound") and for your personal help)
5. In the alsa-driver-1.0.12 root directory, I ran "./configure --with-cards=hda-intel --with-oss=yes --with-kernel=/usr/src/linux-headers-2.6.17-10-386"
6. Then just make and sudo make install, then I built the other packages (lib and utils) as normal.
7. Voila! I now have a headphone control in alsamixer and audio out of the jack.

This has been a rather imprecise outline of my process. If you have any questions, I'll try to answer them, although I'm a newbie. [This thread]("http://https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2412") on the alsa bugtrack contains info on this bug, and may provide better support for this problem than the Ubuntu forums (click guest access at the bottom if you don't want to register.) Anyway,  I hope this helps someone. Cheers!

---

### Post by grcastleton on 2006-12-31
either I'm an idiot or the server with the patch ([http://xopen.dyndns.org/](http://xopen.dyndns.org/) ) is down. Anywhere else I can get it?

---

### Post by ecarlosforero on 2007-01-02
> **grcastleton said:**
> either I'm an idiot or the server with the patch ([http://xopen.dyndns.org/](http://xopen.dyndns.org/) ) is down. Anywhere else I can get it?

[http://www.dev-board.com/files/hda-generic-hp-fix.diff](http://www.dev-board.com/files/hda-generic-hp-fix.diff)

---

### Post by Grayscale on 2007-01-03
Thank you very much for this tutorial, it got my hp dv6125se's headphone jack working perfectly!

---

### Post by Grayscale on 2007-01-04
The only problem I'm having is that after going into suspend, my headphone jack doesn't work again!  It shows up in the mixer but doesn't do anything!

---

### Post by keflavich on 2007-01-12
I've gotten the sound to work alright, and the headphone jack works, the problem is that I can't have the headphones on and the speakers off.  In alsamixer, Master controls the headphones, and PCM controls the *real* master.  i.e. if I have master and PCM on max, I can plug in the headphones and hear both headphones and speakers.  If I turn down/mute PCM, both headphones and speakers go, and if I turn down master, I can't use headphones but the speakers stay on.

This seems like it should be a minor configuration error, but I could be wrong.  Any ideas on what I can do to fix it?

Thanks,
Adam

---

### Post by shadowhywind on 2007-01-12
I believe the 1.0.14rc1 fixes the headphone jack issues *it also turns the mute button red/orange* or at least it did for me i am running an hp dv6040us. I ended up downgrading back the 1.0.12 becuase i liked having my speakers muted 100% even after i unplug my headphones. But i was wondering is anyone else having a problem getting their microphones working, the internal or even the external ones to work?

---

### Post by feiming on 2007-01-16
I install alsa-1.0.12 on my V3100 AMD series.Everything work fine except my slide volume and mute which i set on my gnome-keyboard-shortcut.It control my headphone volume and mute in alsamixer.

How do I set it to control PCM or maybe Speaker Volume?

---

### Post by renesisspeed on 2007-02-07
Help!!! I cant get sound to work at all on my v6000

also have other problems, but i figure i'll tackle those later
below is my hardware profile, if anuyone can help it would be much appreciated :)


lspci
> 0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (revf1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:03:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev01)
0000:07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:07:05.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:07:05.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


---

### Post by keflavich on 2007-02-08
What version of alsa do you have?  I got sound to work with alsa 1.0.12 and 1.0.13, but then something went funky with my whole setup and (with 1.0.13 installed from source) sound stopped working completely.  Can you open alsamixer?

---

### Post by keflavich on 2007-02-08
(please delete this post)

---

### Post by Varin on 2007-03-09
Hello. I have Compaq Hp Presario V6000 laptop. I have same issue, I can't make my headphones jack working. Have tried solution with 1.0.12 and it didn't work. Do you have any other ideas how to make it work? In mixer it shows two things: master volume and PCM.

---

### Post by randall_l on 2007-03-20
Thanks marinosr.  It worked like a charm on my Compaq V6000 (V6215CA).

Any suggestions on how to get volume control back to the media keys?  Before the update, the mute/volume media keys actually changed the volume.  Now they don't (as the "Master" [can't remember if it's actually called "Master" or not] control no longer exists).

Alsamixergui shows: Headphone, PCM, Capture, Speaker

I messed around with some epplet source (from the Emix) for Enlightenment utilizing soundcard.h... Headphone is actually mapped to SOUND_MIXER_ALTPCM.  Capture is mapped to SOUND_MIXER_IGAIN.  PCM and Speaker aren't mapped to any of the other channels (I tried them all) but, I digress.

It's a neat fix, but if I can't figure out how to get the media keys to change the volume, I'll go back to  pre-packaged ALSA.  I've got a Sony PSP for music (and using it doesn't cause the battery to drain any faster).

Cheers!

---

### Post by feiming on 2007-04-15
try using xbindkeys at
[http://mylinux.blogdrive.com/archive/16.html](http://mylinux.blogdrive.com/archive/16.html)

---

