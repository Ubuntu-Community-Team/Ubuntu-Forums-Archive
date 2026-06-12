---
title: "Dell D610 wifi driver install but cannot connect"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by djavet on 2011-06-01
Hello

I'm new to Ubuntu/Linux world and found it amazing. I love it on my Dell D610 with wifi. I've installed Ubuntu 11.04 and land on the wifi problem as explain here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

but the wifi BCM4311 seem not working for me. In the hardware/additional drivers, i've the message that the proprearty driver is working and in use. But i cannot scan the network and no way to connect to my d-link via WPA-PSK (TKIP+AES)...

What can I do to activate it?

Thx a lot for your help.
Regards, Dom

---

### Post by chili555 on 2011-06-01
A Dell, eh?

Please open a terminal and run and post:```
rfkill list all
iwconfig
lsmod | grep dell
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by djavet on 2011-06-02
Yep, I buy it for $50.
Thx to help me. Here are the output:
```
djavet@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
djavet@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

djavet@ubuntu:~$ lsmod | grep dell
dell_wmi               12601  0 
dell_laptop            13515  0 
sparse_keymap          13666  1 dell_wmi
dcdbas                 14054  1 dell_laptop
djavet@ubuntu:~$ 

```

As I installed Unbuntu in a dual boot, the wifi are normally working under windows 7.

Dom

---

### Post by wakko_kid on 2011-06-02
In my dell Vostro 1520 the wifi interface was always set as Unavailable in KnetworkManager.
This was due to the fact that rfkill see two interfaces, one of which always blocked.
I blacklisted dell-laptop, rfkill now sees correctly only one interface and knetworkManager works properly.
Hope it helps.

Similar thread:
[http://ubuntuforums.org/showthread.php?t=1745681](http://ubuntuforums.org/showthread.php?t=1745681)

---

### Post by djavet on 2011-06-02
Thx. I try it, but always the same. No wifi.

---

### Post by chili555 on 2011-06-02
> **djavet said:**
> Thx. I try it, but always the same. No wifi.Let's go back and troubleshoot your wireless driver. Please post:```
lspci -nn | grep -i 14e4
dmesg | grep -e b43 -e wl
```The pipe symbol | is on the right side of my US keyboad on the same key with \. Thanks.

---

### Post by djavet on 2011-06-02
Thx. Here we are:
```
djavet@ubuntu:~$ lspci -nn | grep -i 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
djavet@ubuntu:~$ dmesg | grep -e b43 -e wl
[   20.090102] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.340660] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.340670] wl 0000:0c:00.0: setting latency timer to 64
djavet@ubuntu:~$ 

```

---

### Post by chili555 on 2011-06-02
Looking very good so far. Let's see: ```
iwconfig
sudo iwlist eth1 scan
```The specific message it gives if it won't scan is important, please tell us what it is; don't just say, "No dice."> $ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no> This was due to the fact that rfkill see two interfaces, one of which always blocked.
I blacklisted dell-laptop, rfkill now sees correctly only one interface and knetworkManager works properly.
Hope it helps.Frankly, I don't know why you blacklisted; you are not blocked in any way.

---

### Post by djavet on 2011-06-02
The quest continue:
```
djavet@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

djavet@ubuntu:~$ sudo iwlist eth1 scan
[sudo] password for djavet: 
eth1      Interface doesn't support scanning.

```

Dom

---

### Post by chili555 on 2011-06-02
That's weird! The driver wl ought to grab this device and take off like a rocket. You don't even have *any* wireless interface. Let's see:```
lsmod | grep -e b43 -e ssb -e wl
```If your wireless were hard-blocked, I might understand, but it isn't.

---

### Post by djavet on 2011-06-02
that's like chinese for me :D
```
djavet@ubuntu:~$ lsmod | grep -e b43 -e ssb -e wl
wl                   2642531  0 
lib80211               14570  1 wl
djavet@ubuntu:~$ 

```

---

### Post by chili555 on 2011-06-02
> **djavet said:**
> that's like chinese for me :D
```
djavet@ubuntu:~$ lsmod | grep -e b43 -e ssb -e wl
wl                   2642531  0 
lib80211               14570  1 wl
djavet@ubuntu:~$ 

