---
title: "Wifi hotspot creation in kubuntu 11.10"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by mac4rfree on 2012-01-22
Hi Guys,

I like to convert my laptop to wifi hotspot. Iam currently using Kubuntu 11.10.

Can somebody help me out....

Cheers!!!!

---

### Post by linuxd00d on 2012-01-22
> **mac4rfree said:**
>  I like to convert my laptop to wifi hotspot. Iam currently using Kubuntu 11.10.



As in to do what? share files or to make your laptop as an AP?

Are you possibly thinking of using a wired connection to the laptop then using the wireless card as an AP?

d00d.

---

### Post by linuxd00d on 2012-01-22
After having a look around, if your looking to share your files you are going to need to install SAMBA.

then if you are looking to share your wired internet through the laptops wireless you are going to need to create an AD-HOC network via the wireless manager:

connect your wired connection to your laptop, goto your wireless manager and select "manage connections" once there goto the wireless tab and "add connection" then from there change the mode from "infrastructure" to "Ad-Hoc" add an SSID to identify your network you may also want to add some security like a WPA password, but thats your decision, then click ok.

You *should* then be able to connect to your new Ad-hoc's network name on your other wireless machines. this should also share your wireless with the other machines connected to the ad-hoc.

d00d.

---

