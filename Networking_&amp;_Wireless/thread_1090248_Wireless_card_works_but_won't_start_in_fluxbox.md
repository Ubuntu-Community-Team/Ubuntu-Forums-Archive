---
title: "Wireless card works but won't start in fluxbox"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by 4dplane on 2009-03-08
Hi, 

I have an ubuntu box that I am running fluxbox on(destop manager). The problem is the wireless network card will not start correctly when I first log into the account that starts fluxbox. If I first login into a normal account(no fluxbox) and then back into the fluxbox account the wireless card works fine. So it must be something to do with how the card starts when loggin that fluxbox is not handling. 

**When I only have a wireless card connected:**
I boot the machine I have a login promt. If I do not login and try to ssh from another machine I cannot.

**When I only have a nic card connected:**
I boot the machine I have a login promt. If I do not login and try to ssh from another machine I can.

so the wireless card's setup comes from the destop manager?

Any thought on how I may solve this problem?

---

### Post by kerry_s on 2009-03-08
add "nmapplet &" to your ~/.fluxbox/startup file.

---

### Post by ugm6hr on 2009-03-08
> **4dplane said:**
> so the wireless card's setup comes from the destop manager?

Not quite.

But if you originally had Gnome, then it was being connected by Network Manager.  Hence kerry's suggestion to ensure that NM autostarts with Fluxbox.

There are other options if you don't like NM:

1. Wicd (similar to NM, but appears more lightweight).

2. Connect manually using command line script (NM would then have to be removed; Wicd can work in tandem with commandline control as an applet).

---

