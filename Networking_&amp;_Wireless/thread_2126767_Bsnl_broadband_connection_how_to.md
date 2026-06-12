---
title: "Bsnl broadband connection how to"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by tulsi on 2013-03-18
Hi,

I have installed Ubuntu 12.04.1 LTS on my desktop & I want to connect my bsnl broad band connection.

Actually I bought wifi modem & they configured a all things in modem. I connected desktop to modem through the ethernet cable.
then I added DSL connection & give username, password & all things on network icon on top the ubuntu.
finally in command line i gave a sudo pppoeconf but it shows pado timed out...

kindly give me suggestion to connect the broad band connection on my pc.


Thanks.....

---

### Post by varunendra on 2013-03-18
Hi, Welcome to the forums Tulsi !

> **tulsi said:**
> Actually I bought wifi modem & they configured a all things in modem.
Can you log in to the Admin console of the modem? Try [http://192.168.1.1](http://192.168.1.1) in your browser.
The admin id and password, unless modified, should be mentioned at the bottom of the browser (or you can ask BSNL helpdesk)

See if pppoe is configured in itself. If so, you can't and won't need to configure it in the PC. Just plug in and it should get connected to internet.

---

### Post by tulsi on 2013-03-18
Thank you for reply,

Already i got username & password,i can able to login 192.168.0.1 but internet is not working....

---

### Post by varunendra on 2013-03-18
> **tulsi said:**
> Already i got username & password,i can able to login 192.168.0.1 but internet is not working....

So did you check if the PPPoE is configured in the router/modem itself or not? While you can certainly configure it in the OS, it is a good idea to configure it in the router instead. It is hassle free and gets connected automatically as soon as it is powered On.

On the other hand, if for some reason you prefer to configure it in the system, then the Network Manager is all you need to use, you don't need the commandline.
Once the DSL is configured with username/service name/password, and the Ethernet cable is connected, you should be able to see the newly configured DSL connection in the Network Manager's drop-down list (the nm-applet icon at the top-right corner of the screen).
Just click on it and it should get you connected.

But this or any other configuration method on the systems requires that PPP is NOT already configured in the router/modem.

So log in the Admin console, and make sure whether PPPoE is configured or not in the router.

---

### Post by tulsi on 2013-03-19
Thanks ... i will check in router...

---

