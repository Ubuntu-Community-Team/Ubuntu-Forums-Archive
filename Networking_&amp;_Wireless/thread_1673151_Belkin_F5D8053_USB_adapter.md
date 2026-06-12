---
title: "Belkin F5D8053 USB adapter"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Stefan_McFeeters on 2011-01-22
Hi, I am looking at buying a Belkin F5D8053 USB adapter for Ubuntu 10.10. I am hearing a lot of things about having to install the Rt2870 driver before I can use it, is this true. If so can someone please tell me how to install it before I buy the adapter.

---

### Post by chili555 on 2011-01-22
The driver rt2870sta is built in to the kernel in Ubuntu 10.10. Your device will likely be claimed by another driver rt2800usb. This can be easily fixed with an addition to the blacklist file. If this is an N device and you require N speeds, I suggest you search this forum for rt2870sta and N. Several posters have reported difficulty.

Post back if you need additional guidance.

---

### Post by Stefan_McFeeters on 2011-01-24
> **chili555 said:**
> The driver rt2870sta is built in to the kernel in Ubuntu 10.10. Your device will likely be claimed by another driver rt2800usb. This can be easily fixed with an addition to the blacklist file. If this is an N device and you require N speeds, I suggest you search this forum for rt2870sta and N. Several posters have reported difficulty.

Post back if you need additional guidance.

I think I'll just test and see what happens, hopefully it will work straight out of the box seeing as the driver is already installed I'm Ubuntu 10.10

---

### Post by JNA on 2011-02-11
Any update on how this worked out of the box?  I'm using 10.10 and I am thinking of getting this adapter if I can get a confirmation.


Thanks!

---

### Post by viktormadarasz on 2011-02-13
> **chili555 said:**
> The driver rt2870sta is built in to the kernel in Ubuntu 10.10. Your device will likely be claimed by another driver rt2800usb. This can be easily fixed with an addition to the blacklist file. If this is an N device and you require N speeds, I suggest you search this forum for rt2870sta and N. Several posters have reported difficulty.

Post back if you need additional guidance.

Chili555,

Actually I have this Belkin USB Adapter F5D8053 , its an N speed one, and I would love to use it under Ubuntu 10.10, in the past I tried to make it work without success under earlier Ubuntu version...

So as a matter of fact i could use some guidance to sort this piece out...

Thanks,

Viktor

---

### Post by chili555 on 2011-02-13
Please insert the device and run and post:```
lsusb
```It might be our lucky day!

---

### Post by viktormadarasz on 2011-02-14
> **chili555 said:**
> Please insert the device and run and post:```
lsusb
```It might be our lucky day!

hi,

this is my output of lsusb:

l[I]susb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 050d:016a Belkin Components Bluetooth Mini Dongle
Bus 004 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 050d:815f Belkin Components F5D8053 N Wireless USB Adapter v6000 [Realtek RTL8192SU]
Bus 001 Device 009: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 046d:0825 Logitech, Inc. 
Bus 001 Device 003: ID 1058:1130 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/I]

---

### Post by chili555 on 2011-02-14
> ID 050d:815f Belkin Components F5D8053 N Wireless USB Adapter v6000 [Realtek RTL8192SU]Your device is supported by the driver module r8192s_usb that's built in to recent kernels. Sometimes, there is a problem with firmware. Let's see if there are any messages about it. Please run and post:```
sudo modprobe r8192s_usb
dmesg | grep 819
```Thanks.

---

### Post by viktormadarasz on 2011-02-14
> **chili555 said:**
> Your device is supported by the driver module r8192s_usb that's built in to recent kernels. Sometimes, there is a problem with firmware. Let's see if there are any messages about it. Please run and post:```
sudo modprobe r8192s_usb
dmesg | grep 819
```Thanks.

sudo modprobe r8192s_usb 

It gives no output at all after hitting the enter key..

dmesg | grep 819 gives me the following:

