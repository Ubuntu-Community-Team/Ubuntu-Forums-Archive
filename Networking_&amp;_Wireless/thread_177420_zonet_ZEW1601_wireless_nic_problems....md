---
title: "zonet ZEW1601 wireless nic problems..."
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by nousplacidus on 2006-05-16
Ive spent all day googling and i've gone through every tutorial on the net verbatim. BUT....

So far as i know the rt61 driver is the one for this card. I even had it working earlier today but once I moved my rig and rebooted it stopped working for me. Ifconfig -a shows that the card is present, and lsmod says the rt61 driver is being used by one device. 

iwconfig 

gives shows ra0 with no wirless extension until I do a 

ifup ra0

then I get DHCPDISCOVER ... a bunch of times.

then iwconfig shows ra0 as the only wireless extension but the essid is ""

I try setting the essid with 

iwconfig ra0 essid "Home"

and i get no change. all iwlist ra0 scans show nothing but I am using an apple ibook in the same room and I have full signal. I am completely baffeled and I have tried every tutorial known to man. heres what my network interfaces file looks like 

...
auto eth0
iface eth0 inet dhcp

auto ra0 
iface ra0 inet dhcp
wireless-essid "Home"


Im confused as to what I should do from here im completely lost. 

thanks.
_______________

---

