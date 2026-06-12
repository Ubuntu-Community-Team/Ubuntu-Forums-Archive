---
title: "After Upgrade No Connection, Desperate!"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by pooja on 2009-11-21
Help me! Please!

Over the last 2 days I've been trying and trying to get Ubuntu 9.10 connected to the Internet. By now I've installed and reinstalled the whole OS at least 4 to 5 times.

How can I get Network Manager to connect to my home wireless via Terminal? 
Without connection I can't download Nvidia packages, nor any updates, nor can I report any problems. Please would see into my problem?

I have an hp laptop dv6000 series, dual booting Vista + Ubuntu however GRUB has overwritten Windows Vista's MBR. My home wireless consists of a router connected to an ACCESS POINT, Dlink but somehow Network Manager can't connect to it.

I typed [FONT="Courier New"]iwconfig[/FONT] and [FONT="Courier New"]lshw -C network[/FONT] in the Terminal. I'm attaching the results.

---

### Post by pooja on 2009-11-21
Please help me! I lost all the Java programming, NS2, LaTeX packages and I need to install them quickly back, I need them for University courses. Please, please, please help me!

---

### Post by pooja on 2009-11-22
I really need help, folks.
I need Ubuntu for University classes, please would you look into my problem?
Can I somehow install Wicd that worked just fine under 9.04 via usb pen? I can't install anything from Synaptic because I don't have Internet connection. Would someone please tell me step by step how to get Wicd working as it did with Ubuntu 9.04? Thanks

---

### Post by appraveen on 2009-11-22
I too am unable to connect to network after the upgrade...

anybody here?????

---

### Post by appraveen on 2009-11-22
hahaha......


UBUNTU GREAT UBUNTU............


I just restarted a number of times pulled out the power cord a few times after booting and now **dhan tana** the network did connect.

---

### Post by pooja on 2009-11-22
If it only was so easy for me too! 
I notice the access point of wlan0 is non associated, how do I get it associated to Dlink access point via Terminal?

---

### Post by AlexZaim on 2009-11-22
You're not the only one. Some say that Karmic's network manager is more or less faulty. I don't know, i tried to reinstall the old verision but it has it's dependencies so i fought i'd do something else: install wcid. It's just another network manager for linux. Works perfect, it's light weight, and i'm very satisfied ! 

Try it: you wouldn't know the difference! 

It has one dependence though... i think it was python? but i'm not too sure. forgot :(


My thread: [http://ubuntuforums.org/showthread.php?t=1330641](http://ubuntuforums.org/showthread.php?t=1330641)

---

### Post by pooja on 2009-11-22
Have already done that, didn't work for me so I've installed 9.10

---

### Post by pooja on 2009-11-22
hey I managed to fix the connection! 
I first gave this command from Terminal: 
```
sudo gedit /etc/wpa_supplicant.conf
```
and wrote:
```

network={
	ssid="dlink"
	psk="my_psswrd"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=CCMP TKIP
}

```
Apparently the system connected to my home wireless network but I still couldn't surf the net. When I again ran ```
iwconfig
``` I noticed wlan0 was now associated to the dlink access point. It had an address like say, 00:26:5A etc. I recalled it was different from Network Managers' one so I right-clicked on the NM's icon, Edit Connections, Wireless tab, "dlink", Edit. In the MAC field there was a different address so I just put it as the Terminal said and waited a couple of minutes. Finally Google homepage appeared and I could go to other websites too.

Now I'm updating the system.

---

### Post by AFI420 on 2009-11-22
you gave these commands from a fresh install? or were there other steps before?

---

### Post by gnusci on 2009-11-22
Try with wicd:

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

It is very smart network manager.

---

### Post by AFI420 on 2009-11-22
wicd doesnt find my network. doesnt find any

---

