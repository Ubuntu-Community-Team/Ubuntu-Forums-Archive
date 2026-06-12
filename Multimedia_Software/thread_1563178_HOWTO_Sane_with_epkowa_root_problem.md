---
title: "HOWTO: Sane with epkowa root problem"
date: 2010-08-28
forum: Multimedia Software
---

### Post by mogliii on 2010-08-28
I actually wanted to answer this post
**[http://ubuntuforums.org/showthread.php?t=166944]("http://ubuntuforums.org/showthread.php?t=166944")**
but it is Read-only.

[SIZE="4"]The problem:[/SIZE]
In Lucid (10.04) Epson printer running with **[epkowa driver]("http://avasys.jp/eng/linux_driver/")** will only be available by using sudo.

[SIZE="4"]Why does this happen:[/SIZE]
First all usb devices are only root. Then there are udev rules that allow to grant permission to non-root. However libsane does not officially support epkowa printer. Hence there is no vendor/model rule in 
```
/lib/udev/rules.d/40-libsane.rules
```
See also the explanation in /usr/share/doc/libsane/README.linux.gz

[SIZE="4"]Solution:[/SIZE]
Go to a terminal an run
```
lsusb
```
with the scanner connected and turned on. You will get something like
```
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c518 Logitech, Inc. MX610 Laser Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]**Bus 001 Device 002: ID 04b8:0131 Seiko Epson Corp. **[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
Now open /lib/udev/rules.d/40-libsane.rules as root (make backup copy first) and add the following lines:
```
# Epkowa Epson V30
ATTRS{idVendor}=="[COLOR="Red"]04b8[/COLOR]", ATTRS{idProduct}=="[COLOR="Lime"]0131[/COLOR]", ENV{libsane_matched}="yes"
```
where the idVendor is the first number, before the colon, and idProduct the second number.
Save the file, disconnect and reconnect the scanner and you should be able to scan without additional work.

And write to [FONT="Courier New"][email]sane-devel@lists.alioth.debian.org[/email][/FONT] and tell them about the vendor and product id in case it works.

---

