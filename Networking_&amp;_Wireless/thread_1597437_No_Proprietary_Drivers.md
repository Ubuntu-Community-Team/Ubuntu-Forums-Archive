---
title: "No Proprietary Drivers"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by pinbill on 2010-10-15
Hello All-

I finally got my dual boot set up with win7 and ubuntu 10.4 running good and found an ethernet connection. I updated ubuntu and installed medibuntu. I went to system, admin, hardware drivers, and could not find a driver to enable. Does anyone have any ideas on where to go from here?


Thanks,

Bill

---

### Post by Claus7 on 2010-10-15
Hello,

yup! You have to know which graphics card you have.

Type:
```
lspci | grep VGA
```
and let us know. That way me or someone else will be able to give a hand.

Regards!

---

### Post by pinbill on 2010-10-15
OK, Heres the deal.

lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Thanks a bunch for your help,

Bill

---

### Post by chili555 on 2010-10-15
> yup! You have to know which graphics card you have.Huh?

I just assumed, since he posted in Networking and Wireless and since he said he has an ethernet connection, that he was looking for a wireless driver.

pinbill, can you please clarify for us? If it is wireless you seek, please post either:```
lspci -nn
```Or:```
lsusb
```...depending on whether you have a built-in (lspci -nn) or USB (lsusb) wireless device. Strip out everything that is clearly not related to wireless.

If I am wrong and you are seeking help with graphics, pardon me and I will return to my nap.

---

### Post by pinbill on 2010-10-16
OK, here is the real stuff. I wasn't very clear. The trouble is with the wireless drivers not being accessable. 
 
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
06:00.0 Network controller [0280]: Intel Corporation WiMAX/WiFi Link 6050 Series [8086:0087] (rev 57)
15:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382] (rev 20)
15:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381] (rev 20)
15:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383] (rev 20)
15:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384] (rev 20)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
 
 
and.......
 
Bus 002 Device 002: ID 8087:0020 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8086:0186 Intel Corp. 
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
Thanks again for all the support.
 
Bill

---

### Post by chili555 on 2010-10-16
> Network controller [0280]: Intel Corporation WiMAX/WiFi Link 6050 Series [8086:0087] (rev 57)Your wireless device is supposed to work with the module *iwlagn*. Let's see if it's loaded:```
lsmod | grep iwl
```If this returns nothing, let's load it and see if your wireless springs to life:```
sudo modprobe iwlagn
iwconfig
```Do you have an interface, wlan0 perhaps? If not, let's ask the kernel why not:```
dmesg | grep iwl
rfkill list all
```

---

### Post by Claus7 on 2010-10-16
Hello,

> **chili555 said:**
> Huh?

I just assumed, since he posted in Networking and Wireless and since he said he has an ethernet connection, that he was looking for a wireless driver.


it never occurred to me that proprietary would mean anything else than graphics cards, as this was troubling me for a month or so. The overdose made me overlook the real problem of the OP. Yet, the issue is on good hands, so it's me that I have to go for a nap I think.

My apologies,
I always learn,
Regards!

---

### Post by chili555 on 2010-10-16
No apology needed. We all learn every day, hopefully.

Some wireless cards have open source drivers, some proprietary and some even have open source drivers and proprietary firmware! And then there is ndiswrapper, an open source system wrapping proprietary Windows drivers. My head is spinning.

To make it worse, a new wireless card comes out practically every day! 

It's a real mess.

---

### Post by pinbill on 2010-10-16
Here are the results from this next round of commands:


iwlagn                106815  0 
iwlcore               106050  1 iwlagn
mac80211              205402  2 iwlagn,iwlcore
cfg80211              126496  3 iwlagn,iwlcore,mac80211
led_class               2864  2 iwlcore,sdhci



The second command didn't show anything, not sure why



robertwgrodeska@johnny8:~$ dmesg | grep iwl frkill list all
grep: frkill: No such file or directory
grep: list: No such file or directory
grep: all: No such file or directory

Hope I got them right, thanks again for all the help,

Bill

---

### Post by chili555 on 2010-10-16
> robertwgrodeska@johnny8:~$ dmesg | grep iwl frkill list allThey are intended to be two separate commands:```
dmesg | grep iwl
```And the next one:```
rfkill list all
```And it's not frkill; it's **rf**kill.

---

### Post by pinbill on 2010-10-17
Reran all commands, here are the results.


robertwgrodeska@johnny8:~$ lsmod | grep iwl
iwlagn                106815  0 
iwlcore               106050  1 iwlagn
mac80211              205402  2 iwlagn,iwlcore
cfg80211              126496  3 iwlagn,iwlcore,mac80211
led_class               2864  2 iwlcore,sdhci
robertwgrodeska@johnny8:~$ sudo modprobe iwlagn
[sudo] password for robertwgrodeska: 
robertwgrodeska@johnny8:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
robertwgrodeska@johnny8:~$ dmesg | grep iwl
[   17.337091] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   17.337094] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   17.337160] iwlagn 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.337169] iwlagn 0000:06:00.0: setting latency timer to 64
[   17.337204] iwlagn 0000:06:00.0: Detected Intel Wireless WiFi Link 6050 Series 2x2 AGN REV=0x84
[   17.356265] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.356345] iwlagn 0000:06:00.0: irq 37 for MSI/MSI-X
[   18.277470] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.283037] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   18.309739] iwlagn 0000:06:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   18.309789] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   18.310979] iwlagn 0000:06:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   18.311028] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   18.312217] iwlagn 0000:06:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   18.312267] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   18.313893] iwlagn 0000:06:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   18.313944] iwlagn 0000:06:00.0: Could not read microcode: -2
[   18.415380] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   18.416571] iwlagn 0000:06:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   18.416624] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   18.417811] iwlagn 0000:06:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   18.417860] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   18.419031] iwlagn 0000:06:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   18.419080] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   18.420268] iwlagn 0000:06:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   18.420328] iwlagn 0000:06:00.0: Could not read microcode: -2
robertwgrodeska@johnny8:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Thanks for being patient, hope this helps

Bill

---

### Post by chili555 on 2010-10-17
It seems that you do indeed have the driver but not the required firmware. With a working ethernet connection, please download this:

[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-9.201.4.1.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-9.201.4.1.tgz)

Downloads may go to a folder called Downloads or to your Desktop. Wherever you find the file, right-click it and select 'Extract Here.' Three files will appear; one is named iwlwifi-6050-4.ucode. Now we will use the terminal to get it in the right spot:```
cd Desktop/
```Substitute Downloads or wherever the file was extracted.```
sudo cp iwlwifi-6050-4.ucode /lib/firmware
```Now we will give it the correct ownership and permissions:```
cd /lib/firmware
sudo chown root:root iwlwifi-6050-4.ucode
sudo chmod 644 iwlwifi-6050-4.ucode
```Now, let's remove and reload the iwlagn module and see if the firmware gets picked up and your wireless comes to life:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn
sudo iwlist wlan0 scan
```Please post back with your report.

