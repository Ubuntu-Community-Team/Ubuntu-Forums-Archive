---
title: "Belkin wireless network card (F5D7010uk) help!"
date: 2005-03-23
forum: Networking &amp; Wireless
---

### Post by Jason-X on 2005-03-23
Hi all

I've just managed to get my **Belkin wireless notebook network card (F5D7010uk)** working on a HP(OmniBook XE3) laptop. I followed the instructions using ndiswrapper and it seems to work OK. The only problem I have is that it stops working now and then. It normally works after a reboot or if I go into **system configuration > networking** and enable it again.

The one thing I did notice whilst using ndiswrapper was when I typed the command **"ndiswrapper -l"** to list the installed drivers I got this output:

[B]Installed ndis drivers:
rt2500  hardware present,fuzzy[/B]

Fuzzy does not sound too good to me :???:. Has anybody body else had this output and if so is there a way around it?

Also have I got the correct driver? I got the driver from here: [ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip). 

I pleased to have it working with Ubuntu, but it would be nice to make it more stable. Any help would ne much appreciated.

Thanks Jason  :smile:

---

### Post by Jason-X on 2005-03-23
Another thing I have just noticed is that my mouse stops working at exaclly the same time as the network card stops working.

The only way to get them both back is to reboot. There must be a link there somewhere. :???: 

Thanks in advance.

Jason

---

### Post by Jason-X on 2005-03-24
Ok I've discovered something else.

When I lose connection I go to **system configuration > networking** and everything looks fine. The ESSID setting is set to **"Belkin54g"**

When I go to the Terminal and type:

**iwconfig**

It says that ESSID is set to **off/any.**

If I change it back to "Belkin64g" by typing:

**sudo iwconfig wlan0 essid belkin54g**

It starts working again. So somehow this setting keeps getting lost. Is there any way to make it stick?

As I was typing this my mouse and card stopped again and I had this message in the terminal:

[B]Message from syslogd@localhost at Thu Mar 24 08:10:14 2005 ...
localhost kernel: Disabling IRQ #9[/B]

Maybe this could help point me to the problem.


Thanks Jason

---

### Post by Jason-X on 2005-03-26
*bump*

---

### Post by spd106 on 2005-03-28
Hi,

Not sure if this will be any help, but check which kind of card it is.

I assume you've looked at the ndiswrapper list, 

[http://ndiswrapper.sourceforge.net/phpwiki/index.php/List](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List) 

for belkin driver support and been confused by the number of different ones listed, i know i was :confused:  

I have the belkin f5d7010uk rev3 card with the broadcom 4306 chipset, which works on warty 4.10 with ndiswrapper 0.12 and the dell truemobile driver.

it's not perfect, as i have to reload the ndiswrapper module every time i start up.


I blame belkin for not helping out with open source drivers. 

Good luck in your search

---

### Post by Jason-X on 2005-03-29
Have you tried adding "ndiswrapper" to your /etc/modules?

Here is mine:

[B]psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
ndiswrapper[/B]

This starts ndiswrapper when you boot up.

I have started another post relating to this as I have upgraded to hoary:

[http://ubuntuforums.org/showthread.php?t=22363](http://ubuntuforums.org/showthread.php?t=22363)

If you think I have the wrong driver could you let me know and I will try the driver you  have used. Could you give me a link to  the driver as I am not sure which one you was on about.

Thanks Jason

---

### Post by Jason-X on 2005-03-29
I'm such a dumbass :-? 

I finally got it working. I had to adjust some firewall settings on my router and it works perfectly now.

DOH!! #-o

---

