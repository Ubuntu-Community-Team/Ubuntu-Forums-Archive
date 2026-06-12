---
title: "Nvidia Control panel"
date: 2008-06-27
forum: Multimedia Software
---

### Post by Mr.Useless on 2008-06-27
Hey in windows, i had an app which gave me the option to change my fan speed on my nvidia card (8800GTS512OC) and im just wondering if i can get access to this feature again? i found it great for when i went into using highly graphical apps (i dont mean death and sex everywhere :P) to make sure that it kept cool..

Just wondering, i know there arent many highly graphical needy programs for linux yet (im talking games here) but i reckon soon enough there will be a rise in popularity, with it, and as i say the feature was useful.

Thanks

Mr.Useless

---

### Post by Enlitend on 2008-06-27
Hi,
I'm currently using the "nvclock" utility to  adjust my nvidia 8800gt fan speed.
You can get it by typing this in the terminal.

```
sudo apt-get install nvclock
```

or you can try out the other nvclock with a gui:

```
sudo apt-get install nvclock-gtk
```

I think the nvclock-gtk will not create  a launcher for you on the main menu, so you might want to create one yourself. 

Hope this helps.

---

### Post by Mr.Useless on 2008-06-27
Thanks a lot mate :D

Mr.Useless

---

### Post by Enlitend on 2008-06-27
No problem there. :)

My video card is hot because I'm using the default crappy fan so everytime when I log in I have to set the fan speed to 80 to keep it below 60. :(

---

### Post by Mr.Useless on 2008-06-27
argh i cant create a launcher i cant find the install path -_- noooob

---

### Post by Enlitend on 2008-06-27
It should be " nvclock_gtk", notice the underscore between not the dash.

---

### Post by Mr.Useless on 2008-06-27
Hmh this isnt good, it recognises my card as a..

```
-- General info --
Card: 		nVidia Geforce 7025 nForce 630a
Architecture: 	G67 A1
PCI id: 	0x53e
GPU clock: 	0.000 MHz
Bustype: 	PCI

-- Pipeline info --
Pixel units: 1x4 (01b)
Vertex units: 1x1 (001b)
HW masked units: None
SW masked units: pixel 10b vertex 110b

-- Memory info --
Amount: 	256 MB
Type: 		128 bit DDR
Clock: 		-

```

when im sure its a 8800gts i bought :P

heres the exact card i got...

[http://asia.msi.com.tw/index.php?func=proddesc&prod_no=1370&maincat_no=130&cat2_no=136](http://asia.msi.com.tw/index.php?func=proddesc&prod_no=1370&maincat_no=130&cat2_no=136)


Do i need a driver update? i just got the one it installed for me :S

Mr.Useless

---

### Post by Enlitend on 2008-06-27
That's odd. How did you install the driver when you put the card in on the first place?

---

### Post by Mr.Useless on 2008-06-28
hmh install thedriver....i assumed that because it has set my resolution to the native display size which is 1680x1050 and windows never did that that it was a prerequisite to ubuntu and had it included, obviously not, where can i find thie latest driver? and how hard is it to install?

thanks

Mr.Useless

---

### Post by damis648 on 2008-06-28
> **Mr.Useless said:**
> hmh install thedriver....i assumed that because it has set my resolution to the native display size which is 1680x1050 and windows never did that that it was a prerequisite to ubuntu and had it included, obviously not, where can i find thie latest driver? and how hard is it to install?

thanks

Mr.Useless

On the Panel: System>Administration>Hardware Drivers
and put a check on your card. Reboot. All good. :popcorn:

---

### Post by Mr.Useless on 2008-06-28
yeh i already had done :S

maybe my card isnt compatible? it was the same on 32bit as the 64 bit system im running now :(

 if anyone can find a fix for this that does require stupidly long commands that have to be antered in ctrl + alt +f1 say, but if thats the only way then im gonna have to!

Thanks anyway

Mr.Useless

---

### Post by SnakeHips on 2008-12-09
> **Enlitend said:**
> It should be " nvclock_gtk", notice the underscore between not the dash.

Ah so thats where it's been hiding lol  ...... thankyou!

---

### Post by vulturesrow on 2008-12-09
I feel completely dense but I didnt see an option anywhere in nvclock_gtk to adjust my fan speed :(

---

### Post by helterskelter on 2008-12-09
Mr.Useless, does your MoBo have onboard graphics support? The code from the nvidia software "Card: 		nVidia Geforce 7025 nForce 630a" seems to say so!

You need to go into your BIOS and disable onboard Graphic support if you are using a plug-in card. Do make sure your monitor is plugged into this card and not the MoBo connector.:p

eddie

---

