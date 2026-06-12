---
title: "List of wireless networks available no longer there."
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by Autodave on 2012-08-26
Running Xubuntu 12.04 on a 9" netbook.  Couple of updates ago, wireless networking quit.  Was not a big deal then, but it is now and I need to get it working (as it always worked right out of the box before).

I went to Users & Groups and to Advanced settings.  There I see a box for Wireless privileges and it is checked.

It used to be that when I turned the netbook on, it would tell me that there were wireless networks available and would give me the option to connect to one of.  Now,  I do not get that screen anymore and need to figure out how to get it back.

Any ideas?

---

### Post by sanderj on 2012-08-27
rf-kill-switch on?

Check with:


```
sander@R540:~$ rfkill list
0: samsung-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
sander@R540:~$ 
```

---

### Post by Autodave on 2012-08-27
> **sanderj said:**
> rf-kill-switch on?

Check with:


```
sander@R540:~$ rfkill list
0: samsung-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
sander@R540:~$ 
```


I am typing from the netbook screen to this screen:

rfkill list
0:  eeepc-wlan: wireless LAN
                   Soft blocked:  yes
                   Hard blocked: no

I am assuming that the wireless has been blocked somehow.  How do I UNblock it?

---

### Post by Autodave on 2012-08-27
> **Autodave said:**
> I am typing from the netbook screen to this screen:

rfkill list
0:  eeepc-wlan: wireless LAN
                   Soft blocked:  yes
                   Hard blocked: no

I am assuming that the wireless has been blocked somehow.  How do I UNblock it?

I found it!  You got me 99% of the way there.  After I gave myself "permission" in USERS & GROUPS ( I have NO idea how I lost that permission) to use the wireless, all I had to do was hit the FUNCTION F2 and it was back on again!

Don't know how it got all screwed up, but it works now!

Thanks!

---

