---
title: "onboard ATI Radeon Xpress 200"
date: 2005-12-03
forum: Multimedia &amp; Video
---

### Post by rainbowjoshua on 2005-12-03
Hello Community!

I'm running a nice new MSI board called the RS480M2 with an ATI Radeon Xpress 200 onboard video card with 128MB of RAM, TV output, all the goodies.  Also an onboard ATI sound chip (I think it's the IXP 400 which worked beautifully on my fresh Breezy install).

Everything went well for the installation except X wouldn't work.  Once I got my monitor sync ranges right though, and switched to the VESA driver (the default ATI driver, which does detect the name of the video card at least, and the PCI bus address, doesn't seem to work).  At this point the video worked in VESA at a pretty low level.

When I installed the fglrx stuff from Ubuntu, I had more luck.  The video is now operating in it's proper mode (1280x1028x24bit).  I get the ATI control panel, but it doesn't recognize the card, listing unknown.  I found an enormous thread about this motherboard, and very similar issues:

[http://scottstuff.net/blog/articles/2005/03/17/msi-rs480m2-il-athlon-64-motherboard-mini-review](http://scottstuff.net/blog/articles/2005/03/17/msi-rs480m2-il-athlon-64-motherboard-mini-review)

Okay, next.  Going to the ATI website, and searching their knowledge base for "Radeon Xpress 200", you find several driver versions that claim to be for this card.  I have installed them every way I could.  Every time though, I would run the fglrxconfig and it would list the cards it worked for, and mine wasn't on there (even though it was listed under it on ATI's website!).  So I go through the configuration process again and again.  And over and over, it says it can't find my card!

I would reconfigure my xserver-xorg and try different drivers, and the one that works best is fglrx, however, the REAL ISSUE...

Video, especially at full screen, just crawls.  I've installed every codec and everything plays, DVDs play, etc etc, but when I fullscreen it... I get so jumpy that it's not worth the bother to watch it.

Obviously, I'm not quite using the right video driver!  Mostly, when I would run the fglrxinfo, I would get it telling me I'm running Mesa, but now, after messing with things for a while, I get:

/usr/X11R6/bin/fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


I know I can install an nVidia driver and make this error message go away, but it is replaced by another one when I do, and I don't have an nVidia card.

Anyway, I'm so stumped and I know this is possible, because that post contained at least a few success stories further down.  There's got to be a way to get the right driver in for this chipset!  All help is imensely appreciated!

Joshua

---

### Post by mlomker on 2005-12-03
I don't have experience with that particular card but I have written a [how-to]("http://ubuntuforums.org/showthread.php?t=78466") that has worked for many people.  Perhaps you've already used it, I don't know.  If you are getting the libGL error then something is wrong.

If you haven't done too much with the operating system yet then I'd recommend a clean installation and following my how-to.  If you have a problem then I'll do what I can to help you out.  The Rage3D forum link on the how-to page is also a good resource.

---

### Post by rainbowjoshua on 2005-12-03
Actually, your how-to was about where I started.  I removed all the ubuntu fglrx drivers, and I built the ubuntu packages from the installer and then I installed the packages, but for some reason, I never got fglrxinfo to show anything but Mesa, until now, that it's broken.

It's too late for me to reinstall, I hate to say.  The thing that gets me worst is that when I finally get the drivers installed, they say they can't see the video device, even when I give it the bus id, and when I run dpkg-reconfigure xserver-xorg, it catches even the name "ATI Radeon Xpress 200".

Thanks, IM if you want.  :)
Joshua

---

### Post by mlomker on 2005-12-03
[QUOTE=rainbowjoshua]I never got fglrxinfo to show anything but Mesa[/QUOTE]

You'd have to look in your logs for the reason.  /var/log/kern.log or Xorg.0.log would hold the answer.

---

### Post by adam.tropics on 2005-12-03
I have the exact same card, and had the same problems!

The card is supported by the Mlomker how to as above....however....