dmesg | grep 819
[    0.218191] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.218197] system 00:06: [io  0x0290-0x0297] has been reserved
[   18.969745] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   18.973632] Linux kernel driver for RTL8192 based WLAN cards
[   19.040246] usbcore: registered new interface driver rtl819xU
[   19.378194] r8169 0000:02:00.0: eth0: link up
[   19.378198] r8169 0000:02:00.0: eth0: link up
[   19.548385] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   19.548568] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   19.556836] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   19.557057] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   19.557063] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   19.574685] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   19.574933] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   19.583179] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   19.583459] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   19.583462] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   21.236527] rtl819xU:=============>wlan driver to be removed
[   21.246796] rtl819xU:wlan driver removed
[   22.092393] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   22.092558] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   22.100627] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   22.100804] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   22.100807] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   22.109855] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   22.110059] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   22.118105] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[   22.118308] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[   22.118314] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

---

### Post by chili555 on 2011-02-14
Please see here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35)> wget [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/Please post back if you need further assistance.

---

### Post by viktormadarasz on 2011-02-14
> **chili555 said:**
> Please see here:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492034/comments/35)Please post back if you need further assistance.

Thanks for your help _**[COLOR=Sienna]chili555[/COLOR]**_. That was exactly the solution for my problem, my wireless device now works flawlessly under Ubuntu 10.10 

/ the only extra step i had to make was to create the RTLXXXSU folder under /lib/firmware as root because it was not present.after it went as you described

):P Thanks again

Viktor

---

### Post by chili555 on 2011-02-14
Awesome, Viktor! I'm glad it's working. You have helped some searchers, too. Have fun.

---

### Post by StepNjump on 2011-02-19
Hi viktormadarasz & chili555,

I **just bought the F5D8053 USB WiFi dongle** off *ebay* to work with my new **Ubuntu 10.10** box based on your post. I have been looking for one of those for a while. 

I am sort of new to linux. I'm very scared to death by bash shell commands though I used to be sort of good at DOS & VMS back in the 80's. 
Now though I'm over 40 so my learning curve is somewhat inverted lol. 

Would you *Viktor (and/or Chili555)* kindly letting me know exactly *what you have done* other than *creating a new directory *for this device to work? I hope I bought the right version! 

Thank you very much in advance guys for your help.

Pete StepNjump
ps: Is it a big deal to run at the G level instead of N? My router doesn't support the N mode. Thanks.

---

### Post by chili555 on 2011-02-19
> I am sort of new to linux. I'm very scared to death by bash shell commands though I used to be sort of good at DOS & VMS back in the 80's.
Now though I'm over 40 so my learning curve is somewhat inverted lol. Well, I'm over 60 and my youngest child is over 40! I love helping you youngsters learn new stuff. 

The bash shell, or more commonly (incorrectly) called the terminal is like any tool. It can be wondrous and do exactly what we want and used incorrectly, can make a huge bruise on our thumbs. Don't hesitate here or any time in the future, to ask if you don't understand. I will attempt to explain everything as we go along.

The driver for your Belkin is present in the existing kernel; the needed firmware is not. There is a file with the same name in a different place that is wrong for your device. We must get the correct firmware and put it in the right place; that is, where the driver will be looking for it. First, create a directory to receive the firmware file. The parts in a code block are terminal commands. Either write them exactly as written or, even better, copy and paste. Press Enter. If there is no output, it means the command was executed and there are no errors to report. In several commands, we will temporarily gain super user or root privileges; ordinary users are not allowed to write or change system files. The prefix to temporarily gain super user status is 'sudo.'```
sudo mkdir /lib/firmware/RTL8192SU
```Now, we will go out on the internet and get the firmware package. Be sure the ethernet cable is connected and you have an internet connection.```
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
```Notice the file extension is .gz. That is a compression scheme known as gzip. In order to use the firmware file, we have to g[COLOR="Red"]un[/COLOR]zip it.```
gunzip rtl8192sfw.bin.gz
```Now, we will move the extracted file to the directory we created:```
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```If you remove and reinsert the device and disconnect the ethernet cable, it ought to be working.> Is it a big deal to run at the G level instead of N? None whatever. If you are surfing the web, sending emails or even Skyping, G is just fine. However, if you are streaming high-def video from your HTPC or server, G speeds will cause stuttering, buffering and other artifacts; N is needed. To put it another way, if you don't know why you need N, then you probably don't need N.

Post back if you need more help.

---

### Post by jw1949 on 2011-02-23
Hello Chilli - you seem to be ace at this!