```It means that wl, the module that is supposed to drive your device, and it's dependency lib80211 are loaded. The possibly conflicting drivers b43 and ssb are not loaded, which is correct. Moreover, it means there is nothing wrong here to fix and make your wireless work! I hate it when you open the hood and it's all perfect except it just doesn't work.

We are going to collect a lot of information in a text document, zip it up and attach it to your reply. Please do:```
lsmod > djavet.txt
dmesg >> djavet.txt
sudo lshw -C network >> djavet.txt
rfkill list all >> djavet.txt
sudo cat /var/log/syslog | grep wl >> djavet.txt
zip djavet.zip djavet.txt
```In your home directory, you will find a file called djavet.zip. Attach it to your reply using the little paperclip tool at the top of the reply box.

---

### Post by djavet on 2011-06-02
thx a lot. Hope it can be solve ... I really appreciate your help.
Et voilà.

---

### Post by chili555 on 2011-06-02
Dr. Chili doesn't like this one bit!> [   20.346582] eth%d: 5.100.82.38 driver failed with code 21Did you build this driver from a download? (Booo!) Or did you install bcmwl-kernel-source (Yaaaay!)

May I see:```
modinfo wl | grep -i version
```

---

### Post by djavet on 2011-06-02
Second one. Here:
```
djavet@ubuntu:~$ modinfo wl | grep -i version
srcversion:     1E121706FBA8C851ED8D2F6
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 

