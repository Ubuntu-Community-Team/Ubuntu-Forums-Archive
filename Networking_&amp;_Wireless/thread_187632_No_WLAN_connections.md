---
title: "No WLAN connections"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by zaiyon on 2006-06-03
Hi, I have the Dell Inspiron 1300.
My problem is that Windows does find some secured LAN networks arround, and I cannot find these when in Ubuntu Dapper.

I try to use kwifimanager for this task, but it says "not connected".
Airsnort just doesn't find anything.

Here are some informations:

**lspci**
```

0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

**dmesg**
```

[4294687.016000] bcm43xx driver
[4294687.957000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[4294687.966000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

**ifconfig**
```

eth0      Protokoll:Ethernet  Hardware Adresse 00:14:22:AA:FA:FB
          inet Adresse:192.168.0.27  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::214:22ff:feaa:fafb/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4767 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:1721831 (1.6 MiB)  TX bytes:478761 (467.5 KiB)
          Interrupt:217

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

```

**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

I just guess something is wrong. But since I'm new to this WLAN world, I can absolutely not tell what. The driver complains a bit in dmesg, but it seems to work fine since the device shows up in iwconfig.

I didn't to anything, this is a fresh ubuntu installation and everything works just great, except this WLAN thing. Can someone help me?

---

### Post by KeitaroBR on 2006-06-03
I'm having the same problem here (HP Pavilion zv5000 notebook - amd64 dapper).

Regards

---

### Post by ????? on 2006-06-03
Have to tried wifi-radar?

---

### Post by zaiyon on 2006-06-03
It says:
```

eth1      Interface doesn't support scanning : No such device

```

---

### Post by KeitaroBR on 2006-06-03
Same thing here...

---

### Post by GmAz on 2006-06-03
I have an HP zd8115 laptop with the same issues with Wifi.  The driver won't load at bootup.  The Device manager rocognizes the hardware, but wifi won't work.  

I have a:

Broadcom Corporation
BCM4306 802.11b/g Wireless LAN Controller

I noticed that my Wifi button on my laptop isn't lit and won't light.  I am running the Live CD because I want to make sure that I can get my wifi working.  That is huge since my connection comes into my apartment in living room and Wifi is my only solution, other than a wire strung accross the room.

I just did some google searching and I found this:
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)
If this helps you, please explain what you did...I could use the help using it too  =).

---

### Post by zaiyon on 2006-06-03
This is an interesting link, I'll try it later.

But I'm happy since it seems to work now. I did it via ndiswrapper now, and everything seems to work just fine.

But the bcm43xx driver now creates some problems, so I needed to unload it and I'll not autoload this module on startup.

---

### Post by KeitaroBR on 2006-06-03
Sadly as far as I know ndiswrapper is not an option when you're using the live cd :(  (no space to install it now).

---

### Post by dwarfy on 2006-06-03
Hi ! Have you tried this command :
**sudo iwconfig eth1 mode monitor**
Before launching airsnort ?? 
(They say in airnsort to put your wifi card in monitor mode manually)

And have you tried something else than airsnort ?
Take a look at Kismet for scanning networks ...

Cheers
Mathieu

---

### Post by zaiyon on 2006-06-04
Hm, I don't think there is a way to get wlan working on the livecd.

The above linked method (if working at all) needs a 2.6.17er kernel. We have 2.6.15 with ubuntu right now (on the live cd too afaik)

But perhaps the livecd has unionfs. I don't know it atm, but with this, you can pseudo-write on read-only filesystems, namely change the root partition on the livecd on the fly.

This is what I basically did to get my card working with ndiswrapper:

1. I got the driver they said I should use for my BCM4318 device on this page:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

2. Executed the self extractor with wine. After extracting, I cancelled the installation wizard.

3. Installed ndisgtk and installed the .inf file I got from the installer with it.

4. Used modprobe to unload the bcm43xx module and load the ndiswrapper module.

5. Added ndiswrapper to /etc/modules and bcm43xx to /etc/modprobe.d/blacklist.