I am new to Linux and also the wrong (?) side of 60 but I have a similar problem.  My Belkin 8053 is a V3000 and the driver it uses is called rt2800usb.

This is my output from lsusb
Bus 004 Device 003: ID 0b05:1715 ASUSTek Computer, Inc. 2045 Bluetooth 2.0 Device with trace filter
Bus 004 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and from the modprobe, I get

sudo modprobe rt2800usb
jack@jack-desktop:~$ dmesg | grep 280
[    0.000000]   #39 [00021f2800 - 00021f2810]         BOOTMEM
[    0.004280] CPU: Physical Processor ID: 0
[    1.175561] powernow-k8:    0 : pstate 0 (2800 MHz)
[   13.872125] Registered led device: rt2800usb-phy1::radio
[   13.872140] Registered led device: rt2800usb-phy1::assoc
[   13.872157] Registered led device: rt2800usb-phy1::quality
[   13.873070] usbcore: registered new interface driver rt2800usb
[  212.528093] wlan1: authentication with 00:1b:2f:91:d0:30 timed out
[  560.116082] phy1 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[  607.328046] usb 1-2: new high speed USB device using ehci_hcd and address 3
[  607.525420] Registered led device: rt2800usb-phy2::radio
[  607.525884] Registered led device: rt2800usb-phy2::assoc
[  607.525941] Registered led device: rt2800usb-phy2::quality
[ 5017.240084] phy2 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[ 5021.335376] Registered led device: rt2800usb-phy3::radio
[ 5021.335424] Registered led device: rt2800usb-phy3::assoc
[ 5021.335471] Registered led device: rt2800usb-phy3::quality
jack@jack-desktop:~$ 


I really have no idea what this all means, but my adapter connects readily enough, but shows a connection speed of 48 or 54Mbps - not really good enough for streaming video with the OPlay.

Do I need to change the driver and if so can you guide me through it ?

Thanks in advance.
Jack

---

