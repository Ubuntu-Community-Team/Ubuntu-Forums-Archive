---
title: "Doubt about installing video driver"
date: 2009-09-01
forum: Multimedia Software
---

### Post by vishwanth87 on 2009-09-01
Hi. 

I'm completely in love with ubuntu. Gosh! I'm wondering why I was ever stuck with windows. Glad that I've switched to ubuntu. 

I installed ubuntu and works fine. 
My system does not have a video card. Do I need to install any drivers for the on board card? 

Because, while minimising the windows especially firefox, I see a lag and it minimises slowly.. Is it because of the video driver which I have not installed?

My system specs are,
Intel 945GNT Motherboard  
2GB RAM
320GB HDD

Somebody please help me to install the video driver for my motherboard. I'm a totally new to ubuntu. 

Thanks in advance
Vishwanth.

---

### Post by vishwanth87 on 2009-09-02
somebody please help me out.. :(

---

### Post by bertles86 on 2009-09-02
Try googling your mobo specs, or searching the Intel website and seeing what sort of graphics that has onboard. Then google the onboard gfx type with ubuntu and someone else probably has been there before you!

I should imagine you do need some sort of driver...

---

### Post by gradinaruvasile on 2009-09-02
> **vishwanth87 said:**
> Hi. 

I'm completely in love with ubuntu. Gosh! I'm wondering why I was ever stuck with windows. Glad that I've switched to ubuntu. 

I installed ubuntu and works fine. 
My system does not have a video card. Do I need to install any drivers for the on board card? 

Because, while minimising the windows especially firefox, I see a lag and it minimises slowly.. Is it because of the video driver which I have not installed?

My system specs are,
Intel 945GNT Motherboard  
2GB RAM
320GB HDD

Somebody please help me to install the video driver for my motherboard. I'm a totally new to ubuntu. 

Thanks in advance
Vishwanth.

You do have a video card (integrated on the motherboard) and the driver is already installed. Intel releases drivers for Linux for a long time so their integrated video chipsets drivers are included in the Linux kernel (core) and automatically loaded when needed.

But the integrated Intel video cards are quite slow anyway.

Post the output of (this is a command that is to be launched in a terminal applications-> accessories-> terminal)

```
lspci
```

---

