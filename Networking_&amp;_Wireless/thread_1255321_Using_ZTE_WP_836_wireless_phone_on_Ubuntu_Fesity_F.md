---
title: "Using ZTE WP 836 wireless phone on Ubuntu Fesity Fawn"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by muntasir_120 on 2009-09-01
I am currently on Ubuntu Feisty Fawn and trying to get my new ZTE WP 836 wireless phone to work on it. It plugs into a USB port and uses the Silicon Labs USB to UART bridge driver to apparently work like a its connected to a serial port. On windows this shows up as a modem connected to COM9.

Whenever I connect the phone while on Ubuntu, the modem is never detected. Running "lsusb" shows a device from "Cygnal Integrated Products" connected to a USB port, but it cannot be dialled from wvdial. Searching the web has largely indicated that this driver should be already available on most modern Linux distros and I'm pretty sure it is present in Ubuntu.

Using Windows whenever I need to access the internet is really annoying. Can someone please help me?

PS: I have also tried using Ubuntu 8.10LTS and 9.04 LiveCDs, but neither detects the phone when plugged in.

Solved: A a lot more searching got me to a solution. Apparently Silicon labs drivers are installed but not exactly "turned on" in ubuntu.

---

