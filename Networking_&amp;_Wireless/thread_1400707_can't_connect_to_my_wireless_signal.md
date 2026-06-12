---
title: "can't connect to my wireless signal"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by Jimmyxs on 2010-02-07
I have  Ubuntu 9.10 a dell laptop i am using a tew-644ub usb wireless adaptar and it's seeing signals but wont connect to any my network is unsecured and open. everytime i try it does this swirlly thing then says diconected. im using a diferent computer to post this so if there is any way to fix this please tell me!

---

### Post by chili555 on 2010-02-07
Open a terminal and let us see:```
lsmod | grep rt2
```Thanks.

---

### Post by Jimmyxs on 2010-02-07
still nothing :( it comes up with this


james@landhoe:~$ lsmod | grep rt2
rt2870sta             488820  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  2 rt2800usb,irda

---

### Post by chili555 on 2010-02-08
Please see:  [http://ubuntuforums.org/showpost.php?p=8786509&postcount=16](http://ubuntuforums.org/showpost.php?p=8786509&postcount=16)

---

### Post by nilbus on 2010-04-29
chili555, thanks!  That solution worked for me

---

### Post by WindowsIsBad on 2010-05-06
Hi, I have a TEW-644UB on my desktop, but can not get it to show up at all.

lsmod | grep rt2

shows nothing

I installed the wireless network drivers package and choose the windowsXP .INF file. It says the hardware is present, but on the tray it has a red exclamation mark... 

Help is greatly appreciated :)

Here is another command, and what it shows.

dmesg | grep -e ndis -e wlan
[   13.444702] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.117924] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   14.118503] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   14.119690] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   14.120277] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2010-05-07
> I installed the wireless network drivers package and choose the windowsXP .INF file.I believe it also requires the .sys file. Was the .sys file in the same directory, ideally your desktop, when you installed the .inf?> check system log for messages from 'loadndisdriver'Let's see what it says:```
sudo cat /var/log/syslog | grep loadndis
```Thanks.

---

