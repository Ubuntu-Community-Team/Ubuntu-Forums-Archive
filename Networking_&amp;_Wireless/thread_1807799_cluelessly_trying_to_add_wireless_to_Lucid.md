---
title: "cluelessly trying to add wireless to Lucid"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by jtwdyp on 2011-07-19
Hello. I like to think I'm not stupid or lazy. But when I try to wade through the documentation and or google searches for this I get conflicting info and a lot of references that assume I've either got gnome or kde installed. And anyway, by the time I halfway learn something I find a need to learn something else before I can get the hands-on practice I need to remember any of it. By the time I gave up trying to solve this myself I had a headache could no longer find any of the helpful links I was able to do anything with. And my lady almost knocked the house down slamming the door on her way out because I'm spending too much time on the {her long string of imaginative expletives NOT quoted here} computer...

All I want to do is to be able to occasionally take my laptop out of the office while it's connected to the Internet so I can watch TV with her and check my email at the same time.... I just got a nice new wireless capable router/dsl modem for my new 7 MG fairpoint DSL service.

I don't know much about wireless except that I know I don't want some hacker using my ip address to do lots of spam, or something vile like child porn, or anything that might attract the attention of homeland security. So based on what I found in the routers wireless set-ups and some google searching I decided that my ideal connection would be wpa-2 with a LONG pre shared key (preferably with the ssid broadcasting dissabled though I think I read somewhere that that wouldn't work with the new native broadcom-wl driver that I vaugly remember finding a command line method of extracting some 8 digit )hex?) value to compare against some list that said I could use the broadcom-nl driver and that it was also called broadcom-sta (which I installed with synaptic).

I chose broadcom-nl because a native driver should mean I didn't have to muck about with the firmware like I think I saw was neccessary woyh the b43 driver(s)

I was having problems getting it to work with the connection utility I find at "applications menu->settings->Network-Commections"

(perhaps now is a good time to mention that I use E17 or in a pinch xfce)

So I googled some more and found some claims that wicd was easier etc... It was in the repository so I installed it too...

Network-Commections let me set up "wireless connection 1"
which has my SSID (but since the first time in I was going for a hidden ssid I think I typed it in myself) I've tried both the ad-hoc & the infrastructure mode. {{does ad-hoc mean it can just scan for a trans mitted ssid ???}} I have no idea what bssid is for so I left that blank. And several of the sort of helpful threads I found on this topic said to leave the MAC address feild blank. the wireless security button says I've selected "wpa & wpa2 personal) and I put my shared key string in password. the ipv4 settings are set to DHCP...

With wicd I just get "no wireless networks found"

from my routers wireless status screen I get:

```
Radio Enabled:	Yes
SSID:	xxxxxxxxxxxx
Channel:	6
Security Enabled:	YES 
 	WPA Type:	WPA2 - PSK 
 	WPA Shared Key:	xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx 
 	Group Key Update Interval:	1800 
Frameburst Mode:	Disabled
SSID Broadcast:	Enabled
MAC Authentication:	Disabled
Wireless Mode:	Mixed: accepts 802.11b and 802.11g connections
Packets Sent:	501
Packets Received:	0


```  
I note I've tried both tkip & aes encryption modes on the router with no joy... likewise I tried the older wpa And even {in despair} wep sigh!

Maybe there are some additional steps I need to take to enable the broadcom-sta driver or something??? I really don't want to be stuck with vista when I bring the laptop into the livingroom. in fact I'd rather not even teach vista how to use this connection even if I intend to routinely disable the router's "radio" from the desktop whenever I'm not actively using it...

Can somebody either point me at a good how to that gives me the command-line names and actual repo pacage names of any needed utilities (so I can be sure I'm finding the right one) or if you really have a big heart, would you walk me through this (before I wind up suddenly single???)

Thanks

---

### Post by Bucky Ball on 2011-07-19
Can you get online with a cable? Please do so and check System>Administration>Additional Drivers

You could also try System>Administration>Synaptic Package Manager and search for:

firmware-b43-installer
b43-fwcutter

Install 'em.

If this gets you nowhere, please run:

```
sudo lshw -C network

```... and post the results back here.

---

### Post by jtwdyp on 2011-07-19
> **Bucky Ball said:**
> Can you get online with a cable?Sure can...> **Bucky Ball] Please do so and check System>Administration>Additional Drivers[/QUOTE]That seems to be at least part of it. Though the menu path System>Administration>Additional Drivers doesn't exist for me. But I found a "settings->Hardware Drivers" choioce that listed the broadcom-sta driver (along with a couple of others) And said no propriatory drivers were installed...
But when I tried to activete it I got a permission denied. (I boot to console and use startx) So since it didn said:**
> You could also try System>Administration>Synaptic Package Manager and search for:

firmware-b43-installer
b43-fwcutter

Install 'em.Couldn't find firmware-b43-installer but b43-fwcutter installed just fine. (though I'm not sure what to do with it...

[QUOTE=Bucky Ball]If this gets you nowhere, please run:

```
sudo lshw -C network

```... and post the results back here.[/QUOTE]

And that cli output:

  *-network
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:bb:00:27
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.18 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256)
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:1c:07:98
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:c0300000-c0303fff

---

### Post by jtwdyp on 2011-07-20
I was having such problems that I decided to test if I could at least install their builtin broadcom device to {Eeeeyuck}Vista. I could, after all, find precise step by step instructions for "that". 

But I was unsuccessful even installing to that horrible thing. So I aquired a used TRENDnet 424UB H/W:3.0R, Downloaded the vista driver utility and had vista connected to my wireless router using WPA2 PSK & AES encryption. in less than an hour.

Perhaps this USB wireless device is easier to successfully configure under Lucid than the built in was...

But I'm not sure, do I need to uninstall the broadcom driver? And is there a native driver that will likely work with this USB wireless adapter? etc...

I'll wait a bit for a reply before I just wing it {and hope I don't trash my system from not knowing what I'm doing here...}

Thanks

---

### Post by nm_geo on 2011-07-20
> **jtwdyp said:**
> I was having such problems that I decided to test if I could at least install their builtin broadcom device to {Eeeeyuck}Vista. I could, after all, find precise step by step instructions for "that". 

But I was unsuccessful even installing to that horrible thing. So I aquired a used TRENDnet 424UB H/W:3.0R, Downloaded the vista driver utility and had vista connected to my wireless router using WPA2 PSK & AES encryption. in less than an hour.

Perhaps this USB wireless device is easier to successfully configure under Lucid than the built in was...

But I'm not sure, do I need to uninstall the broadcom driver? And is there a native driver that will likely work with this USB wireless adapter? etc...

I'll wait a bit for a reply before I just wing it {and hope I don't trash my system from not knowing what I'm doing here...}

Thanks

I liked +1 what Bucky Ball  told you, and i am glad I still have xbuntu installed as one of my many versions. The easiest way for you to fix this is in System>Synaptic package manager..  in the quick filter type in _bcm_  now remove bcmwl-kernel-source (not completely remove) just remove.  That gets STA (wl) driver out of the way. Now install b43-fwcutter and firmware-b43-installer if it is present.

Reboot with ethernet cable removed.. Set up wifi in wicd I hope network manager is not installed too. WE will cross that bridge if we come to it.

---

### Post by bkratz on 2011-07-20
> **jtwdyp said:**
> I was having such problems that I decided to test if I could at least install their builtin broadcom device to {Eeeeyuck}Vista. I could, after all, find precise step by step instructions for "that". 

But I was unsuccessful even installing to that horrible thing. So I aquired a used TRENDnet 424UB H/W:3.0R, Downloaded the vista driver utility and had vista connected to my wireless router using WPA2 PSK & AES encryption. in less than an hour.

Perhaps this USB wireless device is easier to successfully configure under Lucid than the built in was...

But I'm not sure, do I need to uninstall the broadcom driver? And is there a native driver that will likely work with this USB wireless adapter? etc...

I'll wait a bit for a reply before I just wing it {and hope I don't trash my system from not knowing what I'm doing here...}

Thanks


The b43 drivers as described should just work well for your internal card. I use the TEW-424 (got a real good deal!) and with 10.04 had it working natively after I used synaptic to get the linux-backports-modules for my particular kernel revision. I believe that it is the out of the box in 11.04, but the backports module took care of it for me in 10.04.

---

### Post by jtwdyp on 2011-07-21
> **nm_geo said:**
> I liked +1 what Bucky Ball  told you, and i am glad I still have xbuntu installed as one of my many versions.

Strongly agree with that sentiment, I've got 4 Linux distro's installed to this laptop. The *xubuntu one is the only one of which which I have much hope of my skills (with lotsa help) being sufficiant to get this thing up & running. {*Note it was installed as xubuntu even if I mostly only run enlightenment on it...}

[QUOTE=nm_geo]The easiest way for you to fix this is in System>Synaptic package manager..  in the quick filter type in _bcm_  now remove bcmwl-kernel-source (not completely remove) just remove.  That gets STA (wl) driver out of the way.[/QUOTE] 

So far so good.

[QUOTE=nm_geo]Now install b43-fwcutter and firmware-b43-installer if it is present.[/QUOTE]

Do I still need the b43 stuff if I'm going to use a NON broadcom USB wireless adapter??? Since I couldn't even get that built in running in the vista that came with this laptop, I'm thinking the broadcom device is defective...

[QUOTE=nm_geo]Reboot with ethernet cable removed.. Set up wifi in wicd I hope network manager is not installed too. WE will cross that bridge if we come to it.[/QUOTE]

Well anyway  I've got fwcutter in there though I've no idea how to use it... And I'm not finding the firmware-b43-installer, "network-manager" WAS installed {isn't now...) & I HAD  wicd already. And now that the STA driver is out of the way, it was able to find the "connection" via the trendnet usb adapter. But any attempt to actually connect generated lots of authentication stuff in wicd's status line followed by a failure notice citing "bad password". 

That is until I uninstalled "network-manager" And rebooted {with the cable already unplugged AND the Trendnet adapter already plugged in) Then suddenly it was working... 

[SIZE="3"][COLOR="Magenta"]**VICTORY!**[/COLOR][/SIZE]

[COLOR="Blue"]And to you great wonderful & clever people who so kindly did help:

       [SIZE="4"]THANK YOU![/SIZE] [/COLOR]

---

