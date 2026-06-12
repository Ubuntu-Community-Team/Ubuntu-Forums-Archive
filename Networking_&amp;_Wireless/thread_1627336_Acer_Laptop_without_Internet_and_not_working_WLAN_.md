---
title: "Acer Laptop without Internet and not working WLAN Button"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by AngelDE98 on 2010-11-21
This is my first post ... 

My problem with UBUNTU is that I can not use acer-wmi because I get this ERROR : 

```
FATAL: Error inserting acer_wmi (/lib/modules/2.6.35-22-generic/kernel/drivers/platform/x86/acer-wmi.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```

... so I can not use the acer_wmi . But this is not my only Problem : 

It is most likely caused of the missing " Firmware " / Driver for my WLAN Card ( Internal ) . Currently I use Ubuntu 10.10 but I tested 10.04 too before 10.10 and it found my Card but not the Button . 

So I want to know if there is any solution for my problem . 

If it is important : 

I use an Acer eMachines e525 with Windows Vista Home Basic ( Pimped up ) and Wubi . I saw a lot of people with simmilar problems they have it as only boot option . 

Thanks if someone helps me .

---

### Post by chili555 on 2010-11-21
> It is most likely caused of the missing " Firmware " / Driver for my WLAN Card ( Internal ) . We need details. Please post:```
lspci -nn
```Feel free to strip away everything you are sure is not your wireless card. Also, if you determined the issue is missing firmware, please share what told you that.

---

### Post by AngelDE98 on 2010-11-22
I just did it and became this as OUTPUT ... 

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
05:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)

```

And if I click on the " 0 % Wireless Icon " top right I just get under Wireless that the firmware is missing or not installed ( writing from Windows now , at least it has WLAN ... ) . 

Edit : 

I forgot to say that I just reinstalled Windows with Ubuntu on my Laptop ( HDD Format ) before doing what you did because my HDD was not fully writeable but readable . It was caused by BSODS on Windows Shutdown and Ubuntu trying to fix the leftovers ...

---

### Post by AngelDE98 on 2010-11-24
Anyone here ?!

---

### Post by chili555 on 2010-11-24
When you run:```
dmesg | grep -i firmware
```Which specific file does it ask for? ucode[COLOR="Red"]??[/COLOR].fw

---

### Post by AngelDE98 on 2010-11-24
Ok ... I am stopping joking ... The Output is in the next Post

---

### Post by AngelDE98 on 2010-11-24
```
[   15.187620] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   16.339845] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   16.339900] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   16.339947] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
``` 

All "FIRMWARE" words were marked RED in the terminal ... 

Should I do what it says ?

---

### Post by chili555 on 2010-11-24
See post #23 here: [http://ubuntuforums.org/showthread.php?t=1610113&page=3](http://ubuntuforums.org/showthread.php?t=1610113&page=3)

Post back if you need further assistance.

---

### Post by AngelDE98 on 2010-11-24
WTF ?! IT IS _NOT_ WORKING !!! :shock: :evil: 

I did this thing for checking if you have missing firmware files again to check out what is missing now ... 

```
[   15.383081] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   16.546558] b43-phy0 ERROR: Firmware file "b43/lp0initvals15.fw" not found
[   16.546617] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   16.546664] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.


