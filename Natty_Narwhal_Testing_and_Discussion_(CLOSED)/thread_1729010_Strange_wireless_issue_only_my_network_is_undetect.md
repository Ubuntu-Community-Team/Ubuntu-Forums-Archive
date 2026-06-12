---
title: "Strange wireless issue: only my network is undetected"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by koma77 on 2011-04-14
I upgraded to 11.04 beta from 10.10 where the wireless (Broadcom Corporation BCM43225 802.11b/g/n (rev 01)) was working just fine.

After the upgrade I can detect lots of wireless network, but _NOT_ mine!

I can connect to other network (even though I had some problems staying connected at one time).

If I dual boot into windows I can use my own network, so the hardware is OK.

Even if I scan for networks with "iwlist wlan0 scan" I cannot find my network. (But all the neighbors).

Anyone else have the same problem?

Or anyone got an idea of what to try?

---

### Post by cariboo on 2011-04-14
Try this command to associate your wireless device with your ap:

```
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
```

---

### Post by 5149.5 on 2011-04-14
Are you sure your AP is broadcasting it's SSID?

---

### Post by koma77 on 2011-04-15
> **cariboo907 said:**
> Try this command to associate your wireless device with your ap:

```
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
```


Ah, yes, but since the AP is not detected, not even by iwlist, that does not work...

---

### Post by koma77 on 2011-04-15
> **5149.5 said:**
> Are you sure your AP is broadcasting it's SSID?

Yep: the SSID is visible on the same computer when I launch Windows 7.
And, it worked flawlessly on 10.10.

---

### Post by koma77 on 2011-04-16
Another strange thing that I found was that when I disabled the Broadcom wireless driver in the "proprietary drivers" settings there was no difference.

The same wireless networks were available (but not mine).

It's almost like the upgrade from 10.10 to 11.04 installed some other wireless driver that overrides whatever is installable via the "prop. drivers" thingy.

This is strange...

---

### Post by koma77 on 2011-04-16
I made a very interesting test!

I put a USB WiFi dongle with a ralink chipset in my laptop running 11.04.

The result: I could just find some of the networks (and of course not mine).

I then popped the USB dongle into my 10.10 computer: Every network found, including mine!

So: The problem is not on a WiFi-chipset-driver-level. It is either a kind of MAC-driver problem or even higher up in the chain.

Anyways, it is a serious problem and I guess I should report it?

---

### Post by koma77 on 2011-04-16
Here is the next interesting piece of information on this problem:

I tried to use airodump-ng, and with that tool I can see my network!

What does that mean?

What is the difference between how airodump-ng operates and how network-manager does?

---

