---
title: "Winbond USB WiFi W89C35 not detecting other computer"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Feynt on 2010-05-01
I've got two computers, with one (my current one I'm posting with) acting as a bridge for the other to access the internet (ICS, yay).  Under windows there's no problems, everything goes smoothly on boot up.  However I got a copy of Ubuntu 9.10 via mail a little while ago and got around to installing it today with the intention of updating it to 10 while I'm sitting here programming.  Thus far, I haven't had any luck getting the networking to happen.  As far as I can tell, here's what's going on:


[LIST]
[*]Ubuntu sees the USB dongle
[*]Lights are flashing on it, it's got power and being interacted with
[*]Ubuntu's Wireless Network dock icon has entries for two nearby WiFi networks (my own with password, and someone else next door, also passworded so I can't try theirs)
[*]Ubuntu asks for a key to use with logging in
[*]After 20-30 seconds of trying it asks again for a key to log in
[/LIST]


lshw -C Network shows:
```

(wired connection info)
...
*-network
    description: Wireless interface
    physical id: 1
    logical name: wlan0
    serial: ##:##:##:##:##:## (omitted)
    capabilities: ethernet physical wireless
    configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

```lsusb shows 
```

Bus 001 Device 003: ID 0416:0035 Winbond Electronics Corp. W89C35 802.11bg WLAN Adaptor

```sudo iwconfig indicates the adaptor is present and being interacted with.

sudo iwlist scanning correctly identifies two access points, however it can't seem to identify what the encryption type is on my computer.

I'm using WEP encryption for my Wii to be able to get online, and the password is set correctly (yay for show key).  Looking at this computer's activity monitor I can see the mac address of the USB key.

Disabling password protection on my computer gets Ubuntu to recognize that there is indeed an unlocked network available now, however it fails to connect, once again.



Am I better off just ordering a copy of Ubuntu 10 on CD?  Besides sneaker net with a 1 gig tumb drive there's not much I can do to get drivers over.

---

### Post by richard.e.morton on 2010-05-02
I am looking to get a similar device running under Ubuntu 10.04 with no luck so far. It detects that it is a winbond device but network connections doesnt seem to like it and the LED on it only very briefly flickers when plugged in.

any help appreciated.
R

---

### Post by Feynt on 2010-07-07
I've obtained a copy of 10.04 via mail and installed.  I think I'm worse off now than before though.  >P
After a fresh install, here's the deal:


lshw shows only my ethernet port (I can't use it in this case, no hub/multi-port router to connect to).

lsusb does show the USB dongle properly.

sudo iwconfig only shows local loopback and eth0, no wireless

And naturally sudo iwlist scanning fails because neither supports scanning.

---