### Post by chili555 on 2011-02-23
> Do I need to change the driver and if so can you guide me through it ?Yes and yes. N speeds are somewhat tricky in Linux these days. I don't know if we will achieve it; however, rt2800usb is a bit flaky and so I'm sure we'll have a better chance with another driver. Please open a terminal and do:```
sudo su
echo rt2870sta >> /etc/modules
gedit /etc/modprobe.d/blacklist.conf
```At the end of the file, add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and let us hear your report.

WARNING TO SEARCHERS: One version of the Belkin F5D8053 uses the r8192s_usb driver; another version uses rt2870sta. They are two entirely different devices and drivers. Be sure you know which you have before you make changes to your system. As always, ask and we'll be happy to help.

---

### Post by jw1949 on 2011-02-23
Hi Chilli

Many thanks for responding so quickly.

I followed the instructions and do seem to have a more stable connection (it did work before but kept losing the connection).  The network applet reports the driver as "usb" and the speed as 54Mb/s - i.e. not as fast as I had hoped.

I have an ASUS OPlay media player (wirelessly connected with a 300 Mbps adapter recommended on the ASUS forum - see link below).  Previously the player said it was "Testing network speed" and would not play.  It is now playing a video (from this desktop in another part of the house) but with some stuttering and is reporting a network speed of 4100 Kbits/sec, which I guess is equivalent to about 4Mbps ?

I'm still very puzzled ?   By the way, what does the blacklist command do?  Should I tell you a bit more about my routers' setup or is that not relevant right now ?

Thanks
Jack

[http://goo.gl/QAlQk](http://goo.gl/QAlQk)

---

### Post by chili555 on 2011-02-23
The addition of a driver to blacklist.conf tells the system to NOT load the module no matter what. Several devices are claimed by two drivers, rt2870sta and rt2800usb. These devices work a whole lot better with just one driver. Of these, rt2870sta is a bit better.> reporting a network speed of 4100 Kbits/sec, which I guess is equivalent to about 4Mbps ?
Correct. I'm not sure I can help any further with speeds. You might search this forum for rt2870sta and N speeds.

---

### Post by jw1949 on 2011-02-24
Hello again Chilli - I'm reading some of these long threads but not really getting anywhere - could you possibly send me a link on this to get things moving again ?

Thanks

---

### Post by chili555 on 2011-02-24
> **jw1949 said:**
> Hello again Chilli - I'm reading some of these long threads but not really getting anywhere - could you possibly send me a link on this to get things moving again ?

ThanksI'll be glad to respond if you start one and post:```
lsusb
```Send me a private message if I don't catch it right away.

---

### Post by StepNjump on 2011-03-15
Hi Chili,

You are awsome! I'm so sorry I didn't get back to you earlier but I couldn't find the link to this forum (because I crashed my previous computer).. besides I got very swamped... 

I want to thank you a million. Just like the friend here and a few days after reinstalling Maverick, I found out that my card was actually working somewhat but kept disconnecting also. So I followed your explanations here to blacklist the other drivers (I think) and it worked great!

Beforehand, in order to avoid having two wifi cards fighting over the same router, I had to issue the following command 

sudo ifconfig wlan0 down but every so often, it would come back up again! so I would have to disconnect my usb key, reconnect and the whole thing. It took a long time. And eventually it would work again for another 5 minutes, other times half an hour. It would depend on it's mood.

Whenever I would perform the ifconfig wlan0 down (built in wifi card in my netbook), I would notice that the orange light showing that the device is on would turn off..

With your method, I notice that there are two devices 

[I]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8448 (8.4 KB)  TX bytes:8448 (8.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:0d:3a:e1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:75ff:fe0d:3ae1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1135305 (1.1 MB)  TX bytes:158644 (158.6 KB)

wlan1-wlan0 Link encap:Ethernet  HWaddr 00:26:c7:cc:c3:28  
          inet6 addr: fe80::226:c7ff:fecc:c328/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:399380 (399.3 KB)  TX bytes:89151 (89.1 KB)[/I]

The one that seems to be working is the wlan0. If I perform a down on wlan0-wlan1 it will turn off the light but then the surfing stops even though the icon at the top next to the battery would still show that the wifi is still on and connected.

My guess is that the wlan0-wlan1 is only a bypass is that correct? Like it,s not really transmitting?

Reason I am saying this is because I am trying to avoid getting cancer or DNA modifications due to RF near my organs. I know it's bad stuff as a ham radio operators, we are sensitized to human exposure to Radio Frequency (RF) radiation (Most people don't care much about talking about those things).

So anyway, it doesn't disconnect anymore.. I just wanted to thank you for all your help. You are amazing and great teacher too.

Sorry for not coming back to you any earlier. Lots of family problems right now too.

Please kindly just confirm that the built in transmitter isn't transmitting any idle signal with this mode (or maybe you know another recipe in order to turn off the wifi).

I had it set up that my Belkin dongle is actually hooked up to an extension cable, far away from the operator.


Thanks and hope to hear from you soon!


Pete, StepNjump
:popcorn:

> **chili555 said:**
> Yes and yes. N speeds are somewhat tricky in Linux these days. I don't know if we will achieve it; however, rt2800usb is a bit flaky and so I'm sure we'll have a better chance with another driver. Please open a terminal and do:```
sudo su
echo rt2870sta >> /etc/modules
gedit /etc/modprobe.d/blacklist.conf
```At the end of the file, add four lines:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and let us hear your report.

WARNING TO SEARCHERS: One version of the Belkin F5D8053 uses the r8192s_usb driver; another version uses rt2870sta. They are two entirely different devices and drivers. Be sure you know which you have before you make changes to your system. As always, ask and we'll be happy to help.

---

### Post by StepNjump on 2011-03-15
Chili, no I was wrong. I can just down on wlan0-wlan1 device and the light turns off on the netbook just fine.. The active connection is simply the wlan0 label.

thanks again.
ps: Chili, are you active at all on the Ubuntu irc channel? How can we get a hold of you next time?

Thanks again for all your great explanations and your patience. You def have great aptitudes to teach.

Have a good day,


Pete, StepNjump

> **StepNjump said:**
> Hi Chili,

You are awsome! I'm so sorry I didn't get back to you earlier but I couldn't find the link to this forum (because I crashed my previous computer).. besides I got very swamped... 

I want to thank you a million. Just like the friend here and a few days after reinstalling Maverick, I found out that my card was actually working somewhat but kept disconnecting also. So I followed your explanations here to blacklist the other drivers (I think) and it worked great!

Beforehand, in order to avoid having two wifi cards fighting over the same router, I had to issue the following command 

sudo ifconfig wlan0 down but every so often, it would come back up again! so I would have to disconnect my usb key, reconnect and the whole thing. It took a long time. And eventually it would work again for another 5 minutes, other times half an hour. It would depend on it's mood.

Whenever I would perform the ifconfig wlan0 down (built in wifi card in my netbook), I would notice that the orange light showing that the device is on would turn off..

With your method, I notice that there are two devices 

[I]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8448 (8.4 KB)  TX bytes:8448 (8.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:0d:3a:e1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:75ff:fe0d:3ae1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1135305 (1.1 MB)  TX bytes:158644 (158.6 KB)

wlan1-wlan0 Link encap:Ethernet  HWaddr 00:26:c7:cc:c3:28  
          inet6 addr: fe80::226:c7ff:fecc:c328/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:399380 (399.3 KB)  TX bytes:89151 (89.1 KB)[/I]

The one that seems to be working is the wlan0. If I perform a down on wlan0-wlan1 it will turn off the light but then the surfing stops even though the icon at the top next to the battery would still show that the wifi is still on and connected.

My guess is that the wlan0-wlan1 is only a bypass is that correct? Like it,s not really transmitting?

Reason I am saying this is because I am trying to avoid getting cancer or DNA modifications due to RF near my organs. I know it's bad stuff as a ham radio operators, we are sensitized to human exposure to Radio Frequency (RF) radiation (Most people don't care much about talking about those things).

So anyway, it doesn't disconnect anymore.. I just wanted to thank you for all your help. You are amazing and great teacher too.

Sorry for not coming back to you any earlier. Lots of family problems right now too.

Please kindly just confirm that the built in transmitter isn't transmitting any idle signal with this mode (or maybe you know another recipe in order to turn off the wifi).

I had it set up that my Belkin dongle is actually hooked up to an extension cable, far away from the operator.


Thanks and hope to hear from you soon!


Pete, StepNjump
:popcorn:

---

### Post by chili555 on 2011-03-15
> ps: Chili, are you active at all on the Ubuntu irc channel?I chime in once in a while, but not regularly. It's a bit chaotic for me. I usually like to put more than four seconds into a thoughtful reply. For me, the IRC channel is more a source of amusement.> How can we get a hold of you next time?Send me a private message here on the forum. 

I travel a fair amount so I may not answer instantly if I'm on a ship at sea.

---

### Post by StepNjump on 2011-03-22
Chili555,

Like I said before, I like to only have my USB wifi dongle to run. By default, both Wifi devices come on (the internal wifi in my laptop + my USB).

Everytime I boot up, I need to do the following
**ifconfig**

[I]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1297302 (1.2 MB)  TX bytes:1297302 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:cc:c3:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:135873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162235746 (162.2 MB)  TX bytes:10812348 (10.8 MB)

wlan1     Link encap:Ethernet  HWaddr 00:22:75:0d:3a:e1  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:75ff:fe0d:3ae1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20586 errors:1 dropped:0 overruns:0 frame:0
          TX packets:4350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4050690 (4.0 MB)  TX bytes:767678 (767.6 KB)
[/I]
then I need to do a 

**sudo lfconfig wlan0 down**

Then I see my wifi LED on my notebook go off..
It works fine but I was wondering if there would be an easiest way for the built in device to turn off automatically whenever my external USB Wifi dongle is connected?

If not, then I guess I could just have my internal device added to the blacklist

**lsusb**
[I]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 001 Device 010: ID 05ac:1265 Apple, Inc. iPod Nano 5.Gen
Bus 001 Device 002: ID 0402:9665 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/I]

Thanks for your help.


Pete, StepNjump

---

### Post by zaphod2003 on 2011-10-30
Excellent response

The only issue I had was that /lib/firmware/RTL8192SU/ was a file not a directory.

I bit the bullet and removed the file and then created the directory.
Copied the driver across and **bang!** - Belkin Wireless adapter sprung into life.

---

### Post by leona on 2012-07-01
I am running Ubuntu 10.04 LTS 64 bit
I have just got this above adaptor.
I've got it to work but only at 54Mbit / G
Is N speeds possible?
I have a Negear DGN3500 Wireless N router which is setup with N enabled and WPA2 AES.
So I know the 'fault' is on my computer.

lsmod produces.
```

lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
pci_stub                1598  1 
vboxpci                14281  0 
vboxnetadp             18254  0 
vboxnetflt             16670  0 
vboxdrv              1855220  3 vboxpci,vboxnetadp,vboxnetflt
nfsd                  304310  13 
exportfs                4202  1 nfsd
nfs                   311217  1 
lockd                  75079  2 nfsd,nfs
nfs_acl                 2709  2 nfsd,nfs
auth_rpcgss            44516  2 nfsd,nfs
sunrpc                228463  15 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
snd_hda_codec_analog    78702  1 
rt2800usb              33496  0 
rt2x00usb              11164  1 rt2800usb
joydev                 11104  0 
usbhid                 41116  0 
rt2x00lib              32165  2 rt2800usb,rt2x00usb
led_class               3764  1 rt2x00lib
mac80211              238928  2 rt2x00usb,rt2x00lib
cfg80211              148725  2 rt2x00lib,mac80211
ppdev                   6375  0 
hid                    83888  1 usbhid
crc_ccitt               1675  1 rt2800usb
rt2870sta             525366  1 
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
parport_pc             29958  1 
nvidia              10832570  46 
edac_core              45423  0 
k8temp                  4040  0 
edac_mce_amd            9278  0 
snd                    71283  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
vgastate                9857  1 vga16fb
asus_atk0110           10033  0 
lp                      9336  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
parport                37160  3 ppdev,parport_pc,lp
i2c_nforce2             6099  0 
usb_storage            50633  1 
floppy                 63156  0 
forcedeth              55624  0 
pata_amd               11962  0 
sata_nv                23714  6 

