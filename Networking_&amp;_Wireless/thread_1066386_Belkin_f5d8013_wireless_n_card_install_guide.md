---
title: "Belkin f5d8013 wireless n card install guide"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by Sk8man on 2009-02-10
ok, i thought id just make a guide for u people who have this card.

Step 1: ok first you are going to need ndiswrapper, this is easy, go to Applications>System>Add\Remove... then search on "ndiswrapper" mark for installation, 

Step 2: ok now we need wine (if u really really dont want wine i can help with this but ill talk about that later) now search for wine (in add\remove)(if u cant find it make sure your searching all "available" applications then try again) and mark that for installation, then click apply changes.

Step 3: ok now go to a search engine (a.k.a. Google, dogpile,..etc,etc,) and search for "belkin f5d8013 driver" click on first link and follow till u get the driver,

Step 4:now install the driver using wine to a folder of your choosing, now go to this new folder (wer you installed the belkin driver) and look for a folder named xp2x (or something like that) and look for a .inf file
once you find it copy it to your desktop,

Step 5: ok now fire up ndiswrapper (application>system>windows wireless drivers) and click on install driver, now select that .inf file on your desktop and then click install, and viola! 

it should work flawlessly, i encountered no problems, if u do get problems firstly i find another .inf file for your card and try installing that, cheers!:popcorn:

oh to not installing wine, i can send u the .inf file if you need me to, but it might take me a while to send it:P

---

### Post by Psyphre on 2009-03-07
thanks for sharing your guide.

I gave it a try but seem to be stuck on installing the inf file.

I downloaded 2 drivers (version 1 and version 3).

Version 1: Says hardware is not present even though it is in and lights are on.

Version 3: Says invalid driver. (makes no sense).

According to Belkin's website I should be using version 3 since that is the version written on my card.

Any ideas? Thanks in advance.

---

### Post by slithymonster on 2010-09-04
I followed these steps, and like *Psyphre*, I got the "invalid driver"  error message when I tried to install the INF file.

**Here's how to fix it**
[LIST=1]
[*]Instead of just copying the INF file itself, I coped the entire directory to a new location.  I chose "~/Drivers/Belkin"
[*]Then I went on the command line and went to the directory ("cd ~/Drivers/Belkin")
[*]Finally I used the command line to add the driver ("sudo ndiswrapper -i XP2K/rt2888860.inf")
[/LIST]

Note, if you already tried using the GUI, make sure you use the GUI to remove the invalid driver.

---

### Post by wolvesdread on 2011-06-12
_**No WINE needed.**_  This solution worked great for me using just ndiswrapper command line with the version 1xxx driver..  I have the Belkin F5D8013 ver 1011.  Thanks!:D

**Here's how to fix it**
[LIST=1]
[*]Instead of just copying the INF file itself, I coped the entire directory to a new location.  I chose "~/Drivers/Belkin"
[*]Then I went on the command line and went to the directory ("cd ~/Drivers/Belkin")
[*]Finally I used the command line to add the driver ("sudo ndiswrapper -i XP2K/rt2888860.inf")
[/LIST]

---

