---
title: "Wireless issues (LEAP/PEAP)"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by lewis595959 on 2009-03-28
I'm trying to connect to the wireless network in my dorm room, which is encrypted using WPA Enterprise, PEAP w/ TKIP.

I can't use PEAP to connect for the simple reason that there is no CA certificate; The network uses a default certificate, but there is no option not to choose a certificate.

As such, I have tried to connect using LEAP instead. This works for me to a certain extent. When I restart my computer I can connect and stay connected to the network for up to 10 minutes, then I get disconnected. 

When I run 'iwevent', The following occurs a few times:

Custom driver event:ASSOCINFO(ReqIE0050f20101000050f20201000050f20201000050f201 RespIEs=01079618243048606c)


Also, there was no option for TKIP or otherwise, but after running 'iwlist wlan0 scanning', I get this in each Cell:

 'IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x'


This leads me to believe that it's picking up on the fact that it's TKIP.


Please note that it's not a hardware issue, since my vista partition (that I had to install because of these issues) interacts flawlessly with the network - I had to run a windows executable first to set up the network, but there is no linux alternative provided.



Also, one more note: I was chatting with a few of the system administrators and they run a few boxes with Ubuntu 8.04 with no connectivity issues.





Thanks in advance - I'm looking forward to finally ditching Vista again. :)




-Steve.




EDIT: FYI, I'm using a Broadcom B43 wireless driver (fwcutter)

---

### Post by lewis595959 on 2009-03-28
Just gonna bump before I go to bed. :)

---

### Post by lewis595959 on 2009-03-30
Another bump. Any ideas?

---

### Post by lewis595959 on 2009-04-02
Yet another bump. C'mon guys, I know you know how to fix this :)

---

### Post by Ryuhayabusa on 2009-04-23
in network-manager-gnome there is usually a box asking you for the certificate.

are you using nm-applet?

---

