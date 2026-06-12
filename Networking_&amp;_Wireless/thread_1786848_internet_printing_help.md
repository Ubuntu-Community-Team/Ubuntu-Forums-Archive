---
title: "internet printing help"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by smokin74 on 2011-06-20
i would like to print to my home printer via the internet

printer is connected to the router directly by ethernet and i have a static ip address

i also have a static ip for the printer on the home network

need to know how to set my netbook up to connect to the printer via the web with the info i have 

printer is a hp photosmart c5180 and afaik it is capable of using ipp

looked around the net at a few tutorials but they only ever refer to one ip address, and the port - how do you route to the printers ip as well

thanks in advance

Chris

---

### Post by dandnsmith on 2011-06-20
Presumably you mean you have a static IP address (the WAN side of the router) as far as the outside world is concerned.
Do you have a separate 'external' IP address which you're using for the printer, or just that the printer is on a static IP address belonging to your local LAN (ie 192.168.x.y 10.x.y.z or similar)?
If it's a local address, you may have to get the router to redirect stuff to the local address.
My knowledge is limited, but you may have to send the printing stuff to a local PC in order to get the spooling organised.

---

### Post by Bucky Ball on 2011-06-20
Nothing in the manual regarding this?

No firewall or VPN blocking? Like dandsmith, my knowledge is limited on printing from outside the WAN via a network but do you need to open a port to allow yourself in?

PS: Just looked at the manual and doesn't seem to cover what you are trying to do which is odd. It is fully explained in my Brother network printer manual. I'll see if I can dig it up online as I'm about 750 Kms away from the hardcopy version at the moment. ;)

Perhaps you could investigate if it is in fact the router preventing you to connect rather than your settings.

---