```

iwlist scan produces

```

wlan0     Scan completed :
          Cell 01 - Address: 30:46:9A:2C:12:91
                    Protocol:802.11b/g/n
                    ESSID:"xena"
                    Mode:Managed
                    Channel:11
                    Quality:81/100  Signal level:-58 dBm  Noise level:-81 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

Added this to /etc/modules
rt2870sta
but didn't add anything to the blacklists.

---

### Post by kurt18947 on 2012-07-01
I'm nowhere near as knowledgeable as others here but looking at your lsmod output, I'd blacklist  rt2800usb then restart.  If that didn't help, also blacklist anything rt2x* except rt2870sta.  These steps are pretty easy to undo if they don't help or make things worse.

---

### Post by leona on 2012-07-01
> **kurt18947 said:**
> I'm nowhere near as knowledgeable as others here but looking at your lsmod output, I'd blacklist  rt2800usb then restart.  If that didn't help, also blacklist anything rt2x* except rt2870sta.  These steps are pretty easy to undo if they don't help or make things worse.

Thank you for replying so quickly.

I followed Chili555 examples and blacklisted 
```

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

```
But I am still connected at 54Mbit

I'm getting the impression that Linux can not do N speeds :(

---

### Post by chili555 on 2012-07-01
> **kurt18947 said:**
> I'm nowhere near as knowledgeable as others here but looking at your lsmod output, I'd blacklist  rt2800usb then restart.  If that didn't help, also blacklist anything rt2x* except rt2870sta.  These steps are pretty easy to undo if they don't help or make things worse.In other words, *UN*blacklist rt2870sta and blacklist rt2800usb. In 10.04, this is likely to work. Also, and this is a long-shot, post for us:```
dmesg | grep ieee
```

---

### Post by leona on 2012-07-01
> **chili555 said:**
> In other words, *UN*blacklist rt2870sta and blacklist rt2800usb. In 10.04, this is likely to work. Also, and this is a long-shot, post for us:```
dmesg | grep ieee
```

Arr, thank you, yes I have done that.

Sadly the dmesg cmd didn't produce any output.

---

### Post by chili555 on 2012-07-01
> Sadly the dmesg cmd didn't produce any output.Correct; rt2800usb depends on mac80211 and rt2870sta doesn't. We therefor have nothing to adjust or tweak here.

Did rt2800usb drive your device OK? We might try it again and tweak ieee80211 a bit and see if it helps.> don't want any of that 'Unity' rubbishYou can install Gnome Shell in about three minutes, if you can tolerate Unity for even that long.