```

---

### Post by chili555 on 2011-06-02
> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:[COLOR="Red"]4312[/COLOR]] (rev 01)Your device is claimed by two drivers:```
chili@LAPTOP60:~$ modinfo wl | grep 4312
alias:          pci:v000014E4d0000[COLOR="Red"]4312[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP60:~$ modinfo ssb | grep 4312
alias:          pci:v000014E4d0000[COLOR="Red"]4312[/COLOR]sv*sd*bc*sc*i*

```Very obviously, wl is not doing the job for us. Therefor, please do:```
sudo apt-get remove bcmwl-kernel-source dkms
sudo apt-get install firmware-b43-installer b43-fwcutter
```Reboot and tell me if the wireless is working.

---

### Post by djavet on 2011-06-02
Sadly it's not working...
```
djavet@ubuntu:~$ sudo apt-get install firmware-b43-installer b43-fwcutter
[sudo] password for djavet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
The following package was automatically installed and is no longer required:
  wfrench
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
djavet@ubuntu:~$ 

```

---

### Post by chili555 on 2011-06-02
How about the first part?```
sudo apt-get remove bcmwl-kernel-source dkms
```Is b43 blacklisted? Please reboot.

---

### Post by djavet on 2011-06-02
How can I know if it's blacklisted?
```
djavet@ubuntu:~$ sudo apt-get remove bcmwl-kernel-source dkms
[sudo] password for djavet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dkms is not installed, so not removed
Package bcmwl-kernel-source is not installed, so not removed
The following package was automatically installed and is no longer required:
  wfrench
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
djavet@ubuntu:~$ 

```

---

### Post by chili555 on 2011-06-02
> **djavet said:**
> How can I know if it's blacklisted?
Try this:```
sudo gedit /etc/modprobe.d/blacklist.conf
```If 'blacklist b43' is there, remove it and save and close gedit. If not, just close gedit and then reboot in either event.

---

### Post by djavet on 2011-06-02
I've reboot, and nothing.
Then I execture your command and found this:
```
# replaced by b43 and ssb.
blacklist bcm43xx
```

I need to remove it? or it's mispell?

---

### Post by chili555 on 2011-06-02
Don't remove it. bcm43xx is an old, old driver. You can leave it alone.

---

### Post by djavet on 2011-06-02
I've rebooted, but still nothing.
Thx a lot for your patience. I dont know what to do now...

---

### Post by djavet on 2011-06-02
Here the blacklist file output:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

---

### Post by djavet on 2011-06-03
Hi,

Do you think I've to try another Linux distribution like Fedora or OpenSuse it it's not possible to activacte the wifi, or it's a general Linux problem I will come on with other distribution?

BTW, a thousand of thx for your time and help. I've blow off with Ubuntu and works exactly the way I wish (except this wifi stuff regardin the D610).

Dom

---

### Post by chili555 on 2011-06-03
Let's have a look at:```
sudo modprobe b43
dmesg | grep b43
```We have pretty much removed wl and we're trying to get b43 working.

---

### Post by djavet on 2011-06-03
You did it!!! I'm posting from my wifi network.
```
djavet@ubuntu:~$ sudo modprobe b43
[sudo] password for djavet: 
djavet@ubuntu:~$ dmesg | grep b43
[  240.920401] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  240.920421] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[  241.047811] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  241.172311] Registered led device: b43-phy0::tx
[  241.172375] Registered led device: b43-phy0::rx
[  241.172431] Registered led device: b43-phy0::radio
[  241.596071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
djavet@ubuntu:~$ 
```

I will shutdown and reboot to see it again... to be sur it's working. See ya.

---

### Post by djavet on 2011-06-03
Not working after reboot automatically. Sadly.
It is possible to fix it?

Dom

---

### Post by chili555 on 2011-06-03
> **djavet said:**
> Not working after reboot automatically. Sadly.
It is possible to fix it?

DomDid the module b43 load on boot? Please check:```
lsmod | grep b43
```If not, let's load it:```
sudo modprobe b43
```If that get's your wireless going, let's get it to load on boot:```
sudo su
echo b43 >> /etc/modules
exit
```***Now*** does it work as expected?

---

### Post by nm_geo on 2011-06-03
Chili,  

I was wondering if the blacklist file that wl creates might be causing a problem.  The file is blacklist-bcm43.conf and it has caused me problems before.
The contents of the file

# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

I seem to remember having to remove it before getting a clean install of b43.  However I am sure the code you gave the OP should work too.

Just wondering?

---

### Post by djavet on 2011-06-04
You're a king! That's work perfectly.
I post just after rebooting twice to be sure from my wifi.

Thank you so much! I appreciate more than I can write...
I can't send you my homebrew beers, because it forbidden to send this without a lot of paper in US, but I will rise some for you!

Dom

---

### Post by chili555 on 2011-06-04
> **nm_geo said:**
> Chili,  

I was wondering if the blacklist file that wl creates might be causing a problem.  The file is blacklist-bcm43.conf and it has caused me problems before.
The contents of the file

# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

I seem to remember having to remove it before getting a clean install of b43.  However I am sure the code you gave the OP should work too.

Just wondering?Whoa! You are exactly right.

Dom, please do:```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```Now does it work after a reboot?

---

### Post by chili555 on 2011-06-04
> **djavet said:**
> You're a king! That's work perfectly.
I post just after rebooting twice to be sure from my wifi.

Thank you so much! I appreciate more than I can write...
I can't send you my homebrew beers, because it forbidden to send this without a lot of paper in US, but I will rise some for you!

DomGlad it's working! I will raise a cool one in your honor today, too!!!

---

### Post by djavet on 2011-06-05
Me too! 

Cheers!
Dom

---

### Post by john89521 on 2011-06-07
Chili – you have been a huge help!!! This D610 wifi issue has been a nightmare. [B]Thank you so much for your time spent on this!
[/B]
John

---

### Post by life in color on 2011-06-19
@Chili555 Thank you 5 trillion I've been searching hopelessly everywhere for a solution and you were the only one who helped you deserve a gold trophy :):D

---

### Post by LanceRooke on 2011-09-30
Would somebody please help me get this accomplished on my Dell Inspiron 1501?  I'm having virtually the same problem.  The internal wifi card is BCM4311.  The drivers are installed yet I can not get it to work.

---

### Post by chili555 on 2011-10-01
> **LanceRooke said:**
> Would somebody please help me get this accomplished on my Dell Inspiron 1501?  I'm having virtually the same problem.  The internal wifi card is BCM4311.  The drivers are installed yet I can not get it to work.Let's make sure we know what we're dealing with. Please open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl -e ndis
dmesg | grep -e b43 -e wl -e ndis
```Thanks.

---

