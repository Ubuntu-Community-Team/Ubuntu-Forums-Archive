---
title: "Atheros AR9285 Compaq laptop CQ61 - 410 US - Wireless N does not work, but G does"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by Dargos on 2011-09-24
I am using a Compaq laptop (CQ61-410US using the Atheros 9285 card) and I'm able to connect to my access point using G, but not N.  This problem existed with me using Ubuntu 10.10 and 11.04.

I'm able to connect to my Cisco 2000 AP using G, but not via N.

I was able to connect to my Cisco 2000 AP using another Windows XP laptop over N.

I've spent a lot of time looking around for an answer and troubleshooting this, but I'm stumped.

One other thing:  After I set up the network connection for N, I get a bogus connection established message.  It says that I am connected to the AP (even when it is turned off!), but I can't access the administrative console.

Can someone offer some ideas on how to fix this?

Many thanks!:D

Output of iwconfig for reference:

me@hplp:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

