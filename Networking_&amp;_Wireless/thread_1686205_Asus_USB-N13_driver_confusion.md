---
title: "Asus USB-N13 driver confusion"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by gameguy on 2011-02-11
I bought an asus USB-N13, mainly because of the sign saying "linux support". I have attempted to set it up, but unfortunately I don't understand the instructions in the driver I downloaded.
 
Here's the driver.
[http://www.asus.com.au/product.aspx?P_ID=UI3ejenXyxqQTIcJ&templete=2](http://www.asus.com.au/product.aspx?P_ID=UI3ejenXyxqQTIcJ&templete=2)
Unfortunately it's coming up with service unavailable for me at the moment. I downloaded it, and extracted the tgz file. It then said to use a command in the command line to extract the file, but since that produced an error I just used archive manager. I don't really understand the other instructions. Would someone be able to translate them for me - The instructions I was given are in the attatchments.
 
I am running 10.10 and using kernel 2.6.35-24-generic.

---

### Post by bkratz on 2011-02-12
You will probably find what you need in this long thread

[http://ubuntuforums.org/showthread.php?t=1419504](http://ubuntuforums.org/showthread.php?t=1419504)

---

### Post by chili555 on 2011-02-12
> **bkratz said:**
> You will probably find what you need in this long thread

[http://ubuntuforums.org/showthread.php?t=1419504](http://ubuntuforums.org/showthread.php?t=1419504)Indeed. Especially see this part:> With the latest ubuntu 10.10 2.6.35-24-generic-pae kernel, the Asus USB-N13 300Mbps adapter is fully plug & play.If yours is not plugging and playing, something else is wrong. I imagine my colleague bkratz will love to see:```
lsusb
dmesg | grep rt2
```Sorry to step on the thread.

---

### Post by gameguy on 2011-02-12
On another computer so I can't type out all the results, but I'll type out the relavent bits.
 
$lsusb
...
Bus 002 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
...
$dmesg | grep rt2
[   19.215863] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   19.230778] usbcore: registered new interface driver rt2870
 
Note that I haven't tried to install the driver yet, if that helps

---

### Post by chili555 on 2011-02-12
So far, so good. Now I betcha bkratz wants to see:```
iwconfig
```He'll be here soon.

---

### Post by bkratz on 2011-02-12
I am back, but you are the real expert, please continue--Hopefully I will learn something!

---

### Post by gameguy on 2011-02-12
Was just about to post that. I bought the wireless adapter because the hardware switch inside my laptop for my wireless broke. The laptop's wireless was originally an intel 5100, which supports AGN, and has a mode for B, which I'm assuming is wlan0
 
$iwconfig
lo no wireless extensions
 
eth0 no wireless extensions
 
wlan0 IEEE 802.11abg ESSID:off/any
Mode:Managed Acess Point: Not-Associated Tx-Power=off
Retry long-limit:7 RTS thr:off Fragment thr:off
Power Management:off
 
[COLOR=navy]wlan1 Ralink STA ESSID:""[/COLOR]
[COLOR=#000080]Mode:Auto Frequency=2.412GHz[/COLOR]
[COLOR=#000080]Link Quality=10/100 Signal level:0dBm Noise level:-143dBm[/COLOR]
[COLOR=#000080]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/COLOR]
[COLOR=#000080]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/COLOR]

---

### Post by Zookalicious on 2011-02-12
Chili555's old and drop dead simple solution at [http://ubuntuforums.org/showthread.php?t=1499153&#2](http://ubuntuforums.org/showthread.php?t=1499153&#2)  is what has always worked for me with that USB dongle. As far as I know it should still work since I just did a fresh install a couple weeks ago using that same method. There might be a better method though but it certainly gets the job done.

Also the Linux instructions for that USB's official support are garbage. I spent a good day or two trying to understand what on earth they were asking.


Edit: Also supposedly this is a better solution from the same thread, but I've always used the one listed above. Less hassle and works great for me. 
Here's the 'better' solution anyways in case you're interested. [http://ubuntuforums.org/showthread.php?t=1499153&#7](http://ubuntuforums.org/showthread.php?t=1499153&#7)

---

### Post by chili555 on 2011-02-12
> I bought the wireless adapter because the hardware switch inside my laptop for my wireless broke. The laptop's wireless was originally an intel 5100, which supports AGN, and has a mode for B, which I'm assuming is wlan0Probably. Let's stop it altogether and see if the Ralink comes to life. Please do:```
sudo su
echo "blacklist iwlagn" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and see if you see any networks when you click the Network Manager icon. When you run:```
iwconfig
```You should now see only wlan1. Does this tell us anything?```
sudo iwlist wlan1 scan
```

---

### Post by gameguy on 2011-02-12
I looked at both. As you said, the second one is a lot harder to understand. The first, however, isn't working for me (or at least there is no "/etc/udev/rules.d/network_drivers.rules".
 
$sudo ls /etc/udev/rules.d/
70-persistent-cd.rules  70-persistent-net.rules  README

---

### Post by chili555 on 2011-02-12
> **gameguy said:**
> I looked at both. As you said, the second one is a lot harder to understand. The first, however, isn't working for me (or at least there is no "/etc/udev/rules.d/network_drivers.rules".
 
$sudo ls /etc/udev/rules.d/
70-persistent-cd.rules  70-persistent-net.rules  READMEI suggest we get it working first and then later rename it to wlan0.

---

### Post by gameguy on 2011-02-12
It worked!!!:P
I think it was because it had wlan0 as my broken wireless. Now it returns wlan0 as the USB adapter. I just did the echo thing, rebooted, and it connected to my network without even asking me. Now for the bit I can never work out - how to mark the thread as solved.:D

---

### Post by gameguy on 2011-02-12
I found the solved button. It just wasn't under the post reply page

---

### Post by chili555 on 2011-02-12
> **bkratz said:**
> I am back, but you are the real expert, please continue--Hopefully I will learn something!What I hope we learned is that if rt2870sta doesn't work on a modern 2.6.35-x kernel, something else is wrong. We just had to dig it up and fix it. My other suspicions were firmware or the RT2870STA.dat file. We saw neither problem in dmesg so we had to dig deeper. I wish all of them were this easy, eh bkratz?

---

