---
title: "RaLink RT3092 Wireless not working"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by Madyan on 2010-09-12
Hi,
I'm new to Ubuntu
and after I installed it on my PC
**[HP Pavilion Elite *HPE*-*130me*]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=hk&lang=en&docname=c01998952&product=4119558")**


wireless is not working
(RaLink RT3092)
I searched for a driver and I found it in this page
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
but I don't know how to install it
Help me please

Thank you very much,
and sorry for my bad English...

---

### Post by chili555 on 2010-09-12
I don't see ***3092*** on the link you gave us. Please open Applications > Accessories > Terminal and run:```
lspci -nn
```Please post the part that describes your wireless.

---

### Post by Madyan on 2010-09-13
This is the output:
```
madyan@Madyan-HP:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b08] (rev 06)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:05ea] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. Device [1106:3403]
04:00.0 Network controller [0280]: RaLink RT3092 Wireless 802.11n 2T/2R PCIe [1814:3092]

```

---

### Post by chili555 on 2010-09-13
Here is the relevant part:> 04:00.0 Network controller [0280]: RaLink RT3092 Wireless 802.11n 2T/2R PCIe [[COLOR="Red"]1814:3092[/COLOR]]Here is a howto for Debian (Ubuntu is based on Debian):  [http://wiki.debian.org/rt2860sta](http://wiki.debian.org/rt2860sta)

Especially see:> The following list is based on the alias fields of modinfo rt2860sta in Debian 2.6.32 (2.6.32-18) kernel images.

    *

     --- snip ---
      PCI: [COLOR="Red"]1814:3092[/COLOR] RaLink RT3092 Wireless 802.11n 2T/2R PCIe
Unfortunately, the rt2860sta driver in Ubuntu doesn't claim your device. Let's "help" it just a bit. Let's create two text files.

Please do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt2860sta /sbin/modprobe --ignore-install rt2860sta $CMDLINE_OPTS; /bin/echo "1814 3092" > /sys/bus/usb/drivers/rt2860/new_id
```Proofread carefully, save and close gedit.

Next, do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="1814", ATTR{idProduct}=="3092", RUN+="/sbin/modprobe -qba rt2860sta"
```Proofread carefully, save and close gedit.

Now reboot and give us your report. If it is not working, please post:```
dmesg | grep rt2
```Thanks.

---

### Post by Madyan on 2010-09-13
I didn't understand u
do I do what is written in the page?
Also, I just did the 2 text files and saved them
then restarted
but it didn't work also
this is the output
```
madyan@Madyan-HP:~$ dmesg | grep rt2
[   21.493316] !!! rt28xx Initialized fail !!!
[   21.810878] !!! rt28xx Initialized fail !!!
```

---

### Post by chili555 on 2010-09-13
> do I do what is written in the page?Yes, exactly.> Also, I just did the 2 text files and saved them then restartedPerfect!

Please let me see the output from these two commands:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e firmware
```

---

### Post by Madyan on 2010-09-13
Here is the output:
```
madyan@Madyan-HP:~$ lsmod | grep -e rt2 -e rt3
rt2860sta             498817  0 
crc_ccitt               1339  1 rt2860sta
rt3090sta             674216  0 
madyan@Madyan-HP:~$ dmesg | grep -e rt2 -e firmware
[   21.493316] !!! rt28xx Initialized fail !!!
[   21.810878] !!! rt28xx Initialized fail !!!
```
and just a moment I will do the instruction in the page
but do I need to redo the 2 files after I finish the instructions

---

### Post by Madyan on 2010-09-13
I didn't understand the instruction
can u write it for me in more easier and detailed way please
thank u very much,

---

### Post by chili555 on 2010-09-13
> **Madyan said:**
> I didn't understand the instruction
can u write it for me in more easier and detailed way please
thank u very much,You did the instructions just perfectly. There was no need to redo the files from post #4. Once a file has been written and saved to your system, it's there until we remove it.

You are doing just fine; no worries.

I do see that the module rt3090sta is loaded and it wants to drive your device. Let's abandon rt2860sta and work on rt3090sta.

