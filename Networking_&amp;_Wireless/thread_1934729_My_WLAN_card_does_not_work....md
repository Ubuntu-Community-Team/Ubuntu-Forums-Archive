---
title: "My WLAN card does not work..."
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by haqthinh on 2012-03-02
I am a (completely) newbie to ubuntu, my friends suggest me using it. :D Now I have two OS, windows 7 and Ubuntu on my laptop.

I cant get onto the internet with ubuntu, while I can easily on my Win. Whenever I try to connect in my ubuntu, the signal of the wireless always jump from blue (enabled) to red (disabled) crazily, and then the wireless refuses to work.

I am currently using hp dv6t-2300. Can any one give me solutions for this trouble? I really like the interface of ubuntu btw, so I want to explore more of its potential. 

Thanks.

---

### Post by praseodym on 2012-03-03
Hi,

please show the terminal (CTRL+ALT+T) outputs of the commands:

```
lspci -nnk
lsmod
rfkill list
iwconfig
```
Any buttons/switches/keys/key combinations (e.g. Fn+F2)? Checked the BIOS settings?

You can copy the outputs to a textfile and upload it.

---

