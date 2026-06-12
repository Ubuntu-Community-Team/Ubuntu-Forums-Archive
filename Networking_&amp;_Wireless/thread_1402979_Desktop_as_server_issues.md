---
title: "Desktop as ?server? issues"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by bakedham on 2010-02-09
Okay, so here's the deal
I have my xbox 1
i have my desktop
i have a wired router
i have my wireless network

my desktop has:
3 wired NICs
1 wireless NIC

what i want to know:
is it possible to:

```
                                                          +---+
                                                          | M |     +--------+
WIRELESS NIC   ............................((|))    +====>| O |====>|INTERNET|
+-----+((|))...:                             |      #     | D |     +--------+
|  D  |__|      +--------------+           +----------+   | E |
|  E  |ETH0     |            R |           | WIRELESS |   | M |
|  S  |<========|WAN PORT    O |           |  ROUTER  |   +---+
|  K  |ETH1     |            U |           +----------+
|  T  |========>|PORT 1      T |
|  O  |      +==|PORT 2      E |
|  P  |      #  |            R |
+-----+      #  |              |
             #  +--------------+
        +----------------+
        |\     \  /     /|
        | \     \/     / |
        |  \   XBOX   /  |
        |  /          \  |
        | /     /\     \ | 
        |/     /  \     \|
        +----------------+
```and have the xbox connect to xbox live/internet?
i know its (somewhat) complex, and there are probably easier ways of doing this, but i basically need to work with the materials i have (i.e. what's in the picture). so here are my thoughts (go easy on me, i'm n00b when it comes to linux)
keep the WIRELESS how it is, but use ETH0 as like a router type thing in that it'll connect my ROUTER to the WIRELESS ROUTER (and thus MODEM and INTERNET) through my DESKTOP's WIRELESS NIC.
the thing i've been having problems with, it seems, is that only one of my ETHX's can be active at once.

any thoughts or pointers?
if you need any more info, feel free to ask and i'll do my best to find it out (n00b)

thanks in advance for any help :D

---

### Post by Charly85551 on 2010-02-10
Hi bakedham,
I don't think it will work. 
1 - only one router can be used, a connection between desktop and WAN-port is not allowed. (anyway one connection between desktop and router is enough!)
2 - What you should get is a switch to distribute your internet connection. For example:
Use your wired router as the first connection to the modem and try to use your wireless router just as an access point which can then act as a switch. But make sure the DHCP service of the wireless router is switched off!

To me it looks like you have some other restrictions not mentioned here.:wink:

cheers

charly85551

---

### Post by bakedham on 2010-02-10
aww... lameness...
thanks for the response :D

---

