---
title: "lost wifi after latest update"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by audichris on 2010-02-01
i have a acer aspire one (zg5) with a 2 week old installation of unr. shortly but not immediately following my last update my wifi no longer functions. when i go to the network connections tab in my toolbar it does not list available wifi networks. it does not apparently recognize wifi capability at all. but the wifi worked right off the rip on new install. im fairly new to linux so any help would be appreciated.

---

### Post by rrinjapan on 2010-02-01
I'm having exactly the same problem. I'm also a newbie and I was doing okay but I upgraded and now wifi shows nothing. I'm at a bit of a loss at the moment ...

RR

---

### Post by rrinjapan on 2010-02-02
Hey Audichris,

I forgot my buddy put me on to this, not sure it'll help but it might be the place to go.

In the menu (I'm using Mint so it's a little different) go to >Administration >Hardware drivers

It should some wireless drivers that are not part of Linux that probably need to be installed. 

I'm a newbie so take this advice with a grain of salt. I'm working on it in the background at the moment so if I have any luck I'll keep you posted.

RR

---

### Post by lotharmat on 2010-02-02
What wireless card do you have

You can find out by posting the output of

```
lspci
```

or 


```
lsusb
```

---

