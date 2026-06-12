---
title: "Controlling GPU fan speeds"
date: 2013-02-06
forum: Multimedia Software
---

### Post by Vire on 2013-02-06
I only recently transitioned from Win7 to Ubuntu, and most of the time since has been spent customising and/or getting some essential programs up and running in Linux. 

One application I always had running in Win7 was MSI Afterburner, the reason being that my GPU seems to have some kind of faulty bios and refuses to properly regulate its own fanspeed - it always sets itself to 70% by default, which is unbearably loud and stupidly overkill considering it's normally around 35'C idle temperatures at 40% fan speed. 

Unfortunately it seems msi afterburner is unavailable in Ubuntu, so I've been trying to get Nvidia X Server to set the fan speed manually lower, but it seems to refuse to actually save any settings. 

I've changed the xorg.conf (configuration) file so that I could actually adjust the fan speeds myself, using 

```
gksudo gedit xorg.conf
```

to open it with permissions, then added 

```
Option         "Coolbits" "4"
```

to the device section. This enabled fan speed manipulation. That saved in the configuration file okay. 

But when I actually go into Nvidia X Server, enable manual fan speed and change it down to say 45%. I'll save it and quit and it'll be fine so long as I'm logged in. The moment I log out or restart the computer, it defaults back to automatic fan speeds.

System specs:
OS - Ubuntu 12.10 amd64
CPU- Intel i5 2500k
GPU- Gigabyte GTX570 OC
RAM- 12gb DDR3

Also, for some reason it says 'graphics - unknown' when I go into system settings > details, not sure if that's related at all.

---

