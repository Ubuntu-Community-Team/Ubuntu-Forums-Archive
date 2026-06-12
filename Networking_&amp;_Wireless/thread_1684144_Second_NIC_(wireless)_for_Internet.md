---
title: "Second NIC (wireless) for Internet"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by OldManRiver on 2011-02-08
All,

I have the standard wired LAN NIC and a wireless NIC installed.

What my problem is, the wireless NIC will not take any internet traffic.  The LAN connection gets it's internet from my LAPTOP with a Clear 4G module.  I have a very strong wireless connection, but when I remove the LAPTOP from the network, I get nothing on my Ubuntu computer here, even though I have a solid connection.

What is needed in the config to let the wireless run in the "back up" internet connection mode?

All help appreciated!

Thanks!

OMR

---

### Post by OldManRiver on 2011-02-09
Can I get some help here?

---

### Post by P4man on 2011-02-09
I dont understand the question :confused:
Your laptop has a 4G connection that you share through an ethernet cable with your desktop? And what is the wifi (?) card of the desktop supposed to connect to?

---

### Post by OldManRiver on 2011-02-11
> **P4man said:**
> I dont understand the question :confused:
Your laptop has a 4G connection that you share through an ethernet cable with your desktop? And what is the wifi (?) card of the desktop supposed to connect to?

The DT connect via regular LinkSys wifi card, and connection is good but it is like DNS is disabled.

Since the primary internet is on "Auto eth0" when the laptop is removed the "Auto wifi" even though connected with solid connection, does not ping or see any internet traffic.

---

### Post by P4man on 2011-02-11
I still dont understand. Can you just explain the setup? What machine is connected to what through what means?

---

### Post by grahammechanical on 2011-02-11
Am I correct in thinking that the > Clear 4G module is a wireless adapter that acts like a mobile telephone to connect to the Internet? If I am correct then you will need a second Clear 4G module to plug into your desktop computer so it can access your mobile service provider. The standard wireless adapter does not work on mobile phone frequencies.

If you have a modem/router that plugs into the telephone line and you have a subscription to an Internet Service Provider and the modem has wireless then you will need to left click the network manager icon and select your wireless network from those available and authenticate the connection. If this connection is set to connect automatically, then when you unplug the laptop from the ethernet cable the wireless device in the computer will carry the connection to the Internet.

I am connected by ethernet cable to my modem. I am also connected to by wireless. If I unplug the cable I will still have a connection through wireless.

If none of this is relevant, then I am like p4man - I do not understand.

Regards.

---

### Post by OldManRiver on 2011-02-17
> **grahammechanical said:**
> Am I correct in thinking that the  is a wireless adapter that acts like a mobile telephone to connect to the Internet? If I am correct then you will need a second Clear 4G module to plug into your desktop computer so it can access your mobile service provider. The standard wireless adapter does not work on mobile phone frequencies.

Yeah I realize that most of the World does not know what "Clear" is.  Clear is a service from "Clearwire Holdings" the company that Craig McCaw (Mr Cell phone that built and sold the 4 celluar networks to 1. AT&T, 2. Verizon, 3. Sprint, 4. T-Mobile) built with Bill Gates.  After Gates left MS 15 years ago (still has board position only), he and Craig bought NexTel, out of bankruptcy, made it profitable, added "Turn-by-turn" GPS, using Teldesic (another McCaw acquisition, that investors labeled his "Edsel"), then sold NexTel to Sprint.  McCaw sold off Teldesic seperately after gaining all the contracts for Garmin and other GPS direction services that you now enjoy.

They next bought Clearwire (then an Arlington, TX company) moved it to Redmond, WA developed the 4G data only technology and now have implemented it in some of the select larger cities.

You can read about Clear at:

