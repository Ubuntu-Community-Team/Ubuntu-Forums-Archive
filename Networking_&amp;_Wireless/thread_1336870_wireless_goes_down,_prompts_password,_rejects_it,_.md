---
title: "wireless goes down, prompts password, rejects it, requires reboot"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by morganpatrick on 2009-11-24
The title says it all. On my laptop, the wireless goes down, thinks forever, eventually prompts me for a password, then rejects it. Logging out doesn't even work. Only rebooting does. I can provide more info if needed. pls help. Thank you.

---

### Post by morganpatrick on 2009-11-25
Please, someone throw me a bone. This upgrade to Karmic has been an absolute nightmare and has ground my productivity to a dead halt. These are the types of issues that made me eventually give up on Ubuntu over 3 years ago. Then it got its act together and I returned but this latest release is like a huge step backwards. Everything is jacked on my machine.

Anyway forgive my rant. Please just help me get reliable wireless so I can at least function. Thanks.

---

### Post by morganpatrick on 2009-11-25
you know what, **** this. WORD TO THE WISE: DON'T ANYBODY UPGRADE TO KARMIC. IT'S ******* GARBAGE.

---

### Post by JimHQ on 2009-11-26
I feel your pain as I am suffering the same issue on an Acer Aspire 3810T. Have so far had no luck in troubleshooting, despite a couple of late nights. Thought initially it may be related to the fact that I enabled power management via backport, but disabling power management has not improved matters.
Now think it might be related to security settings as if I go into Edit Connections and delete the connection under the wireless tabs then I am able to reconnect. 
Any good suggestions appreciated.
Jim.

---

### Post by iponeverything on 2009-11-26
Try removing and reinstalling network-manger.

```

sudo dpkg -r network-manager  network-manager-gnome
sudo apt-get install network-manager  network-manager-gnome

```

---

### Post by morganpatrick on 2009-11-26
Thanks for the suggestion but I installed wicd which I believe removed the standard network manager. When I run the command you specified I get:

```
dpkg: warning: ignoring request to remove network-manager, only the config
 files of which are on the system. Use --purge to remove them too.
dpkg: warning: ignoring request to remove network-manager-gnome, only the config
 files of which are on the system. Use --purge to remove them too.
```

btw thank you for your sincere responses to my asinine post. I am frustrated beyond belief but I'll get through this with your support.

---

### Post by rigar1 on 2009-11-27
I had the same problem and after alot of goggling to no help it turned out to be under network connections, some how there were 2 connections with the same ssid I deleted one and no problem, worth a check, hope this helps

---

### Post by morganpatrick on 2009-11-27
Can you tell me what steps you took so that I might reproduce this? Thanks

---

### Post by Cypher1101 on 2009-11-27
What brand is your wifi card? I spent about a week getting my 2004 laptop's broadcom working, but it works perfectly now. It even supports wpa2, which didn't even exist when the card was made.

This sounds a lot like the problem i had with mine, the main solution I ran into was trashing ssb (default module for wifi.) After that, my card was perfectly happy.

---

### Post by coober85 on 2009-11-27
same problem... only rebooting doesn't fix the problem

I know it's just my computer because my ipod touch gets wireless, and my desktop computuer AND laptop (the one with problems) gets internet just fine when hooked up to a LAN cable.

```
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:bf:8b:f3:ac
Sending on   LPF/wlan0/00:1c:bf:8b:f3:ac
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
```

if that helps

other stuff:
Lenovo T61
Linux Mint 7 Gloria (variant of Ubuntu 9.04 Jaunty Jackalope)
2WIRE router which has been working perfectly for over a year until now
no upgrades or anything.

THE ONLY change was that I tried to connect to a new 2WIRE router today. It connected to this new router but the connection seemed very low (I was 6' away from the hub) and I could not get on to the internet (gave me some kind of server error). when I got home I couldn't connect to my own 2WIRE router. 
  usually it automatically connects, but this time it "connected" to this new router again, even though it's 50miles away from my house. I tried to to force it too connect to my home router, and it hasn't been able to connect. 

sees it just fine and I'm definitely within range of the router, but still it just attemps to connect for about 2 mins and then asks for authentication over and over. 

makes you want to pull your hair out... 
I will buy whoever fixes this a beer, so get to work! thank you.

---

### Post by coober85 on 2009-11-27
hey, what do you know? It works now!

I did an update that installed a few headers and some other stuff, hit reset on my 2WIRE Router and poof! it works!


probably just a needed a reset...

if you have a linksys router I know you have to press and HOLD that reset button for like 30secs to get it to work. if that doesn't work try unplugin it and repluging it in after a minute.

I need to go buy myself a cold one. happy thanksgiving

---

