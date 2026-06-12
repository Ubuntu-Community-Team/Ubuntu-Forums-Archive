---
title: "Where does 169.254.10.5 come from"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by madtom1999 on 2011-02-09
I'm having trouble setting up my wireless on new installs
despite asking for DHCP or even setting a static IP the system kicks off whatever seems to work and settles on 169.254.10.5 which is nothing to to with my configuration or any nearby (I live in the country and there's only one house within 1 mile) 
The network configuration seems to have a mind of its own - even when I get it working a little later it just wanders off on its own.
One thing I've noticed is the files in /etc/network/if-pre-up.d change every couple of minutes or so....

I've 5 other machines that are now living happily but every time I install a new one I get this to one degree or another...

---

### Post by slooksterpsv on 2011-02-09
Usually a 169.254.x.x is set when it doesn't get anything from the router/modem. I'd suggest powercycling your router, and try to connect again.

Also if you have the incorrect password, some routers may give you this address for a wrong password (WEP/WPA/WPA2).

---

### Post by P4man on 2011-02-09
Maybe your router isnt configured (or able?) to handle more than 5 clients.

---

### Post by puppywhacker on 2011-02-09
169.254.0.0/16 is a random link local address which if self assigned if no static address is set or no dhcp response is received. 

[http://en.wikipedia.org/wiki/Link-local_address](http://en.wikipedia.org/wiki/Link-local_address)

Do you request real dhcp addresses from your internet provider (they may have a cap on addresses in use) or are you using private ip addresses provided by your router (private addresses start with 192.168. or 172.16. or 10.)

---

### Post by madtom1999 on 2011-02-25
I've managed to track the problem down to a dodgy USB connection - theres nothing in the logs but I noticed the wireless wasn't flashing when it should have been and after much testing it appears one port on the machine has connectivity problems with the wireless connector. The port works fine on other devices and I've tested the wireless on other machines and it seems if the USB port is used and worn it may cause problems with this device!

I hate intermittent problems!!!
Ta for the help!

---

