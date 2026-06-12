---
title: "Network manager and other issues after installing Lazarus"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by skywatcher on 2013-02-12
Hi

I'm hoping someone can help me with a serious problem. I have a dual-boot Mint 13 and Ubuntu Studio 12.04 running on a 64-bit machine. No problems for several months. This morning I downloaded Free Pascal 2.6 and Lazarus 1.0.6 on Ubuntu Studio and tried to install it. There was some dependency error (don't remember now what it was), which I was in the process of trying to fix when I lost my 3G wireless connection. I tried to get it going again, but all I got was a message saying "NetworkManager is not running...". So, I tried to reboot, but I couldn't -- I got this message:

> Unable to perform shutdown
shutdown command failed

I had no option but to switch off the PC.

Next, I started it up again, this time in Mint. I used the file manager to get into the Studio partition and successfully installed Free Pascal and Lazarus from there. I started Lazarus and everything seemed OK. Then, suddenly, I lost my 3G connection on Mint as well! 

I tried to get the network manager running on both distros from the command line with

```
sudo start network-manager
```

but I received this

```
start: Job is already running: network-manager
```

I also noticed that the respective partitions and my external USB devices, e.g. portable hard drive and USB flash drive (and I suspect the USB 3G modem), no longer mounted automatically on either distro.

The only common thing between Mint and Studio is the installation of FPC and Lazarus.

By the way, Mint shuts down OK, unlike Studio

Any ideas, anyone?

---

