---
title: "disabled wireless by hardware switch~rfkill doesnt work"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by muzzyr on 2013-01-03
Hey guys
I have ubuntu 12.04 on lenovo 460 and my wireless is disabled by hardware switch. As I see this is a common issue, I've tried suggested solutions which apparently worked for some people, but none of them worked for me. rfkill, reseting the BIOS to default, etc. 
It's a dual boot machine and I could not enable the wireless in windows xp neither. 
Will appreciate any suggestion to solve the problem.
Thanks

---

### Post by muzzyr on 2013-01-06
Any suggestion guys?:confused:

---

### Post by muzzyr on 2013-01-10
I upgraded my os to ubuntu 12.10, hoping that it would help. nothing happened

---

### Post by tgalati4 on 2013-01-10
Remove your Ugg boots.  Static electricity can cause the wireless to shutdown.  On my Dell 600m, I have to shutdown, open BIOS, and turn wireless back on.  This only happens when I am wearing my sheepskin slippers, and only in the winter.  And only when I move the computer and shuffle from one side of the house to the other.

---

### Post by muzzyr on 2013-01-10
I'm not sure if I exactly understand what you suggest. But it doesnt seem to be static electricity
Thanks anyway

Strange thing is that I cannot connect even with an external wireless modem!

---

### Post by chili555 on 2013-01-10
Let's have a look at:```
lspci -nn | grep 0280
rfkill list all
```Once we see these results, we'll look a bit deeper.> rfkill, reseting the BIOS to default, etc.
It's a dual boot machine and *I could not enable the wireless in windows xp neither*. I wonder if it's a hardware failure.

---

### Post by tgalati4 on 2013-01-10
Turn your wireless on in BIOS.  Sometimes wireless shuts down and there is no way to turn it back on unless you boot into BIOS and turn it on manually in BIOS.  Do you have a function switch (say FN-F2) to turn on wireless?

---

### Post by muzzyr on 2013-01-11
Thanks tgalati, it doesnt work...

Dear chili

here is the result 

```
muzzy@muzzy-laptop:~$ lspci -nn | grep 0280
06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
muzzy@muzzy-laptop:~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes

```

surprisingly I lost the xp and cant boot the machine with that!
but whether it is the hardware problem or not, why I even the external wireless is disabled.

---

### Post by chili555 on 2013-01-11
>  why I even the external wireless is disabled.I wasn't aware you were also running an external wireless. Many laptops, including two of mine, work exactly that way. The wireless switch turns off *all* wireless, absolutely.

Let's try a couple of things:```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
rfkill list all
```Any improvement?

How about:```
sudo modprobe -r ideapad-laptop
sudo modprobe ideapad-laptop no_bt_rfkill=Y
sudo rfkill unblock all
rfkill list all
```How about now?

---

### Post by muzzyr on 2013-01-12
still same
soft block no and the god damned hard block yes
:))

---

### Post by muzzyr on 2013-01-12
and I have to confess that something has disabled my mind too. what a masterpiece of english:

>  			 				 why I even the external wireless is disabled. 			 		

---

### Post by chili555 on 2013-01-12
> **muzzyr said:**
> still same
soft block no and the xxx hard block yes
:))Please, family-friendly for me and my grand-daughter.

Let's see if there is a clue in dmesg:```
dmesg | grep -i -e error -e 06:00
```Thank you.

---

### Post by muzzyr on 2013-01-13
apologies.
this is the result:

```
[    0.963110] pci 0000:06:00.0: [14e4:4727] type 00 class 0x028000
[    0.963157] pci 0000:06:00.0: reg 10: [mem 0xd9100000-0xd9103fff 64bit]
[    0.963389] pci 0000:06:00.0: supports D1 D2
[    0.963391] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    0.972840]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    3.213700] usb 2-1.3: device not accepting address 3, error -71
```

---

### Post by praseodym on 2013-01-13
Check the key combinations Fn+F5, etc. Is there a switch for headphones and mic somewhere? Check this one...

---

