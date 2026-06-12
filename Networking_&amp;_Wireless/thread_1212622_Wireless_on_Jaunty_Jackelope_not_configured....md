---
title: "Wireless on Jaunty Jackelope not configured..."
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by cwrighta70 on 2009-07-13
Hello, All.

I'm a brand new Ubuntu user, and I've been searching and searching for a solution to getting my wireless working.  I'm currently on a wired connection, and if I click on the "connection icon" in the panel it says my Wireless Networks "device not managed".

If I enter "sudo iwlist scan" in the command line, I get:

```
lo          interface doesn't support scanning
etho        interface doesn't support scanning
wmaster0    interface doesn't support scanning
wlan0       interface doesn't support scanning
pan0        interface doesn't support scanning
```

If I ping my home IP, I get:

```
network unreachable
```

Could anyone provide some help on this please?

Thanks!
Chris

---

### Post by cariboo on 2009-07-14
Have a look at this [thread=1211618]thread[/thread] post #7

---

### Post by cwrighta70 on 2009-07-14
Well, I followed the steps I found in the thread above, and it started to fix part of the problem.  Then I realized I needed to download the correct drivers for my Broadcom hardware.  After that, I changed the nm-system-settings.conf to show ifupdown:managed=true.  Now, my computer is finding networks, but I cannot connect to them.  

Also, a while back I tried to manually create my home wireless network "Wright's".  Even though I deleted it, any time the ethernet is disconnected I get a popup that says "Wright's Disconnected".  Where is this coming from?!  Is it cached somewhere?  Or did I accidentally set it somewhere else?

Regardless, I can pick up my work's wireless network, but cannot connect to it.

Any help would be greatly appreciated!
Chris

---

### Post by cwrighta70 on 2009-07-14
Nevermind!  I figured it out.  Thank you, anyway.

---

