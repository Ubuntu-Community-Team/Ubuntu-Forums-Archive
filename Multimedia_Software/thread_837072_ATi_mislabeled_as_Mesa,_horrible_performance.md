---
title: "ATi mislabeled as Mesa, horrible performance"
date: 2008-06-22
forum: Multimedia Software
---

### Post by JerichoKru on 2008-06-22
I followed this guide here:  [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

After doing all of "Method: 1" and used```
fglrxinfo
```

It was mislabeled as "Mesa"


I followed the link to a later section of the page to try to fix the issue, only to be confused on what they are suggesting ( It seems confusing to me, as a new user to Ubuntu...but have used Fedora in the past...but that has a geforce 7600gs)

I didn't see anything specific in the stickies regarding this issue, so I posted here.  I apologize if it is listed somewhere and cannot find it.

any assistance will be grateful


System Specs:
AMD Athlon 64 x2 4200+
2gb of ram
ATi HD 2600XT
Ubuntu 8.04 x86_64

If you need anything else, I shall provide it.
[RIGHT]~JerichoKru[/RIGHT]

---

### Post by JerichoKru on 2008-06-24
Well, right now it appears to be fixed...not sure what I did.

It's detecting it properly...but, now (think) I don't have proper 3D acceleration.

I will try the newest ATi drivers to see if it fixes the issue.

( a certain game running in wine is not running properly, aka crashes, when it worked on a Fedora 9 install on an older tower  ](*,) )

---

### Post by socngill on 2008-06-24
There was a recent upgrade for the fglrx files, which I think your ATI card should use.  Could be wrong but that's what mine is supposed to use (apparently) although it doesn't seem to want to!!

So that upgrade could have fixed it.

---

### Post by Gunman1982 on 2008-06-24
Did you reboot after installing the fglrx driver? Maybe that was the fix ;-)

About the game and wine, maybe you should post that issue with some more information (like what game, wine version, driver version of fglrx) in the wine section in this forum. Some games run with wine in combination with a nvidia card but not with an ati card.

---

### Post by socngill on 2008-06-24
Just out of interest, are there any graphics cards that just work out of the box...?

I might give up with my ATI (X1650) and buy a different generic one.  I could swap it with my media machine (Radeon 9250) but I don't think that works on a 1440x900 screen :(

---

### Post by Pjotr123 on 2008-06-24
> **socngill said:**
> Just out of interest, are there any graphics cards that just work out of the box...?

I might give up with my ATI (X1650) and buy a different generic one.  I could swap it with my media machine (Radeon 9250) but I don't think that works on a 1440x900 screen :(

Tip: buy an Nvidia. Not the latest model, because the restricted driver in the Ubuntu repositories isn't the latest version. 

Plug the card in your machine and then do this:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

---

### Post by socngill on 2008-06-29
I thought I would post in here instead of starting a new one.

I am having the same problems.  I have gone through the fglrx install process but as with the guy who started this post it is labelled as MESSA.

When typing FGLRXINFO I get the following:

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)


And when I go into ATI Catalyst settings it confirms that MESA is being used for OpenGL.

The instructions I got for installing the FGLRX on these forums said to uninstall MESA drivers by removing the xserver-xgl package.  That however, is already not installed.

Any ideas what I need to do to fix this and get my ATI X1650 working?

---

### Post by socngill on 2008-06-30
Anybody got any advice on my post above?  Can I just go into the package manager and remove everything labelled as MESA - or would this cause further problems?  Don't want to go deleting things I shouldn't :)

---

### Post by markbuntu on 2008-06-30
There are a few long running threads already about the particular problems of the ATI X1650 video card and fixes for it. You should try to find them.

Go to the top of the forums, where all the forums are listed, and do a search from there.

---

### Post by stchman on 2008-06-30
All you have to do is just enable the ATI proprietary driver in the restricted driver manager.  The xorg-driver-fglrx supports teh HD 2600 series of cards.

---

