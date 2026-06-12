---
title: "GeForce go 6800 Nvidia Issues"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by burquedout on 2006-08-03
Currently I don't have the nvidia drivers installed, because I reinstalled dapper for the 5th time today lol.  Whenever I install the invidia drivers I run into wierd problems that I can't quite figure out such as playing games like supertux or the new one cold war or any game really it doesn't really go full screen it just centers itself in the middle and is surrounded by a black box.  Also when I shutdown the computer I don't see the shutdown screen it's just black for a minute til it finishes shutting down.  If I hit shift-backspace to get out of gnome the screen goes blank, I can then type in my username and pass then startx and gnome will start up again.  This wasn't an issue until I messed up some stuff on a previous install and reinstalled earlier this summer.  The wierd thing is before I couldnt get the shutdown stuff to work but games worked fine.  I am somewhat of a linux noob, but I try my best to find solutions myself but after a few weeks of searching I decided I would just ask you guys for help.

---

### Post by tseliot on 2006-08-04
First of all you don't need to reinstall Ubuntu every time the Xserver crashes.

Just do this:
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine


Ok, now about your problem with the driver:
try point 13 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I can't help you with the games (since I don't use them). I guess you should ask in the gaming section for that

---

### Post by burquedout on 2006-08-04
I am going to try that it threw me off because the guide didn't say it would effect my graphics card.  My X isn't crashing in fact everything works great except for the random problems I stated I honestly don't really care about reinstalling, I guess it's cause I'm so used to windows lol.  I already had everything backed up from the initial reinstall so the others wern't a bid deal really.  I was reinstalling every time thinking that I messed up in the installation of the driver and I was trying different ways to install every time yours is probly my favorite method :)

---

### Post by burquedout on 2006-08-04
Ok I did that problem 13 fix and it worked for that problem I'll post on the gaming forum about the other issue, though I'm sure it's a driver issue because without the driver I can play supertux full screen no problem just no opengl.  Is there no way that I can have a usplash for the startup and shutdown or maybe some other kind of splash?  Thanks

Edit:  I'm not going to post on the gaming forum because on the sticky on top it said anything relating to newly installed drivers has to stay in hardware.

---

### Post by tseliot on 2006-08-04
> **burquedout said:**
> Is there no way that I can have a usplash for the startup and shutdown or maybe some other kind of splash?  Thanks
try putting "splash" back together with "vga=792"

---

### Post by burquedout on 2006-08-04
Ok so that worked but the screen flickers wierd before it goes to the splash.  Also the splash isn't fullscreen it does the same thing as all the fullscreen games I've tried, It runs it at a lower resolution and instead of stretching it to fit the screen it just sits there in a box in the middle of the screen.  Also it's widescreen, if that makes any difference.

---

### Post by tseliot on 2006-08-05
> **burquedout said:**
> Ok so that worked but the screen flickers wierd before it goes to the splash.  Also the splash isn't fullscreen it does the same thing as all the fullscreen games I've tried, It runs it at a lower resolution and instead of stretching it to fit the screen it just sits there in a box in the middle of the screen.  Also it's widescreen, if that makes any difference.

Try vga=791

BTW it's not a problem if the bootsplash doesn't fit

---

### Post by burquedout on 2006-08-05
I did that and now I get a flash of white horizontal lines when I restart instead of flickering white lines.  What do those numbers mean?  Also you are right I don't really care about the splash not fitting the screen I was just thinking if I can find a solution to get that to stretch to fullscreen I would be able to get other things to stretch like that.

---

### Post by tseliot on 2006-08-05
> **burquedout said:**
> I did that and now I get a flash of white horizontal lines when I restart instead of flickering white lines.  What do those numbers mean?  Also you are right I don't really care about the splash not fitting the screen I was just thinking if I can find a solution to get that to stretch to fullscreen I would be able to get other things to stretch like that.

```
Try setting another resolution for GRUB. Have a look at this table:

                640x480 800x600 1024x768 1280x1024 1600x1200
---------------+-------+-------+--------+---------+---------
256 (8 bit)    |  769     771     773       775       796
32,768 (15 bit)|  784     787     790       793       797
65,536 (16 bit)|  785     788     791       794       798
16.8M (24 bit) |  786     789     792       795       799
```

and set vga=xxx according to your desired resolution

This is the link that table belongs to:
[http://wiki.archlinux.org/index.php/Grub_configure_examples](http://wiki.archlinux.org/index.php/Grub_configure_examples)

---

### Post by burquedout on 2006-08-05
Thanks I'm trying new stuff out now but I think I got it I figured out my problem with the games it was my xorg.conf file, it only had 1920x1200 as a resolution for all screen depths, I changed them all to also include a bunch of different fullscreen and widescreen modes and now games fill the full screen:D :D   I'm going to keep messing with stuff thanks for the help if I mess it up or have a question Ill post back on this topic you've been a huge help.

---

