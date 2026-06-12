---
title: "Wireless receiver/card not working"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by mtngirl on 2009-05-20
I have a computer with a wireless USB receiver. I think there is also a card in the computer. Ubuntu is not recognizing any wireless.

The receiver says Logitech and has the following numbers on the back.

P/N: 810-000595
PID: LZ827AS
M/N: C-BT44

It also has some more writing that I would need a magnifying glass to read.

Any thoughts on how or where to get started trying to make this work?

Thanks!

---

### Post by rudy.b on 2009-05-20
I guess the wireless Logitech USB receiver is for a keyboard and/or mouse.  What you can try is open your system log viewer, scroll to the bottom of the log and unplug and re-plug in your USB device and see what messages appear in the log.  You can find your system log here:

System > Administration > Log File Viewer > messages

---

### Post by oldsoundguy on 2009-05-20
you have to have a wireless mouse and keyboard to go along with the receiver.  And you connect them by using the "connect" buttons on both the receiver and then the mouse and keyboard.
NO OS will see the receiver alone.

I have them on a couple of my work stations and they are hooked up to a KVM so they can run more than one computer with the same keyboard/mouse/display.

---

### Post by mtngirl on 2009-05-21
Argh! My bad - that was the receiver for the keyboard which is working fine.

The wireless one is a Dell with part number CN-OWX492-00842-899-1406, REV A00. No other words or logos than the Dell one.

Ideas on how to get it working? (It's physically working, the light is on and it works if I boot the system into Vista but not with Ubuntu.)

I'm sure this one is the wireless receiver/antena! :)

---

### Post by superprash2003 on 2009-05-21
in your terminal type lshw -C network and post output

---

### Post by mtngirl on 2009-05-21
*-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:6e:34:40
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=24.9.101.58 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 4a:e7:46:6d:23:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by rudy.b on 2009-05-24
Hi mtngirl,

Your wireless controller is BCM4328 (Broadcom).  I found another thread which relates to the same interface which seems to provide a fix that has worked for several people, you may want to give it a look:  [Jaunty Broadcom (BCM4328) Wireless Problem]("http://ubuntuforums.org/showthread.php?t=1134631").

---

