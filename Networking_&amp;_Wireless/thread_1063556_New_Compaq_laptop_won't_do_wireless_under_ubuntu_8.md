---
title: "New Compaq laptop won't do wireless under ubuntu 8.10"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by muchdugan on 2009-02-08
Ubuntu Wireless Problem with new laptop:

I just got a Compaq Presario CQ60-216DX with Vista Basic preloaded.
Since I am a long time ubuntu user I decided to dual boot the 2 OS's...
My Compaq laptop has a wireless button right by the power button for turning the wireless on/off. When it's on, it's blue and off=orange.
Under vista it's blue.
Under ubuntu it's orange.

I cannot seem to get this wireless button on my new laptop to work with ubuntu
Any ideas?

---

### Post by superprash2003 on 2009-02-08
go to the terminal and type the following commands and post its output
1)lshw -C network
2)iwconfig
3)iwlist scanning

---

### Post by drunkardivan on 2009-02-08
You've probably already tried this, but on both of my 8.10 installations, wireless didn't work until I restarted the laptop. I think one I actually had to restart twice, and then it worked fine.

---

### Post by ginnie6 on 2009-02-08
When I installed on my HP I had the internet hardwired at first until I could do the updates..once they were done wireless worked.

---

### Post by racie on 2009-02-08
What wireless card do you have?

---

### Post by kylesgirl138 on 2009-02-22
Hiya there, I'm brand-spankin' new to Ubuntu (I mean, in the sense that I just installed this morning and have no clue what I'm doing).  I have the exact same laptop as muchdugan, a Compaq Presario CQ60-216DX, came with Vista Basic...and I have the same problem.  The wireless switch is blue in Vista, and internet works fine - and it's orange in Ubuntu, no internet connection.  I press the switch but wireless remains off.

Help!!! :(

---

### Post by Reiger on 2009-02-22
First you must know what wireless card you have; some will work with 'proper' linux drivers, others will work with NDISWrapper + Windows (XP) driver and yet others may not work at all. To obtain information about your wireless card. In Windows type:
```

ipconfig /all

```
in the CMD shell. Find your device there, and try to see if for instance Google already yields guides & howto's for that device under Ubuntu. (If it can be found via Google then that will save you time waiting for answers here...)

---

### Post by facundo31 on 2009-02-22
hi,  i have the same laptop,  and the wireless data is:
*-network
description:wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter

*-network DISABLED
description: ethernet interface
physical id: 1


i tried many things to make this work, but nothing happend


thanks

---

