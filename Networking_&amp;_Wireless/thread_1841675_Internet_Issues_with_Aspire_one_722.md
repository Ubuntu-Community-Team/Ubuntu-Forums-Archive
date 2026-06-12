---
title: "Internet Issues with Aspire one 722"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by Aldariun on 2011-09-09
I have a new Aspire one 722 netbook. Loaded Ubuntu 10.04 onto it and all network detection stopped.

Turns out I have a Broadcom 4727 wireless chipset and and Atheros wired chipset. Both unsupported by Ubuntu drivers I need to know how to upload the Broadcom drivers via usb drive so I can get online to fix other issues. I am not very familiar with terminal comands so kind of need them spelled out.

---

### Post by tehchibipanda on 2011-09-09
Can you even get online with an ethernet cable hardwired directly to the router/modem?

---

### Post by praseodym on 2011-09-10
Hi,

for this wireless device you need the Broadcom-STA-driver. You can install it from installation CD/DVD. Add the medium to your software sources and install the packages **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source** from CD. After that:

```
sudo depmod -a
```
Now you should be able to activate the driver in System->Settings->Hardware drivers.

For wired:

please show the outputs of

```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by Aldariun on 2011-09-10
No have no ethernet because of the Atheros chipset also have no way to use CD I installed by usb because its a netbook and has no cd drive
Am having to use school computers to use the net and I don't live on Campus so sorry for late replies
Atheros chipset is AR8152 if that helps. Alternatly if you know and Linux installs availabe for usb, compatible with either chipset I could try a different OS

---

### Post by praseodym on 2011-09-11
32 bit:

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb)

64 bit:

[http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_amd64.deb)

For both additionally:

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb)

Save them on your Desktop and install via:

```
sudo dpkg -i ~/Desktop/*.deb
sudo depmod -a
```
Then activate the driver via System->Settings->Hardware drivers

You may reboot, too.

---

### Post by Aldariun on 2011-09-11
That worked with the 32 bit files after reboot! Thank you so much I was beginning to consider going back to Windows I was getting so frustrated. That would have sucked because I really do love Ubuntu.

---

