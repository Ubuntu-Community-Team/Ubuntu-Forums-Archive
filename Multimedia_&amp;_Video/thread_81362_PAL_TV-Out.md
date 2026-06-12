---
title: "PAL TV-Out?"
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by Kadafi on 2005-10-24
Trying to get TV-Out working on my ATI Radeon 9100 IGP - it's close, but can't seem to get it quite right.

Using this modeline I can see the login screen, but it's all over the screen:

ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
Using the settings from this page:
[http://www.kingcot.eclipse.co.uk/unichrome/fc3/xorg.conf.txt](http://www.kingcot.eclipse.co.uk/unichrome/fc3/xorg.conf.txt)
(including "nodpms", "noddc", DisplaySize, Viewport etc)


Does anyone have an easy, working modeline for PAL? Or even NTSC? Or perhaps an idea why this isn't working?

---

### Post by Kadafi on 2005-10-27
Bump...

Hm...

OK - I've spent about another 20 hours tooling around with this and I'm back where I started. 

Seems that nobody else has this problem, that all other Radeon 9100 IGP users stopped bitching about TV-Out six months ago, and that my eyes are slowly beginning to adapt to the weird out-of-sync display as if it were a sterogram.

Tried fglrx, that only seemed to lead me further away...no picture at all.

Anyway - to sum  up my request...does anyone have TV-out working (properly) on a Radeon 9100 IGP? I'm willing to settle for a  non-PAL resolution, fglrx drivers, whatever bizarre fix you can suggest - just need some help! 

My xorg.conf is presently as it was when I started - really back to square one.

---

### Post by Kadafi on 2005-10-29
Fixed...

For the benefit of anyone else who's having a similar problem, I installed the fglrx drivers (the "safe" ones from Synaptics), and ran fglrxconfig...which curiously didn't add the one line I absolutely needed in the graphics card Device section:

Option "ForceMonitors" "tv"

I know, feel very stupid given how easy this turned out to be in the end... all apologies for not reading properly if it was listed in a "How To" (didn't see it). 

Damn ATI for its confused, dyslexic drivers, incomplete config, lack of fundamental support for just about everything. Having said that, the Linux drivers DO seem to be better at TV out than their Windows equivalent :D

---

### Post by iluciv on 2005-10-29
Hi I've got a  Ati 9200 card in this ubuntu box that I'm trying to set up as a myth box. 
I have tv-out working (clone mode) after running fglrxconfig, using the ubuntu drivers, BUT its black and white on the TV and the Monitor picture is squashed but still usable and probably adjustable with actual monitors display settings (on the monitor itself).  

I'd also like to note, that when I first plugged in the s-video cable connector (which goes to composite connectors on the telly) in preperation of configuring the TV-Out the colours on the monitor where very pale (like lacking contrast) So I unplugged the s-video cable and rebooted then the picture was fine on reboot (on the monitor) 
While typing this, I've had the thought, to try just booting with the television onlym, connected and see what happens (will post result after trying) 
But has anyone else discovered this problem and has a fix for it?? 
The picture on the televison (pal-b) is fine just black and white S-video(card) --> composite connection(pal-b tv)
 
Thanks in advance

---

### Post by iluciv on 2005-10-29
wOOtage :D 
I found a little s-video to RCA connector and used that and an RCA Video cable and ran it to the normal av port on telly and now its colour!!! 
IMHO The Ati drivers have come along way since the last time I attempted to use this card in linux. kudos 
Now to set up mythTV

BTW It didn't work booting up with composite connected (having colour that is) I've also noticed that the TV really doesn't like the boot time it has no hold (v-sync h-sync) untill GDM welcome screen then its fine 
meh

---

### Post by Kadafi on 2005-10-30
Nice one - that's what I'm using too...comes with most ATI cards, but strangely not with my box. The fun never stops ;)

---

### Post by mun3kh on 2005-12-30
I have an Asus Pundit-R350 which has an Ati IGP 9100, built into the motherboard. as you might expect.

I too am having trouble with TV-out, I'm about to try using fglrxconfig again and add that one line that Kadafi mensions above.

I'm in the UK so the tv standard is PAL, i think that translates to PAL-I in xorg type language. I'm using it for MythTV with a Hauppage Nova-T Freeview card. Oh the joys of setting up MythTV

---

### Post by mun3kh on 2005-12-30
I've reverted back to my original xorg.conf with the "ati" driver.

When I tried using the "fglrx" driver it kills the wireless 
card I have in the PCMCIA slot on this Pundit-R350 
jobbie. Literally as soon 
as I do:
```

sudo /etc/init.d/gdm start
```
The lights on my wireless card go out and ifupdown 
commands act as if the device doesn't exist. I tried 
taking it out and putting it back in but to no avail.


Back on topic, I thought oh well I expect opengl will 
be working anyway
```
glxgears
```
Linux just freezes, damned proprietry ati binaries.
Reboot the box and try again, same problem. 
TV-Out...I can't even get glxgears to work.:(

---

### Post by mun3kh on 2006-01-06
Success...well sort of. I have found that I can get TV-out by simply using the "vesa" driver in my xorg.conf

It's pretty clear on screen but I can only have 800x600 resolution. I set the BIOS to:
TV only
PAL

I can only hope that the proprietry ati drivers will eventually support the TV-out on my 9100 IGP. Worst comes to the worst I could shove it up in the loft next to the aerial and just use it to record stuff.

---

### Post by drwatson on 2006-11-24
hi mun3kh!

currently im also trying to get my nice little pundit to work with some kind of dual screen support, even if it be tv-out.

could you post or send your xorg.conf?

greetings from germany

---

### Post by mun3kh on 2006-11-24
I'm so sorry drwatson. But the internal Hard drive in my Pundit failed back august and I had to replace it. I've not attempted TV-out since April 2005

---