```

It wants more ? All I know is that I still need "b43-open/ucode15.fw" but "b43/lp0initvals15.fw" ... wtf is this ? Can you help me please and tell me what to do / what to add ? 

Edit : Now trying the files from [http://www.omattos.com/node/6](http://www.omattos.com/node/6) ...

Edit 2 : JUST THE SAME " ERROR " BUT JUST WITH OTHER NUMBERS ON BEGINNING ( [   16.XXXXXX] ... where : X = new Numbers ) ... Can someone help me please ?

---

### Post by chili555 on 2010-11-24
Please try a reboot. Also, post:```
ls -al /lib/firmware/b43
```

---

### Post by AngelDE98 on 2010-11-24
> **chili555 said:**
> Please try a reboot. Also, post:```
ls -al /lib/firmware/b43
```

Umm ... Reboot ? I reboot my Ubuntu every time I made changes in the System ... And I am writing now from my Windows . As " Data Transfer " or " System Bridge " I use my 4gb Usb Drive ... 

Just checking it out ... wait a while

---

### Post by chili555 on 2010-11-24
> I reboot my Ubuntu every time I made changes in the SystemThat's generally not necessary in Linux; usually the system will prompt you.

---

### Post by AngelDE98 on 2010-11-24
Thanks for the Info . But still before I switch to Windows after making changes in the System ( ... sorry ... Is it named Kernel ? ) I just reboot . 
```
insgesamt 208
drwx------  2 root root  4096 2010-11-24 20:57 .
drwxr-xr-x 51 root root  4096 2010-11-24 20:57 ..
-rw-r--r--  1 root root    18 2008-04-18 19:27 a0g0bsinitvals4.fw
-rw-r--r--  1 root root   158 2008-04-18 19:27 a0g0bsinitvals5.fw
-rw-r--r--  1 root root  2680 2008-04-18 19:27 a0g0initvals4.fw
-rw-r--r--  1 root root  1858 2008-04-18 19:27 a0g0initvals5.fw
-rw-r--r--  1 root root   158 2008-04-18 19:27 a0g1bsinitvals13.fw
-rw-r--r--  1 root root   158 2008-04-18 19:27 a0g1bsinitvals5.fw
-rw-r--r--  1 root root  2056 2008-04-18 19:27 a0g1initvals13.fw
-rw-r--r--  1 root root  1858 2008-04-18 19:27 a0g1initvals5.fw
-rw-r--r--  1 root root   158 2008-04-18 19:27 b0g0bsinitvals13.fw
-rw-r--r--  1 root root    18 2008-04-18 19:27 b0g0bsinitvals4.fw
-rw-r--r--  1 root root   158 2008-04-18 19:27 b0g0bsinitvals5.fw
-rw-r--r--  1 root root  2056 2008-04-18 19:27 b0g0initvals13.fw
-rw-r--r--  1 root root  2680 2008-04-18 19:27 b0g0initvals4.fw
-rw-r--r--  1 root root  1858 2008-04-18 19:27 b0g0initvals5.fw
-rw-r--r--  1 root root   158 2008-04-18 19:27 lp0bsinitvals13.fw
-rw-r--r--  1 root root  2052 2008-04-18 19:27 lp0initvals13.fw
-rw-r--r--  1 root root  1320 2008-04-18 19:27 pcm4.fw
-rw-r--r--  1 root root  1320 2008-04-18 19:27 pcm5.fw
-rw-r--r--  1 root root 26600 2008-04-18 19:27 ucode11.fw
-rw-r--r--  1 root root 24424 2008-04-18 19:27 ucode13.fw
-rw-r--r--  1 root root 30488 2010-11-17 20:30 ucode15.fw
-rw-r--r--  1 root root 20080 2008-04-18 19:27 ucode4.fw
-rw-r--r--  1 root root 22088 2008-04-18 19:27 ucode5.fw


```

" insgesamt " is German and means something like " total of ... "

---

### Post by chili555 on 2010-11-24
Please do:```
sudo mkdir /lib/firmware/b43-open
sudo cp /lib/firmware/b43/ucode15.fw /lib/firmware/b43-open
sudo rmmod -f b43
sudo modprobe b43
dmesg | grep b43
```We are interested in entries after about 16.5466.

---

### Post by AngelDE98 on 2010-11-24
```
[    1.461545] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.461563] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[   14.987325] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.183705] Registered led device: b43-phy0::tx
[   15.183721] Registered led device: b43-phy0::rx
[   15.183743] Registered led device: b43-phy0::radio
[   16.653147] b43-phy0 ERROR: Firmware file "b43/lp0initvals15.fw" not found
[   16.653204] b43-phy0 ERROR: Firmware file "b43-open/lp0initvals15.fw" not found
[   16.653252] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

Let me guess ... I have the missing b43 drivers / firmware ... 
Where to download it as " Ready-To-Extract " package or is it not possible ?

---

