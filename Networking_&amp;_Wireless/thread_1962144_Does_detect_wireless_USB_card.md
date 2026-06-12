---
title: "Does detect wireless USB card?"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by Cheetah05 on 2012-04-20
```

lsusb | grep VIA

```

returns "VIA VNT-6656" which is my wireless card/usb dongle but it is not detected.

Could it be because I am running the 12.04 beta?

Wireless is my only form of connection (I do have another internet enabled ultra book though). Is it possible to get wireless to work?

---

### Post by chili555 on 2012-04-20
There is more data than that in lsusb; we'd love to see the usb.id.Is it 160a:3184? If so, it is driven by *vt6656_stage*. It requires firmware *vntwusb.fw* which may not be installed. Please check for messages on that subject:```
dmesg | grep vt6
```If you are missing firmware, temporarily hook up the ethernet and do:```
sudo apt-get install linux-firmware
```Reboot and enjoy your wireless.

If that is *NOT* the usb.id, post it and we'll proceed.

---

### Post by Cheetah05 on 2012-04-20
> **chili555 said:**
> There is more data than that in lsusb; we'd love to see the usb.id.Is it 160a:3184? If so, it is driven by *vt6656_stage*. It requires firmware *vntwusb.fw* which may not be installed. 

It is that one yes.

> 
Please check for messages on that subject:```
dmesg | grep vt6
```


Returns nothing

> 
If you are missing firmware, temporarily hook up the ethernet and do:```
sudo apt-get install linux-firmware
```Reboot and enjoy your wireless.

If that is *NOT* the usb.id, post it and we'll proceed.

I am unable to hook up any ethernet, however I can download something and transfer via USB to ubuntu if need be.

---

### Post by chili555 on 2012-04-20
Before we download firmware, let's just confirm. Again, with the device plugged in, try:```
sudo modprobe vt6656_stage
dmesg | grep vt6
```Either your device springs to life because it simply needs the driver loaded, or it did not because it lacks firmware; *dmesg* will tell us which.

I'll get a firmware file ready, just in case.

---

### Post by Cheetah05 on 2012-04-20
> **chili555 said:**
> Before we download firmware, let's just confirm. Again, with the device plugged in, try:```
sudo modprobe vt6656_stage
dmesg | grep vt6
```Either your device springs to life because it simply needs the driver loaded, or it did not because it lacks firmware; *dmesg* will tell us which.

I'll get a firmware file ready, just in case.

I got impatient (not with you - with the computer) and installed 11.10 32bit.

It detected the card automatically but I can't connect. It just prompts me with a dialog box asking for the key (which is correct)

**EDIT:**

Just tried it with the iPhone wifi hotspot also and it didn't work...my iPhone briefly reported a connection, but it didn't sustain.

dmesg returns that the module is from the staging directory.

---

### Post by chili555 on 2012-04-20
Let's see:```
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```I will be leaving for a while in ten minutes.

---

### Post by Cheetah05 on 2012-04-20
> **chili555 said:**
> Let's see:```
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```I will be leaving for a while in ten minutes.

Apparently:

> 
Interface doesn't support scanning.
no authentication information.


---

### Post by Cheetah05 on 2012-04-20
Strange, its registered itself as eth7 when I run ifconfig

(I think)

---

### Post by chili555 on 2012-04-20
Please run, but no need to post:```
iwconfig
```Is your wireless interface not wlan0? Please post *scan* and *auth* for whatever it is. wlan1? eth1??

Gotta run. See you later.

---

### Post by Cheetah05 on 2012-04-20
```

iwlist eth7 auth

```

Returns wpa, wpa2, cipher-tkip, cipher-ccmp

```

iwlist eth7 scan

```

returns

> 
ESSID:...
Mode:Managed
Channel:11
Frequency:2.462
Quality65/100 Signal level=-64dBm Noise: 0
Encryption key: on
Bit rates: ....
Extra: bcm_int=100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher: CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK


EDIT:

> **chili555 said:**
> 
Gotta run. See you later.

Thanks for your help :)

**Still have the issue for anyone else passing through!**

EDIT again:

This is probably the issue: [http://ubuntuforums.org/showthread.php?t=1748355&page=1](http://ubuntuforums.org/showthread.php?t=1748355&page=1)

---

### Post by chili555 on 2012-04-20
> ESSID:...
Mode:Managed
Channel:11
Frequency:2.462
Quality65/100 Signal level=-64dBm Noise: 0
Encryption key: on
Bit rates: ....
Extra: bcm_int=100
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher: CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK Is that all of it? I am hoping your network is set to WPA2 only, not the tricky mixed WPA and WPA2.

This driver has been dropped from Ubuntu 12.04. The bug referred to in your link says:> Ok, just to sum up: This has been reported half a year ago, 10 people are affected and likely many more not on Launchpad, bug information is present, the bug is unassigned and no action whatsoever has been taken. Because of this bug I have been forced to use a different OS on the relevant machine since without WLAN the machine is useless to me.

I really hope this bug will be addressed for the LTS release in April.
Well, it was addressed; it was removed!

I suggest we try to install the Windows driver using ndiswrapper. What is on the disk?

---

### Post by Cheetah05 on 2012-04-20
> **chili555 said:**
> Is that all of it? I am hoping your network is set to WPA2 only, not the tricky mixed WPA and WPA2.

This driver has been dropped from Ubuntu 12.04. The bug referred to in your link says:Well, it was addressed; it was removed!

I suggest we try to install the Windows driver using ndiswrapper. What is on the disk?

Well I copied the bits that were important. My Wifi is WPA2 only.

What disk would you be referring to?

---

### Post by chili555 on 2012-04-20
No driver disk on hand? We can try the attached. Are you confident about installing a driver with ndiswrapper or do you need a little help? You can extract this package by right-clicking it and selecting *Extract Here*.

I notice the 32-bit .inf is in two versions; v1 and v2. If you have a 32-bit system, I suggest you try one and then the other to get it working.

You'll need to blacklist *vt6656_stage*.

---

### Post by Cheetah05 on 2012-04-22
> **chili555 said:**
> No driver disk on hand? We can try the attached. Are you confident about installing a driver with ndiswrapper or do you need a little help? You can extract this package by right-clicking it and selecting *Extract Here*.

I notice the 32-bit .inf is in two versions; v1 and v2. If you have a 32-bit system, I suggest you try one and then the other to get it working.

You'll need to blacklist *vt6656_stage*.

Thank you very much for you help!

I have enabled a Guest WEP network which works with the 11.10 inbuilt driver.

I will be upgrading to a new setup soon so I'm not going to bother putting any more time into this.

Thank you again!

---

