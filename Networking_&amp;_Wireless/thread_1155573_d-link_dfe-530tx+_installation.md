---
title: "d-link dfe-530tx+ installation"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by harryhoughmagandy on 2009-05-10
I installed Ubuntu 8.04 on an old desktop using the live CD-ROM. It didn't recognize this ethernet card. I've tried many things to get it to work, and I am at a total loss.  The card came with linux drivers, but they do not compile.  I can't use synaptic because the computer has no internet connection due to the card not being recognized.  I read every post on the internet about it, all with no working solution. Does anyone know how to get the drivers installed?  Should I give up, buy 10 CDs, and try the full install? Will the ethernet card be recognized automatically if I do this? (The computer does not have a DVD drive.)   All help is appreciated. I can post any information you may need to diagnose the problem. Cheers!

---

### Post by chili555 on 2009-05-11
Let's ask the computer what the card actually is and then see if we can find a driver existing now in the kernel that will get it to work. Please open Applications -> Accessories -> Terminal and do:```
sudo lshw -[SIZE="4"]C[/SIZE] network | grep -i ethernet
```Post the result here.

---

### Post by harryhoughmagandy on 2009-05-11
> **chili555 said:**
> Let's ask the computer what the card actually is and then see if we can find a driver existing now in the kernel that will get it to work. Please open Applications -> Accessories -> Terminal and do:```
sudo lshw -[SIZE=4]C[/SIZE] network | grep -i ethernet
```Post the result here.

It flashes this:
```

PCI (sysfg)
SCSI
frame buffer

```
with no final output.

The DSL live CD picks up on it. Would you like the output while running that?

---

### Post by chili555 on 2009-05-11
> Would you like the output while running that?Please.

---

