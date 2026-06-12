---
title: "Possibly destroyed microSD card, any ideas?"
date: 2016-02-03
forum: Mobile Technology Discussions (CLOSED)
---

### Post by ghost25 on 2016-02-03
Hey all, got a quick question which I'm sure is going to unravel into a multi-page thread quite quickly. Ah well, here goes.

I told a buddy that I was good with computers, and he handed me a microSD card from an old phone he used to use (ex-military, so not sure what I can and can't say... for sure, can't say what is on the card). He wanted to show me pictures of his time overseas, but he told me his card just up and quit working one day.

I've been playing with this card in Windows, using a few different programs like Recuver and the like, but no such luck. Windows, if it sees the SD card, won't open it beyond showing the blank screen reserved for empty folders. However, if I view the properties, I can tell there's a bunch of stuff on this card. Nothing shows up no matter what I do.

Ubuntu behaves even more strangely. I'm no stranger to using mSD cards with Ubuntu, it's how I've loaded music onto my phone. But, something tells me there's got to be a way to at least make a ghost image of this thing, so that I can recover the data for him and burn it on a CD or something. Ubuntu has yet to let me down, so fingers crossed.

Ubuntu simply doesn't react when I load the mSD into the computer. I've tried using my phone (not recognized as being there), digital camera (some sort of error about can't use the card, might be due to the camera using a standard SD card instead of mSD), USB-plug type reader (registers the reader, but not the card), and the onboard SD slot using an adapter (nothing recognized). There's GOT to be a way this can be rescued... once the card is rescued though and backed up in my own archives (he tends to be rough on his stuff) I'm destroying the card so I'm not tempted to use it myself.

Tech specs: It's a SanDisk Ultra 16GB class 1 (I believe) microSDHC I. Using an HP Pavilion dv6 with Ubuntu 12.04.1 LTS 64 bit, no updates performed recently as I'm running out of space (issue for another day).

---

### Post by sudodus on 2016-02-03
You can check if the micro SD card is recognized as a mass storage device in more than one version of Ubuntu (also newer versions, not only 12.04.1 LTS), and some other linux distros. You need not install anything, try with live systems from a USB drive.

Try also with different hardware: computers, USB ports, adapters etc (like you did before).

The following command will show if the card is recognized as a mass storage device (as /dev/sdx, where x is the drive letter, a, b, c ...).

```
sudo lsblk -fm
```

If the card is recognized as a mass storage device, you can clone it to another drive of at least the same size with ***ddrescue*** and then use various tools to try recover the files. I would recommend ***testdisk*** and ***photorec***.

There are more tips and links at [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986), the paragraph about 'Advanced repair of a partition table, file system and/or recovery of files'.

If the card is ***not*** recognized as a mass storage device, I have no method to recover data from it. There are probably methods, but you would need help from people who know much more about the built in circuits and machine code programming in the micro SD card.

---

