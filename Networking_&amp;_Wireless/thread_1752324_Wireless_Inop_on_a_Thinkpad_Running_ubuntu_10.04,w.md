---
title: "Wireless Inop on a Thinkpad Running ubuntu 10.04,with a Netgear Router"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by ChewBaca on 2011-05-07
I have been looking around since this morning when comcast gave me my modem and Router, but to no avail. ive read countless threads. on numerous site and i finally admit defeat to this problem of mine
    Everything works fine. Internet wise, i am getting the Router to output my Signal from the modem and my Laptop sees the Connection but when i click it and give it my "Wpa/wpa2 Personal" password, nothing ever happens 
      It tries to connect and it will ask for my WPA again, then again then again then again. - i know its right and working cuz my android phone grabbed up the signal with no thought and its online.  then the network manager finally just disconnects me
my laptop is also working just fine wired to the router

im running Ubuntu 10.04
on a IBM Thinkpad
with a Netgear WNR1000v2-VC wireless router.

im desperate for any help from anyone who has a fresh set of eyes :(

i have also run countless commands in my terminal :confused: 
Please help

---

### Post by jaredwlane on 2011-06-03
I have the same problem have you found any answers yet?

---

### Post by nm_geo on 2011-06-03
> **ChewBaca said:**
> I have been looking around since this morning when comcast gave me my modem and Router, but to no avail. ive read countless threads. on numerous site and i finally admit defeat to this problem of mine
    Everything works fine. Internet wise, i am getting the Router to output my Signal from the modem and my Laptop sees the Connection but when i click it and give it my "Wpa/wpa2 Personal" password, nothing ever happens 
      It tries to connect and it will ask for my WPA again, then again then again then again. - i know its right and working cuz my android phone grabbed up the signal with no thought and its online.  then the network manager finally just disconnects me
my laptop is also working just fine wired to the router

im running Ubuntu 10.04
on a IBM Thinkpad
with a Netgear WNR1000v2-VC wireless router.

im desperate for any help from anyone who has a fresh set of eyes :(

i have also run countless commands in my terminal :confused: 
Please help

Some people have installed wicd with good results.  I have seen where some re-installed network manager and it also worked.
I just installed wicd on my Maverick version and it is working well after removing network-manager-gnome and rebooting. Just to see 
if it works here .. It does think I will keep it for awhile and experiment.

---

