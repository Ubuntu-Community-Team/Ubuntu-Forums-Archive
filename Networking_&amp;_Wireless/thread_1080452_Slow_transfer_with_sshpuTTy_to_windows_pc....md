---
title: "Slow transfer with ssh/puTTy to windows pc..."
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by roger4306 on 2009-02-25
Hi, I have at my work set up an ubuntu 64 pc for solving analysis.

The analysis is remotely solved from my windows workstation via a windows que pc to the linux machine. The transfer is done with openSSH and putty. The file transfer from windows to Linux is ok, with a transfer rate of approx 7-8 MB/s which is ok on a 100Mbit network.

But, when the results file are transferred back on the same network, on the same PC's the rate is only approx 1 MB/s, which is really bad.

I have tested manually file copy on both the windows and the Linux to other sites, and they are OK both up and down.

If anyone should have any idea what to do, please let me know. This is really a pain.

Regards,
Roger

---

### Post by puppywhacker on 2009-02-25
either the MTU causing fragmentation, or your PC is slow to encrypt the link, lower your encryption method to something faster

---

