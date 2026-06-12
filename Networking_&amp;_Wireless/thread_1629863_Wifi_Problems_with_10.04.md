---
title: "Wifi Problems with 10.04"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by adiosgang on 2010-11-24
I've tried searching the internet and the forums to find the answer to this problem, but I can't come up with anything.  

When I'm on my home network (WRT54G with DD-WRT) on my netbook (Ubuntu 10.04) the entire wifi network will go down (every device connected wirelessly drops its connection) in what seems a download dependent manner.  For example, when I'm just browsing the web it takes a while but when I start streaming video it usually goes out in about 2-3 minutes.  I've tried to get the same thing to happen with my wife's MacBook, but I can never get the network to go down.  I also just got a Boxee Box that's connected via wifi (until my 50ft ethernet cable gets here from newegg) and that won't take the network down.  It seems to only be my netbook and I can't figure out why.

Having no idea where to start, I'll post the out put of iwconfig.

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"CHEW"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:40:10:10:00:03   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks for the help everyone.

---

### Post by grahammechanical on 2010-11-24
That listing from iwconfig looks OK. My listing is similar. Your signal level is a reasonable 52 dBm.  I do not understand what you mean by:

> entire wifi network will go down (every device connected wirelessly drops its connection)

Perhaps it is the router? Or Is there too big a load being put on the router?

Regards.

---

### Post by adiosgang on 2010-11-24
I don't think it's the router since it only happens when my netbook is on the network.  

In regards to my explanation, it seems like all of the devices lose their connection to the router and then have to re-connect.  Does that make sense?  It's like the router isn't there for a second and then it's back, but every device on wifi has lost its connection and has to re-connect.

---

