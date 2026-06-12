---
title: "Wireless won't work"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Duncan7221 on 2010-01-17
I just installed ubuntu 9.10 on my compaq presario v5000 and everything seems to be working so far except for my wireless. It says it's a proprietary drive "I think" I press the button to enable it but it doesn't work.

---

### Post by Crafty Kisses on 2010-01-17
I need some more information, go into the terminal, **(Applications->Accessories->Terminal)** once your in the terminal you can run:
```
lspci
lsusb
lshw -C network
```
That will tell me a bit more information about your setup, then from there I can help you from there.

---

### Post by Duncan7221 on 2010-01-17
I don't know if I'm entering it correctly. It's says lspci isn't valid and it shows me a bunch of options.

---

### Post by bkratz on 2010-01-17
> **Duncan7221 said:**
> I don't know if I'm entering it correctly. It's says lspci isn't valid and it shows me a bunch of options.

You are probably not entering the right command

lspci ( is actually LSPCI in lowercase)

---

### Post by Duncan7221 on 2010-01-18
the correct command ended up being sudo instead of lspci. anyway i got it fixed by setting up a wired connection and trying to enable  the wireless then. i guess it had to download the driver.

---

### Post by bkratz on 2010-01-18
> **Duncan7221 said:**
> the correct command ended up being sudo instead of lspci. anyway i got it fixed by setting up a wired connection and trying to enable  the wireless then. i guess it had to download the driver.

Actually lspci was the correct command to display the devices connected to the pci bus. Congratulations on getting it working!




Edit: I see you were asked to also do a command that required lshw---that would have required a sudo to be correct

---

