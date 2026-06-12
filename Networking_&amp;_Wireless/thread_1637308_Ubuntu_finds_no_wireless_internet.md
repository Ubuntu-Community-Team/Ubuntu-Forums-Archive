---
title: "Ubuntu finds no wireless internet"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by click66 on 2010-12-04
Hi guys, 

I've installed ubuntu on my laptop, but i've got one problem... I can't see my wireless internet? 

On my mac I see my wireless internet i click on it, put the password in and i'm connected, but on my ubuntu he doesn't show the wireless internet? 

When i connect via cable i've got internet so i think it can't be my network card because else he wouldn't connect via cable not? 

Who can help me please, i've installed all updates everything... 

thanks ahead,

Information about my laptop:

[http://pastebin.com/tphjBYFb](http://pastebin.com/tphjBYFb)

---

### Post by chili555 on 2010-12-04
> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.datLet's try a quick fix; if it doesn't work, we can try Plan B. Open a terminal and do:```
sudo mkdir /etc/Wireless/RT2860STA
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```The text editor gedit will open. Add one word:```
Default
```Save and close gedit. Now do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2860sta
dmesg | grep 286
```Post or pastebin the result. Thanks.

---

### Post by click66 on 2010-12-04
hi thanks for your help but the sudo rmmod -f command doesn't work it sais No such file or directory so i skipped that command and did modprobe that did the job and the grep gives me this as output:

0.369286 pci 0000:00:lc.3: bridge 64 bit mmio pref Oxe0000000-0xe09fffff
0.900286 firmware did not grant requested _OSC control
16.628640 input: FSPPS/2 sentelic fingersensingpad as /devices/platform/i8042/seriol/input/input10
493.401809 rt2860sta: mode is from the staging directory, the quelity is unknown, you have been warned

---

### Post by chili555 on 2010-12-04
It seems the error has been fixed. What does this tell us?```
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by wangsuda on 2010-12-04
OP, just out of curiosity, are you using 10.10 64 bit? I had the same problem in 10.10 64 bit and could not figure out how to solve it (see [http://ubuntuforums.org/showthread.php?t=1634221](http://ubuntuforums.org/showthread.php?t=1634221)). I hope you find a solution. I also hope that what is posted on the aforementioned thread can help you.

---

### Post by click66 on 2010-12-05
[chili555]("http://ubuntuforums.org/member.php?u=35909") thanks, but I want to know what the problem was so I can learn something ..

and [wangsuda]("http://ubuntuforums.org/member.php?u=751507")  I'm using the 32 bit version 10.04... I think.

---

### Post by chili555 on 2010-12-05
The module rt2860sta requires a .dat file. If it can't access one, the process of starting the interface and connecting just stops, as you saw in the dmesg part of your pastebin. As I have read in some bug reports, it's quite often good enought to create the .dat file with just one word: Default. In your case, it seems to have fixed it. Post back if we can help you again.

---

### Post by wangsuda on 2010-12-05
And where would you put the .dat file?

---

### Post by chili555 on 2010-12-05
> **wangsuda said:**
> And where would you put the .dat file?I would put it where we put it in post #2 above. This assumes you are using the rt**2860**sta driver. Do you have a similar message in *dmesg*?

---

### Post by wangsuda on 2010-12-05
I have an identical problem using 64 bit 10.10. I do not have the problem in 32 bit 10.10.

---

### Post by chili555 on 2010-12-05
Do you have the same message when you do:```
dmesg | grep 286
```If so, did you try the fix above? 

May I see, from 64-bit:```
lspci -nn
lsmod | grep rt2
```Thanks.

---

### Post by wangsuda on 2010-12-05
I test 64 bit from a live CD. I'll have to wait until later to run those commands and post the results.  Thanks for taking an interest in this problem!

---

### Post by wangsuda on 2010-12-05
> **chili555 said:**
> Do you have the same message when you do:```
dmesg | grep 286
```If so, did you try the fix above? 

May I see, from 64-bit:```
lspci -nn
lsmod | grep rt2
```Thanks.

Here are the results you requested:

CODE: dmesg | grep 286
```
ubuntu@ubuntu:~$ dmesg | grep 286
[    2.441286] ACPI: AC Adapter [AC] (on-line)
[   86.900277] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.

```


CODE: lspci -nn
lsmod | grep rt2
```
ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
04:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
07:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
07:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
07:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
07:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
ubuntu@ubuntu:~$ lsmod | grep rt2
rt2860sta             559618  0 
rt2800pci              10233  0 
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  2 rt2860sta,rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
led_class               3393  2 rt2x00lib,sdhci

```

---

### Post by chili555 on 2010-12-06
> rt2860sta             559618  0 
rt2800pci              10233  0 
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  2 rt2860sta,rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170293  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
led_class               3393  2 rt2x00lib,sdhciMan, oh man! That is sure a lot of driver modules fighting for control of one poor little wireless device. Let's kick some out and see if we get better performance. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Please add four lines at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot and let us hear your report.

---

### Post by wangsuda on 2010-12-06
and this would work on a live CD? The reason I ask is that I don't have 64 bit installed. I run 32 bit well and just test 64 bit. This wireless problem has intrigued me. Well, let's see what happens . . .

---

### Post by chili555 on 2010-12-06
> and this would work on a live CD?It won't work if you reboot. Instead, simply remove all of the rt2800 and rt2x00 modules:```
sudo rmmod -f rt2800pci
etc.
```Remove all of them instead of blacklisting. Check to see if they're all gone ***except rt2860sta*** with:```
lsmod | grep rt2
```

---

### Post by chili555 on 2010-12-06
If your wireless device is USB, you could remove it, then rmmod *all* the drivers, write the blacklist file changes and then reinsert the device. It ought to work perfectly.

---

### Post by AZBiker on 2010-12-06
I've got a pcmcia card in my Dell Inspiron 1000 that is also acting up.  It was working in 10.10, but I decided to wipe it and downgrade to 10.04.  So I burned a CD of 10.04 and did a fresh install.  Now my wireless card (which used to work) no longer works.  Card itself is powered up.  It is a Netgear WN511B.  It uses a Broadcom BC43XG Rev 01 chip.

Is there any solution that doesn't involve a network cable?  I'm broke and don't want to buy one.

Thanks for the help!!

---

### Post by chili555 on 2010-12-06
> **AZBiker said:**
> I've got a pcmcia card in my Dell Inspiron 1000 that is also acting up.  It was working in 10.10, but I decided to wipe it and downgrade to 10.04.  So I burned a CD of 10.04 and did a fresh install.  Now my wireless card (which used to work) no longer works.  Card itself is powered up.  It is a Netgear WN511B.  It uses a Broadcom BC43XG Rev 01 chip.

Is there any solution that doesn't involve a network cable?  I'm broke and don't want to buy one.

Thanks for the help!!Please start a new thread. I'll try to catch it right away, but PM me if I don't answer right away. With the card plugged in, please post:```
lspcmcia -v
```Thanks.

---

