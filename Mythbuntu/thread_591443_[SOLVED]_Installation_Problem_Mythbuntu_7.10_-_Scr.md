---
title: "[SOLVED] Installation Problem Mythbuntu 7.10 - Screen stays black"
date: 2007-10-25
forum: Mythbuntu
---

### Post by Stefan6183 on 2007-10-25
Hi,

I am trying to install Mythbuntu 7.10, but my screen stays blank during the installation:

I selected "Start or install Mythbuntu" or "Start Mythbuntu in save graphics mode".
Then the following messages appear:
"Kernel alive"
"Kernel direct mapping tables up to 130000000 @ 8000-e000"
After a few seconds my screen gets black.

My hardware configuration:
Mainboard: Gigabyte GA-P35 DS3P
CPU: C2D E6750
RAM: 4GB CL4 Corsair
VGA: GeForce 8800GTX
Display: Dell 2707WFP (1920x1200 pixel) connected via DVI
HDD: 2x Seagate 500GB

Any ideas?

Thx
Stefan

---

### Post by tgm4883 on 2007-10-25
Is there onboard video on that MB?  I have had a theory about some of these where the BIOS is outputing on the right card, but Ubuntu is not.  If there is onboard video, could you try switching the cord in the back and seeing if you get the picture then?

---

### Post by superm1 on 2007-10-25
First thing:

Check the CD for errors in its boot menu, check the md5sum against the cd image you downloaded.

If these are both ok, you may consider trying options such as noapic or noacpi upon boot.

---

### Post by Stefan6183 on 2007-10-26
Hi, thanks for your answers!
No, I don't have onboard video and the CD is also errorfree.

The following steps did the trick:
1) Highlight safe mode
2) Hit F6
3) Remove the word quiet at the end, and change splash to nosplash
4) Hit enter (and then again if that doesn't start up safe mode)

Thanks to Falcorian who postet this solution in another thread:
[http://ubuntuforums.org/showthread.php?t=580020&highlight=8800gtx&page=3](http://ubuntuforums.org/showthread.php?t=580020&highlight=8800gtx&page=3)

---

### Post by gcordoba on 2007-10-29
I just tryed the tip on a laptop compaq AMD64 (using ubuntu). There where no longer a black screen just untill the usual test. Afterwards the black screen appeared again.
Any additional tip?
Thanks,
Gustavo

---

### Post by gcordoba on 2007-10-29
Fixed! 
I added
noapic irqpoll noirqdebug
to he boot options as finnen suggest in that post
Gustavo

---

### Post by GackY2K on 2007-12-11
Great advice...worked like a charm for me too!  I was about to go crazy!  It's been years since I've tried a distro and have heard many good things about Ubuntu...glad I could get the CD to finally run!  

Installing now!

---

### Post by gcordoba on 2007-12-12
However, any of you know where to put those lines in order to make them a permanent part of the boot?
Thanks,
Gustavo

---

### Post by gcordoba on 2007-12-14
Found!
that can be done in:
/boot/grub/menu.lst

---

