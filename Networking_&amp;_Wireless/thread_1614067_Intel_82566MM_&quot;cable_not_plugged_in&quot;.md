---
title: "Intel 82566MM &quot;cable not plugged in&quot;"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by majkey on 2010-11-05
Hi have problems with my Intel 82566MM gigabit NIC. Using the default e1000e module. The module finds and load the nic but it doesn't recognize that i have plugged in cable or not. It always says "cable not plugged in". Using xubuntu now but same problem with regular ubuntu not that i think it matters.
I tried downloading and installing e1000 from Intel but it doesn't seem to find the nic at all.

Any suggestions how to work this out? My googling says others too have had problems with this card. Couldn't find any real working solution though.
Its Lenovo Thinkpad T61 laptop.
Using 10.10 Maverick btw.

---

### Post by chili555 on 2010-11-05
> I tried downloading and installing e1000 from Intel but it doesn't seem to find the nic at all.That's because e1000e and e1000 are two different animals; even though they have similar names.

I wonder if there are any kernel messages about this. In a terminal, do:```
dmesg | grep e100
```Post the result and let's see what's happening under the hood.

---

### Post by majkey on 2010-11-07
Yes i know that e1000 is a different driver, my googling suggested i should try it instead of e1000e.
i have disabled e1000 and now running default e1000e driver again, still no progress though.

dmesg shows this:

[    1.140315] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    1.140318] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    1.140365] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.140383] e1000e 0000:00:19.0: setting latency timer to 64
[    1.140619] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[    1.625064] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:16:2b:56
[    1.625067] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.625102] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1008ff-0ff
[   13.340298] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   13.400154] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X

---

### Post by chili555 on 2010-11-07
Well, that's good news and bad news. There is nothing apparently wrong. That's bad news because we see nothing to fix.

Are you certain the cable and the port on the router are sound? What does this tell us?```
sudo ethtool eth0
```

---

### Post by majkey on 2010-11-07
Ok i dug out my docking station and it works through it. I think the driver somehow is set to always use the docking stations port not the internal on the laptop. The laptops internal port worked under windows so im sure its not broken.

---

### Post by chili555 on 2010-11-07
> I think the driver somehow is set to always use the docking stations port not the internal on the laptop]I wonder if there's a setting in the BIOS that you can change for this. I am going to go look at my T60 right now.

EDIT: I looked in the BIOS for my T60 and didn't see anything that obviously enables/disables the NIC depending on whether it's attached to a dock. I wish I could be of more help.

---

### Post by majkey on 2010-11-09
*Bump*

Still need help with this, anyone know how you edit settings in the driver? For example in windows you can do advanced properties and change a ton off minor settings. Is it possible too do this in linux? The internal networkport is still visible so its no problem to use when i have my laptop docked. So never use the dockport would work just fine.

---

### Post by chili555 on 2010-11-09
> anyone know how you edit settings in the driver?Please see *modinfo e1000e*. For example, to enable smart power down, you could temporarily do:```
sudo rmmod e1000e
sudo modprobe e1000e SmartPowerDownEnable=1
```To make it permanent, write a file /etc/modprobe.d/e1000e.conf. Add a single line:```
options e1000e SmartPowerDownEnable=1
```I only used this as an example of how to invoke an option. I am not suggesting this specific option will resolve your issue.

---

### Post by jhjessup on 2011-04-20
> Please see modinfo e1000e. For example, to enable smart power down, you could temporarily do:
Code:
```

sudo rmmod e1000e
sudo modprobe e1000e SmartPowerDownEnable=1
```

To make it permanent, write a file /etc/modprobe.d/e1000e.conf. Add a single line:
Code:
```

options e1000e SmartPowerDownEnable=1
```

I only used this as an example of how to invoke an option. I am not suggesting this specific option will resolve your issue. 



This worked with Natty (11.04) on my Thinkpad T61 to enable the ethernet.

---

