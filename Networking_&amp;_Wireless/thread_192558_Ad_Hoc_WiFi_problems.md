---
title: "Ad Hoc WiFi problems"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by kingedwin on 2006-06-08
I am trying to set up an ad-hoc wifi network between two computers running Dapper so that I can share a DSL connection.  Both use a Linsys WMP54G.  I've tried connecting both cards via DHCP, one assigned 222.222.222.0 for IP mask and gateway address, and both cards this way.  I can activate the cards, but Firestarter says that the connection isn't properly configured.  Wifi-radar will connect with the other computer and get an IP address, but as far as I can figure out, nothing shows up on connection strength.

Each time I do this, my internet connection on the first computer (physically connected to the DSL modem via eth0) quits working, and I have to restart the computer for it to work again, although network-admin says it's still working. :P  Since I have to rely on online guides, this is more than a little frustrating.

Here's what I need to know:  

What is making my internet connection cut off?
How do I need to configure the two network cards?  (lots on stuff on WiFi or ad hoc, but I can't find anything on ad hoc wifi)
How do I make sure that I am sharing the internet connection with the other computer?

Here's what I get with iwconfig (second computer isn't the exact format):

Computer A - WiFi not currently running, DSL modem connected to eth0.

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:113
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Computer B - WiFi is on

ra0       RT61 Wireless  ESSID:""
Frequency: 1Mhz
          Mode:Auto  Channel:0
          RTS thr=0 B   Fragment thr=0 B
          Link Quality:0/70  Signal level:-121dBm  Noise level:-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by kingedwin on 2006-06-08
BTW - When I run "iwlist ra0 scan" on either computer, I get 
"ra0  No scan results"

---

### Post by kingedwin on 2006-06-09
Anyone?

---

### Post by Stone123 on 2006-06-09
and rts61.dat file is set to adhoc?

---

### Post by kingedwin on 2006-06-09
I don't have an rts61.dat file, or anything starting with rts on either computer.  How and where do I add it?

---

### Post by kingedwin on 2006-06-09
*bump*  Can't find anything on this, even on Google.

---

### Post by rmjb on 2006-07-05
You can find an ad-hoc wifi command here:
[http://www.ubuntuforums.org/showthread.php?t=205501](http://www.ubuntuforums.org/showthread.php?t=205501)

It worked for me.

- rmjb

---

### Post by rmjb on 2006-07-11
You can also check out wifi-radar to get a more powerful configuration gui for your wifi: [http://packages.ubuntu.com/wifi-radar](http://packages.ubuntu.com/wifi-radar)

- rmjb

---