### Post by socngill on 2008-07-01
> **markbuntu said:**
> There are a few long running threads already about the particular problems of the ATI X1650 video card and fixes for it. You should try to find them.

Go to the top of the forums, where all the forums are listed, and do a search from there.

Tried searching previously and found lots of threads for ATI problems, but not my specific card.  This was specifically for a issue I was having - but I shall search again.


> All you have to do is just enable the ATI proprietary driver in the restricted driver manager. The xorg-driver-fglrx supports teh HD 2600 series of cards. 

Every time I have tried enable this I get a blank white screen on restarting the X-Server.  I shall try again this evening and see what happens...

Also, would that solve the problem of my machine using MESA drivers when I have installed the FGLRX drivers?

---

### Post by NotTheMessiah on 2008-07-01
> **socngill said:**
> 
Also, would that solve the problem of my machine using MESA drivers when I have installed the FGLRX drivers?

I've read somewhere that people have fixed this with envy-ati.
My card is not even recognized :) HD4850 - in the restricted hardware box. You have to soldier on :)

---

### Post by socngill on 2008-07-01
> **NotTheMessiah said:**
> I've read somewhere that people have fixed this with envy-ati.
My card is not even recognized :) HD4850 - in the restricted hardware box. You have to soldier on :)

I shall count myself lucky then!

Shall continue to soldier on as usual - but it is a bit annoying when you've spent money on something and it doesn't work (properly).  Especially when that item controls the smoothness of web pages, rendering of graphics etc etc.

Soldiering on.. I think there should be a smilie for soldiering on :)

---

### Post by markbuntu on 2008-07-01
If you use envy be sure to remove the old driver before installing any new one.

If you tried Method 1 and it did not work for you and envy also did not work then try Method 2. It always worked for me.


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

After doing this run Update Manager to get the updated restricted linux modules. Update Manager always seems to have them for me when I update my ATI driver.

---

### Post by socngill on 2008-07-02
> **markbuntu said:**
> If you use envy be sure to remove the old driver before installing any new one.

If you tried Method 1 and it did not work for you and envy also did not work then try Method 2. It always worked for me.


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

After doing this run Update Manager to get the updated restricted linux modules. Update Manager always seems to have them for me when I update my ATI driver.

I had a bit of a play with it last night and did some of the steps from Method 1 (I used method 2 originally) and it seemed to install a few bits and when I restarted the X-Server it did make a difference.  the graphics are much crisper and smoother (and Firefox scrolls smoothly!!).  So from that point of view it has made a big difference.  It is still all labelled as Mesa instead of FGLRX which is weird, and watching video in full screen is still choppy (tested with IPlayer only) but that is still an improvement on previous performance.  That's not a major issue to be honest.  

It's just strange that it is still labelled as Mesa?  Anyway, I am pretty happy with the performance now so I shall probably leave it alone for now.

But the one question I would ask is that if I went into the package manager and removed all traces of Mesa would that seriously screw up my system or would it help?

Big thanks to all those who have helped.

Edit: Answered my own question about Mesa last night.  went to uninstall it and looked at the list of software it would remove - it was about 40!  So I won't be doing that :)  Also noticed that I had both ATI drivers and ATI-Envy drivers installed, so removed the Envy ones.  Doesn't seem to have made any difference but at least the system is a bit "cleaner" :)

I shall try the compiz forum in the reply below tonight and see how I get on.

---

### Post by markbuntu on 2008-07-02
If you want to fix your full screen playback problem make sure that 

unredirectfullscreenwindows

is checked in Advanced Desktop Effects Settings/General (or with the compizfusion icon, they are the same thing).

If that does not make a difference or you are not using desktop effects, try the directions here:


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by NotTheMessiah on 2008-07-03
I managed to install the 8.6 catalyst with the second method:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

My card is now recognized as Radeon HD48XX and compiz is working. But Hardy crashes every time i try to watch TV with Kaffeine. I can use MeTV

It's not exactly stable.

---

