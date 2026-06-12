---
title: "can I connect to tv?"
date: 2008-12-28
forum: Multimedia Software
---

### Post by babujbf on 2008-12-28
Hi I have a geforce 8500 gt working flawlessly on my ubuntu partition, and this card has s video out and my tv has to connect the s video. Now the question is... is it that simple? Just use the cable to plugin the computer to the tv? Do I have to configure anything?

---

### Post by theozzlives on 2008-12-28
An RCA video plug cannot connect to S-Video without an adapter

---

### Post by easybake on 2008-12-28
It can be almost that easy. Plug it in. Restart. and then...

run nvidia-settings from terminal. if it says it isn't installed install it with 

```
sudo apt-get install nvidia-settings
```

once the download is finished, start nvidia-settings and configure the display how you want it.

---

### Post by babujbf on 2008-12-28
no, they are both svideo... no rca the tv has s video in and the computer s video out

---

### Post by babujbf on 2008-12-28
I configure the display on nvidia settings, can I still run two displays at the same time? computer monitor and tv? and if it was s video to rca using a converting cable would it still be the sma econfiguration?

and one more question a little off topic... lets say I get an old pc and I only have vga out and I use a vga convertor to connect to the tv... how do I configure that? does it work?

---

### Post by easybake on 2008-12-28
> **babujbf said:**
> I configure the display on nvidia settings, can I still run two displays at the same time? computer monitor and tv? and if it was s video to rca using a converting cable would it still be the sma econfiguration?

You can run two separate displays at the same time a couple of ways. You can set it up as twinview which will set up the displays to act as one large desktop. 

If you choose separate x screen then they are 2 separate desktops. 
If you want to use this option you will probably have to run sudo nvidia-settings and be sure to click the "save to x configuration" button and then restart.

---

### Post by babujbf on 2008-12-28
how about when u simply get a vga to rca adapter and connect from the computer to the tv, how does that work? do you need a video card or is the vga adapter from the motherboard enough?

---

### Post by easybake on 2008-12-28
> **babujbf said:**
> how about when u simply get a vga to rca adapter and connect from the computer to the tv, how does that work? do you need a video card or is the vga adapter from the motherboard enough?

The adapter would do the job. Having to get a separate video card would ruin the point of buying an adapter.

---

