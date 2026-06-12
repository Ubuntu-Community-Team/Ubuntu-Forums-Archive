---
title: "Locating Wireless access points Available?"
date: 2005-03-02
forum: Networking &amp; Wireless
---

### Post by jMack on 2005-03-02
Hello-

I've done a few searches; hopefully this isn't already posted.

I'm a noob with Ubuntu.  Love it so far.  Be nice ;)

I'm trying to see if there's a way to 'SEE' what wireless connections are available in the vicinity of my laptop.  I've got a Toshiba Satelite M35X-S111 laptop with a D-link DWL-g650 wireless card.  The card appears to work (possible hangups though), when I manually type in my home router's address and WEP.  I just happen to have it at work, and see that i'm getting some connectivity to an Access Point, and I'm curious to see what it's name is so I can try and connect.

Is there any program that shows what Access Points are available in the area by name?

---

### Post by alastair on 2005-03-02
You could try :

iwlist <device> scanning

e.g.

iwlist wlan0 scanning

---

### Post by lordofkhemenu on 2005-03-02
[QUOTE=jMack]Hello-

I've done a few searches; hopefully this isn't already posted.

I'm a noob with Ubuntu.  Love it so far.  Be nice ;)

I'm trying to see if there's a way to 'SEE' what wireless connections are available in the vicinity of my laptop. I've got a Toshiba Satelite M35X-S111 laptop with a D-link DWL-g650 wireless card. The card appears to work (possible hangups though), when I manually type in my home router's address and WEP. I just happen to have it at work, and see that i'm getting some connectivity to an Access Point, and I'm curious to see what it's name is so I can try and connect.

Is there any program that shows what Access Points are available in the area by name?[/QUOTE]
Looking for something like Netstumbler for windows?

---

### Post by jMack on 2005-03-03
In windows you can just right-click on your little wireless-network task button and ask to see all available wireless connections.

'tis all I'm interested in.

From here i could configure a Network setting to use one of the available connections...is there another way?

-EDIT-
I just tried running the command.  It appears to do what I'm interested in doing although it found nothing; will test again around a known wireless hub.  It would be a nice feature if this was wrapped-up in the Network Setup Wizard so you wouldn't have to know precisely what the wireless hub address/name is.

I'm all for more GUI than Terminal.  It is the way Linux will conquer all, in my opinion.

---

### Post by gny on 2005-03-03
As stated before you can use the command: 

sudo iwlist <interfacename> scanning 

for example:

sudo iwlist eth1 scanning

You can also check out airsnort. which you also can use with a gps for wardriving and it has a nice gui.
playing around with WEP? look for airodump and aircrack.

---

### Post by alastair on 2005-03-03
There's a new application coming along called "NetworkManager" that works very similarly to the NT wireless/network tool. I am not sure it is completely ready for prime time, but some people have had success with it already. Worth having a look at it, if only to watch progress :

[http://www.redhat.com/magazine/003jan05/features/networkmanager/](http://www.redhat.com/magazine/003jan05/features/networkmanager/)

Work in progress!

---

### Post by grakhul on 2005-03-06
I tried the command listed above and it works like a charm, thank you.
sudo iwlist eth1 scanning

Now.  Are the programs listed above better than kismet?  I have downloaded kismet and have yet to do a "configure" "make" as I am relatively new to Linux.  I can hold my own around the O.S.,  but when it comes to more advanced stuff I have to read read.

---

