---
title: "WLAN stops to work every 15-20 min..."
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by vickoxy on 2010-03-17
Well, i have this problems not only with xubuntu 9.10, but i had it with gnome (ubuntu 8.04-9.10)-so i do not know is it xubuntu or my wlan router issue.

Every 10-20 minutes my wlan connection seems to be freezing-no download/no upload. Can´t read any sites/downloads stop. Network Manager works just fine-shows 100% network strength-and then, after maybe one minute it starts to up/download again. 
So, my nm is not broken-no need to reboot/logout-it just stops, and goes on.

So, this is just a little annoyance not a very big problem...

Anyone has similar experiences?

I have Xubuntu 9.10 on dell mini 10v and nm 0.7.996 (before that i had mini 9 and same problems with gnome).

---

### Post by akand074 on 2010-03-17
I've had that problem on my laptop on the school network, worked fine at home. I installed a different network manager (wicd) and the issue never came back. The network manager that comes default with Ubuntu has never really been that good. Maybe give wicd a try and let us know if you continue to have the problem. That way we will know if it was just me or if the network manager is actually the problem

```
sudo apt-get install wicd
```

---

### Post by vickoxy on 2010-03-17
Thanks for advice-once i installed wicd, and for some time i had no freezing issues, but after a while it came again. 

Still, i will give it now a try.

Thanks for advice...

---

### Post by vickoxy on 2010-03-17
Still, i have one small issue with WICD-it doesn´t show signal strength in %. In preferences everything stays as it should be-but on panel i have error:

---

### Post by akand074 on 2010-03-17
> **vickoxy said:**
> Still, i have one small issue with WICD-it doesn´t show signal strength in %. In preferences everything stays as it should be-but on panel i have error:

Hmm I haven't used wicd in a while, I've been playing around with different distributions on my laptop and use windows mostly for school so I don't recall. But is the internet at least running fine so far? Sorry for the delay.

---

### Post by jrssystemsnet on 2010-03-18
> **vickoxy said:**
> dell mini 10v

The Dell-branded Broadcom wireless NIC that comes in the Mini 10v is a piece of junk.  It sucks under Windows, it sucks under Linux, and it'll suck under any other OS you install on the netbook.

I've installed quite a lot of Intel half-height mini-PCIe wireless NICs in the Mini 10v netbooks; that cures the problem (and gets you a hell of a lot better reception, to boot).

I know this isn't the answer you want, but unfortunately it's the answer you get. :)  Check eBay, you can usually find them for $50 or less.  Be sure to get the **half height** mini-PCIe, though; a full-height won't fit.  (Oh, and the Intel will have three posts on it, where your Dell-branded Broadcom only has two leads - don't worry about it; just put the leads on posts 1 and 2 and ignore post 3, and it'll work fine.)

---

### Post by vickoxy on 2010-03-18
> **akand074 said:**
> Hmm I haven't used wicd in a while, I've been playing around with different distributions on my laptop and use windows mostly for school so I don't recall. But is the internet at least running fine so far? Sorry for the delay.

For now it is working... we will see

Thanks

---

### Post by vickoxy on 2010-03-18
> **jrssystemsnet said:**
> The Dell-branded Broadcom wireless NIC that comes in the Mini 10v is a piece of junk.  It sucks under Windows, it sucks under Linux, and it'll suck under any other OS you install on the netbook.

I've installed quite a lot of Intel half-height mini-PCIe wireless NICs in the Mini 10v netbooks; that cures the problem (and gets you a hell of a lot better reception, to boot).

I know this isn't the answer you want, but unfortunately it's the answer you get. :)  Check eBay, you can usually find them for $50 or less.  Be sure to get the **half height** mini-PCIe, though; a full-height won't fit.  (Oh, and the Intel will have three posts on it, where your Dell-branded Broadcom only has two leads - don't worry about it; just put the leads on posts 1 and 2 and ignore post 3, and it'll work fine.)


Probably that explains why i had the same problem with dell mini 9 too...

For the time being i will stay with dell card...
Thanks

---

### Post by vickoxy on 2010-03-18
jrssystemsnet was probably right-wicd is also freezing after sometime for 30-60 sec...

Seems i have just to live with it...

---

### Post by vickoxy on 2010-03-21
UPDATE: after all it seems that wicd works really better than the network-manager. For a very long time i didn´t notice any freezing (at least those who are lasting 1 or more minutes)

---

### Post by akand074 on 2010-03-23
> **vickoxy said:**
> UPDATE: after all it seems that wicd works really better than the network-manager. For a very long time i didn´t notice any freezing (at least those who are lasting 1 or more minutes)

Oh great, yeah I'll probably recommend trying a different network manager more often in this case.

---

