---
title: "Restricted Drivers Manager = Broke 7.04"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by iammike on 2007-04-27
I installed Ubuntu on one of my desktop systems that's using a Nvidia 6600 GT AGP vid card.  Once the install was done I was not running at the native resolution of 1680x1050 that my LCD runs at.

I then clicked the Restricted Drivers Manager and it suggested I install the Nvidia drivers.  I had it do just that and rebooted like it asked.

When I came back up, when I'd normally get a login screen my monitor was simply saying "Out of Range".

I used Ctrl-Alt-2 to get to a command line and started looking through the forums for ideas.

In the end, not many ideas and nothing actually fixed it but I did run "dmesg | grep -i nv" as was suggested in one of the threads for ideas.  Here is what I ended up with.....

```
36.844070 nvidia: module license 'NVIDIA' taints kernel.
37.935435 NVRM: loading NVIDIA Linux x86 Kernel Module 1.0-9631 (date and time here)
51.913952 **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
51.917723 **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
51.921150 **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
```

---

### Post by RAKninja on 2007-04-28
oddly enough i get 
```
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[   50.403096] nvidia: module license 'NVIDIA' taints kernel.
[   50.676325] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   70.882938] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:04.0] forgot to specify physical device; fix it!
[   70.883695] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:04.0] forgot to specify physical device; fix it!
[   70.884335] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:04.0] forgot to specify physical device; fix it!

```

do you have an intel integrated gfx chip? i do, cant seem to get it 100% fixed, and no one else seems to know how.

---

### Post by iammike on 2007-04-28
Nope, MB has no gfx card on it, just the Nvidia in the AGP slot.  :-/

---

### Post by RAKninja on 2007-04-28
no one knows why this is happening?

---

### Post by amorangi on 2007-04-29
Same thing happened to me with 8800GTS graphics card. I haven't looked into fixing it yet, but if I were a noob I'd be a little perturbed by this - activating the driver like this is obviously not ready for prime time.

---

### Post by thedaemon on 2007-04-29
I get almost the same message from dmesg that you do and my system is working fine. It seems like your x configure file is using a refresh rate that is not acceptable for your monitor. I added in my 1920x1200 resolution to the xorg config file manually and all is well.

---

### Post by kerry_s on 2007-04-29
first run> sudo dpkg-reconfigure -phigh xserver-xorg
to get you back to stock and undo anything you might have done.
then
try running> sudo nvidia-xconfig

---

