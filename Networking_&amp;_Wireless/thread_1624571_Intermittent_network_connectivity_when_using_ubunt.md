---
title: "Intermittent network connectivity when using ubuntu 10.4 on the work network"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by sebastianfaunes on 2010-11-17
Hello Everyone,

I am having a big problem trying to use my Ubuntu 10.4 system (on a netbook) at work. I have 2 APs, a wired and wireless one. I also have a static IP address, but can use DHCP as well. My "work" computer runs without a hitch (other than the fact that it has a duplicate NetBIOS name), it is on WindowsXP. Both the linux system and windows OS is running 32 bit OSs

Issues:

[LIST]
[*]I can either configure my static IP or run Dhclient. Either way I only have internet from periods lasting from ZERO to a couple minutes at a couple megs per sec.
[*]Afterwards, I can't use the internet, can't ping any website, or even my default gateway (I can ping it during the brief periods of connectivity).
[*]When I lose connectivity I also can't run commands like dig or nslookup. No DNS resolution at all.
[*]Sometimes (and only sometimes) if I run _sudo gedit /etc/resolv.conf_ and change the nameservers to my default nameserver at work, it will work for a while. Sometimes I won't get anything unless I set at least 2-3 nameservers, but still it'll only work for a minute or two.
[*]If I run dhclient multiple times, sometimes I can get back up, other times I can't. In any case it's only a temporary solution. This is true whether I am using the wireless or wired AP.
[*]I can use ubuntu 10.4 anywhere else, wired or wireless, with no major issues
[/LIST]
Summary:

[LIST]
[*]Intermittent network connectivity when using ubuntu on the work network
[/LIST]
This issues has me going nuts. I've spent a couple hours a day all week trying to find a solution. Everything I try just has me going yay!! for like a minute, until it goes back down again. My brother, who is net+, tells me I should change my MAC address. But I am not sure how that could solve my problem, what should I change it too.

Best Regards, 

Seb :confused:

---

### Post by uncaspi on 2010-11-17
I dont think the MAC address has something to do wwith it. I would rather change channel on the card and/or increase txpower.

Start with channel one and increase. I assume your wifi is called wlan0.


sudo iwconfig wlan0 channel 1 txpower 15

Increase your power until you get an error.Try 16 and 17 also.

---

### Post by sebastianfaunes on 2010-11-18
Yeah, the wireless is not so hot to begin with on my net-book. But, that wouldn't explain why I have the exact same problem when I plug in the wired connection. 

Though, thanks for the note, cause I had no idea I could up the txpower on my wireless card. Sometimes I can't get through a single wall.

But as far as the other issue, still no luck. I also tried to manually set the connection speed and set autoneg to off. I thought maybe it was that, but also negative.

Seb

---

### Post by uncaspi on 2010-11-18
Try the OpenDNS nameservers or google 8.8.8.8
Right click the network icon and cchoose edit connections. Goto ipv4-settings and put in the nameservers.

---

### Post by sebastianfaunes on 2010-11-19
Ok, I'll try that. Did the forum go down yesterday? When I tried to  reply to your first post I wasn't able to, and I noticed that all posts  on the forum had stopped at a certain time. Wierd8-[

---

### Post by sebastianfaunes on 2010-11-19
well changing the MAC address worked. I spoofed my desktops's MAC, and all of a sudden things work fine. 

But, I have no clue why spoofing the MAC address would take me from limited connectivity to normal internet. Should'nt I have had no internet at all.

Whatever, it worked...... for now:popcorn:

---

### Post by uncaspi on 2010-11-19
Remember to put SOLVED on the thread.

---

### Post by sebastianfaunes on 2010-11-23
Not solved yet..... the solution only worked for a while. I'm going to upgrade to version 10.10 and see if that works, I'm all out of ideas.

---

