---
title: "RT2501/RT2573 problem installing driver"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by shirux on 2011-08-23
MY card: Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

When I do sudo make install then login I get this error:
```
make -C /home/brandt/Desktop/2009_1221_RT3090_Linux_STA_v2.2.1.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/brandt/Desktop/2009_1221_RT3090_Linux_STA_v2.2.1.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/brandt/Desktop/2009_1221_RT3090_Linux_STA_v2.2.1.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3090sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3090sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/brandt/Desktop/2009_1221_RT3090_Linux_STA_v2.2.1.0/os/linux'
make: *** [install] Error 2

```

---

### Post by chili555 on 2011-08-23
Your device is claimed by two different drivers that conflict. That's probably why you decided to try another driver. Let's check:```
lsmod | grep -e rt7 -e rt2
```If both rt73usb and rt2500usb are loaded, let's kick out rt2500usb, reboot and see if it's working now.```
sudo su
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

Incidentally, this is for a PCI device, not your USB:> 2009_1221_[COLOR="Red"]RT3090[/COLOR]_Linux_STA_v2.2.1.0

---

