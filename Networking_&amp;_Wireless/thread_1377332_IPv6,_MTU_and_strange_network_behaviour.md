---
title: "IPv6, MTU and strange network behaviour"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by asearle on 2010-01-10
Hallo Everyone,

I hope that someone out there can help me with this strange problem:

The installation of Ubuntu 9.10 on my HP NC640 worked fine and the network adaptor was successfully recognised:  I see the message 'Wired Network Connection 'Auto Eth0' active' and when I open Active Network Connections I see the IP addresses that have been assigned.

However, if I open Firefox, I cannot connect to the internet.  I tried pinging some addresses ([www.yahoo.com](www.yahoo.com)) and that seemed fine.  I then tried to run a first system update and Ubuntu seemed to be able to retrieve some packages but not others.

I then tried opening 'Network Connections' and adjusted the MTU (to 1100) and changing the settings of IPv6 (various settings: eg. 'ignore') but none of that seemed to help.  Here I wanted to switch off IPv6 but it looks like none of the settings did this.  Is there maybe another place where I should be looking?  Do I have to do this with the command line?  (I hope not) Or can I switch off IPv6 in the system settings?  And should MTU be automatic?  Or should I set something there?

I had a similar problem (sporadic and/or none-existant network access) with SuSE and was able to fix it by deactivating IPv6 and reducing the MTU but I am unfamiliar with Gnome/Ubuntu and so hope that someone can help me out with this problem?

Many, many thanks,
Alan Searle

---

### Post by bkratz on 2010-01-10
> **asearle said:**
> Hallo Everyone,

I hope that someone out there can help me with this strange problem:

The installation of Ubuntu 9.10 on my HP NC640 worked fine and the network adaptor was successfully recognised:  I see the message 'Wired Network Connection 'Auto Eth0' active' and when I open Active Network Connections I see the IP addresses that have been assigned.

However, if I open Firefox, I cannot connect to the internet.  I tried pinging some addresses ([www.yahoo.com](www.yahoo.com)) and that seemed fine.  I then tried to run a first system update and Ubuntu seemed to be able to retrieve some packages but not others.

I then tried opening 'Network Connections' and adjusted the MTU (to 1100) and changing the settings of IPv6 (various settings: eg. 'ignore') but none of that seemed to help.  Here I wanted to switch off IPv6 but it looks like none of the settings did this.  Is there maybe another place where I should be looking?  Do I have to do this with the command line?  (I hope not) Or can I switch off IPv6 in the system settings?  And should MTU be automatic?  Or should I set something there?

I had a similar problem (sporadic and/or none-existant network access) with SuSE and was able to fix it by deactivating IPv6 and reducing the MTU but I am unfamiliar with Gnome/Ubuntu and so hope that someone can help me out with this problem?

Many, many thanks,
Alan Searle

I use 1492 for MTU (which seems to work quite well)Also here is a blog about IPV6

[http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

---

### Post by asearle on 2010-01-23
Hi again everyone,

This is driving me crazy:  I have set mtu to 1492, set ipv6 Settings to 'ignore' and disabled IPv6 (in both grub and in modprobe.d/aliases ... following the instructions given) but am still having trouble.

The weird thing is that the network tells me that it is connected and I am able to ping addresses (e.g. [www.google.com](www.google.com)) but when I try to run a software update or view a site from Firefox, I get either no or only sporadic connections.  Even weirder is that, when I try a software update, most of the files fail but a few register 'done'.

I find this really bemusing because apparently, the network thinks it is connected.  I believe that it is an ipv6 issue but I am rather out of my depth.

Any ideas or tips would really help.

I hope that someone can help me.

Regards and thanks,
Alan Searle

---

