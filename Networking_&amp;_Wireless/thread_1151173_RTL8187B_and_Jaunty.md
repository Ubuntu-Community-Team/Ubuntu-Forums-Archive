---
title: "RTL8187B and Jaunty"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by icdelg on 2009-05-06
I bought my laptop one and a half years go and still can't get wireless to work. I have the rtl8187b wireless card with device id 8197. I have tried pretty much all solutions I could find and just upgraded to jaunty hoping for native support. I can view wireless networks and "connect" to them but when I try to view webpages I receive errors like "failed to connect."

**I am running 64 bit ubuntu and my network uses WPA.

Any help would be awesome! I love ubuntu but this is driving me nuts...

---

### Post by phantom3113 on 2009-05-06
I believe either something may be wrong with your install, or you don't have the RTL8187b Realtek Card. Since 8.10, that card has had native support and I know by experience that it works fine

```
Bus 006 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 006 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
```

(that's an excerpt from my lsusb)

---

### Post by icdelg on 2009-05-06
here's the result of lsusb

```

isabella@me-laptop:~$ lsusb
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter

```

---

### Post by phantom3113 on 2009-05-06
Yours lists the "ID 0bda:" as 8197 as opposed to 8189 in mine. As minor as that sounds, I think that's what's causing the trouble. I'll see if I can find something, but if anyone else knows right now, feel free to chip in! :)

*Ok, I may have found something. This thread is a little old, but it may work for you: [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092) The instructions are pretty straightforward.

This one may also help if the first doesn't, although it's a little lengthy and looks like it may be a bit technical: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

---

### Post by icdelg on 2009-05-07
I never thought of trying a different web browser before but just tried epiphany and I was able to load pages. I'm guessing the problem is with firefox...

---

