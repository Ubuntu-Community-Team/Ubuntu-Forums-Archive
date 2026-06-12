---
title: "Help!!!!"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by elkoselim on 2010-02-18
I have an HP6735s laptop (bcm4322 wireless adapter) with ubuntu 9.10 (2.6.32-02063208-generic). First of all, I tried to use aircrack-ng. FAILED! :sad: Now, could anyone send me step by step solution for installing driver and how to make bcm4322 work with aircrack-ng.

---

### Post by chili555 on 2010-02-18
Please see: [http://www.aircrack-ng.org/doku.php?id=b43](http://www.aircrack-ng.org/doku.php?id=b43)

Also see: [http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation](http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation)

Especially see: > Ubuntu/Debian

In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you:```
sudo apt-get install b43-fwcutter
```You will be asked to automatically fetch and install the firmware into the right location.You will need to be hooked up to the internet by wired ethernet to proceed. Also, open System -> Admin -> Software Sources and be sure that universe, restricted and multiverse are enabled. Select a proper download location if you are not in the USA.

---

### Post by elkoselim on 2010-02-18
> **chili555 said:**
> Please see: [http://www.aircrack-ng.org/doku.php?id=b43](http://www.aircrack-ng.org/doku.php?id=b43)

Also see: [http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation](http://wireless.kernel.org/en/users/Drivers/b43#device_firmware_installation)

Especially see: You will need to be hooked up to the internet by wired ethernet to proceed. Also, open System -> Admin -> Software Sources and be sure that universe, restricted and multiverse are enabled. Select a proper download location if you are not in the USA.

I installed driver, but packet injection doesn't work. 
code:
airmon-ng eth2


ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth2 <#>'
Sysfs injection support was not found either.


I was reading about it.I need a patch, but I have a problem to apply it. So, if you could.... :) ANYONE! NEED HELP HERE!

---

### Post by chili555 on 2010-02-18
Please try:```
sudo airmon-ng
```Is your interface really eth2?

---

### Post by elkoselim on 2010-02-18
> **chili555 said:**
> Please try:```
sudo airmon-ng
```Is your interface really eth2?


sudo airmon-ng


Interface    Chipset        Driver

eth2        Unknown         wl


What could be a problem?Is there any solution?

---

### Post by DrMelon on 2010-02-18
Just a note to you in future - when posting a help topic, please make the title more descriptive. "Help!!!!" doesn't really show us what you're talking about, whereas something like "Aircrack-ng not working with 9.10" would be more descriptive, and more likely to attract attention from people who know more about aircrack-ng.

---

### Post by elkoselim on 2010-02-18
Sorry :) I'll remember that

---

### Post by chili555 on 2010-02-18
What happens when you do:```
sudo airmon-ng start eth2
```

---

### Post by H4F on 2010-02-18
And there is airdriver-ng which might help you to load different drivers for your wireless card.

---

### Post by elkoselim on 2010-02-18
> **chili555 said:**
> What happens when you do:```
sudo airmon-ng start eth2
```

airmon-ng start eth2


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
919    avahi-daemon
920    avahi-daemon
996    NetworkManager
1095    wpa_supplicant
3599    dhclient


Interface    Chipset        Driver

eth2        Unknown         wl (monitor mode enabled)

---

### Post by chili555 on 2010-02-18
> monitor mode enabledLooks like you are off and running. Have fun.

---

### Post by elkoselim on 2010-02-18
Thanks, but still I have packet injection problem. Any idea? I have read almost all posts, but without success. I know just *I need a patch*, but when I download patch and try to apply it nothing happens. Very, very difficult problem for me.

---

### Post by chili555 on 2010-02-18
> Any idea?None whatever, but I suggest you post a new thread referring to patching Broadcom driver for packet injection, after you search this forum thoroughly. I am fairly sure this has been asked several times before.

---

### Post by H4F on 2010-02-18
> **elkoselim said:**
> Thanks, but still I have packet injection problem. Any idea? I have read almost all posts, but without success. I know just *I need a patch*, but when I download patch and try to apply it nothing happens. Very, very difficult problem for me.

There are many problems with wireless craking regarding to interference and distance problems.this might be one think which want allow you to inject packets.

What kind of wireless security are you trying to broke in ? wep wpa ...?

---

### Post by elkoselim on 2010-02-18
On the first place WEP, but if is possible and WPA :) . I spent 4 days by the computer, looking for solution :( I found several, but nothing. 
one of them:
patch -p1 <patch file name>

when I input this, nothing happens.

---

