---
title: "Divio Chicony TwinkleCam 06a5:d800 (Yeap, yet another thread)"
date: 2012-07-10
forum: Multimedia Software
---

### Post by Jugurtha on 2012-07-10
Hello everyone,

I have looked on the internet for quite long, and either threads get no response or they don't fit the problem I'm facing.

lsusb gives this output.

```
jugurtha@Jugurtha-Box:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 014: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 015: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]
Bus 005 Device 013: ID 06a5:d800 Divio Chicony TwinkleCam

```While some other people didn't have "/dev/video0", I on the other hand have that.

When I unplug the webcam,

```
jugurtha@Jugurtha-Box:~$ dir /dev/video0
dir: cannot access /dev/video0: No such file or directory

```When the cam is plugged

```
jugurtha@Jugurtha-Box:~$ dir /dev/video0
/dev/video0

```I unplug the cam and run

```
jugurtha@Jugurtha-Box:~$ sudo udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

```Once I plug the cam, I get:

```
KERNEL[35082.303348] add      /devices/pci0000:00/0000:00:1d.3/usb5/5-2 (usb)
KERNEL[35082.306192] add      /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0 (usb)
KERNEL[35082.317337] add      /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/video4linux/video0 (video4linux)
UDEV  [35082.471504] add      /devices/pci0000:00/0000:00:1d.3/usb5/5-2 (usb)
UDEV  [35082.486379] add      /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0 (usb)
UDEV  [35082.513933] add      /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/video4linux/video0 (video4linux)

```So, does anyone have an idea how to get this thing working. It's an old dog that I like. If possible, without having to use NDISwrapper.

Thanks for your time.

--
~Jugurtha Hadjar,

---