We will undo the steps from post #4 and see if the module rt3090sta will work. Please enter these commands in the terminal carefully.```
sudo rm /etc/modprobe.d/network_drivers.conf
sudo rm /etc/udev/rules.d/network_drivers.rules
```Now, please reboot and open a terminal and post:```
dmesg | grep rt3
iwconfig
```Do you have an ethernet cable attached? Do you have an internet connection as you are trying to fix the wireless?

If you have any questions, please post back. I am here for you!

---

### Post by Madyan on 2010-09-13
Thank u
It didn\t work
this is the output
```
madyan@Madyan-HP:~$ dmesg | grep rt3
[   17.092087] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   17.096005] rt3090 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.096019] rt3090 0000:04:00.0: setting latency timer to 64
madyan@Madyan-HP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
Yes, I have plugged in Ethernet cable and I'm talking to u
using Ubuntu, but the wireless not working
I'm going now,
I may come back after about 4 hrs
thank u very much

---

### Post by chili555 on 2010-09-13
I will look forward to your reply when you get back.

The reason I asked about your ethernet and an internet connection is that Network Manager will *turn off* your wireless if wired is available. Please see: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themPlease detach the ethernet cable and see if you can click the Network Manager icon and see networks and connect.

If not, please open the terminal and do:```
sudo iwlist wlan0 scan
```Thanks.

See you later.

---

### Post by Madyan on 2010-09-13
Hi again,
I deatached the cable
but it didn't find the networks
it written "diconnected" under "wireless"
I runed the command
this is the output
```
madyan@Madyan-HP:~$ sudo iwlist wlan0 scan
[sudo] password for madyan: 
wlan0     No scan results
```

---

### Post by chili555 on 2010-09-13
Please detach the cable and try the following in the terminal:```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 rate auto 
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Madyan on 2010-09-13
Hi Chili again,
I'm sorry I can't use the PC now
I'm now talking to u from another computer
and I will do the instruction in your replay after about 7 hrs
thank u very much for helping me

---

### Post by chili555 on 2010-09-13
I'll see you then. Have a pleasant day.

---

### Post by Madyan on 2010-09-14
Hi again,
This is the output
```
madyan@Madyan-HP:~$ sudo iwconfig wlan0 mode managed
[sudo] password for madyan: 
madyan@Madyan-HP:~$ sudo iwconfig wlan0 rate auto 
madyan@Madyan-HP:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

---

### Post by chili555 on 2010-09-14
Please post:```
ls /etc/Wireless
ls /etc/Wireless/RT2860
cat /etc/Wireless/RT2860/RT2860STA.dat
```Thanks.

---

### Post by Madyan on 2010-09-14
Hi
```
madyan@Madyan-HP:~$ ls /etc/Wireless
ls: cannot access /etc/Wireless: No such file or directory
madyan@Madyan-HP:~$ ls /etc/Wireless/RT2860
ls: cannot access /etc/Wireless/RT2860: No such file or directory
madyan@Madyan-HP:~$ cat /etc/Wireless/RT2860/RT2860STA.dat
cat: /etc/Wireless/RT2860/RT2860STA.dat: No such file or directory

```

---

### Post by chili555 on 2010-09-14
The reason I asked about those files is explained here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=588863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=588863)

Let's create the file. Please open a terminal and do:```
sudo mkdir /etc/Wireless
sudo mkdir /etc/Wireless/RT2860STA
sudo gedit /etc/Wireless/RT2860STA/RT2860STA.dat
```The text editor gedit will open a blank file. Add one word:```
Default
```Proofread, save and close gedit. Reboot and let us have your report.

---

### Post by Madyan on 2010-09-14
Dear Chili555,
Thank you very much
the wireless is working now
and I'm talking to you now using it
Thank you again
and sorry for taking your time

---

### Post by chili555 on 2010-09-14
I'm glad it's working. I was happy to have been of help.

---

### Post by barbseven on 2011-11-06
I would just like to say thanks to [chili555]("http://ubuntuforums.org/member.php?u=35909"), this solution worked for HP pavilion elite 575a, with RaLink rt3092 mini wireless card. This card is also known as HP Mini Card. Thanks a million guys \\:D/

---

