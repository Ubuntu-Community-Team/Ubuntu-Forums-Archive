---
title: "Asus usb-n13"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by David Talucci on 2012-01-15
New to UBUNTU, I've put Ubuntu 11.10 onto an old IBM ThinkPad R51 which has a PCMIA slot (no card) and I'm trying to get an ASUS USB-N13 wireless adapter to work.

I have a D-link DIR-615 router.

lsusb recognizes the adapter and the "network manager" can see the network.  I just can't connect.

I have the linux drivers on a disk.

Please help

---

### Post by chili555 on 2012-01-15
I assume it is using the driver rt2800usb. Please check:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Your driver may need the newer firmware. Please see posts 42 and following here: [http://ubuntuforums.org/showthread.php?p=11612899#post11612899](http://ubuntuforums.org/showthread.php?p=11612899#post11612899)

Post back if you need additional guidance.

---

### Post by David Talucci on 2012-01-15
yes

rt2800usb     22300 0
rt2800lib     48717 1 rt2800usb
rt2x00usb     20092 1 rt2800usb
rt2x00lib     48118 3 rt2800usb, rt2800lib, rt2x00usb
mac80211     272785 3 rt2800lib, rt2x00usb, rt2x00lib
cfg80211     172392 2 rt2x00lib, mac80211
crc_ccitt     12595 2 rt2800lib, irda

---

### Post by David Talucci on 2012-01-15
All seamed well until the last step/s unloading rt3070sta and loading rt2800usb

FATAL: rt3070sta not found

I think I need to unload something else

---

### Post by chili555 on 2012-01-16
You need to unload rt2800usb and reload it letting it grab the newer firmware:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb
```Or simply reboot. Now does your device connect?

---

### Post by David Talucci on 2012-01-16
chili555, thanks again I'm enjoying your assistance

My goal is to buy a handful of cast of computers and laptop for my whole family.  Get them running Ubuntu, and wean them off Windows or what ever comes from Redmond, Wa.

---

### Post by David Talucci on 2012-01-16
sudo modprobe -r rt2800usb causes the laptop to lock up. should I reinstall Ubuntu and try again?  this adapter is the only thing I need to get working.

quick plug, I have a Chromebook and love it.  actually would like to setup a handfull of old laptops and PCs to work like Chromebooks.

maybe peppermint, but need to solve the wifi issue first

---

### Post by chili555 on 2012-01-17
It will be perfectly acceptable to reboot in order to get the later firmware to load. If your computer locked up, I'm sure that, by now, you've rebooted. Did the wireless work as expected? Are there any clues here?```
dmesg | grep rt2
```I wouldn't reinstall for a tiny glitch like that.

---

### Post by David Talucci on 2012-01-17
thanks, I'll hang in with this install, still no wireless

any ideas?

---

### Post by chili555 on 2012-01-17
> **David Talucci said:**
> 
any ideas?Yes:> Are there any clues here?
```
dmesg | grep rt2
```



---

### Post by David Talucci on 2012-01-17
dmesg | grep rt2, does not return any info

---

### Post by chili555 on 2012-01-17
It appears that the module didn't load as expected. Let's load it:```
sudo modprobe rt2800usb
dmesg | grep rt2
iwconfig
```Thanks.

---

### Post by David Talucci on 2012-01-18
[    24.164559] Registered led device: rt2800usb-phy0::radio
[    24.164619] Registered led device: rt2800usb-phy0::assoc
[    24.164675] Registered led device: rt2800usb-phy0::quality
[    24.171577] usbcore: registered new interface driver rt2800usb

iwconfig

lo       no wireless extension
eth0     no wireless extension
irda0    no wireless extension
wlan0    IEEE 802.11bgn   ESSID: "Talucci" (that's my wifi network)
         Mode: Managed  Frequency:2.437 Access Point 00:24:01:73:44:2B
         Bit Rate=81 Mb/s  Tx-Power=27dBm
         Retry long limit: 7   RTS thr:off   Fragment thr:off
         Power Management:on
         Link Quality=65/70  Singla level=-45dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:2 Invalid misc:25  Missed beacon:0

---

### Post by chili555 on 2012-01-19
You don't say so explicitly, but it appears that if the module is simply loaded, it works fine and at N speeds. Let's be sure it loads on boot:```
sudo su
echo rt2800usb >> /etc/modules
exit
```> My goal is to buy a handful of cast of computers and laptop for my whole family. Get them running Ubuntu, and wean them off WindowsA certain 70-something grandmother in this house loves her some Ubuntu! You can do it!

---

### Post by David Talucci on 2012-01-22
no good

don't I need to "make" the driver and install/configure from the disk included with the adapter?

note, that I have a d-link adapter that had been working with the windows PC's that I've now installed Ubuntu.  the d-link adapter worked immediately, I had purchased another d-link adapter and could not get it to work.

---

### Post by chili555 on 2012-01-22
Likely the drivers on the disk are fairly old in Linux terms. If so, they'd likely not play well with your new modern 3.0xx kernel. What is the version on the disc?

I am not sure what this means:> no goodDoes that mean that the driver rt2800usb does not load on boot? Does it mean that, although it loads, no wireless interface wlan0 is created? Does that mean that an interface is created and it tries but does not connect? Or...??? 

Please reboot so we have a clean slate and post some troubleshooting diagnostics:```
lsmod | grep rt2
iwconfig
dmesg | grep wlan
sudo iwlist wlan0 scan
```

---

### Post by David Talucci on 2012-01-22
I got it I got it I got it

I manual input the device MAC and DNS and it connected immediately

I got it

Free at last, free at last, thank god I'm free at last

one small line of code, one giant feature for my new (old) laptop.

thank you very very very much

---

### Post by chili555 on 2012-01-22
Awesome! Glad it's working. Have fun.

---

### Post by David Talucci on 2012-01-22
Let me know if there is anything I can do for you.  I'm a commercial construction manager, working primarily in hospital.  MRI's, Cancer Treatment, etc.  LEED AP+ if that means anything.

off to play

---

### Post by bigman1970 on 2012-01-26
> **David Talucci said:**
> I got it I got it I got it

I manual input the device MAC and DNS and it connected immediately

I got it

Free at last, free at last, thank god I'm free at last

one small line of code, one giant feature for my new (old) laptop.

thank you very very very much
I have exactly the same problem with asus n13 and dlink dir 615 router where did you manually input the device MAC and DNS info? Please reply asap because this has been bugging me for a few days. Thanks.

---

### Post by David Talucci on 2012-01-27
click on the "wireless icon" on the top ribbon and select "EDIT CONNECTIONS" the first tab of the edit connections dialog box you can input the MAC address (printed on the adapter)

and on the IPV4 tab you can input the DNS server, address, netmask and gateway, print on the router

---

