---
title: "No Video after after &quot;Kernel Log&quot; loaded during boot"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by jamisonaw on 2006-06-03
Hi everyone,

I am installing EduBuntu server, and the install process worked fine. I got no errors. I've verified the disk, even used it to set up workstations.

When I reboot a very strange thing happens. It goes to Grub, then into the Graphical loader, but when it gets to "Kernel Log" the output to the screen shuts off. My monitor indicator just starts to blink. Hence, I think it is a Video driver. The Vid card is on a SiS chipset, but I don't know how to get more info.

I've tried using the CD to go into rescue mode and editing the xorg.conf file. "sudo gedit /etc/X11/xorg.conf" but it can't open the file (null). I am an admitted novice in the shell.

I also tried:

sudo nano /etc/X11/xorg.conf
sudo: unable to lookup ubuntu via gethostname()

I did another full install, and have the same problem. I've tried logging (without visual) and the hard drive works. Probably loading Nautilus etc. So my guess is that it really is the video card.

Thanks for the forum, and ubuntu is wonderfull.

---

