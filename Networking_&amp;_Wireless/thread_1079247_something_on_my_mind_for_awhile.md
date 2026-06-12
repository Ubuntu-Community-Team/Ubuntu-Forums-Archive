---
title: "something on my mind for awhile"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2009-02-24
I was wondering, since Ubuntu don't work with my WinModems, would it be possible to but a "bare bones" Windows box in front of a router and share the TCP/IP protocol on a dynamic internet connection?

---

### Post by puppywhacker on 2009-02-24
linux has winmodem support, it's called linmodem. it may or may not be supporting your specific modem though.

you can use the microsoft internet connection sharing, I played with ICS last century, I still remember my frustration about inexplicable things happening, but that was over 10 years ago

---

### Post by theozzlives on 2009-02-24
Well right now I have Broadband, I was thinking of an "what if" situation.

---

### Post by mpokrywka on 2009-02-24
"Internet connection sharing" can teoretically be chained without limits, I don't know Windows configuration, but as I remember, WinXP's built-in ICS has hardcoded internal network address (192.168.0.0/24). But there are other ($$$) solutions for windows (WinRoute?).
But your idea (barebone Windows box only to use modem) seems way off - cost of barebone pc+winXP will be higher than only modem that linux supports.

---

### Post by theozzlives on 2009-02-25
> **mpokrywka said:**
> "Internet connection sharing" can teoretically be chained without limits, I don't know Windows configuration, but as I remember, WinXP's built-in ICS has hardcoded internal network address (192.168.0.0/24). But there are other ($$$) solutions for windows (WinRoute?).
But your idea (barebone Windows box only to use modem) seems way off - cost of barebone pc+winXP will be higher than only modem that linux supports.

but I want the connection to go thru my router across the network (this is hypethetical you know)

---

### Post by mpokrywka on 2009-02-25
Heh, I can't imagine this: *"I want the connection to go thru my router across the network (this is hypethetical you know)"* (+previous posts context),
you'll need to draw it for me ;)
```

INTERNET <==DSL==> ROUTER? <---- LAN ---> your computer?
 ||                   |                    ^
 ||                   | ???                |
  \==> MODEM <=> WINDOWS BOX <=====???=====/

```
use those items to visualize your idea...

---

### Post by theozzlives on 2009-02-25
internet ===> windows box w/modem ===> router ===> network ===> my computers

---

### Post by mpokrywka on 2009-02-25
AFAIK ICS on Windows works with dialup, so you'll need connect WindowsPC with router using ethernet, Windows will run dhcp server on ethernet side with addresses from subnet 192.168.0.0/24. Your router will get IP through dhcp from windows and your internal network should be configured to something different than 192.168.0.0/24.

Or maybe I didn't understood you and you meant:
```

INTERNET ==DSL==> [DSL modem] ==ethernet==> [windowsPC] ==ethernet==> [router] =>...
 ||                                         /
 \\                                        / RS232
   ===PSTN========================> [ modem]

```

---

### Post by theozzlives on 2009-02-26
> **mpokrywka said:**
> AFAIK ICS on Windows works with dialup, so you'll need connect WindowsPC with router using ethernet, Windows will run dhcp server on ethernet side with addresses from subnet 192.168.0.0/24. Your router will get IP through dhcp from windows and your internal network should be configured to something different than 192.168.0.0/24.

Or maybe I didn't understood you and you meant:
```

INTERNET ==DSL==> [DSL modem] ==ethernet==> [windowsPC] ==ethernet==> [router] =>...
 ||                                         /
 \\                                        / RS232
   ===PSTN========================> [ modem]

```

No DSL where'd you get that from?

---

### Post by mpokrywka on 2009-02-26
> **theozzlives said:**
> No DSL where'd you get that from?
That was only my interpolation of your "now I have Broadband" and your idea of modem connection - I thought you may want to use it as "hot standby" backup link in case of broadband failure.

But for standard ICS, WindowsXP should work (see [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126) or [http://support.microsoft.com/kb/314066](http://support.microsoft.com/kb/314066) ).

---

### Post by theozzlives on 2009-02-26
No I was playing with ideas of how to get along on the network with nothing but winmodems incase some day I'm without broadband.

---

