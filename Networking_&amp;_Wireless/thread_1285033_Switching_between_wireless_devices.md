---
title: "Switching between wireless devices"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by dyslexicfurby on 2009-10-07
In my Toshiba satellite I have an internal wireless card. I also purchased a high gain Alfa wireless adapter. Here is what I would like to do:

I want to set up my laptop and connect to a given network. If the signal strength is poor, or insufficent, I want to shut off my internal card, pull out my wireless adapter and connect it, and use it to connect to the wireless network. Preferably with minimal fuss. I'd like to automate this if possible, maybe with a script or something.

I'd like to do this because this wireless adapter is high gain and should boost my signal when I use it; the wireless on my college campus is sketchy sometimes.

I'm very new to Ubuntu, so I'd prefer a step by step explanation please.

---

### Post by sedawk on 2009-10-07
I'm not quite sure about it, but I think when using
Network Manager, the settings are not bound a specific
device, but to wireless in general.
So if you disable the internal card (bringing down the
interface, removing the loaded kernel module for the device)
and then plug in the external device, it might use the
same settings the previous adapter used because it
is detected as a wireless adapter and so the wireless
settings are used ...

---

### Post by dyslexicfurby on 2009-10-07
The problem I have is that when I do "ifconfig wlan0 down" the wireless card turns itself back on shortly after even if I plug in the wireless adapter. As a result, the laptop connects with both devices, when I just want the wireless adapter.

---

### Post by sedawk on 2009-10-08
Any difference when you try "ifdown wlan0"?

Have you tried to unload the kernel module afterwards (in case
the devices do not use the same one).

---

### Post by dyslexicfurby on 2009-10-09
I will try ifdown wlan0. How do I unload the kernel module?

---

### Post by dyslexicfurby on 2009-10-16
Are we allowed to bump? I still can't switch wireless devices.

---

