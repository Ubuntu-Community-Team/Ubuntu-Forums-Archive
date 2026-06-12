---
title: "Monitor doesn't turn on Linux"
date: 2019-10-07
forum: Multimedia Software
---

### Post by greenredbean on 2019-10-07
When I run Windows, I am able to turn on my monitor straight away by plugging it in. However, on Linux (Ubuntu 18.04) the monitor doesn't seem to turn on. The monitor I am using is the AOC e1659fwu. It is connected by a USB 3.0 cable. Also, I don't know if this is normal but it seems that my screen display settings only have 4 different options which can be seen in this image ([https://imgur.com/gallery/lwNpxZn](https://imgur.com/gallery/lwNpxZn))
I know I haven't given much information but hopefully someone else has encountered this problem and could help me. Thanks!

---

### Post by Autodave on 2019-10-07
Would you please give us some info on your system?

---

### Post by jimmyrus on 2019-10-14
> **greenredbean said:**
> When I run Windows, I am able to turn on my monitor straight away by plugging it in. However, on Linux (Ubuntu 18.04) the monitor doesn't seem to turn on. The monitor I am using is the AOC e1659fwu. It is connected by a USB 3.0 cable. Also, I don't know if this is normal but it seems that my screen display settings only have 4 different options which can be seen in this image ([https://imgur.com/gallery/lwNpxZn](https://imgur.com/gallery/lwNpxZn))
I know I haven't given much information but hopefully someone else has encountered this problem and could help me. Thanks!
That uses displaylink to power up and work. Drivers:
[https://www.displaylink.com/downloads/ubuntu](https://www.displaylink.com/downloads/ubuntu)

Sure you've got that going to a usb3 port? If drivers dont get you going get to a terminal, and run "sudo dmesg -c", then plug the monitor in and run "sudo dmesg" and post the output.

---

