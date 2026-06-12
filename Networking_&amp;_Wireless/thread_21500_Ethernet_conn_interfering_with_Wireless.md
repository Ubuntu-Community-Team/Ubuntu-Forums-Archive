---
title: "Ethernet conn interfering with Wireless"
date: 2005-03-22
forum: Networking &amp; Wireless
---

### Post by taki on 2005-03-22
Okay, after a lot of trouble, I finally got ndiswrapper and my Broadcom chip working just fine.

The problem I have is that every time I boot up, the ethernet connection (eth0) is set to Active, even though it's not connected to anything. The computer takes the ip from there, ignoring the active (and connected) wlan0.

Moreover, the bootup process hangs at Configuring Network, likely because eth0 is set active but has nothing to pull from.

How do I keep eth0 from going active?

Am using Hoary, btw, and everything else seems peachy. Well, having issues with xorg and my ati card and changing screen rez, but I'll deal with one thing at a time.

---

### Post by techlord on 2005-03-22
what is in your /etc/network/interfaces file.

In this file you should a portion of it that looks like this

mapping hotplug
script grep
map eth0

the easiest way to stop eth0 from comming up at boot time, and make wlan0 your primary would be to change this to 

mapping hotplug
script grep
map wlan0

I hope this helps.

---

### Post by taki on 2005-03-22
Oh yeah! You have the undying gratitude of a Linux newb. I'm a die-hard OS X user, and a grudging Win XP user for some work stuff, but I figured it was time to jump in. So far, Ubuntu is not disappointing.

And rapid help like yours has made the tricky parts not only tolerable but strangely satisfying as I get things to work.

Thanks again:)

---

### Post by CAPTAIN RON FL on 2005-03-22
How do you find  " /etc/network/interfaces file."
I am new to this stuff.
I have a new Toshiba Satellite M35-S109 and a NetgearWG511 wireless pc card.
It also has built in etho. I have not put Hoary on my hdd yet. I tried hoary live 7 but no joy.
I am willing to do a hdd install if I can get my wireless to work.....shaking a little though....being new and all.
I looked at the ndiswrapper route and it seem too hard for me.
Thanks, Ron

---

### Post by taki on 2005-03-23
The way I did it was to open a terminal, then at the command prompt type:

sudo gedit /etc/network/interfaces

gedit is the the gui-based text editor, and the sudo part lets you edit a file as root. Without that, it won't let you make changes. That's why if you open the Text Editor from the Applications menu, you can't make changes to system files. The program needs to be run as root.

As for ndiswrapper, it took me a while to get it working. First I had problems with installing it properly, which were fixed by making sure I had the right version linux headers installed before compiling it. Then I didn't realize I needed not only the proper .inf file for the drivers, but the accompanying .sys file as well. But now after a few days of searching, testing and cursing I have connectivity without a problem and I don't need to run ethernet cable the length of my apartment. I'd say experiment. You shouldn't break anything as long as you stick with the Ndiswrapper How To page ( [http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper) ). You can get help here on the forum as well.

In regards to your networking needs for a laptop, this seems to be interesting:

[http://higgs.djpig.de/ubuntu/www/hoary/doc/laptop-net-doc](http://higgs.djpig.de/ubuntu/www/hoary/doc/laptop-net-doc)

Although I can't find any documentation on how to actually configure it as of yet.

---

### Post by reid on 2005-04-26
[QUOTE=taki]Okay, after a lot of trouble, I finally got ndiswrapper and my Broadcom chip working just fine.

The problem I have is that every time I boot up, the ethernet connection (eth0) is set to Active, even though it's not connected to anything. The computer takes the ip from there, ignoring the active (and connected) wlan0.

Moreover, the bootup process hangs at Configuring Network, likely because eth0 is set active but has nothing to pull from.

How do I keep eth0 from going active?

Am using Hoary, btw, and everything else seems peachy. Well, having issues with xorg and my ati card and changing screen rez, but I'll deal with one thing at a time.[/QUOTE]
 I have a similar problem.  I am trying to share my connection through this ubuntu machine.  I have my WiFi set up as wlan0 fine with ndiswrapper (that was well worth the effort).  Whenever I activate eth0, using the gnome 'Networking settings' tool it becomes the 'Default Gateway Device'.  I do not want that to happen because I am connected to the 'net through wlan0.

I changed my /etc/network/interfaces as techlord suggested (thanks)
and then did:
 sudo /etc/init.d/networking restart just to see if that helped, but it did not.

What obscure text file do I need to change, heh heh?

---