[http://www.clear.com/](http://www.clear.com/)

Anyway since is totally mobile, as I have the USB adapter seen at:

[http://www.clear.com/support/download/device/usb-modem](http://www.clear.com/support/download/device/usb-modem)

which lets me use the laptop anywhere there is coverage (see their coverage map).

What I found is that I can use the Ubuntu box, as I am now, with eth0 disconnected, over the wireless just fine, but can not connect any to the shared resources, that are on the LAN, since eth0 is down.

When I enable eth0 then I must have the Clear USB dongle inserted as the DNS from the wireless is somehow de-activated by the use of or the presense of the eth0 connection.

I do not want the DNS from the wireless to be overwritten by the eth0, but want both DNS setting to be searched, like in "least cost routing", so that if the eth0, does not have either the laptop attached, or laptop attached with the "Clear" dongle removed, that I will still have an internet connection via DNS from the wireless, as that is always there.

Oh for those that are curious the wireless is a D-Link wireless card running the Atheros AR5001X+ Wireless Network Adapter driver/software which is working fine.

Hope this explains all this better.

Sorry about the history lesson.  Been and insider for 35 years.

Thanks!

OMR

---

### Post by P4man on 2011-02-17
Ah, that explains a bit. So you have a wireless connection for the internet, and a wired one to connect the LAN.  Have you configured any static routes? Im not specialist, but you will need one for the LAN. Something like

```
route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0
```

Obviously replace the IP range with the one of your LAN and eth0 with the adapter you use to connect to it. Then make sure the default route is to the internet, using the appropriate NIC. You can check the routing table with

```
route
```

You can also modify (and read for a lot of info)
```
/etc/network/interfaces
```

---

### Post by OldManRiver on 2011-02-18
All,

I read the interfaces file which has:```
auto lo
iface lo inet loopback
```If possible I still want Auto DNS, not static, for the IPs to the two NICs, but since I do not see the wireless in the file, think that is where the problem originates.

I added "auto eth0" to the file, but not sure what to call the wireless.  Will run "lshw" to try for a clue.

Input please!

Thanks!

OMR

---

### Post by OldManRiver on 2011-02-18
Ok,

Running lshw found the name for the wireless was wlan0, so added "auto wlan0" to the file.

Now restarting networking to see if it works.

I tried using the "route add" syntax, but they error, and on restart with the new text in the intefaces file, I also get errors.

Code is now: ```
auto eth0
auto wlan0
auto lo
iface lo inet loopback
```
and error on restart are:```
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface wlan0=wlan0.
```

What next?

OMR

---

### Post by P4man on 2011-02-19
Are you using network manager? If so, I believe you have to configure the routes (and DNS) there. Right click network manager > edit connection > select your connection > edit > IPv4 > Routes

---

### Post by OldManRiver on 2011-02-19
All,

Help please!

OMR

---

### Post by OldManRiver on 2011-02-19
> **P4man said:**
> Are you using network manager? If so, I believe you have to configure the routes (and DNS) there. Right click network manager > edit connection > select your connection > edit > IPv4 > Routes
P4man,

I see that Network Manager is installed, from Synaptic Package Manager, but have no icon in any of the menus for it.

What is commandline to run it?

OMR

---

### Post by P4man on 2011-02-19
Its not in the menu's, its in the system tray, top right. The icon that changes when you connect/disconnect from a wired or wireless network.

---

### Post by OldManRiver on 2011-02-19
> **P4man said:**
> Its not in the menu's, its in the system tray, top right. The icon that changes when you connect/disconnect from a wired or wireless network.
P4man,

Sorry I only have menus.  Have another ticket open on that issue.

OMR

---

### Post by P4man on 2011-02-19
You dont have a notification area at all? You are using ubuntu 10.10 and not mythbuntu or xubuntu?

If you are using gnome (ubuntu) and dont have a notification area at all, just add it. Right click the top bar, add to, notification area.

If its just network manager that is missing, try this
```

sudo killall nm-applet
nm-applet&
```

---

### Post by OldManRiver on 2011-02-20
P4man,

OK, I see and opened them and both are on "AutoDNS" and when I tried adding route info, neither took it.

Appears you have to deselect the "AutoDNS" for routing to register and I'm not doing that as I never know what the IPs will be so must stay dynamic.

Do I need to look up a HOWTO for "least cost routing" to get this done?

OMR

---

### Post by P4man on 2011-02-21
I dont even have an "autodns" feature; which ubuntu version are you using?
Either way, dont confuse DNS with DHCP. DNS resolves names (like [www.google.com](www.google.com)) to IP addresses, DHCP is about obtaining dynamic IP addresses for your network card. You may need DHCP on your internet connections, but you probably want a fixed IP address for the local network card as I doubt you have a local DHCP server, unless its connected to your router and its configured as DHCP server.

---

### Post by OldManRiver on 2011-02-25
> **P4man said:**
> dont confuse DNS with DHCP.

P,

Sorry man, senior moment, forgot and used the wrong term.  Yes DHCP for auto IP assigning.

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-20
All,

Still do not have this working and now up to 9 machines on the network, so becoming critcal.  Thank goodness only one Widow box, the laptop, so all are Ubuntu and need to work when the laptop is gone.

Finally got WebAdmin install, so resovling my issues with backups, so will be backing up in next few days and running complete re-install on the box with mouse, keyboard and intermittent crash errors.

Hope someone can find this answer for me.  I still think it is the "lest cost routing" which is old method for auto switching NICs.

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-29
All,

Been too busy to get the backups done on this machine, since can not get bacula to work on it, but finally got the files copied to external HD.  Now downloading 10.04 for new CD and will toast the drive and see where I get.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-04
All,

OK got this machine stable, but still having this issue with the NICs.

Help please.

Thanks!

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #31 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

