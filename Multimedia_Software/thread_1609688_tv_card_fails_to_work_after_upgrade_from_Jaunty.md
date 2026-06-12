---
title: "tv card fails to work after upgrade from Jaunty"
date: 2010-10-30
forum: Multimedia Software
---

### Post by pickarooney on 2010-10-30
I upgraded fro Jaunty to Karmic and then to Lucid and my TV card has stopped working. I had been informed that this was a result of the splitting of the linux-firmware into two separate packages, but having installed the linux-firmware-nonfree package the problem persists. The card is a Hauppauge WinTV PCI and although it is properly recognised by commands like lsmod, lspci and in the sound card settings, I can't tune in a single channel. It worked out of the box in Jaunty. 

Is there anything else that needs to be done to get the nonfree firmware working properly?

---

### Post by pickarooney on 2010-10-31
I've tried following the instructions in [this](http://howtoubuntu.org/?p=20) tutorial but there's still not a sniff of a channel. This is so annoying.

---

### Post by pickarooney on 2010-10-31
I tried restarting from scratch and then ran tvtime-scanner. It claims to have found channels and added them to the XML file 

```

  <list norm="SECAM" frequencies="Custom" audio="bg">
    <station name="509.50MHz" active="1" position="1" band="Custom" channel="509.50MHz" finetune="0"/>
    <station name="510.50MHz" active="1" position="2" band="Custom" channel="510.50MHz" finetune="0"/>
    <station name="557.25MHz" active="1" position="3" band="Custom" channel="557.25MHz" finetune="0"/>
    <station name="558.00MHz" active="1" position="4" band="Custom" channel="558.00MHz" finetune="0"/>
    <station name="558.75MHz" active="1" position="5" band="Custom" channel="558.75MHz" finetune="0"/>
    <station name="581.50MHz" active="1" position="6" band="Custom" channel="581.50MHz" finetune="0"/>
    <station name="582.00MHz" active="1" position="7" band="Custom" channel="582.00MHz" finetune="0"/>
    <station name="605.25MHz" active="1" position="8" band="Custom" channel="605.25MHz" finetune="0"/>
  </list>

```

But when I run tvtime there are no channels available.

---

### Post by pickarooney on 2010-12-13
Trying this from scratch after reformatting and installing MAverick but still no channels. Doesn anyone know of a good resource for tv cards so that I can confirm if this one is simply no longer supported?

---

