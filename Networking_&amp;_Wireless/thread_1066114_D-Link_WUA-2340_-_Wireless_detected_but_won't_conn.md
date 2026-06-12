---
title: "D-Link WUA-2340 - Wireless detected but won't connect"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by dodd_alex on 2009-02-10
I am brand new to Linux, coming from Windows and I am getting discouraged and having problems with my wireless internet connection.

I am using an already working D-Link DBR-1310 router which has flawless connection to my roommates laptop running Windows and to my PC running Ubuntu 10 when connected by a wire. I am using a D-Link WUA-2340 USB 2.0 adapter. Using ndiswrapper have installed the driver and had the usb wireless dongle completely working for a few days. I did a system upgrade to Ubuntu and when I restarted my computer the dongle was no longer flashing. It is detecting wireless networks but it is unable to connect for some reason. I have completed every tutorial I can find, and everything appears to be fully setup, but I still can't connect.

Please help.

---

### Post by knattlhuber on 2009-02-16
Maybe the system upgrade was a kernel upgrade and now for some reason ndiswrapper is not loaded anymore or conflicts with a new/updated module.
Check if ndiswrapper is loaded:
```
lsmod | grep ndiswrapper
```
ndiswrapper should show up

Make sure that the RT73 modules are blacklisted and not loaded:
```
lsmod | grep rt73
cat /etc/modprobe.d/blacklist | grep rt73

```
Should return blank lines

Is the wpa_supplicant file installed?
```
sudo apt-get install wpasupplicant
```

Is your adapter listed in /etc/network/interfaces?
```
cat /etc/network/interfaces
```
Should contain something like
```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>
```

---

### Post by dodd_alex on 2009-02-24
Thanks for this. I eventually had to give up on it though. It was far too frustrating and for the short period that it was working (as I ended up reading on many other forums as well) it's just an unreliable product. I ended up ordering an Edimax instead and it worked out of the box.

Lesson learned - research before buying hardware. I haven't gone back to Windows yet! Thanks for your support.

---

### Post by aaronhahn777 on 2009-03-18
I have the same problem... only I've spent over 40 hrs trouble shooting.  I tried the above and still just a pain in the butt.  

Which Edimax wireless unit did you get?

---

### Post by knattlhuber on 2009-03-18
Oddly, when I dug out my WUA-2340 recently to use it on an old computer, it wouldn't work either despite all the good advice that I posted above ;)

If you are looking for a USB WiFi adapter, the D-Link WUA-1340 works out of the box under Linux (using the rt73usb module).

---

### Post by aaronhahn777 on 2009-03-18
just bought a "retail plus+ IEE 802.11B/G V1.0" and it worked flawlessly out of the box...  

after wasting 40 hours with d-link and ndiswrapper... and almost going back to xp...  dang that's nice (also cheapest one in the store... $24)


Simply:
>installed 8.10
>inserted usb stick
>enjoyed surfing

---

### Post by cpickeri on 2011-04-10
use the driver for the dlink dwl-g132 and it works fine with the wua-2340 usb stick
[ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlG132_drivers_130.zip](ftp://ftp.dlink.com/Wireless/dwlg132/Driver/dwlG132_drivers_130.zip)

cheers.

---

