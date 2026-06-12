---
title: "Can't enable wireless BCM4306 in Jaunty"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by oldmanjank on 2009-05-26
iwconfig gives me "no wireless extensions" for lo, eth0, wcmaster0 and pan0.  For wlan0 it gives:
> 
IEEE 802.11bg ESSID:""
Mode:Managed  Frequency 2.412 GHz Access Point: Not-Associated
etc..


b43 shows up when i lsmod

dmesg | grep roadcom gives:
> 
b43-phy0: Broadcom 4306 WLAN found
Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
 

iwlist scan gives:
> 
wlan0 Failed to read scan data : Resource temporarily unavailable


And when I click on the NetworkManager icon on the top bar, both "Wired Network" and "Wireless Networks" are greyed-out.
System Administration > Hardware Drivers  comes up blank (No proprietary drivers are in use on this system)

/etc/modules contains
```

lp
wl

```

and /etc/network/interfaces contains:
```
auto lo
iface lo inet loopback
iface wlan0 inet dhcp

```

Can anyone help me get my wireless working?

---

### Post by kerry_s on 2009-05-26
did you install the firmware? **sudo apt-get install b43-fwcutter**

---

### Post by oldmanjank on 2009-05-26
Thanks for writing back!

So... I copied the b43-fwcutter I had lying around on an old hard drive on the same machine as well as an old wl_apsta.o I had from 7.04.  Doing a **sudo bcm43xx-fwcutter -w /lib/firmware/ Desktop/wl_apsta.o** seemed to work.  Doing so did not seem to change the status of my wireless predicament (i did it before my first post).  But technically, I did not do a proper **sudo apt-get install b43-fwcutter**, does that matter?  BTW, i *could* go carry the 9.04 machine all the way downstairs and connect it to an ethernet port if I need to properly start apt-getting stuff, but of course only if I have to.

---

### Post by kerry_s on 2009-05-26
> **oldmanjank said:**
> Thanks for writing back!

So... I copied the b43-fwcutter I had lying around on an old hard drive on the same machine as well as an old wl_apsta.o I had from 7.04.  Doing a **sudo bcm43xx-fwcutter -w /lib/firmware/ Desktop/wl_apsta.o** seemed to work.  Doing so did not seem to change the status of my wireless predicament (i did it before my first post).  But technically, I did not do a proper **sudo apt-get install b43-fwcutter**, does that matter?  BTW, i *could* go carry the 9.04 machine all the way downstairs and connect it to an ethernet port if I need to properly start apt-getting stuff, but of course only if I have to.

hmm, not sure.
what the " sudo apt-get install b43-fwcutter " does now is downloads the latest drivers and puts them in the right place.

have you done tried the commands?
bring up the interface> **sudo ifconfig wlan0 up**
give it a name to attach to> **sudo iwconfig wlan0 essid "any"**
grab a dhcp lease> **sudo dhclient wlan0**

---

### Post by oldmanjank on 2009-05-26
sudo ifconfig wlan0 up gives
> 
SIOCSIFFLAGS:  No such file or directory


sudo iwconfig wlan0 essid "ANY" returns nothing for any value of ANY

sudo dhclient wlan0 gives
> 
wmaster0:  unknown hardware address type 801
SIOCSIFFLAGS:  No such file or directory
SIOCSIFFLAGS:  No such file or directory
wmaster0:  unknown hardware address type 801
Listening on  LPF/wlan0/00:0c:41:60:06:37
Sending on    LPF/wlan0/00:0c:41:60:06:37
Sending on    Socket/fallback
receive_packet  failed on wlan0: Network is down
DHPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down


I tried a known unsecured network for the essid but nothing changed.

---

### Post by kerry_s on 2009-05-26
that don't look right. :(

maybe try ndiswrapper and the windows driver:
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

---

### Post by oldmanjank on 2009-05-26
Hmm...  Well thanks for the tips.  I'll see if hauling this thing down to the ethernet port and doing a proper b43-fwcutter install helps.

---

### Post by t0mppa on 2009-05-27
Bcm43xx driver is deprecated, you should update to b43 or b43legacy. See [here]("http://linuxwireless.org/en/users/Drivers/b43"), you can also do the wgets listed there on another computer and then just use an usb stick to carry the FWcutter files to your Ubuntu computer, rather than carrying your Ubuntu computer to the wired access.

Also, take the wl out of /etc/modules, since that's the module for the Broadcom STA driver and having two drivers loaded at the same time can cause conflicts.

---

### Post by oldmanjank on 2009-05-27
Thanks for the info, t0mppa.  I'll try removing wl and using the usb stick when I get home tonight.

---

