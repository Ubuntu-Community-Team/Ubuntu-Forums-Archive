---
title: "IPsec and Racoon"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by Tim_Vrakas on 2013-08-24
I'm working on setting up IP sec and I'm stuck.

   setkey                                 racoon  <-------(IKE)-------> somebody
       |                                           ^      |      (5)
       |                                            |     |(6)
       |(1)                        +-----+   +---+
       |                        (4)|                            |
    v                              |                            v
+-----+      (2)     |         (3)  +-----+
| SPD |<----- kernel ------>| SAD |
+-----+                      |                      +-----+
                                       |(7)
                       v
(ASCII ART MESSED UP)
[http://stackoverflow.com/questions/18392121/ipsec-and-racoon-custom-function](http://stackoverflow.com/questions/18392121/ipsec-and-racoon-custom-function)

(1)The administrator sets a policy to SPD by using setkey.
(2)Kernel refers to SPD in order to make a decision of applying IPsec to a packet.
(3)If IPsec is required, then kernel get the Key for IPsec-SA from SAD.
(4)If it is failed, then kernel send a request to get the Key to racoon.
(5)racoon exchange the Key by using IKE with the other to be established IPsec-SA.
(6)racoon put the Key into SAD.
(7)Kernel can send a packet applied IPsec.
  That was on the KAME website.

How does Racoon set itself up to recive requests from the kernel?
I don't understand the interface. I need to write a program to go between the kernel and racoon.
It should be possible. The kernel is not provided by racoon, and the kernel can run variose IKE's (racoon, openswan).
I need to do some stuff before racoon is called, So i efectively to replace racoon with my own program, which does what it wants and then calls racoon.

---

