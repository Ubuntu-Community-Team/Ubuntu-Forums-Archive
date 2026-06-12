---
title: "Please help me. I'm getting desperate!!"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by ObliviousFreak on 2011-06-06
Okay, this might be really simple, I'm brand new to linux. 

So I'm running a live disk of ubuntu 11.04 because my windows 7 is totally messed up and wouldn't recognize my external hard drive and I cant back up my documents. I actually really like Linux and wanna keep it, but I have 2 problems. 1, I can't figure out for the life of me how to connect to the Internet. Its not scanning for any wireless networks and only seems to want me to connect via Ethernet. I think the problem is that it doesn't recognize my wireless card/doesn't know it's installed. Is there any way to fix that? I just want to be able to connect to wifi. 

Now my second question. I can acess all my files fine, but Linux doesn't seem to register my external hard drive either, nor any other USB device. It just acts like there not plugged in. No error message or Anything. Is the a way to fix that? I fear that there might be some sort of hard ware issue, because in windows seven it doesn't recognize USB devices or my wireless card (among many many other problems) either. Although, I tried An older version of ubuntu on this same computer once and had a similar wireless issue which I was never able to resolve before my 7 was having any wireless issues.


Anyway, and help whatsoever would be really appreciated. I really need my computer back

---

### Post by mmad on 2011-06-06
1. For the wireless problem, establish what hardware you are using then look for Linux compatibility and hopefully download some drivers. This should be an easy fix.

2. It sounds like a hardware problem because it is unlikely that two operating systems would have a problem like this. Check your BIOS and see if there are any settings that may turn off external device compatibility. 

I hope you get this sorted!

---

### Post by matt_symes on 2011-06-06
Hi

I have to concur. That sounds like a hardware issue. We may be able to get more information though.

Open a terminal in the live cd. Plug in a USB device and copy and paste this into the terminal (or type)

 ```
dmesg | grep usb
```

Post the results back here. Do that by selecting the text in the terminal, right clicking and selecting copy and right clicking and selecting paste into your next post.

When you post back wrap the text in code blocks like this

[noparse]```
 out from dmesg command
```[/noparse]

That makes it much easier to read.

Kind regards

---

### Post by dargaud on 2011-06-06
The following commands might be useful to help you find your hardware (use 'man' and some time to figure out the details, some need 'sudo' before them):
> lshw
lspci
lsusb
hwinfo
fdisk -l
dmesg

---

