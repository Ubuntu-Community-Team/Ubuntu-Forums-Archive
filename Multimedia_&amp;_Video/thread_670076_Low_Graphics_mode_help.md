---
title: "Low Graphics mode help"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by Elpants on 2008-01-17
I did some searching on this, but found nothing. That fit me problem at least.

I run a Sony VAIO laptop with an Intel 945gm integrated video card, dual boot 7.10 and vista.

I have an external moniter I use when my laptop is on my desk. It has worked all fine and dandy till when I tried making the display go from the external moniter to the laptop screen so I could switch the external to another input and play some Wii.

Anyway, once I did that I got an alert telling me I need to log out to take effect. which I did, as soon as I did I got the box telling me Ubuntu is now running Low Graphics mode. and to use multiple moniters I needed to set it up myself. Which I tried and now I can't get it to work on the external moniter and my laptop screen is now only going in 800x600 or lower resolution.

I tried enabling the driver through restricted drivers like other threads told. But the display driver isnt listed.

Is there a way to go back to the way I had it set up 20 minutes ago? Or ways to get out of this low-graphics mode?

Sorry if there is a thread like this already or I put it in the wrong forum. My searching turned up nothing.

---

### Post by linksolo74 on 2008-01-31
I am currently having this problem too. Did you ever find out anything? I'll tell you if i find out anything.

---

### Post by linksolo74 on 2008-01-31
on [http://ohioloco.ubuntuforums.org/showthread.php?t=683291&highlight=low+resolution](http://ohioloco.ubuntuforums.org/showthread.php?t=683291&highlight=low+resolution)
it says to open the terminal and type:


Code:

sudo dpkg-reconfigure -phigh xserver-xorg

and when complete use the command to reboot
Code:

sudo reboot

it worked for me,

---

