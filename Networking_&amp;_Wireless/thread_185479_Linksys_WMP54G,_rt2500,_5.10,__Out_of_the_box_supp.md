---
title: "Linksys WMP54G, rt2500, 5.10,  Out of the box support?"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by motionsiren on 2006-05-31
I just picked up a new Linksys WMP54G PCI card for my Ubuntu 5.10 system. I booted up, did a dmesg, then went to Gnome's network interfaces preferences and set my SSID... there is no authentication required, we're in a trusted environment. I click activate and it the progress dialog box pops up for a long while.... either DHCP or it can't connect to the WAP at all. How can I tell?

This chipset is suppose to have out-of-the-box support, maybe it does? /var/log/messages, dmesg and ifconfig/iwconfig report no errors, just successful stuff. 

I am however, already excited that you've included the drive in 5.10, it makes these sorta things super easy... any ideas on my situation tho? Any more tools I can learn about?

---

### Post by bryanl on 2006-05-31
As long as you avoid WAP you should be able to use the net manager applet in the toolbar to connect with your network.

The last I heard, the rt2500 driver didn't support the interface that net manager needs to implement WAP but no security and WEP are supposed to work.

For a WAP connection, I needed to add a stanza in /etc/network/interfaces but even then the connection didn't last long so I had to 'sudo ifdown ra0' and then 'sudo ifup ra0' at an annoying rate. (you might try to down then up the interface manually to see what happens) Still haven't figured that out.

---

### Post by motionsiren on 2006-05-31
Hrm... well, I'll keep on it. I need to. have three Kiosks i need to setup here at work, for tomorrows grand opening :eek: Thanks for the hints, I'll be sure to contribute my notes to the wiki and report back here with my status.

btw, is there any odd log that'd show whats going on? im not seeing anything in the normal places.

---

### Post by motionsiren on 2006-05-31
ya know, im not seeing the applet you mentioned... i remember seeing one, but that may of been a few years ago already. is there one? i know it's nothing special, but it's a nicer interface when running around testing this stuff out ;)

---