6. Had it working.

---

### Post by jml on 2006-06-04
GmAz, Wireless cards with the Broadcom Chipset are the toughest to get working in Linux because the company does not offer any help with drivers.    I have an HP nx6110 and in Linux, the blue wi-fi light only comes on when the card is either sending or recieving data.  Its off the rest of the time.  In order to get the card working, you will need to use NDISWRAPPER plus the windows driver for the card.  Good luck, I was never able to get it to work right.  That's why I gave up and am running Mandriva 2006 on my laptop and Ubuntu at home.  I'm told that Dapper Drake does support the Broadcom chipset, so you may be able to use it.  Since I need WPA encryption and Ubuntu still does not support it, I still can't use it on my laptop.  Good luck.

Joe

---

### Post by KeitaroBR on 2006-06-05
I think I will just wait for the next version of Ubuntu. For now I will use coLinux.

Anyway, thanks for the replies.

---

### Post by H.E. Pennypacker on 2006-06-07
[QUOTE=zaiyon]
This is what I basically did to get my card working with ndiswrapper:

1. I got the driver they said I should use for my BCM4318 device on this page:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

[/quote]

Check (completed this step).

> 2. Executed the self extractor with wine. After extracting, I cancelled the installation wizard.

I extracted the compressed file using right-click, "Extract here." Step: check.

> 
3. Installed ndisgtk and installed the .inf file I got from the installer with it.

Check.

> 
4. Used modprobe to unload the bcm43xx module and load the ndiswrapper module.

First of all, to be honest, I have no idea what modprobe is or what it does.  Regardless, I've done modprobe ndiswrapper.  I haven't done anything with bcm43xx that began with modpobe, though (didn't do modprobe bcm43xx).  I have not sure what this step entails, and what I am supposed to do here, or what to type into the terminal.

> 
5. Added ndiswrapper to /etc/modules and bcm43xx to /etc/modprobe.d/blacklist.

Check.

> 
6. Had it working.

Didn't work for me.  It may be because I can't get passed step 4.  

In any event, using Wireless Assistant, I can see the various networks in my neighborhood, but I can't connect to any.  When I type dhclient into the terminal, I get a response, not a failure.  I thought dhclient would be the end of it all, the final sign that everything was properly working.

---

### Post by H.E. Pennypacker on 2006-06-07
Problem solved.  Wireless Internet connection is now working very well.  I am not sure exactly what I had done to solve the problem, but I am sure it involves following lots of instructions provided on this messageboard, as well as playing around with "Networking" as well.  The most likely solution of mine was to probably change DHCP to Static IP and adding the IP address myself, instead of DHCP pulling it in.  In addition to the IP address, I added some other information (Gateway, Subnet, etc.), but that proved to be an unwise decision, because the connection would only work if I removed the additional info.  Just the IP address was needed for me.

Any questions?  Feel free to ask.

---

### Post by zaiyon on 2006-06-07
Sorry, I think I haven't been verbose enough on that.

modprobe is a program that can load and unload kernel modules, they are device  drivers most of the time.

So with our:
```

modprobe -r bcm43xx

```

We unload the linux driver for our device.

Then, with:
```

modprobe ndiswrapper

```

We load ndiswrapper as a driver. ndiswrapper can use Windows drivers and make them useable in Linux, so that's the reason why it works now ;)

Seems to be an unelegant last-resort solution nonetheless.

You allready solved it on your own, but perhaps this helps others who happen to find this thread.

I don't know if WLAN actually works for me. To be honest, this is my first laptop, my first WLAN card and I have never ever been to a WLAN network.

I just wanted the good feeling of working hardware, and since I can see networks, I'm satisfied for the moment ;)

I think I'll try it out soon anyways. I hang around in Starbucks very frequently, so...

---

### Post by KeitaroBR on 2006-06-07
I've just tried Mepis and my wifi works flawless in it (it uses ndiswrapper). Looks like I'm sticking to Mepis for now.

Thanks for the attention anyway :)

---

