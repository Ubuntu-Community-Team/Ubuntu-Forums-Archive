---
title: "Nvidia Driver Woes w/13.04"
date: 2013-09-30
forum: Multimedia Software
---

### Post by Jon_Machen on 2013-09-30
Thanks to boot loader hassles, it's been a longer struggle getting Ubuntu 13.04 up and running than I anticipated.  However, I finally have all of that sorted out and am now fighting a new battle to get working Nvidia drivers installed.

The machine is a new Lenovo y510p.

Here's what I've done and what I'm experiencing:

- Shrunk Win 8 partition by 100 gigs
- Installed Ubuntu from USB stick
- ran sudo apt-get install nvidia-current
- rebooted to an apparent hang
- pressed the power button briefly and the OS shut itself down ("warm" shutdown)
- rebooted to grub, edited commands and replaced "quiet splash" with "--verbose text"
- I went through the process described here: [http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

I can see that the driver is present "with sudo /sbin/lsmod | grep nvidia" ? But it doesn't show up when I run "sudo modprobe nvidia_current" and nothing I do (apart from removing nvidia and going back to nouveau) seems to render me a desktop.

Can anyone lend a hand?

What information can I provide to make it easier for you to assist me?

Thanks in advance,

Jon

---

### Post by Jon_Machen on 2013-09-30
For what it's worth.  I'm willing to scrap it and start again as I haven't gotten far enough in the process to lose anything but my patience ;-)

---

### Post by Yellow Pasque on 2013-10-01
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Jon_Machen on 2013-10-01
Weird.  Thanks.  I'll check this out.

---

### Post by Bucky Ball on 2013-10-01
*Thread moved to **Multimedia & Video**.*

---

### Post by Jon_Machen on 2013-10-01
Whoops.  Sorry about the bad topic placement.

---