The fglrx will only show mesa until linux restricted modules are removed. Be careful if you are using madwifi, in which case I reccomend [this]("https://wiki.ubuntu.com/MoreRecentMadwifiHowto?highlight=%28morerecentmadwifihowto%29") first.

Then try the ati drivers howto again, having got rid of restricted modules and covered yourself with relation to wireless drivers, and all should be well.

The only problem I never sorted was that of resolution. I have a wide screen so had to manually edit xorg.conf for the 1280x800. However I don't think you will have that problem, guessing though!

As for the DVD speed etc, same here, but was cured by enabling DMA on the DVD and hard drives. Reccomend [Automatix....]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix")it doesn't seem you have tried it. It is very useful indeed, and quite apart from taking care of dma etc, it installs many of the smaller things that can drive one mad finding and sorting, all in one hit. It takes a little while though if not on a fast connection, worth being aware of.

Hope this helps.

---

### Post by wargames on 2005-12-04
Hi

I have that same motherboard and I used this following How-to: in order to install the 8.16.20 driver and it worked.

How-to: Ati 8.16.20 (easy Way)
[http://ubuntuforums.org/showthread.php?t=76057&highlight=How-to%3A+Ati](http://ubuntuforums.org/showthread.php?t=76057&highlight=How-to%3A+Ati)

Hope this helps. :)

---

### Post by rainbowjoshua on 2005-12-04
Adam!

Thank you for your very informative reply!  I just did what the ubuntuguide recommends with my sources.list and it then told me there were updates available, so I updated.  I'm going to restart X and see if it did anything, but I wanted to clarify with you exactly which packages I need to remove to make this work.  Also, I've run the installers and built and installed ubuntu packages, and I wonder if there is any way I can make sure all that is cleaned up.

Right now, the error I'm getting seems to be related to the Nvidia driver.  Do you have that package installed?  Also, WHICH linux restricted packages are we talking about?  One of them, I try to remove and it tells me it wants to take ubuntu-desktop with it.

Also, enabling DMA for the IDE, do you do that in the bios?

I appreciate your help so much!  I am on IM if you can talk direct.  Thank you!
Joshua

---

### Post by WildTangent on 2005-12-04
I have the exact same board, and I haven't yet had any luck with it. :( However, I'm getting a new video card for christmas, so hopefully that will solve the problem. I might give your solution a try though in the mean time.

-Wild

---

### Post by adam.tropics on 2005-12-04
DMA was enabled as one of the things done by Automatix. But if you need to do it manually for some reason,# sudo gedit /etc/hdparm.conf

and add the lines:

/dev/hdb {
dma = on
}

Change the drive to whatever it is, hda2 or whatever. That one's a massive improvement for the dvd thing. Save and exit.
Restricted modules:
First type in terminal, uname -r  This will give you the current kernel version. Next, open Symantic Package manager, search for linux-restricted-modules. It will come up with a list, one of which, will pretty obviously relate to your current kernel. Uninstalling it will not cause a problem in terms of ubuntu desktop. Ubuntu desktop is just a definition if you like, of all the packages that make up ubuntu.(this is how it was explained to me) This is one. Removing it causes no problems, although it is advisable to replace it before upgrading to the next ubuntu version whenever that may be!

The nvidea error i assume is related to the above, but if it happens after all this, paste it in here and see if anyone recognises it!! The forums here are the best I've come across, and very well populated, so the odds are good!

---

### Post by rainbowjoshua on 2005-12-04
You guys... that's fantastic.  I did eventually break down and reinstall when I couldn't get X to come up at all anymore, but this time I knew how to get ndiswrapper working from the CD and I followed that howto (the easy one), and tada!

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series SW TCL Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```

And Automatix is running right now, and it sure is saving me a hell of a lot of time and effort!  Thanks for all your help everyone.  I can't wait to try a DVD and see if it works reasonably now!

Joshua

---

### Post by adam.tropics on 2005-12-04
Well done! (take notes about what works.....trust me, it's the safe bet!!!)

---

