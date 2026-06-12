---
title: "WPA Enterprise on a WPA personal network?"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by ivancruz on 2009-11-03
Just give up configuring Karmic on a WEP wireless network and now trying to go WPA all the way.

All my computers are connected to a DIR-635 wireless router, configured to use WPA2-personal as a security option.

I have now 4 computers connected:

1. my desktop, Karmic upgraded from Jaunty, wired connection, works fine.
2. kids desktop, Win XP, wireless, works fine.
3. sister laptop, dual boot Win XP and fresh Karmic install, wireless, both works fine.
4. wife desktop, Karmic upgraded from Jaunty, wireless, does not work. The reason? Karmic keeps asking for a WPA enterprise security parameters on that machine. There is no option to go WPA personal, the only other option is dinamic WEP. What can I do?

Ivan.

---

### Post by ivancruz on 2009-11-03
Just to illustrate my problem...

First attachment is the dialog I was expecting to see (sorry labels in portuguese, but I believe it speaks by itself).

And the second one is what I get.

---

### Post by ivancruz on 2009-11-03
Solved!!!!

By comparing the result of [FONT="Courier New"]iwlist scan[/FONT] command on two different machines I could see, the one with problems where listing 802.x as the Authentication Suite for my network (it was PSK on the working machine, as well for all the other neighboring networks). The solution was removing the old driver inherited from Jaunty and installing a new one downloaded from here:

[http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip](http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip)

---

