---
title: "Wireless disabled by hardware switch on HP Pavilion"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by accidentallyc on 2012-12-02
Hey guys, i just started using Ubuntu 12.04LTS and i can't seem to solve my issue. I've been hovering around the forums for a while but none of the solutions i've seen have worked on mine. I'd love to have this fixed xD

**Laptop:** HP Pavilion Dv5
**Problem: **Wireless disabled by hardware switch
**How i got here: **I reformatted my entire computer and replaced my Win Vista with Ubuntu Karmic Koala then i upgraded and upgraded till i got to Ubuntu 12.04

**rfkill list all**
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes

**other info**
1. the indicator is also off, cant turn it on specially since i have no more Win OS
2. tried downloading broadcom drivers (since earlier i discovered i was broadcom)
 ... (unless i read it wrong... hahah)
3. im no linux/ubuntu expert

please and thank you!

---

### Post by pepschmir on 2012-12-03
I had the same problem and solved it with the following command:

sudo rfkill unblock wifi

Good luck!

---

### Post by accidentallyc on 2012-12-03
> 
sudo rfkill unblock wifi


If it were that easy i wouldn't have posted xD but i appreciate the help haha

---

### Post by accidentallyc on 2012-12-03
Hey guys, i'm not sure why this happened but what i did was during reboot sequence before i even got into ubuntu os. i simply spammed clicking the  wireless "touch" and the wifi turned on.

it might not have been that but thats what happened. hahah

---

### Post by muzzyr on 2013-01-06
same problem, its driving me crazy.
Can you explain what did yo do exactly?

---

### Post by accidentallyc on 2013-01-07
I'm sorry i have no clue, it just "magically" turned on which i know is like saying Jesus suddenly came in and troubleshot my laptop for charity.

But generally the notion is to force the laptop's wifi to turn on through hardware so if you are able to do this via the original O.S. then do it there. I'm sorry if i cant be more helpful than that haha

---

### Post by leoyde on 2013-01-15
its not a case that you have a physical switch on the hardware above / below keyboard is it? ):P


If its killed by hardware switch, then its something outside the OS and more like the button

---

### Post by accidentallyc on 2013-01-15
The pavilion has a touchscreen switch and its digitally implemented so there are other means to turn it on other than a physical switch xD

Just check the other forums, some have actually done it ( says them ) xD

---

### Post by shyflower on 2013-09-09
> **pepschmir said:**
> I had the same problem and solved it with the following command:

sudo rfkill unblock wifi

Good luck!


This worked for me! Thanks!

---

