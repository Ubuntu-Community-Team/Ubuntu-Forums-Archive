---
title: "No more wireless after quantal update: 'Module wl not found'"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by Keunes on 2012-10-22
Hi all,

On my new Dell Vostro 3460 I had Ubuntu 12.04 installed with wireless up & running (thanks to [_some tweaking_]("http://askubuntu.com/a/175115/22147")). With the update to quantal, however, it stopped working.
Trying to follow [_these instructions on askubuntu_]("http://askubuntu.com/a/203082/22147").com, I got to the point where my comments became a bit off-topic: The suggestion was that the wl module should be loaded automatically, but apparently the module is not installed on my system, as indicated by the outcome of [FONT=Tahoma][COLOR=DimGray]lsmod | grep ^wl[/COLOR][/FONT]: [FONT=Tahoma][COLOR=DimGray]FATAL: Module wl not found.[/COLOR][/FONT]

In the attachment the outcome of ```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

How do install the wl module?

Cheers

---

### Post by chili555 on 2012-10-22
The current version of *wl* doesn't support your device:> Broadcom Corporation BCM43142 802.11b/g/n [[COLOR="Red"]14e4:4365[/COLOR]] Please see: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809)> Updated package that compiles on 3.2.x - 3.4.x here:...and:> I tested the updated deb I posted in #5 on linux 3.5.0-4.dmz.1-liquorix-amd64, and it works for meI suggest you download the .deb file and try it:```
sudo dpkg -i wireless*.deb
sudo modprobe wl
```We look forward to your report.

---

### Post by Keunes on 2012-10-22
Dear chili555,
Thanks for your reply. I know that my device is not supported, and that's why I turned to askubuntu.com. There Jasmine gives basically the same answer as you (see [http://askubuntu.com/a/203082/22147](http://askubuntu.com/a/203082/22147), you refer to the same package indirectly through Lauchpad).
Now, I might have not been clear on this, but I was the one who commented on her answer, stating that installing her debian package doesn't work for me. As you can reed there, she asked me to the following:
```
lsmod | grep ^wl
```Then, if that didn't return anything (and it didn't), I should do the following to start the wl module:
```
sudo modprobe wl
```That, however, gives the following output (thus despite installing the package):
```
FATAL: Module wl not found.
```Here we arrive at the point where I turnt to the forums, because starting such help session on askubuntu didn't seem appropriate.

N.B.: I followed the above procedure (including downloading & installing Jasmine's .deb) again to make sure it indeed doesn't work for me. See attachment for terminal in- & output

---

### Post by chili555 on 2012-10-22
> This package appears to be a binaries-only package
 you will not be able to build against kernel 3.5.0-17-generic
 since the package source was not providedCan you confirm you have installed linux-headers-generic, build-essential and dkms?

This is a weird one. I learn something astounding every day!

---

### Post by Keunes on 2012-10-23
Didn't even see that one.  Dunno if it has anything to do with it, but I deselected all source code sources in the Software Sources.
```
dpkg -s build-essential dkms linux-headers-generic
```gives the following for each package (see attachment for full output):
```
install ok installed
```thanks!

---

### Post by chili555 on 2012-10-23
Please try this instead: [http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb](http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)

Generally, I try all these packages before I suggest them to posters, however, mine is not a 64-bit system.

---

### Post by Keunes on 2012-10-23
Hi Chili555,

Thanks for your reply. The package you linked to was exactly the one I had installed before.
After removing the package, adding Jasmine's repository & installing the newest package my wireless worked again :)
Please read output of the installation procedure in the attachment (although I don't think there's anything special to see there).

Thanks for your help

**Anyone with the same problem as me** (having a Dell Vostro 3460 or any other 64-bit system with a Broadcom BCM43142 wireless card & ubuntu 12.10+ installed):
- add Jasmine's repository as presented on [http://jas.gemnetworks.com](http://jas.gemnetworks.com)
- click through to the broadcom page, and follow the installation instructions

---

### Post by chili555 on 2012-10-23
> Anyone with the same problem as me (having a Dell Vostro 3460 or any other device with a Broadcom BCM43142 wireless card & ubuntu 12.10+ installed):...*and a 64-bit system.* Note the package is for _x86_64_ only.

I'm very glad it's working. Hopefully, he'll write a 32-bit .deb for the rest of the searchers.

---

### Post by Keunes on 2012-10-23
> **chili555 said:**
> ...*and a 64-bit system.* Note the package is for _x86_64_ only
added the 64-bit part to the description sentence in my other post. Tnx for your alertness

---

### Post by jawz101 on 2012-10-24
After running 12.10 updates on my laptop with Broadcom 4312 wireless my wireless broke with the new 3.5.0-18 kernel update.
To fix I went into Software Sources & disabled the STA driver then I'm assuming at least the last 3 commands in this fixed it:
```
sudo modprobe -r b43 ssb wl
sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install build-essential dkms linux-headers-generic
sudo apt-get install bcmwl-kernel-source
```

I didn't have to reboot or anything.  It just immediately found my wireless adapter and connected wirelessly again.

---

### Post by Arpy222 on 2013-03-30
Thank you jawz101, it solved my problem too! :)

---

