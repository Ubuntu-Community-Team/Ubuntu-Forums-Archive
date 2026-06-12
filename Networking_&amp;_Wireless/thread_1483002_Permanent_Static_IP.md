---
title: "Permanent Static IP"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by takuhii on 2010-05-14
Hi,
I've tried to search the forums for an answer, but I can't seem to find one specific to my situation...

I need to set my Netbook to a static IP address. I've tried doing this through Network Manager and can't get it to work, it either doesn't work at all, or disconnects me permanently from any type of network. :(

I am on Sky Broadband in the UK. I need to set my Netbook to a static IP adress (as I have specific rules on the router), but don't know which fields to fill in specifically. Can anyone help me set my Netbook to a static IP address??

I am using Ubuntu Netbook Edition 10.04

Many thanks
Darren

---

### Post by kerry_s on 2010-05-14
right click the wifi applet-> edit connections
wireless tab-> edit
ipv4 settings tab
change "automatic (dhcp)" to manual
click "add" & put your settings

here's what mine looks like.

---

### Post by mhgsys on 2010-05-14
yep follow kerry;

Just wanted to add.
Find the correct dns settings in your router. 

f.e I have to go to 192.168.1.1 (my router) once there click advanced , go into system statistics , . look for WAN ETHoA 2 in the top, and dns on the left... there I see my primary and secondary  dns.

So; browse around in your router, or see if you can find a manual for your router on the web somewhere;

---

### Post by takuhii on 2010-05-14
I did try it like this and it didn't work, but I may use OPENDNS DNS instead of Sky's.

As I have to access the router to find the DNS servers Sky use, it may be a better option this way, I'll give it a whirl and let you know how I get on...

Thanks for all the help so far guys...

---

### Post by takuhii on 2010-05-14
Worked a treat mate, thank you. I couldn't figure out Sky's DNS servers, so I used OpenDNS instead ;)

---

### Post by lisati on 2010-05-14
> **takuhii said:**
> Hi,
I've tried to search the forums for an answer, but I can't seem to find one specific to my situation...

I need to set my Netbook to a static IP address. I've tried doing this through Network Manager and can't get it to work, it either doesn't work at all, or disconnects me permanently from any type of network. :(

I am on Sky Broadband in the UK. I need to set my Netbook to a static IP adress (as I have specific rules on the router), but don't know which fields to fill in specifically. Can anyone help me set my Netbook to a static IP address??

I am using Ubuntu Netbook Edition 10.04

Many thanks
Darren

My "standard" reply about static IP addresses is that I prefer to set them with my router. This helps avoid possible conflicts when I use my laptop on someone else's network. Setting a specific IP address is fine on my own network, but the admins of other networks might have different ideas.

---

### Post by mhgsys on 2010-05-14
Well lisati.

If you want to switch back to dhcp on your network; or for another reason.... 

It is as simple as going back to right clicking the wifi applet-> edit connections
wireless tab-> edit
ipv4 settings tab
and changing "manual to automatic (dhcp) again 

Btw; Come to think of it; 

Seems to me other networks (I was connected to) and settings are automatically saved, 

f.e
I have mine set on static at home, and when I'm over at a friends house I get the Ip and dns from dhcp.
gnome-network-manager saves it for me.

---

### Post by takuhii on 2010-05-15
I have set the static IP on a per network basis, so my home network is set to my static number, and any other network I connect to to set to AUTO ;)

LOVE 10.04

---

