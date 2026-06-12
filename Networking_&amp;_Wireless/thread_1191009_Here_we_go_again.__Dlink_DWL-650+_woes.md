---
title: "Here we go again.  Dlink DWL-650+ woes"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by wheelhorse2347 on 2009-06-18
I have a dell Inspiron 3800 laptop, with an Intel Celeron processor, and 10 GB hard drive.  I've been using Ubuntu as my OS for about 2 years, but, I have recently switched to Xubuntu.  I'm running Jaunty.  

I have a Dlink DWL-650+, and I'm hoping to get things working.  The computer has no ethernet port, so I am limited to the wireless card.

Upon installation, I got a message that Xubuntu couldn't detect network interfaces, which I expected.  Now that it's up and running, I noticed the 'link' light on the card does blink, and the network icon in the upper right corner DOES show the network I'd like to connect to.  Unfortunately, after filling in the passcode, the icon disappears, and I am not connected to the internet.

I have heard many conflicting arguments when it comes to this card.  I've heard some people say it works out of the box, while others suggest ndiswrapper or prism54.  I am wondering if any of you have had experience with this card in jaunty, and if so, is it possible to get the wireless working without requiring an already existing lan internet connection.

Thank you,
Jordan

---

### Post by wheelhorse2347 on 2009-06-18
Results of iwconfig

lo         no wireless extentions.


wlan0      IEEE 802.11b+  ESSID:""  Nickname:"acx v0.3.36"
           Mode:Managed  Frequency:2.422 GHz  Access Point:  Not-Associated
           Bit Rate:22mb/s    Tx-Power=18 dBm   Sensitivity=176/255
           Retry min limit:7   RTS thr:off
           Power Management:off
           Link Quality=60/100  Signal level=45/100  Noise level=0/100
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx exessive retries:0  Invalid misc:0  Missed beacon:0

---

### Post by wheelhorse2347 on 2009-06-18
btw, the smileys are colon then the letter O.  I don't know why that happened.

---

