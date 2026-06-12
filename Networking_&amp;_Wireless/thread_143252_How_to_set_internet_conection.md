---
title: "How to set internet conection?"
date: 2006-03-12
forum: Networking &amp; Wireless
---

### Post by kaimietis on 2006-03-12
I was trying to set internet connection ADSL modem NOKIA model: mp 5121 but it failed. I think tha something is wrong withs my modem but wich windows everithing is ok. So can someone clearly tell me from whe to start and what to do.

---

### Post by encompass on 2006-03-12
it is a little distante on your request. Can you access the internet at all with the linux side?
From the terminal try this...
Can you post this information...
> sudo ifconfig
what is your IP address?
or you can try this...
> sudo dhclient eth0 up
that is a zero not an O.
than after running that command if you get an IP address a xxx.xxx.xxx.xxx number try this 
> ping google.com
are you getting responses back?
if you are.. then you have internet... if not press ctrl and C and report back.

---

