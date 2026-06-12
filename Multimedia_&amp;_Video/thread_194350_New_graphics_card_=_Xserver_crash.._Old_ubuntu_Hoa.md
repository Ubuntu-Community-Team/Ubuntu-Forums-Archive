---
title: "New graphics card = Xserver crash.. Old ubuntu Hoary Hedgehog"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by Mazey on 2006-06-11
Hi, I haven't used my Ubuntu install for a while, and while I were using Win, i got a new Graphic card, and a new Motherboard. My problem is that Xserver crashes on boot, all I get is the command line. I've tried to run "sudo dpkg-reconfigure -phigh xserver-xorg"

But then It can't modify the configfile, because it allready excist... So I tried to remove the file, but it doesn't help..
I also tried to get the newest driver from:

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)

But it says I allready have the latest versions..

 Since I can't get any GUI, I can't get the update.. I'm pretty fresh in linux..


Thanks, (Sorry if this is in the wrong section)

---

### Post by campnic on 2006-06-11
Well, lets try to figure this out.  I'll need some more information

What type of graphics card is it?  What type of monitor are you using?  It sounds like your xorg.conf file is setup incorrectly for your combonation.  I see fglrx, so that suggests ATI, is that what you are using?  Depending on what card you are using there are a couple different things that could be happening.

---

### Post by Mazey on 2006-06-11
[QUOTE=campnic]Well, lets try to figure this out.  I'll need some more information

What type of graphics card is it?  What type of monitor are you using?  It sounds like your xorg.conf file is setup incorrectly for your combonation.  I see fglrx, so that suggests ATI, is that what you are using?  Depending on what card you are using there are a couple different things that could be happening.[/QUOTE]

I'm using a Radeon 850 XT...
Everything was working perfectly till I got it..(and the motherboard...)

Thanks

---

### Post by Mazey on 2006-06-13
Now I tried to reinstall Ubuntu, but after the install it still didn't work, even the live cd crashes on startup.. I can only run it in graphical safe mode. What can be wrong?!

---

### Post by glasscleaner on 2006-06-13
samething as me?

[http://www.ubuntuforums.org/showthread.php?t=196150](http://www.ubuntuforums.org/showthread.php?t=196150)

---

