---
title: "Stop wifi radio killswitch from disabling USB wifi device"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by deadvirus on 2010-07-03
Hello,

My laptop has an internal wireless device and a button to turn it on/off, but since it has bad reception I use an external USB wireless adapter.
The problem is that if I turn the internal wireless device off using the button, it also turns the USB wireless adapter off.

Is there anyway to use the killswitch (the button) only for the internal wireless device?

This only started to happen in Ubuntu 10.04. 

From syslog I've found this, so the NM is responsible for managing the killswitch:
```
NetworkManager: <info>  WiFi now disabled by radio killswitch
```

---

### Post by deadvirus on 2010-07-06
Bump!

---

### Post by MartyBuntu on 2010-07-06
Have you tried disabling from the BIOS?

---

### Post by flash63 on 2010-07-06
Hello,
> Is there anyway to use the killswitch (the button) only for the internal wireless device?
no, unfortunately not.

Possibly you can automatically switch between the two devices with an udev-Rule. For that i need more Informations about the internal Card and the Wifi-Stick:
```
lsusb
lspci -nnk | grep -i net -A2
```

---

### Post by deadvirus on 2010-07-11
> **flash63 said:**
> Hello,

no, unfortunately not.

Possibly you can automatically switch between the two devices with an udev-Rule. For that i need more Informations about the internal Card and the Wifi-Stick:
```
lsusb
lspci -nnk | grep -i net -A2
```

I don't have the usb adapter with me right now so I can't post that... 
But it would be nice to don't have to touch the killswitch button at all...

---

### Post by xavivars on 2010-07-31
I have a related problem: my hardware switch is not working properly, and it randomly switches off and on when it's on "on" position ("off" position is working well, it's always disconnected).

That's a real problem, because you get disconnected from internet, and have to touch and move softly the switch until it gets on again. So I bought a USB wireless card, because I thought it would be always on.

My surprise was when I realised that when my hardware switch switched off, my USB device was also disabled!

Is there no way to keep it enabled?

---

### Post by digitaleagle on 2010-07-31
I just started having the same problem.  My wireless would not work -- disabled and I couldn't enable it.  I thought it was a kernel update or something that broke it.

I found the message you talked about in the syslog, and that is what led me to look at the switch.  It was switched on, but I thought I would play with to see what happened.

I just now got it working by:
- switching the switch to off
- rebooting
- switching the switch back on
Then, it started working again.

Is it possible that any of this is a software thing?  Is it maybe that the driver is misinterpreting the status of the switch?

---

### Post by xavivars on 2010-08-01
No, it's not a software related problem: it's a hardware problem, because the button is not working properly both on Windows and Linux (the light switches on and off when it wants)

---