---

### Post by pinbill on 2010-10-18
Here is what I came up with. I am not sure if I got this right, but my laptop is recognizing the server at work and asking for the password. I think its working. Thank you so much, I am totally psyched with my new computer and setup,

robertwgrodeska@johnny8:~$ cd Desktop/
robertwgrodeska@johnny8:~/Desktop$ sudo cp iwlwifi-6050-4.ucode /lib/firmware
[sudo] password for robertwgrodeska: 
robertwgrodeska@johnny8:~/Desktop$ cd /lib/firmware
robertwgrodeska@johnny8:/lib/firmware$ sudo chown root:root iwlwifi-6050-4.ucoderobertwgrodeska@johnny8:/lib/firmware$ sudo chmod 644 iwlwifi-6050-4.ucode
robertwgrodeska@johnny8:/lib/firmware$ sudo rmmod -f iwlagn
robertwgrodeska@johnny8:/lib/firmware$ sudo modprobe iwlagn
robertwgrodeska@johnny8:/lib/firmware$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:10:19:71:A9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"GPB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005264ad4c670
                    Extra: Last beacon: 3120ms ago
                    IE: Unknown: 0003475042
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080000000000000000000000000000000000000000
          Cell 02 - Address: 00:1C:10:19:73:68
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"GPB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000552477f88d7
                    Extra: Last beacon: 3052ms ago
                    IE: Unknown: 0003475042
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 03 - Address: 00:1C:10:42:87:74
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"GPB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000550db1c286e
                    Extra: Last beacon: 14808ms ago
                    IE: Unknown: 0003475042
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001700000000000000000000000000000000000000
          Cell 04 - Address: 00:1D:7E:2C:C1:7B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"GPB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005523d04c2bf
                    Extra: Last beacon: 3004ms ago
                    IE: Unknown: 0003475042
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000

robertwgrodeska@johnny8:/lib/firmware$ 


Thanks again, 

Bill

---

### Post by chili555 on 2010-10-18
It's working indeed! Great work. You have also probably helped some searchers.

Have fun and post a new thread if we can help with anything else.

---

### Post by pauls_boat on 2010-10-18
[SIZE=3]just wanted to say i have just installed ubuntu 10.10 (this is the first time i have ever tried ubuntu[/SIZE]) [SIZE=3]as part of a duel boot system alongside win 7 64 bit, and it works first time even my mobile broadband conection (virgin) which on the virgin site states does not work with linix.

i thought this would make a change for once that every thing went right not always going wrong.

regards paul
[/SIZE]

---

### Post by rummy77 on 2010-11-08
I'm kind of having the same problem with the 6050 card on my hp-dm4, and maybe someone can help me out:

When I boot into 10.10, I don't have any wireless device available.  I run ```
lsmod | grep iwl
sudo modprobe iwlagn

```and it works. However, I'd like to get it to recognize my wireless device on boot, rather than have to run this every time.

Also, I've gone through the rest of the thread, and copied the iwlwifi-6050-4.ucode file to /lib/firmware and ran ```

