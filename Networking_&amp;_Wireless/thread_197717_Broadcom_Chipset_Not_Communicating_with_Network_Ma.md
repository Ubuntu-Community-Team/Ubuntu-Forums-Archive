---
title: "Broadcom Chipset Not Communicating with Network Manager"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by Twister594 on 2006-06-16
Here is the billionth thread about Broadcom chipsets, mine is 4306.  I followed the fw-cutter and Network manger instructions, and it worked brilliantly.  I was very happy and everything worked great, including the icon by the clock that showed the "connection strength" in bars, and the connecting icons.

However, now when I turn on my computer (Dell Inspiron 1150), I can use wireless internet, but I see an annoying "No network connection" icon from network manager.

Okay, now for what I've done and tried:
Problem first occured after I booted into Ubuntu and unplugged an ethernet connection (I had it running to get faster speeds on the network).

Tried removing and reinstalling Network Manager.

Tried reinstalling fw-cutter driver and Network Manager in original process.

Tried commenting out all "auto" in /etc/network/interfaces, also tried commenting out entire file.  :rolleyes: 

Okay, I should probably shut up because I have a Broadcom Dell working in Ubuntu, but... this is weird!  Anyways, after all of my attempted "fixes" I'm back to the same status quo that I had when the problem first occured.  Thanks.

---

### Post by towy71 on 2006-06-16
I too  had similar problems and fixed it by doing:
```
sudo gedit /etc/rc.local
```
and entering the following
```
iwconfig $IFACE rate 54M
iwlist $IFACE scan
```and it now works everytime ;)

---

### Post by Twister594 on 2006-06-16
Okay, that didn't work.  I tried inserted the text BEFORE exit0, and then after exit0 as well.  I still get the two little monitors and the bright red "X".  Is there any way that network manager would only be displaying my ethernet connection while connecting to my wireless anyways?

---

### Post by Timmn on 2006-08-09
I have the same problem, and the solution above didn't work for me either.

From some of the horror stories I've seen here, maybe I should just be happy that it works at all.

---

