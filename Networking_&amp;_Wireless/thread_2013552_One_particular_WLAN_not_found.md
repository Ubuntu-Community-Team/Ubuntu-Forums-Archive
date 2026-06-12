---
title: "One particular WLAN not found"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by ubossel on 2012-07-01
Quickly Google-searched for it, but haven't found anything similar.

Kubuntu 11.10 on Samsung laptop, but no previous problems with wireless. Have changed nothing, no update or anything, last night everything worked fine. After waking up, no connection to WLAN. Network manager finds a lot of networks but not mine. Several restarts of laptop, but always the same.

WLAN router is working fine (using it now to write this on my girlfriend's laptop), just my laptop doesn't find it. 
Scanning for wireless with Kubuntu network manager finds all my neighbours' networks, but doesn't show the Netgear router I have. So, it can't be a hardware problem with my laptop.

All hardware seems to be working fine. Therefore it's probably a software problem, but what could it be?

BTW, WLAN is not hidden or anything.

---

### Post by jackyboy633 on 2012-07-01
Please could you show me the output of this command:
```
lspci | grep Network
```
Could you also tell me the model of Samsung laptop you have?
This will help me diagnose the problem for you. :)

Jackyboy633

---

### Post by ubossel on 2012-07-01
Thanks for offering to help.

The problem solved itself. Don't know how, don't know why. Haven't changed anything. Just went shopping, after coming home I started laptop & wlan, & everything works fine again. Not as if I had not restarted laptop & router before (several times).  :confused:

But just FYI the requested information:
Samsung NP-R540-JS08CN
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

I would file it under "another Broadcom issue", if it were not for some other erratic behaviour this system shows recently. Don't know, I'll probably have to upgrade to 12.04 sooner or later.
Although ... , installed 12.04 on my old HP laptop recently & there the old Broadcom issues resurfaced which I thought long resolved. Hmph...

---

### Post by ubossel on 2012-07-02
Seems to be a recurring problem. Same today.

Wonder whether it will solve itself again after I go shopping later. :popcorn:

---

### Post by ubossel on 2012-07-02
&, oh wonder, it really works again after I returned from shopping.

Still don't have a clue where the problem originates from, but the solution is clear: go shopping!

---

### Post by sudodus on 2012-07-02
> **ubossel said:**
> &, oh wonder, it really works again after I returned from shopping.

Still don't have a clue where the problem originates from, but the solution is clear: go shopping!
Nice but kinda expensive and time-consuming solution ;-)

Don't click Thread Tools at the top of this page to mark this thread as SOLVED

---

### Post by ubossel on 2012-07-03
> **sudodus said:**
> Don't click Thread Tools at the top of this page to mark this thread as SOLVED
Well, it's not really solved as long as I don't know what's going on.

But since I found a workaround (or, if you want, a seemingly working solution) I will mark it as solved.

The workaround is not shopping, but starting the router a few minutes before the laptop. If I do so, Kubuntu detects it on start-up. If I start the router simultaneously or later, Kubuntu can't see it (even after hours).

Since the router works fine with other laptops, I don't think, it's a router problem. But, since I'm not tech-savvy enough to find out what's really behind it, I mark the thread as solved. If by chance I find out anything more, I'll give an update.

---

### Post by sudodus on 2012-07-03
> **ubossel said:**
> Well, it's not really solved as long as I don't know what's going on.

But since I found a workaround (or, if you want, a seemingly working solution) I will mark it as solved.

The workaround is not shopping, but starting the router a few minutes before the laptop. If I do so, Kubuntu detects it on start-up. If I start the router simultaneously or later, Kubuntu can't see it (even after hours).

Since the router works fine with other laptops, I don't think, it's a router problem. But, since I'm not tech-savvy enough to find out what's really behind it, I mark the thread as solved. If by chance I find out anything more, I'll give an update.
Glad you found a real solution :-)

It's similar to what we need for my son's old IBM Thinkcentre via Home Plug: Internet should work upstream when the computer is booted.

---

### Post by asmoore82 on 2012-07-03
Are you using a non-Broadcasting SSID?

and/or

Are the wireless router and laptop too *close* to eachother? It's a long shot, but I've heard it can be a problem.

---

### Post by ubossel on 2012-07-05
> **asmoore82 said:**
> Are you using a non-Broadcasting SSID?

and/or

Are the wireless router and laptop too *close* to eachother? It's a long shot, but I've heard it can be a problem.
Thanks for your input, but no to both. It's not a hidden network & the laptop is usually in another room.  

It's really strange. Everything was working fine, didn't change a thing, no update, nothing. & then...
Well, I have a workaround, & it's not too inconvenient. So, it's ok with me now.

---