cd /lib/firmware
sudo chown root:root iwlwifi-6050-4.ucode
sudo chmod 644 iwlwifi-6050-4.ucode
```I'm not sure if this was needed or not, but it hasn't made 10.10 recognize wifi on boot.

Any suggestions?

---

### Post by chili555 on 2010-11-08
Let's tell the system that we want the driver module iwlagn loaded on boot. Please do:```
sudo su
echo iwlagn >> /etc/modules
exit
```You should be all set, but don't hesitate to post back if not.

---

### Post by rummy77 on 2010-11-08
Worked perfectly.  Thanks!

---

### Post by rummy77 on 2010-11-11
I've got another question/issue with this wireless card (I think).  The battery life in Ubuntu is far less than Win7, and I think it's because of what I read in this driver README file:

> 2. WiFi ONLY CONFIGURATION

Introduction:

Intel(R) Centrino(R) Advanced N + WiMax 6250 is a multi-comm WiFi and WiMax
product. This release only supports the WiFi portion of this product.

Problem:

The WiMax portion of this product is connected via internal USB interface,
which on power up is actively drawing power from the USB bus. If you are
working with a platform software configuration which is not loading the
WiMax driver for the Intel(R) Centrino(R) Advanced N + WiMax 6250 device,
then the WiMax portion of this device should be put into power save mode.
This results in a minimum power draw, ultimately resulting in better power
performance when running as WiFi only device.

Solution:

To place the WiMax portion of this device in power save mode it is required
to enable autosuspend for it. With autosuspend enabled the kernel will
autosuspend the WiMax portion of the device when it is determined to be idle.

NOTE:  Dynamic PM (autosuspend/autoresume) support for USB is present only
if the kernel was built with CONFIG_USB_SUSPEND enabled.  Please refer to
Documentation/usb/power-management.txt from the kernel documentation for more
information on USB Power management.

At the end of your Linux startup script, you need to search for the Intel(R)
Centrino(R) Advanced N + WiMax 6250 device in the sysfs file system.  Search for
a device with vendor ID = 8086(Intel) and product ID = 0186|0187|0188(Intel
WiMax portion of the device) under /sys/bus/usb/devices/<appropriate usb
device number>.  The following will need to done with administrative rights.  If
the device is found, echo the number of seconds after which you want the device
to be in selective suspend into /sys/bus/usb/devices/<appropriate usb device
number>/power/autosuspend.  The default is 2 seconds.
echo "auto" > /sys/bus/usb/devices/<appropriate usb device number>/power/control,
which will enable USB autosuspend for this device only. (If using a kernel
earlier than 2.6.35 the filename will be "/sys/bus/usb/devices/<appropriate
usb device number>/power/level").You'll have to bear with me, because I'm a relative newbie, but here it goes.  I browsed around and found that the autosuspend file is at /sys/bus/usb/devices/2-1.3/power/autosuspend.  So i went into the terminal and ```
josh@josh-dm4:~$ sudo gedit /sys/bus/usb/devices/2-1.3/power/autosuspend
[sudo] password for josh:
``` which opened the file with root privileges.  I tried changing the 2 to both auto and "auto" (meaning with and without the quotation marks, and each time I did, gedit said could not save because "Unexpected error: Error writing to file: Invalid argument" and in the terminal window I get: ```
josh@josh-dm4:/sys/bus/usb/devices/2-1.3/power$ sudo gedit autosuspend

** (gedit:31390): WARNING **: Hit unhandled case 13 (Error writing to file: Invalid argument) in parse_error.

```So what I'm asking is: 1) am I right in believing that this crazy wifi/wimax card is what's sucking my battery power? and, if so, 2) what do I need to do to autosuspend the wimax part as described?

Thanks in advance!

---

### Post by chili555 on 2010-11-12
I think you actually have to echo it:```
sudo su
echo 2 > /sys/bus/usb/devices/2-1.3/power/autosuspend
exit
```You could also add this to /etc/rc.local. The sudo su and exit are not required.

If you are not using the Wimax at all, I might also look at:```
rfkill list all
```If it looks something like this:> [COLOR="Red"]0[/COLOR]: i2400m-usb:1-2:1.3: WiMAX
Soft blocked: no
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: noYou might block the Wimax part:```
sudo rfkill block [COLOR="Red"]0[/COLOR]
```This could also be coded into /etc/rc.local. 

The searchers and I will be interested in the result.

---

### Post by rummy77 on 2010-11-12
Very interesting.  When I ran rfkill I got this output:

```
josh@josh-dm4:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```which clearly shows that the wimax device is not being used by Ubuntu.

If I understand this right, then, the iwlagn driver for 10.10 activates wifi only, regardless of the information found in the intel package at [http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-9.201.4.1.tgz](http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-9.201.4.1.tgz). 

To clarify, I'm not interested in wimax, so I don't feel put-out by the fact that it's not initialized.  Thanks for the help, though.

---

