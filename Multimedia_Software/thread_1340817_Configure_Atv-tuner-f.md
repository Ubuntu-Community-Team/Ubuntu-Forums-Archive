---
title: "Configure Atv-tuner-f"
date: 2009-11-29
forum: Multimedia Software
---

### Post by lordrayden31 on 2009-11-29
The problem is that i've installed this pci card on ubuntu 9.04 (gnome) it works fine, until i turn of Tvtime or gnome radio. The sound continues and it does not turn off. 


Also i would like to configure the remote control for this pci card.

i have done cat /proc/bus/input/devices in this are the results:

I: Bus=0001 Vendor=109e Product=036e Version=0001
N: Name="bttv IR (card=38)"
P: Phys=pci-0000:00:08.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/input/input8
U: Uniq=
H: Handlers=kbd event5 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 10000ffc

---

### Post by xc3RnbFO8P on 2009-11-29
Try: 
> alsamixer -c 1

---

### Post by lordrayden31 on 2009-12-02
> **Ringi said:**
> Try:

Thanks it worked but using pulseaudio

---

