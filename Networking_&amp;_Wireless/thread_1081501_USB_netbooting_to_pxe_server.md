---
title: "USB netbooting to pxe server"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by Serpreme on 2009-02-26
Howdy all,
I was wondering if i could setup a USB drive to specifically PXE boot off a server without DHCP being involved.
I have a PXE server setup, but i can not run my own dhcp service. So i was thinking i could try to emulate the PXE process, but feed it my IP and such, and still gain the PXE menu system.
Thanks! If you need any more information, let me know.

---

### Post by nixscripter on 2009-02-27
I'm not quite sure what you're asking. If you want to do this:

1. Take a USB drive.
2. Stick it into a machine.
3. Machine boots from the USB.
4. USB flash drive downloads a file from named server and boots it.

You still need a mechanism for obtaining an IP so that packet routing works. DHCP is the way it's done in the PXE loader, because it's simple. If you don't want to run a DHCP server (it's actually not too bad with the **dnsmasq** package), then you'll have to do something like this:

1. Put GRUB and a tiny linux kernel on the USB.
2. Kernel boots off of USB.
3. Kernel sets up network interfaces, including static IP.
4. Kernel downloads boot file over TFTP (the way PXE does).
5. Kernel runs kexec() to start the booted file.

It's possible, but very complicated. I'd suggest you just use a DHCP/TFTP boot server instead -- or just have the file to boot on the USB in the first place.

---

