---
title: "WiFi not working in ubuntu 11.10."
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by ankur.trapasiya on 2011-10-25
Hello,
I am using lenovo B560 and i have installed ubuntu 11.10. But wifi is not working in it. Is there any solution for it ? I tried the solution for ubuntu 11.04 but it is not working in 11.10.

here is the link for that solution
[http://ubuntuforums.org/showthread.php?t=1791389]("http://ubuntuforums.org/showthread.php?t=1791389")

---

### Post by chili555 on 2011-10-25
Please let us see:```
lspci -nn | grep 0280
rfkill list all
cat /etc/modprobe.d/blacklist.conf | tail -n10
```Thanks.

---

### Post by ankur.trapasiya on 2011-10-25
output of 1st command

> lspci -nn | grep 0280
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

2nd

> rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

3rd command


> cat /etc/modprobe.d/blacklist.conf | tail -n10

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


---

### Post by chili555 on 2011-10-25
Please try this:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report. If it's not working, let us see:```
rfkill list all
```Thanks.

---

