---
title: "Unable to install driver"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Gnosiz on 2010-03-03
Hey.

Basically, I have just installed Ubuntu (9.10) on a Asus Eee 4g netbook I have recently acquired and I cannot connect to the internet because my machine won't find any available wireless networks. I am assuming this is because my wireless module isn't isn't installed - I don't quite know the problem.

I've searched the internet and came across this tutorial: [http://www.mustnofee.com/tutorials/37-tutorials/50-setting-up-atheros-ar5bxb63-on-ubuntu-804](http://www.mustnofee.com/tutorials/37-tutorials/50-setting-up-atheros-ar5bxb63-on-ubuntu-804)
I know it is for Ubuntu 8.04, but I'm hoping it will work.

Unfortunately the link provided isn't working so I can't download the driver (and I'm struggling to find it online anywhere, other than .exe files).

So, what I need is:

a) someone to help me find the type of file I need to download (following the tutorial)

or

b) just otherwise direct me on how to go about making this work.

--

Sorry for the long post.

Many thanks in advance,
Gnosiz.

---

### Post by chili555 on 2010-03-03
I'll take option *b*. First, let's further identify your card. From a terminal, please do:```
lspci -nn | grep Atheros
```Please post the result.

Can you temporarily get a wired ethernet connection, if we need it?

---

### Post by Gnosiz on 2010-03-03
> **chili555 said:**
> I'll take option *b*. First, let's further identify your card. From a terminal, please do:```
lspci -nn | grep Atheros
```Please post the result.

Can you temporarily get a wired ethernet connection, if we need it?

OK.

Well, I did

```
lspci -nn
```and this came up:
[IMG]http://i50.tinypic.com/apjz1y.png[/IMG]

and this (scrolled down slightly):


[IMG]http://i46.tinypic.com/2rdgbd4.png[/IMG]

but nothing happened when I did

```
grep Atheros
```But yeah, I can connect my netbook to the internet with the wireless adapter my desktop is using, or I could just use the desktop I'm using now.

Thanks.

---

### Post by chili555 on 2010-03-03
I don't see any wireless device at all. Is it built-in or USB or...what? What tells you it's an Atheros, as referenced in the link you provided?

---

### Post by deadlockedgamer on 2010-03-03
if it is a netbook there hardware is fairly standard. Try the karmic if you don't have it. Go to system aministration hardware drivers while connected via Ethernet cable and see if the driver is available by default!

---

### Post by Gnosiz on 2010-03-04
> **chili555 said:**
> I don't see any wireless device at all. Is it built-in or USB or...what? What tells you it's an Atheros, as referenced in the link you provided?

Hey, I know... this is what I've been told.

It says at the bottom of (underneath) my netbook:

Wireless Module : Atheros AR5BXB63

Thanks.

---

### Post by Gnosiz on 2010-03-04
But is it also something to consider that I installed Ubuntu Notebook Remix on it... it came OOTB with Debian (I think)

---

### Post by Gnosiz on 2010-03-04
Bump.

---

### Post by chili555 on 2010-03-04
Let's check a few more places. Please post:```
lspcmcia
lsusb
```Thanks.

---

### Post by Gnosiz on 2010-03-05
```
lspcmcia
```

does not do anything.

```
lsusb
```

Shows this:

[IMG]http://i47.tinypic.com/tao7dl.png[/IMG]

Thanks.

---

### Post by chili555 on 2010-03-05
Still no sign of any wireless networking device. I wonder if there is a switch that totally turns off the device somewhere on the netbook. Generally, even if there is a switch, the device shows up, even if it shows up as disabled.

Of course, the other possibility is that Asus forgot to install the card. You might call them or email them or the retailer for further guidance.

---

### Post by Gnosiz on 2010-03-05
> **chili555 said:**
> Still no sign of any wireless networking device. I wonder if there is a switch that totally turns off the device somewhere on the netbook. Generally, even if there is a switch, the device shows up, even if it shows up as disabled.

Of course, the other possibility is that Asus forgot to install the card. You might call them or email them or the retailer for further guidance.

That is overly annoying. lol.

Well, yes there is a switch to turn it off and on; and when it's on - a little blue light flashes...

But I just get this feeling they'll blame it on the fact I've installed UNR on the machine!

Thanks anyway!

---

### Post by chili555 on 2010-03-05
> when it's on - a little blue light flashes...You might try all those commands both with the light flashing and without. See if there is any change.

---