---

### Post by leona on 2012-07-02
> **chili555 said:**
> Correct; rt2800usb depends on ieee80211 and rt2870sta doesn't. We therefor have nothing to adjust or tweak here.

Did rt2800usb drive your device OK? We might try it again and tweak ieee80211 a bit and see if it helps.

Yes both drivers seemed to work ok.
So yes I can put it back and tweak it a little, just let me know what I need to tweek :)

> **chili555 said:**
> 
You can install Gnome Shell in about three minutes, if you can tolerate Unity for even that long.
Now you see, the tricky thing is, this computer is shared with  my partner, its taken me a long time to get her to use the computer, so I do not wish to change the GUI as this would throw her, so I need to ensure that what I install looks Very similar to what we have now, which is why I've not taken to installing 12.04 yet, I need to see what Gnome-classic looks like before I go changing anything, but thank you for the advice.  A topic for another thread :)

---

### Post by chili555 on 2012-07-02
First we are going to write one file. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/mac80211.conf
```Add a single line:```
options mac80211 ieee80211_default_rc_algo=minstrel_ht
```Proofread, save and close gedit.

Now we unload rt2870sta and load up rt2800usb. rt2800usb will load all its dependencies, including mac80211.```
sudo modprobe -r rt2870sta
sudo modprobe rt2800usb
```Any improvement? N speeds perhaps?

If not, reverse it with:```
sudo modprobe -r rt2800usb
sudo modprobe rt2870sta
```

---

### Post by leona on 2012-07-02
> **chili555 said:**
> First we are going to write one file. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/mac80211.conf
```Add a single line:```
options mac80211 ieee80211_default_rc_algo=minstrel_ht
```Proofread, save and close gedit.

Now we unload rt2870sta and load up rt2800usb. rt2800usb will load all its dependencies, including mac80211.```
sudo modprobe -r rt2870sta
sudo modprobe rt2800usb
```Any improvement? N speeds perhaps?

If not, reverse it with:```
sudo modprobe -r rt2800usb
sudo modprobe rt2870sta
```

Thank you
the cmd
```
sudo modprobe -r rt2870sta 
```
gave me
```
FATAL: Module rt2870sta is in use.
```

Do I have to change the Blacklists or loaded modules?

---

### Post by chili555 on 2012-07-02
> 
```
sudo modprobe -r rt2870sta

```
gave me
```
FATAL: Module rt2870sta is in use.
```

Do I have to change the Blacklists or loaded modules?It simply means the module was already in place and being used. I would, temporarily, change the blacklists to blacklist rt2870sta and UNblacklist rt2800usb. Reboot and verify that rt2800usb is loaded and not rt2870sta:```
lsmod | grep rt2
```Do you have N speeds?

---

### Post by leona on 2012-07-03
Arr thank you
the result of ```
lsmod | grep rt2
```
was
```

rt2800usb              33496  0 
rt2x00usb              11164  1 rt2800usb
rt2x00lib              32165  2 rt2800usb,rt2x00usb
led_class               3764  1 rt2x00lib
mac80211              238928  2 rt2x00usb,rt2x00lib
cfg80211              148725  2 rt2x00lib,mac80211
rt2870sta             525366  1 
crc_ccitt               1675  1 rt2800usb

```
But connection info still reports speeds of 54Mbit/s :(

---

### Post by chili555 on 2012-07-03
You have *BOTH* rt2800usb and rt2870sta loaded. Please check and adjust your blacklists. Then unload rt2870sta:```
sudo modprobe -r rt2870sta
```Or reboot.

---

### Post by leona on 2012-07-03
> **chili555 said:**
> You have *BOTH* rt2800usb and rt2870sta loaded. Please check and adjust your blacklists. Then unload rt2870sta:```
sudo modprobe -r rt2870sta
```Or reboot.

Arr it seems removing the RT2870sta driver causes the wireless not to see 'my' network, can see my neighbours but not mine, if it try to add it manually it just gives me the spinny thing and then constantly asks for my password.

Ok, don't think that is going to work, not to worry, it was an experiment but I think the best course of action is to get some gigbit power plugs.

Thank you so much for taking the time to try this, that was very kind of you and I very much appreciate it.

---

