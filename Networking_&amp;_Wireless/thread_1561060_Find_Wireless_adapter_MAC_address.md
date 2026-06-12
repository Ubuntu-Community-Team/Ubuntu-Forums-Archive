---
title: "Find Wireless adapter MAC address"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by rykel on 2010-08-25
Hi, I am looking for the MAC address of my Wireless adaptor.

However, as noted above, ifconfig no longer shows the wifi HWaddr and without an internet connection (wifi), I am unable to run **hwinfo --wlan** (program not installed) and there is no **"Connection Information"** available in Network Manager (greyed out).

Is there any other way to find out the MAC address of a machine that is not connected to the internet without wifi or ethernet?

Sometimes I wish that upstream developers would NOT remove existing features without consulting the users or having a replacement.   :p

---

### Post by sgosnell on 2010-08-25
ifconfig gives my wireless adapter MAC address whether or not I'm connected.  It does have to be enabled, but a connection makes no difference.  I also get the ethernet address regardless of connection.  I'm not sure why you're not getting it.

---

### Post by Iowan on 2010-08-25
Moved to separate thread.

---

### Post by zionLobo on 2010-08-25
type this code:
macchanger -s wlan0
that should do the trick

---

### Post by zionLobo on 2010-08-25
sorry u shd first install macchanger from synaptic...

---

### Post by rykel on 2010-08-25
> **sgosnell said:**
> ifconfig gives my wireless adapter MAC address whether or not I'm connected.  It does have to be enabled, but a connection makes no difference.  I also get the ethernet address regardless of connection.  I'm not sure why you're not getting it.

I forgot to mention that the wireless adaptor IS enabled, because I can see a list of wireless networks when I click on Network Manager applet in the Notification Area at the top right hand corner.

btw, I need to find the MAC because my wireless network enables access only by specified MAC addresses.

---

### Post by rykel on 2010-08-26
Thank you everyone for reading and helping me in this thread.

I finally found the "problem"... the wireless MAC was always there in **ifconfig**, except that it said "eth1... ethernet" so I thought that referred to my LAN.

It was not, and indeed was referring to my wifi.

---

### Post by Iowan on 2010-08-26
> **rykel said:**
> I finally found the "problem"... the wireless MAC was always there in **ifconfig**, except that it said "eth1... ethernet" so I thought that referred to my LAN.

It was not, and indeed was referring to my wifi.My laptop calls the wireless card eth1 - I'm not sure why... but it works - so I let it.  Glad you got your answer. Consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

### Post by rykel on 2010-08-29
Done, and thank you!!!   :D

---