### Post by chili555 on 2010-11-24
Try here. I'd copy it to both /lib/firmware/b43 and /lib/firmware/b43-open. Then do:```
sudo rmmod -f b43
sudo modprobe b43
dmesg | grep b43
```

---

### Post by AngelDE98 on 2010-11-24
OMG ... Thanks ... but I still need one file ... JOKE ! 
I added the File myself with google and ONLY ONE LINK !!! 
Now I am writing from Ubuntu ... Big thanks ! And this goes to you : :popcorn: ( Miss-use of SMILIES ) ! 
I gonna do some " last things " before my Dad comes and says " GO TO BED " ... 

But just THANKS !

---

### Post by chili555 on 2010-11-24
LOL! Glad it's working. Have fun!

---

### Post by AngelDE98 on 2010-11-25
umm ... What is DMA ? I am writing from my Desktop ( not my Laptop ) now and I can not connect to ANY ACCESS POINT ! Ubuntu shows all but is not connecting . And if I reloaded the Drivers manually I get something with DMA error ... And Windows is showing 0 ACCESS POINTS !!! It just worked right but then I could not login to Youtube on Ubuntu ... AND BOOM ! It started . Serveral REBOOTS were not helping . Please help me ! 

PS : I am away now .

---

### Post by chili555 on 2010-11-25
> And if I reloaded the Drivers manually I get something with DMA error ...I'd love to see it. Please copy and paste it, or, if that's impossible, copy and Postit it! Post it (!!) here and we'll diagnose and cure it.```
sudo modprobe b43
```

---

### Post by AngelDE98 on 2010-11-26
Somehow it works on Windows again ... 
Gonna test Ubuntu . If Ubuntu has working WLAN then I do not know what was the matter ... 

Edit : Wtf ... Ubuntu is working ... Most likely temporary hardware failure ...

---

### Post by AngelDE98 on 2010-11-26
Ok ... this is s**t ... I think Ubuntu is not liking my WLAN Card ... 

I just need to reconnect to my AC every 2 1/2 minutes ! 
If I want to update drivers WLAN disappears from the " Connection List " ( Only Cable is avaible ) ... then I need to do : 
```
sudo modprobe b43
dmesg | grep b43
```
to get it work ! 

And the worst thing : THE b43 FOLDER DISSAPEARED FROM \lib\firmware !!! I just have b43-open !!! 

I just can not watch youtube , download things , hear webradio ... DO ANYTHING IN THE INTERNET WITH UBUNTU ... 

Can you just somehow help me / tell me what to do ?
And should I create a new Topic ?

---

### Post by chili555 on 2010-11-26
> Ok ... this is s**t ...Why, because it removed your b43 file without your knowledge or permission? Unless someone else has access to your computer who has your administrative password, it's impossible.> sudo modprobe b43
dmesg | grep b43Let's fix that first; please do:```
sudo su
echo b43 >> /etc/modules
exit
```Now, please run:```
dmesg | grep b43
```What firmware is missing? Once we know that, we can fix it.

---

### Post by AngelDE98 on 2010-11-27
Ok ... my Laptop is just weird ... 
I am writing from Windows now ( Laptop ) . At least it works properly ... 
This is my DMA Error : 
```
[    1.520391] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.520409] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[   89.245092] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   89.324322] Registered led device: b43-phy0::tx
[   89.324339] Registered led device: b43-phy0::rx
[   89.324358] Registered led device: b43-phy0::radio
[   89.548253] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   98.676234] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   98.676242] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[   98.676245] b43-phy0: Controller RESET (DMA error) ...
[   98.981468] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  104.441070] b43-phy0: Controller restarted


```

... just before rebooting :p 

And the b43 folder " somehow " appeared again ... but I gonna check if it is permanent ... 

S**T is that I need to reconnect to my AC after a while and this DMA error ... 

I gonna do what you told me now in a while ... emm ... as fast as I can ...

---

### Post by AngelDE98 on 2010-11-27
Ok ... I just did what you sayd and ... 
```
[    1.490496] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.490513] b43-pci-bridge 0000:04:00.0: setting latency timer to 64

```
I just activated the " Wifi Script " ( ```
sudo modprobe b43
dmesg | grep b43
``` ) and it was just the same ... After a Reboot the big thing : IT CONNECTED AUTOMATICLY !!! 

```
[    1.482398] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.482416] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[   18.793276] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   18.917248] Registered led device: b43-phy0::tx
[   18.917264] Registered led device: b43-phy0::rx
[   18.917283] Registered led device: b43-phy0::radio
[   21.763310] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
```

I do not think it will work for a long time so I think I will get some bugs again ... But currently it just works ... Thanks ;)

Edit : NO RECONNECTING NEEDED ! YAY ! NORMAL DOWNLOADS !

---

### Post by chili555 on 2010-11-27
> [   98.676234] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   98.676242] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
[   98.676245] b43-phy0: Controller RESET (DMA error) ...
Let's fix this. Please do:```
sudo gedit /etc/modprobe.d/b43.conf
```A new, empty file will open. Write:```
options b43 pio=1 qos=0
```Proofread, save and close gedit. When you reboot, things should run much better.

---

### Post by AngelDE98 on 2010-11-27
You came in the right moment ... it just affected Windows again ...
I gonna try this in a while because I am writing now from my Desk ...

---

### Post by AngelDE98 on 2010-11-27
OMG ! Thanks ! It is working ! 

But I still think more will come because the fight has been won but the war is not over ...

And I think I will not change to Windows until I need it ;)

---

### Post by AngelDE98 on 2010-11-28
I think the War has been won , too because the only problem today was that I needed to reboot to connect to my AC but it was no big problem ... This topic can be closed if possible ...

---

### Post by chili555 on 2010-11-28
I'm glad it's working. You can select Thread Tools at the top and Mark Solved.

---

### Post by xamouras on 2012-01-26
i have a problem :/ i am new here so dont blame me if i dont undestand the most you write. :P I cant connect to internet. Even when i plug in the ethernet wire i dont have a connection. I cant connect to wireless connections. Please help me.

---

### Post by chili555 on 2012-01-26
> **xamouras said:**
> i have a problem :/ i am new here so dont blame me if i dont undestand the most you write. :P I cant connect to internet. Even when i plug in the ethernet wire i dont have a connection. I cant connect to wireless connections. Please help me.Since we're not at all sure that the wireless button is or isn't your problem, would you please start your own new thread and I'll be very glad to help. Leave a link to your new thread here. Thanks.

---

