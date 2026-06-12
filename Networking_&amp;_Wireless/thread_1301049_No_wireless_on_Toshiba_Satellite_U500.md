---
title: "No wireless on Toshiba Satellite U500?"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by shawnpeps on 2009-10-25
Hi there.

I installed 9.04 on my Toshiba Satellite U500 last night. Install went awesome, it was super quick and everything seems to work great although my main problem is the fact that I'm unable to pull up the wireless network I have setup in my house. 

I'm not sure if it's an issue with the install or my wireless card, or if I'm just not seeing something and doing it wrong. From what I've gathered from the Toshiba site, the wireless card is a Realtek 802.11b/g/n but that could be entirely wrong.

So any help is hugely appreciated.

---

### Post by codedash on 2009-11-02
Any update about the problems in Karmic? Also could you define which u500 model you bought?

---

### Post by BizCasFri on 2009-11-11
I am also having this problem. I've done a but of research and the card is an Intel Integrated WiFi 5100. The card is not recognized when doing an lshw check, and using ndiswrapper on the 32bit Windows driver doesn't seem to work either, and just says "Hardware present: No" (I use a GUI ndiswrapper as I'm fairly new to this whole game)

There was a page on Bugzilla that detailed a patch but it was really complicated and I had no idea on how to do it, and I've lost that page, unfortunately.

Otherwise 9.10 works like a charm, with only a few other small issues. I'm really at a loss on what to do now.

---

### Post by BizCasFri on 2009-11-11
Ha HA! Found the patch! I just have... no idea how to install this. Any help would be appreciated!

[http://bugzilla.kernel.org/show_bug.cgi?id=13940#c3](http://bugzilla.kernel.org/show_bug.cgi?id=13940#c3)

---

### Post by juju27 on 2009-11-29
I have the same laptop. I successfully installed the driver following the instrusction given on [https://bugs.launchpad.net/ubuntu/+bug/401126](https://bugs.launchpad.net/ubuntu/+bug/401126) post #15 and #20.
Ask me, if you need more informations

Julien

PS. I try to install the nvidia driver, but without success. Did you try?

---

### Post by Dude-PWB- on 2009-11-29
Although you seem to have the same laptops, it is best to check and make sure you have the same chipsets for your wireless cards.

```
lspci -vv
```

In the terminal, and determine the chipset you have. RTL8192e and RTL8192se are different chipsets and require different drivers.

---

### Post by richporter3 on 2010-02-08
> **juju27 said:**
> I have the same laptop. I successfully installed the driver following the instrusction given on [https://bugs.launchpad.net/ubuntu/+bug/401126](https://bugs.launchpad.net/ubuntu/+bug/401126) post #15 and #20.
Ask me, if you need more informations

Julien

PS. I try to install the nvidia driver, but without success. Did you try?


Can you please give me a step by step list of how to install this file I am very new to this?

---

