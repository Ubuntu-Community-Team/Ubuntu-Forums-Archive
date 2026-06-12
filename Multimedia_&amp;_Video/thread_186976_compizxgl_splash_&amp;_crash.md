---
title: "compiz/xgl splash &amp; crash"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Staceman on 2006-06-02
I somewhat successfully got XGL+Compiz working on 3 different machines using the guide here: [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

It worked flawlessly on the machine with an ATI 9650 video card. I of course had to make a few changes for the other machines as they have nVidia cards in them, one being a laptop with a "GeForce2 Go" chipset, and the other having an older PCI Geforce2 MX400 card. The main change I made was adding "+extension Composite" to the Xgl command line, since I was getting errors regarding the composite extension early on. I also added the [www.beerorkid.com](www.beerorkid.com) and xgl.compiz.info sources to sources.list, updated and then got the latest versions of everything. Oh, and I also enabled the RenderAccel and AllowGLXWithComposite options in xorg.conf.

On both machines with nVidia chipsets, Xgl and Compiz load up and appear to be working fine, I get all the effects. However, the Ubuntu/Gnome splash screen stays in the middle of the desktop, stuck on the "Window Manager" part. After about a minute, the splash screen goes away, and then it crashes me back to the GDM login screen.

Has anyone else ran into this problem? I also can't seem to find any logs that have info about this crash.

---

### Post by franestepona on 2006-06-02
I only have problems with those programs. I tried to configure them in the same link, and got stuck in the splash screen as well. I have ATI mobility radeom 9600.

---

### Post by Staceman on 2006-06-02
Interesting. My card is pretty much the same thing, X identifies it as a "9600 Mobility", the vendor is Sapphire. Went without a hitch. The only thing I possibly done different than the guide shows, is that I installed xserver-xgl, compiz, and compiz-gnome through Synaptic. Same difference pretty much. The splash screen does seem to stick around longer than it should on the ATI also, but clicking it makes it go away. I had it working even before I added the "quinns" sources to sources.list. The only thing different that the new sources/files brought, was that the menus are no longer wobbly, they just fade. I'll figure that out. (well, ok, to be totally honest, X did lock up upon restarting it right after I installed the updated stuff, but it was fine after a reboot.)

One thing I've noticed while trying to figure out the nVidia problem, is that somehow X and/or Gnome/GDM, seems to stop looking at the .Xsession file eventually, totally ignores it. I found a workaround for this, sort of borrowing from another guide. I created this file:

sudo vi /usr/share/xsessions/xgl.desktop

and it contains:

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
## Exec=/usr/bin/startxgl.sh
Exec=/home/sdunkle/.Xsession
Icon=
Type=Application

The commented out entry was for a script that the other guide suggested. In addition to forcing X to look at the .Xsession file again, this also creates another session to choose from on the GDM login screen, so that you don't have to mess with your main session. Unfortunately, you still have to edit and comment out the RenderAccel and other added options in xorg.conf before using your regular session, and you also have to re-enable dri and GLCore if you had it, otherwise your session freezes as soon as you start Firefox, forcing you to reboot.

Did you try adding the compiz sources for apt, and getting the updated required files?

Anyway, still having the problem with the nVidia machines, any help would be appreciated, even just confirmations that others are having the same problem! :)

---

### Post by nemesa on 2006-06-07
I'm having exactly the same problem... The splash screen stays on the screen for a while...

:confused:

---

### Post by Staceman on 2006-06-07
As long as it doesn't crash on me, I don't mind the splash screen sticking around a little bit.

I have found an interesting thing though. I can get the machine with the ATI screen to crash as soon as the splash screen goes away, just like what I'm experiencing on the machines with nVidia cards, if I enable the 'dock' plugin.

I'm pretty sure I don't have dock enabled on the nVidia machines (I haven't messed with them in a few days) but this may offer some insight into the problem...

---

### Post by Staceman on 2006-06-07
Well hot damn...

Upon checking out the machines with the nVidia video chipsets today, lo and behold, both of them did indeed have the dock plugin enabled by default!

I disabled the dock plugin, made the required changes in xorg.conf, restarted X, splash screen came and went, and neither machine crashed! :)

So there you have it. The "dock" plugin is evil. This bug is probably documented somewhere, though I did do my share of reading and searching around.

The splash screen still hangs around a while, but hey, I can live with that, as long as everything else works. ;)

---

### Post by JeremyHarrison on 2006-06-11
I have been having exactly the same problem. It was getting so bad that I couldn't stay logged in for more than about 5 mintues at a time.

I've been looking into solutions. I think I might have found one. I think that there must be a problem with the directions a lot of us are following from this site:

[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

I think the problem lies in the way that it suggests you start Compiz as a .Xsession.

I have found another site that provides very clear instructions that you can use without changing/breaking anything in your existing configuration.

Go to the following page and step through the instructions that they provide:

[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_(or_KDM)](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_(or_KDM))

I've just tried it and I've been solid for more than 5 minutes! <grin> I'll edit this post after a couple of hours if it appears that the problem is gone completely.

By the way, it's already gotten rid of the lingering splach screen which is a good sign.

If anyone else gives it a try, report your results to help others.

Edit 1: Well, I can report that it doesn't like screen saves. After about 30 minutes I was getting a little over confident and figured I would try out a GL-based screen saver. I am able to get it to crash immediately by doing this. So avoid screen savers.

Edit 2: Okay, now we're holding about 3 hours after the change and it's way more stable than before but it's still subject to crashing from time to time. I would definitely recommend the above method to anyone who is experiencing the problems mentioned in the first post of this thread.

Edit 3: 9 hours and going strong. No crashes during normal use. (Only when I start tweaking my compiz settings, turning things on and off...)

---

