---
title: "HELP! Please, My internet isn't working."
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by RobFS1 on 2009-08-01
Okay, this all happened a couple of days ago. It is a long story, but please read it. 

I wanted to dual boot, so i read up on it and i finally got Ubuntu 8.04 and windows xp on the same computer. Ubuntu was the first operating system installed. But to my dismay, and not to my surprise, xp didn't have any of the necessary drivers installed for my Acer Veriton M621. So i thought to just install the drivers by moving some i downloaded from my Ubuntu partition to the xp partition, and then installing them to xp. My Ethernet card (which is integrated on the motherboard by the way) was one of the things that wasn't supported by the xp, so i thought to install that first, so that i could install the rest of the drivers using xp. When i finally got the Ethernet driver installed on xp, i went back to Ubuntu to download Firefox for xp, and i realized that i couldn't get onto any website except for Google on Ubuntu. I can make Google searches, but i cant go anywhere but those searches.:confused: I cant even update Ubuntu because i cant get the package information downloaded for the updates.](*,) Does anyone have an idea about what is wrong? Is there a way to reinstall the Ethernet card on Ubuntu? Thank You.

---

### Post by quixote on 2009-08-03
*install the drivers by moving some i downloaded from my Ubuntu partition to the xp partition, and then installing them to xp*

Not sure what you mean there.  Hardware drivers written for Ubuntu aren't going to work for Windows.  Or did you mean you'd downloaded some Windows-specific drivers into Ubuntu and then moved them?  The latter shouldn't cause a problem.

As for your larger problem, that you can't access any site but Google, that sounds odd.  If you couldn't access anything at all, it would make sense and means your Ethernet needs reconfiguring.  But if you can access one site, then it's not your connection that's at fault.

Are you sure you're actually accessing the web?  Or maybe just reloading from cache on your local machine?  Try Shift-Ctrl-R in Firefox to force a true reload, and see if it goes anywhere.  Once it's a bit more clear what's going on, we can try to deal with it.

---

### Post by Crafty Kisses on 2009-08-03
Can you ping other sites than Google? What are the results of the following?
```
ping yahoo.com
```

---

### Post by RobFS1 on 2009-08-03
> **quixote said:**
> *install the drivers by moving some i downloaded from my Ubuntu partition to the xp partition, and then installing them to xp*

Not sure what you mean there.  Hardware drivers written for Ubuntu aren't going to work for Windows.  Or did you mean you'd downloaded some Windows-specific drivers into Ubuntu and then moved them?  The latter shouldn't cause a problem.

As for your larger problem, that you can't access any site but Google, that sounds odd.  If you couldn't access anything at all, it would make sense and means your Ethernet needs reconfiguring.  But if you can access one site, then it's not your connection that's at fault.

Are you sure you're actually accessing the web?  Or maybe just reloading from cache on your local machine?  Try Shift-Ctrl-R in Firefox to force a true reload, and see if it goes anywhere.  Once it's a bit more clear what's going on, we can try to deal with it.

"Or did you mean you'd downloaded some Windows-specific drivers into Ubuntu and then moved them?" Yes this is what i meant.

I did that reset that you told me to do with Shift-Ctrl-R and it still didn't change that i can only access google, but it did sign me out of my iGoogle.

---

### Post by superprash2003 on 2009-08-04
try using opendns servers - 208.67.222.222 and 208.67.220.220 ..

---

### Post by RobFS1 on 2009-08-04
how do i do that?

---

### Post by quixote on 2009-08-04
I'm not sure whether superprash2003 means to ping those servers or to use them as your nameservers in network settings.  First try pings on those IPs, on yahoo.com, on [www.google.com](www.google.com).  Anything.  We're just all wondering whether you actually have a connection or are just loading that one google page from cache.

Open a terminal (Start > Accessories > terminal) and type ```
ping yahoo.com
``` If it finds the site, it'll return a string including the time the transit took.  Stop it by hitting Ctrl-C.  If it just sits there and doesn't return anything, try: ping 208.67.222.222

---

### Post by superprash2003 on 2009-08-05
i meant using it as a nameserver  , take alook at this [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

