---
title: "hotplug usb and pcmcia (wireless) problems"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by key on 2006-01-10
Hi ubuntu forum,

I am having some weirdness with my linksys pcmcia wireless card. Specifically, the card just disconnects and then I can't get it to reconnect again until I reboot. I think the problem may have to do with the hotplug subsystem and usb devices. 

As long as my logitech usb mouse and/or my PNY 1gig usb key drive are not connected, everything works great. After plugging in either of the usb devices above (or booting with one attached),  I lose wireless connectivity in anywhere from 1 to 10 minutes. Once the connection is lost, I haven't been able to reconnect the wireless by any means I know of, aside from a reboot. 

Suprisingly, the pcmcia card is immune to my usb external maxtor hard drive.

Anyone else have this issue? 

Should I hotplug blacklist the pcmcia card modules? 
Has anyone else had to do this? 

here is what I am using:
a crappy dell inspiron 1100 laptop,
linksys wpc54 pcmcia card, ndiswrapper, linksys windows drivers, and wpa_supplicant for authentication

kubuntu breezy w/ fluxbox

thanks in advance,
key

---

### Post by key on 2006-01-11
I take that back about the external maxtor being benign - it took me down once this morning. Oh well, time to play with the hotplug blacklist I guess. Good times. 

key

---

### Post by key on 2006-01-13
UPDATE:
Still struggling - making some progress though. Thought I'd update this post in case anyone else had a similar problem -  no need to reinvent the wheel as they say. 

I am no longer suspect of the hotplug system. I blacklisted the appropriate pcmcia modules and it didn't fix the problem. I now suspect the issue is a dhcp renewal problem and may not have anything to do with the USB, or the wireless. It even happens when I am plugged in directly though ethernet. Quite trange. 

I found an ubuntu bug report about a possible dhcp bug in 3.0.2 that had all the same symtoms I have experienced and that was corrected by downgrading dhcp. I downgraded to 3.0.1, It didn't fix the problem though. At least I dont think it did.  

Yesterday, on a whim I tried specifying some parameters for the dhcp in dhcpclient.conf to sort of help it out when renewal time came. I should say that my router is crap - it is built into the dsl modem and it has been a flakey piece of crap since I got it. 

specifically I specified the following by uncommenting the appropiate line and filling in the values:

lease {
  interface "wlan0";
  fixed-address 10.0.0.153;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
  option subnet-mask 255.255.255.0;
  option broadcast-address 10.0.0.255;
  option routers 10.0.0.138;
  option domain-name-servers 10.0.0.138;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
}

that seems to have done it. It has been up for a while with no problems now and happily renews its dhcp lease when the time arrives. lets hope it sticks ...

key

---

