---
title: "Video Card not working"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by GuitarHero on 2006-06-21
I have an ATI RAGE 128 video card I want to use with ubuntu so I can play Wolfenstein, but everytime i try to boot with it it gives me some X something or other failure error or something and wont boot.  When I try to play wolfenstein as it is now without a video card I dont see anything on the screen at all when I try to start the game, all black.

---

### Post by patrick295767 on 2006-06-21
[QUOTE=GuitarHero]I have an ATI RAGE 128 video card I want to use with ubuntu so I can play Wolfenstein, but everytime i try to boot with it it gives me some X something or other failure error or something and wont boot.  When I try to play wolfenstein as it is now without a video card I dont see anything on the screen at all when I try to start the game, all black.[/QUOTE]
  
Hi, 

you have dapper or breezy ? Is your video well installed (not mesa , i mean) : [http://ubuntuforums.org/showthread.php?t=198335](http://ubuntuforums.org/showthread.php?t=198335) ?

---

### Post by GuitarHero on 2006-06-21
I never installed anything for it, i thought ubuntu came with all the drivers it needed

---

### Post by GuitarHero on 2006-06-21
[QUOTE=GuitarHero]I never installed anything for it, i thought ubuntu came with all the drivers it needed[/QUOTE]
oh and i have dapper.  the wiki says i need at least a radeon level card, mnines a rage. do rage cards not work?

---

### Post by GuitarHero on 2006-06-21
i tried installing some xorg ati driver thing and it made my computer unable to boot, im back on my windows pc right now.  It gave me the X server error, i assume because now i have the xorg drivers and i need the ones i had before that worked with my motherboard's onboard video.  what do i do?  Is there a way to get the video card to work? If not, how do I get it back to the way it was?

---

### Post by GuitarHero on 2006-06-21
well i reconfigured the xserver-xorg conf file and now i can boot into ubuntu, but i still wanna use my video card so could someone tell me how to get an ATI rage 128 card wroking?

---

### Post by patrick295767 on 2006-06-21
[QUOTE=GuitarHero]i tried installing some xorg ati driver thing and it made my computer unable to boot, im back on my windows pc right now.  It gave me the X server error, i assume because now i have the xorg drivers and i need the ones i had before that worked with my motherboard's onboard video.  what do i do?  Is there a way to get the video card to work? If not, how do I get it back to the way it was?[/QUOTE]
 
You can do : 
into the console (alt F1)
sudo dpkg-reconfigure xserver-xorg
and select ati or vesa (ati will give better results), but unfortunately your 3d acceleration will not work. :-(   the fglrx module should be selected for 3d acc.
In /etc/X11 you '"ll find automatic backup's of your vital file : xorg.conf

 
/etc/init.d/gdm restart
(or /etc/init.d/kdm restart)

In X, glxgears should be fast fpp enough to play games.
 
 I have found these links too about the rage:
--rage3d:
[http://www.rage3d.com/board/forumdisplay.php?f=61](http://www.rage3d.com/board/forumdisplay.php?f=61)
Mesa problem:
[http://www.rage3d.com/board/showthread.php?t=33858827](http://www.rage3d.com/board/showthread.php?t=33858827)
  
[http://www.ubuntuforums.org/showthread.php?t=189811&highlight=ati+rage](http://www.ubuntuforums.org/showthread.php?t=189811&highlight=ati+rage)
  
[http://www.ubuntuforums.org/showthread.php?t=76116&highlight=ati+rage](http://www.ubuntuforums.org/showthread.php?t=76116&highlight=ati+rage)
  
I hope that can help you and others too who are ati rage concerned :-(

---

### Post by patrick295767 on 2006-06-21
and the Agp should maybe be enabled if it's an agp card ?
  
in xorg.conf 
there is : 
```
Option "UseInternalAGPGART" "no"
```
> /etc/modules
agpgart
fglrx

maybe ?
  
----
[http://ubuntuforums.org/archive/index.php/t-3764.html](http://ubuntuforums.org/archive/index.php/t-3764.html)
  
into this link : [http://forum.ubuntu-fr.org/viewtopic.php?id=2487](http://forum.ubuntu-fr.org/viewtopic.php?id=2487)
  sounds nice to be done too : 
> par
Code:

      Driver      "fglrx"

Dans la section [Module]
commentez "Load "extmod" " et rajoutez des lignes afin d'avoir ceci:
Code:

#    Load    "extmod"
    SubSection "extmod"
        Option    "omit xfree86-dga"
    EndSubSection

Cela vous donne accès à xrandr, qui permet de changer la taille de l'écran sans redémarrer.
  
Did you see also : [http://www.ubuntuforums.org/showthread.php?t=188925&highlight=ati+rage](http://www.ubuntuforums.org/showthread.php?t=188925&highlight=ati+rage) ?

---

### Post by GuitarHero on 2006-06-21
no its a pci card.  even with the flgrx or whatever installed it doesnt work.

---

### Post by GuitarHero on 2006-06-21
by looking at pictures ive figured out that the card is actually an all in wonder card powered by ati rage 128, so is the driver i need different or something? i ran the driver for radeon 8something and higher off of ati's site, but it still gives me the xserver error.

---

### Post by GuitarHero on 2006-06-22
I think im just going to give up on using linux, the difficulty of getting anything to work far outweighs any advantages it has.

---

