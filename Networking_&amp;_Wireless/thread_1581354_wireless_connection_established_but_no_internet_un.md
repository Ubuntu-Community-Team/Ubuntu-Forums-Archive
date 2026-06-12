---
title: "wireless connection established but no internet unsolved"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by #1 fisherman on 2010-09-24
Thanks for the help that i was receiving earlier it was just getting too late to stay up.
Although i still have not been able to bring up the Internet but it is saying i have a wireless connection established something wrong with the static ip address i think would sure like to figure it out.
Help would be greatly appreciated

---

### Post by booah on 2010-09-24
fisherman this is probably no help but i had a similar problem tonight. After installing 10.4 I installed my usb wireless dongle but what I didnt know then was ubuntu already installed my wireless card driver (which is dodgy) and it was getting priority over the usb. So i was connected to the network but I couldnt even get google open. Just in case you had a similar setup

---

### Post by #1 fisherman on 2010-09-24
thanks booah i am pretty inexperienced at the whole networking thing 
I sure would like to get this laptop to where it will bring up the internet 
i wonder if it is a problem with security of the router 
when i click on the wireless connection icon uper right corner  ubuntu 10.04 
i see my network connection appears connected but i see a lock next to it 
would you think the router is preventing me from accessing the internet

---

### Post by SeijiSensei on 2010-09-25
> **#1 fisherman said:**
> it is saying i have a wireless connection established something wrong with the static ip address i think would sure like to figure it out.

Do you need to use a static address?  What happens if you let the router assign you an address instead?  (That's usually the default approach here; having a static IP on the wireless interface is pretty uncommon.)

Are you sure you're using the correct authentication method and password?

Can you see your router's configuration page with a web browser on the Linux computer?  Usually the page is at [http://192.168.1.1/](http://192.168.1.1/) or [http://192.168.0.1/](http://192.168.0.1/) depending on the router's defaults.

If all else fails, perhaps you should reset the router to factory settings and start over.  Usually there's a tiny little button you can press and hold to do this.  Read the router's manual for details.

---

