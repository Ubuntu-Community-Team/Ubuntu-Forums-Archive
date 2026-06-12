---
title: "Disable WiMAX init at Bootup?"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by Elmer Fudd on 2011-08-28
Any easy way to stop the initialization of WiMax during bootup? I don't use Wimax and it noticeably slows down the boot up process.

Sony F-Series laptop running 10.10. 

02:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5f)

---

### Post by chili555 on 2011-08-29
I'd suggest you look in the computer's BIOS first to see if there is any option to disable wimax. You might also see if there is any module loaded to enable wimax:```
lsmod | grep wimax
```If so, it may be helpful to blacklist it:```
sudo su
echo "blacklist <some_module>" >> /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by Elmer Fudd on 2011-08-31
Thank you for the suggestions. 
I have already tried to disable WiMax in the BIOS (unavailable) and did find and blacklist the 'wimax' module in blacklist.conf. 
It still initializes and shows "WiMax ready" during bootup.
Not a big problem. Just annoying having something I don't use delaying the bootup.

---

### Post by chili555 on 2011-09-01
Is there a wimax listing in here?```
rfkill list all
```If so, does it help to do:```
sudo rfkill block wimax
```Is that a declaration you could add without the 'sudo' to /etc/rc.local?

---

### Post by Elmer Fudd on 2011-09-02
"rfkill list all" returns:

```
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-wimax: WiMAX
	Soft blocked: yes
	Hard blocked: no
2: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: i2400m-usb:1-1.5:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
5: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Ran "rfkill block wimax" both in root terminal and in "/etc/rc.local" at boot. No change.

---

### Post by lfruiz on 2011-10-03
nd im having this "bug" as well...  got the asus g73 and this is the only thing that bugs me..:(

---

