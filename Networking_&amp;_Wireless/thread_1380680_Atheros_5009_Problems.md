---
title: "Atheros 5009 Problems"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by bluefoxox on 2010-01-13
I recently bought a sweet new HP dm3-1039wm netbook, and I love it. I decided to get into Linux by installing Unbuntu 9.10 64 bit. Since the notebook does not have a DVD drive I used wubi (9.10) from windows 7 and was impressed with its ease of use. So far everything is great! Well almost everything =) about 5 minutes into being online I was disconnected from my wireless router. The routers ssid is linksys, and still showed up as being available but I could not reconnect to it unless I restarted (this happened over a dozen times). Over the next few days I tried using my Linux install on campus, at McDonalds, and at the library. It was the same thing no matter where I tried to stay connected, plugged in or running on battery. Here is a little bit about my install I hope will help given someone reaches out to me.
 
kernel 2.6.31-17-generic
AR5009 Wireless card (not sure of the chipset though)
9.10 64 bit installation
 
remember ssid of networks show up, they just can not be connected to after the connection is lost. Almost any guidance would be great, thanks!

---

### Post by bluefoxox on 2010-01-15
The Chipset is AR928X I may have found a solution here [http://art.ubuntuforums.org/showthread.php?t=1378485&highlight=AR928X+backports](http://art.ubuntuforums.org/showthread.php?t=1378485&highlight=AR928X+backports) I have no idea how I am going to be able to stay connected long enough to get this install completed... I will leave another post if I get it working in Linux.

---

### Post by bluefoxox on 2010-01-15
This worked perfectly.  I do not know exactly what occurred (I will before the night is over) but it worked.

---

### Post by rossmoore on 2010-01-15
I have the same wireless chipset on my zotac ion board. I have had that up and working non-stop - both connected to a wireless router and, more recently, as a wireless access point itself (using hostapd). Let me know if you need any more help debugging it.

---

