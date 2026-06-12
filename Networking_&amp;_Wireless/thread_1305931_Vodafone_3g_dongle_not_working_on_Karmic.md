---
title: "Vodafone 3g dongle not working on Karmic"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by Nightstrike2009 on 2009-10-30
My Vodafone 3G Dongle is not working on 9.10 Final Karmic Koala, but did on 9.04, Firefox error console reports this:


> Error: uncaught exception: [Exception... "Component returned failure code: 0x80040111 
(NS_ERROR_NOT_AVAILABLE) [nsIXMLHttpRequest.status]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  
location: "JS frame :: chrome://ubufox/content/startpage.html :: anonymous :: line 51"  data: no]

This is very annoying as it worked on 9.04 and still does on windows xp (dual boot) so it is not the modem, i cant get any connection at all and is my only way of going on internet. In 9.04 it was just plug & play.

The modem is detected and set up under the wireless connection signal applet and can connect & disconnect but still the internet doesn't work, personally i think this should have been fixed before final as RC version did the same :(. 

Any ideas on how to fix this?

---

### Post by dj-toonz on 2009-10-30
Try this

Open up places, Computer & if you see a virtual CD rom & a SSD card slot

right mouse click on the Virtual CD rom (you don't need it, there windows drivers) & select safety remove device)

then when the SSD card reader & virtual CD rom has dissapered , close the computer browser box


open a terminal up

Applications , Accessory , Terminal

then copy & paste these

sudo rmmod usb-storage

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001

sudo pppd ttyUSB0

then when you goto Network-Manager your modem should be working. My How To I must of posted at least 100 times and worked for every body

---

### Post by Nightstrike2009 on 2009-10-30
Thanks my friend copied that to notepad as using XP on net, I will reboot & try it, do you have to do this every time you want to go on net or is it permanent?

---

### Post by dj-toonz on 2009-10-30
Every time you boot up the connection the first time (when you disconnect, you don't need to again)  till you reboot, It's just a quick fix till the bug is fixed

---

### Post by Nightstrike2009 on 2009-10-30
Thanks but didnt work on mine, resorting to Ubuntu 9.04 (Wubi) modem works on 9.04. This 9.10 3G Dongle situation is a farce are they trying to get people off ubuntu to Windows 7. Because this bug could cause that to happen should have been fixed before final, not happy or impressed with 9.10 over this. :(

---

### Post by hogsmate on 2009-10-31
im using Vodafone Huawei E220 modem to get connected to internet its not working with ubuntu 9.10(i installed Karmic yesterday 30 Oct 2009) it worked flawlessly in Ubuntu 9.04 but the interesting thing is when i reboot from windows to ubuntu it works i think something is wrong with the drivers can anyone help me cos really don't like to go to windows to get connected to internet and plus i work in ubuntu 
my kernel version is 2.6.31-14-generic
HELP ME!!:(

---

### Post by kesamaa on 2009-10-31
This worked for me. Thank you!

---

### Post by normanp on 2009-10-31
> **dj-toonz said:**
> Every time you boot up the connection the first time (when you disconnect, you don't need to again)  till you reboot, It's just a quick fix till the bug is fixed

I have been delighted using the Vodafone dongle with 9.04 - and will certainly not upgrade to 9.10! This raises a couple of questions:

Why was 9.10 not offered as 9.10 Beta? This thread and others would then seem a normal part of beta testing. I have often wondered whether Ubuntu is rushed out too fast - a symptom being that bugs fixed in previous releases reappear.
Any networking bug is very damaging to Ubuntu's reputation and stops newbies in their tracks.

Second question:
If a bug is fixed then is the downloadable iso for say 9.10 updated? If not then 9.10 is a broken OS for all time. If it is updated then how can I tell on a given day what fixes have been applied?

Third question:
Is it true to say that basically any downloaded Ubuntu is broken in some ways until you apply all available online updates? Only then is it ready to run. This is not made clear at all on the download page ([http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)). It means that in my opinon Ubuntu is not a suitable OS in cases where access to the Internet is unavailable. It also means that if networking doesn't work out of the box you are stuffed!

I love Ubuntu and try to promote it to others but Ubuntu must come of age and never pretend a version is ready until ample feedback on a beta has been received and dealt with. 

Finally - it is curious to me that I have not knowingly seen any comments from whoever creates the distribution - surely they would be the ones who could give reasons for the problems that arise? The rest of us just seem to have to blindly, without understanding, follow instructions given (very helpfully) such as the above.

Sorry about the length of this!

---

### Post by madmax75 on 2009-10-31
I have a Huawei E169 3G dongle and dj-toonz's advice worked for me, but it is not meant to be a permanent solution.

normanp: 

I 've wondered the very same thing myself. From my perspective, this "final" release of 9.10 is clearly defective, because upgrading to it completely destroyed my internet connection, which worked beautifully in 9.04 and 8.10 (in 8.04 I had to use wvdial).

These defects existing especially in the networking area are pretty much unacceptable. 

Should there be a fix to the problem - if you're ONLY connection to the net happens to be the 3G modem that doesn't work in the first place - how exactly are you able to get the fix?

So, wake up Ubuntu people! This is not a minor bug. This is a thing that drives people away from the distro. Extremely BAD PR for Ubuntu.

---

### Post by pdc on 2009-10-31
Hi Madmax75: sorry to hear of your 9.10 problems

what happens if you type

> lsusb

and > dmesg into a terminal with the 169 connected?

(using 9.10 ??)

---

### Post by madmax75 on 2009-11-01
This is AFTER I've applied the dj-toonz fix on 9.10:

lsusb

> 
Bus 002 Device 003: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 002 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg

> 
from ttyUSB1
[   88.233319] option 2-2:1.1: device disconnected
[   88.233424] option1 ttyUSB0: GSM modem (1-port) converter now disconnected fr
om ttyUSB0
[   88.233444] option 2-2:1.2: device disconnected
[   88.409039] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   88.620179] option 2-2:1.2: GSM modem (1-port) converter detected
[   88.620275] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   88.622555] option 2-2:1.1: GSM modem (1-port) converter detected
[   88.622663] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   88.624814] option 2-2:1.0: GSM modem (1-port) converter detected
[   88.624921] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   88.657045] option: option_instat_callback: error -108
[   88.657164] option1 ttyUSB2: GSM modem (1-port) converter now disconnected fr
om ttyUSB2
[   88.657186] option 2-2:1.0: device disconnected
[   88.657248] option1 ttyUSB1: GSM modem (1-port) converter now disconnected fr
om ttyUSB1
[   88.657266] option 2-2:1.1: device disconnected
[   88.657326] option1 ttyUSB0: GSM modem (1-port) converter now disconnected fr
om ttyUSB0
[   88.657342] option 2-2:1.2: device disconnected
[   88.833039] usb 2-2: reset full speed USB device using ohci_hcd and address 2
om ttyUSB0
[   88.657342] option 2-2:1.2: device disconnected
[   88.833039] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   89.039183] option 2-2:1.2: GSM modem (1-port) converter detected
[   89.039282] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   89.039742] option 2-2:1.1: GSM modem (1-port) converter detected
[   89.039827] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   89.040058] option 2-2:1.0: GSM modem (1-port) converter detected
[   89.040136] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   89.080045] option: option_instat_callback: error -108
[   89.080156] option1 ttyUSB2: GSM modem (1-port) converter now disconnected fr
om ttyUSB2
[   89.080177] option 2-2:1.0: device disconnected
[   89.080242] option1 ttyUSB1: GSM modem (1-port) converter now disconnected fr
om ttyUSB1
[   89.080259] option 2-2:1.1: device disconnected
[   89.080318] option1 ttyUSB0: GSM modem (1-port) converter now disconnected fr
om ttyUSB0
[   89.080334] option 2-2:1.2: device disconnected
[   89.256037] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   89.470175] option 2-2:1.2: GSM modem (1-port) converter detected
[   89.470271] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   89.471078] option 2-2:1.1: GSM modem (1-port) converter detected
[   89.471169] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   89.471288] option 2-2:1.0: GSM modem (1-port) converter detected
[   89.471360] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
om ttyUSB0
[   88.657342] option 2-2:1.2: device disconnected
[   88.833039] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   89.039183] option 2-2:1.2: GSM modem (1-port) converter detected
[   89.039282] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   89.039742] option 2-2:1.1: GSM modem (1-port) converter detected
[   89.039827] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   89.040058] option 2-2:1.0: GSM modem (1-port) converter detected
[   89.040136] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   89.080045] option: option_instat_callback: error -108
[   89.080156] option1 ttyUSB2: GSM modem (1-port) converter now disconnected fr
om ttyUSB2
[   89.080177] option 2-2:1.0: device disconnected
[   89.080242] option1 ttyUSB1: GSM modem (1-port) converter now disconnected fr
om ttyUSB1
[   89.080259] option 2-2:1.1: device disconnected
[   89.080318] option1 ttyUSB0: GSM modem (1-port) converter now disconnected fr
om ttyUSB0
[   89.080334] option 2-2:1.2: device disconnected
[   89.256037] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   89.470175] option 2-2:1.2: GSM modem (1-port) converter detected
[   89.470271] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   89.471078] option 2-2:1.1: GSM modem (1-port) converter detected
[   89.471169] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   89.471288] option 2-2:1.0: GSM modem (1-port) converter detected
[   89.471360] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   89.935827] option 2-2:1.1: device disconnected
[   89.935888] option1 ttyUSB0: GSM modem (1-port) converter now disconnected fr
om ttyUSB0
[   89.935905] option 2-2:1.2: device disconnected
[   90.113039] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   90.319177] option 2-2:1.2: GSM modem (1-port) converter detected
[   90.319275] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   90.320129] option 2-2:1.1: GSM modem (1-port) converter detected
[   90.320230] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   90.320354] option 2-2:1.0: GSM modem (1-port) converter detected
[   90.320418] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   90.360045] option: option_instat_callback: error -108
[   90.360170] option1 ttyUSB2: GSM modem (1-port) converter now disconnected fr
om ttyUSB2
[   90.360195] option 2-2:1.0: device disconnected
[   90.360274] option1 ttyUSB1: GSM modem (1-port) converter now disconnected fr
om ttyUSB1
[   90.360290] option 2-2:1.1: device disconnected
[   90.360353] option1 ttyUSB0: GSM modem (1-port) converter now disconnected fr
om ttyUSB0
[   90.360369] option 2-2:1.2: device disconnected
[   90.533039] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   90.739173] option 2-2:1.2: GSM modem (1-port) converter detected
[   90.739273] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   90.741393] option 2-2:1.1: GSM modem (1-port) converter detected
[   90.741491] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   90.741617] option 2-2:1.0: GSM modem (1-port) converter detected
[   90.741724] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   90.765045] option: option_instat_callback: error -108
[   90.765160] option1 ttyUSB2: GSM modem (1-port) converter now disconnected fr
om ttyUSB2
[   90.765179] option 2-2:1.0: device disconnected
[   90.765240] option1 ttyUSB1: GSM modem (1-port) converter now disconnected fr
om ttyUSB1
[   90.765256] option 2-2:1.1: device disconnected
[   90.765313] option1 ttyUSB0: GSM modem (1-port) converter now disconnected fr
om ttyUSB0
[   90.765329] option 2-2:1.2: device disconnected
[   90.941037] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[   91.148865] option 2-2:1.2: GSM modem (1-port) converter detected
[   91.148961] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   91.151267] option 2-2:1.1: GSM modem (1-port) converter detected
[   91.151377] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   91.153283] option 2-2:1.0: GSM modem (1-port) converter detected
[   91.153392] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   91.193047] option: option_instat_callback: error -108

[etc etc etc for several pages]



So lots of "interesting" stuff going on there ;)

---

### Post by alex88 on 2009-11-01
It's a know kernel bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

just wait to a fix in ubuntu updates or install the kernel you can find in that page..

---

### Post by madmax75 on 2009-11-01
Thanks alex88! Nice to see something is happening out there at Launchpad ;) I cross my fingers and watch for a fix.

---

### Post by pcirne on 2009-11-01
Same issue with HUAWEI E220 3G Modem, when I plugin the modem the OS enters a loop trying to mount the "CD-ROM" and keeps reseting:

[ 4060.068051] usb 3-1: new full speed USB device using uhci_hcd and address 22
[ 4060.230258] usb 3-1: configuration #1 chosen from 1 choice
[ 4060.237777] scsi134 : SCSI emulation for USB Mass Storage devices
[ 4060.238017] usb-storage: device found at 22
[ 4060.238022] usb-storage: waiting for device to settle before scanning
[ 4060.424127] usb 3-1: USB disconnect, address 22
[ 4061.160061] usb 3-1: new full speed USB device using uhci_hcd and address 23
[ 4061.323258] usb 3-1: configuration #1 chosen from 1 choice
[ 4061.330765] option 3-1:1.0: GSM modem (1-port) converter detected
[ 4061.330850] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 4061.333206] option 3-1:1.1: GSM modem (1-port) converter detected
[ 4061.333274] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 4061.339421] scsi137 : SCSI emulation for USB Mass Storage devices
[ 4061.351221] usb-storage: device found at 23
[ 4061.351225] usb-storage: waiting for device to settle before scanning
[ 4066.350149] usb-storage: device scan complete
[ 4066.354135] scsi 137:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 4066.383094] sr1: scsi-1 drive
[ 4066.383346] sr 137:0:0:0: Attached scsi CD-ROM sr1
[ 4066.383494] sr 137:0:0:0: Attached scsi generic sg2 type 5
[ 4077.753095] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 4077.753122] sr: Sense Key : No Sense [current]
[ 4077.753131] sr: Add. Sense: No additional sense information
[ 4078.016109] sr1: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 4078.016137] sr: Sense Key : No Sense [current]
[ 4078.016146] sr: Add. Sense: No additional sense information
[ 4078.155063] option: option_instat_callback: error -108
[ 4078.156301] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4078.156324] option 3-1:1.0: device disconnected
[ 4078.156388] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4078.156405] option 3-1:1.1: device disconnected
[ 4078.324045] usb 3-1: reset full speed USB device using uhci_hcd and address 23
[ 4078.471254] option 3-1:1.1: GSM modem (1-port) converter detected
[ 4078.471417] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
[ 4078.479115] option 3-1:1.0: GSM modem (1-port) converter detected
[ 4078.479276] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
[ 4078.876079] option: option_instat_callback: error -108
[ 4078.877639] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4078.877683] option 3-1:1.0: device disconnected
[ 4078.877796] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4078.877827] option 3-1:1.1: device disconnected
[ 4079.000069] usb 3-1: reset full speed USB device using uhci_hcd and address 23
[ 4079.124035] usb 3-1: device descriptor read/64, error -71
[ 4079.296744] usb 3-1: USB disconnect, address 23

 cirne@cirne-laptop:/var/log$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 026: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

cirne@cirne-laptop:/var/log$ uname -a
Linux cirne-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by lunatico on 2009-11-01
I have the same problem. I have:
Bus 004 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem

Launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/)

It can't all be prefect can it? I was so happy and impressed, specially with the audio device manager... but then this...

---

### Post by RJWEcology on 2009-11-02
I've been having the same issues. I use the Vodaphone 3G modem (K3520 model) in Australia and my system won't even find the device when it's inserted! I tried the method above but nothing happened. I can't see my external HDD or my Windows files either (I did a Wubi install). 

I'm stuck without any updates from the net or this message board!

---

### Post by CbrPad on 2009-11-02
> **normanp said:**
> I have been delighted using the Vodafone dongle with 9.04 - and will certainly not upgrade to 9.10! This raises a couple of questions:

Why was 9.10 not offered as 9.10 Beta? This thread and others would then seem a normal part of beta testing. I have often wondered whether Ubuntu is rushed out too fast - a symptom being that bugs fixed in previous releases reappear.
Any networking bug is very damaging to Ubuntu's reputation and stops newbies in their tracks.

Second question:
If a bug is fixed then is the downloadable iso for say 9.10 updated? If not then 9.10 is a broken OS for all time. If it is updated then how can I tell on a given day what fixes have been applied?

Third question:
Is it true to say that basically any downloaded Ubuntu is broken in some ways until you apply all available online updates? Only then is it ready to run. This is not made clear at all on the download page ([http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)). It means that in my opinon Ubuntu is not a suitable OS in cases where access to the Internet is unavailable. It also means that if networking doesn't work out of the box you are stuffed!

I love Ubuntu and try to promote it to others but Ubuntu must come of age and never pretend a version is ready until ample feedback on a beta has been received and dealt with. 

Finally - it is curious to me that I have not knowingly seen any comments from whoever creates the distribution - surely they would be the ones who could give reasons for the problems that arise? The rest of us just seem to have to blindly, without understanding, follow instructions given (very helpfully) such as the above.

Sorry about the length of this!

A huuuge +1 on this !   Because of this issue I've actually left Ubuntu after using it as my sole o/s for five years, massively disappointing.  

Have you seen [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all)

---

### Post by taviroquai on 2009-11-02
Hi all,

The first post also worked for me.

I'm using Huawei E169 Usb modem selled by Kanguru - Portugal.

It just worked right after line 4! 
1. sudo rmmod usb-storage
2. sudo modprobe -r option
3. sudo modprobe -r usbserial
4. sudo modprobe usbserial vendor=0x12d1 product=0x1001
5. sudo pppd ttyUSB0

Thank you so much!

Please all, be patient... just don't through out Karmic on the first problem... have some respect for this FREE OS.

---

### Post by ubuntu-freak on 2009-11-02
Same issue here. Can't get my E169 aka E620 working at all in Karmic. Even when I try using Jaunty kernels it doesn't work, despite the fact it always worked fine in Jaunty itself. I'm having to post this on my phone, as I only use a USB modem to get online in Ubuntu these days. Bugger.

---

### Post by ebsbel on 2009-11-02
I had the same problem with 3 dongle. I noticed that the file /etc/resolv.conf was empty. I copied over a working version to /etc/ and the internet works just fine.
I too find Karmic a bit unfinished.
E

---

### Post by RJWEcology on 2009-11-02
I might be able to help! I'm at work at the moment but I think I might have some info for you all. 

I currently live in Sydney as I'm backpacking, so I bought a Vodaphone 3G dongle for the net. While I was in the UK, I also had a O2 3G dongle. While I tried to use the Vodaphone one, it wouldn't even show up on my system (nothing happened at all). Out of interest, I put my sim in the old O2 dongle and tried again. Huzzah! It worked fine! Nothing was needed to be done in terminal either. I just plugged it in and set up my connection as per normal. 

Tonight, would you like me to run anything or to post any code here? Obviously something is different with my O2 dongle but I'm not sure what (they're different modles of Huwei, which might be the cause). I'll log on tonight and post any output you want me to run.

---

### Post by hogsmate on 2009-11-04
hey guys this might be a bit stupid but it worked for me 
when i log in to ubuntu the modem doesn't work but it says or the notification area says that the network connection is established and available but cant browse or chat or do an installation using apt-get then wat i did was i logged out and logged in again vola it works fine :D i think its the easiest way to overcome this till this bug is fixed.:popcorn:

---

### Post by daka on 2009-11-04
This is good to hear, Hogsmate, the difference between the two usb modems, one working and the other not working!  Mine is a Huawei E220 / vodafone.

I live in Spain.  Spain is different in many ways.  The fix that is suggested to work for everyone does not work for me:

I suspect, also that there is something peculiar about the vodafone usb modem and service in Spain that is additionally problematic.

This is from the link that was not helpful for me here in the forum....

--------------------------------------------------------------

 Re: Huawei E169 in Karmic
seems there is a show-stopping bug

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/446146](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/446146)

you might like to try the fix of dj-toonz

[http://ubuntuforums.org/showthread.php?t=1305931](http://ubuntuforums.org/showthread.php?t=1305931)
-------------------------------------------------------------------

I understand that we can't keep complaining to the 'BUG' thread.  BUT all of us are running around in circles, wasting loads of time in this forum, in complete confusion, and there is a complete absence of communication with the people involved in maintaining 9.10.  I understand they are all busy, but PLEASE could someone in the know say something definitive and helpful about this very problematic situation with USB mobile modems?


Is there a fix in a kernel update available now?  If I go running down my mountain to a cybercafe can I solve this easily?

Does anyone know if the Betavine mobile connect software will work in Karmic?

Any helpful information greatly appreciated.

Daka

---

### Post by pdc on 2009-11-04
hi daka;

we have used the VMC version for the Eee running Xandros; it worked well, and picked up the various (phone) networks available and we could select;

install it; try it out;  you can delete if it does not work;

apart from that, others suggest installing 9.04 and it will allow the 3G modems to work

---

### Post by CbrPad on 2009-11-05
Hi Daka,

I also have an E220 and have the same problems.  In my case doing...

sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003

eventually works after plugging the modem in and out several times and doing the rmmod bit.  However I find it not worth the hassle as it can take up to forty minutes of cursing at the thing, so I've moved to Mandriva for the forseeable future as there's no info as to when a working solution will be found.

---

### Post by StewartG on 2009-11-05
> **hogsmate said:**
> hey guys this might be a bit stupid but it worked for me 
when i log in to ubuntu the modem doesn't work but it says or the notification area says that the network connection is established and available but cant browse or chat or do an installation using apt-get then wat i did was i logged out and logged in again vola it works fine :D i think its the easiest way to overcome this till this bug is fixed.:popcorn:
Damn that's simple. Worked for me. Many thanks.

---

### Post by ubuntu-freak on 2009-11-05
Seems that different Huawei models are affected by this bug in varying ways. Mine isn't even recognised as a modem in Karmic and doesn't even connect as a storage device properly. Also, I don't believe it's merely a kernel issue, as using Jaunty kernels in Karmic didn't help me. Anywho, I've backed up my home directory and gone back to Jaunty.

---

### Post by redbook4574 on 2009-11-05
> **CbrPad said:**
> Hi Daka,

I also have an E220 and have the same problems.  In my case doing...

sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003

eventually works after plugging the modem in and out several times and doing the rmmod bit.  However I find it not worth the hassle as it can take up to forty minutes of cursing at the thing, so I've moved to Mandriva for the forseeable future as there's no info as to when a working solution will be found.


I agree I've moved to suse 11.2

---

### Post by pave_FM on 2009-11-07
U right,
Is time to migrate from Ubuntu to OpenSuse or anoter distro... Using for one year Ubuntu for amd64 the best was 9.04 for my machine. With 9.10 I've lost internet connection by usb stick K3520/E620, no way now to compile gspca driver for my Microsoft LifeCam VX-1000 and I've got unstable kernel for my Toshiba. Ubuntu is getting worse... Like was told before Ubuntu 9.10 is Beta!
Anyway many thanks for everything!

---

### Post by ubuntu-freak on 2009-11-07
Go back to 9.04 then, that's what I've done. I don't see why you need to migrate to other distros. I'll be very shocked if 10. 04 isn't awesome.

---

### Post by jbernardo on 2009-11-12
> **ubuntu-freak said:**
> Seems that different Huawei models are affected by this bug in varying ways. Mine isn't even recognised as a modem in Karmic and doesn't even connect as a storage device properly. Also, I don't believe it's merely a kernel issue, as using Jaunty kernels in Karmic didn't help me. Anywho, I've backed up my home directory and gone back to Jaunty.

I'd go back to Jaunty too if I could. My E1692 (id 12d1:140c or sometimes 12d1:1446) also doesn't connect as a storage device, and doesn't get recognized as a modem.
From what I found, it was probably supported before - [http://www.santinoli.com/open/e1692-howto.html]("http://www.santinoli.com/open/e1692-howto.html")

---

### Post by ubuntu-freak on 2009-11-12
> **jbernardo said:**
> I'd go back to Jaunty too if I could. My E1692 (id 12d1:140c or sometimes 12d1:1446) also doesn't connect as a storage device, and doesn't get recognized as a modem.
From what I found, it was probably supported before - [http://www.santinoli.com/open/e1692-howto.html]("http://www.santinoli.com/open/e1692-howto.html")
Why can't you install Jaunty? Try the Live CD first and make sure your modem works, though.

---

### Post by jbernardo on 2009-11-12
> **ubuntu-freak said:**
> Why can't you install Jaunty? Try the Live CD first and make sure your modem works, though.

Kde 4, updated firefox, etc... :) But I might have to roll back the install, if the modem doesn't get fixed soon.

---

### Post by ubuntu-freak on 2009-11-12
> **jbernardo said:**
> Kde 4, updated firefox, etc... :) But I might have to roll back the install, if the modem doesn't get fixed soon.
There are ways to upgrade certain applicationns and other parts of the system, PPA repositories and backports for example.

---

### Post by pdc on 2009-11-12
from this bug report, it may well be that the Huawei modems are now recognised, as everyone would wish them to be recognised

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

sounds like running karmic updates may be beneficial

---

### Post by jbernardo on 2009-11-12
> **pdc said:**
> from this bug report, it may well be that the Huawei modems are now recognised, as everyone would wish them to be recognised

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

sounds like running karmic updates may be beneficial

Not all. My E1692 still doesn't work, even with all the backports and updates.

---

### Post by mannchy on 2009-11-13
hey my dongle thingy isnt working either lol go figure would anyone would be able to help im new to ubuntu atm  i have a huawei k3520 dongle its not responding it lights up so its got power but its not coming up

---

### Post by ubuntu-freak on 2009-11-13
> **mannchy said:**
> hey my dongle thingy isnt working either lol go figure would anyone would be able to help im new to ubuntu atm  i have a huawei k3520 dongle its not responding it lights up so its got power but its not coming up
First of all, download and run the 9.04 (Jaunty) LiveCD and check if the USB modem works. Stick with that version if it does.

---

### Post by pdc on 2009-11-13
ie go here

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

and click on 

PC (Intel x86) desktop CD

---

### Post by SLA_leandrin on 2009-11-15
Perhaps you guys would prefer configuring the dongle via pppconfig? That's what I've done so far, and worked fine...

---

### Post by jbernardo on 2009-11-16
The problem wasn't configuring, was detecting the dongle as a modem and not only as a cd/sd card reader. Anyway, I managed to "fix" it for now, and just posted on the [bug]("https://bugs.launchpad.net/linux/+bug/446146/comments/271") - basically it seems that there is a udev race issue at work, at least with my E1692 dongle and the latest backports kernel.

---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

### Post by tonywoody on 2009-11-17
HOPE THIS HELPS
The main point is to make sure you get the &#8220;**modprobe usbserial vendor=0x12d1 product=0x1001**
&#8221; correct for your device.

Greetings.  I have been getting the same problem.  I am running Ubuntu 9.10 (clean/new build) and using Vodafone K3530 (Huawei) on a Samsung NC10 Laptop.

After lots of clean/new rebuild I have managed to get it working by using the following:

1st - Upgrade BIOS to 11CA (needed to install Windows first) what a pain
2nd - Clean build (mainly so I know what bit fixed the problem)
3rd - Ran update manager for all of the patches
4th - ran the following script.

#!/bin/bash
sudo umount /media/Vodafone\ MC\ Installer
sleep 5
sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001


I have narrowed it down to the "modprobe usbserial vendor=0x12d1 product=0x1001" line.  YOU NEED TO MAKE SURE THAT YOU HAVE THE CORRECT "product=0x1001".  I was using "0x1003" so it did not work for me until I changed it to "0x1001".  I must have found my original work around from a site that was using a different 3G card.



I also added these.  Not sure if the are needed
#tony@icts-u910:~$ history 
sudo apt-get install usb-modeswitch 
sudo apt-get install usbmount

---

### Post by Johan-Steyn on 2009-11-18
Hi All,

Since updating to Karmic the gnome network manger  failed to recognize my Vodafone Mobile Connect USB Stick K 3765.

The issue was resolved by downloading and installing the vodafone linux driver & software  - even allowing the gnome network manager to work & recognize the usb stick.

Download the following files from [Betavine]("https://forge.betavine.net/frs/?group_id=12").

Ubuntu > **ozerocdoff_0.4-2_i386.deb**

Ubuntu > **usb-modeswitch_0.9.7_i386.deb**

Ubuntu > **vodafone-mobile-connect_2.10.01-1_all.deb**

Ubuntu > **INSTALL_UBUNTU.TXT**

Install the packages in the following order to resolve the dependencies:

Install the usb_modeswitch package. (This package is required to flip some USB devices from storage device mode to modem mode.)

**sudo dpkg -i usb-modeswitch_0.9.7_i386.deb**

Install ozerocdoff package. (This package is used for modems which use the HSO kernel driver. It also flips this type of modem from storage device mode to modem mode.)

**sudo dpkg -i ozerocdoff_0.4-2_i386.deb**

Install Vodafone Mobile Connect and it's dependencies

**sudo aptitude install wvdial hal usb-modeswitch ozerocdoff python-twisted python-serial python-sqlite python-tz python-gobject python-dbus python-cairo python-crypto python-gtk2 python-gnome2 python-gnome2-extras lsb-release python-glade2**

**sudo dpkg -i vodafone-mobile-connect_2.10.01-1_all.deb**

Run the application  from the command line in terminal:

**vodafone-mobile-connect-card-driver-for-linux**

You will also find a launcher for** Vodafone Mobile Connect** in the Applications > Internet menu.

Regards,

JS

---

### Post by dvl300 on 2009-11-18
I recently came up with a solution for wireless problems in 9.10
Follow this quick easy guide by me :)
Download ndiswrapper packages for Ubuntu 9.10 karmic koala, from this .gz archive i have put together download [here](http://www.sendspace.com/file/id9nmh)
Boot Ubuntu 9.10 live cd without your wireless adapter attached and install Ubuntu.
Once installed and your up and running, unpack the .gz file you downloaded earlier :wink: and install all the packages, then run Windows Wireless Drivers, pop in the disc that came with your wireless adapter, copy over the driver files, then restart then in Windows Wireless Drivers, click install new driver and select the windows .inf, then open and install.

Now select your access point and enter your key if needed? and you should be connected :D
Enjoy!
:)
[http://ubuntuforums.org/showthread.php?t=1329515](http://ubuntuforums.org/showthread.php?t=1329515)

---

### Post by pdc on 2009-11-18
Hi dvl300; we applaud your hard work in putting together a package; it will be helpful to someone with wireless (pci card?) issues;

in any other linux forum, someone would comment that you have added your comment to a long stream that is ... actually ... about .... a different topic:

......... namely mobile broadband accessed over a 3G GSM network, using portable USB modems;

so folks would notice your comments if you ...

made a new posting; with a new heading about the topic that you have worked hard on, and would like folks to know about presumably

... and avoided pig-backing on a posting that doesn't seem related to what you would like folks to know about

---

### Post by dr_james2k on 2009-11-28
Thanks Johan-Steyn, that worked like a charm.  Only took a minute.

Have my vodafone dongle now working on my samsung nc10 with 9.10 netbook remix installed, great stuff.

---

### Post by istaveren on 2009-11-29
The new kernel update 2.6.31-15-generic from this week. Solved the problem for me. :D

---

### Post by alfielee on 2009-12-11
](*,)
I have a Virgin 3G usb dongle, the Huw??? 220 which worked beautifully on 9.04 but on 9.10 it recognises it but fails to get it running. Once the settings are made it just spins constantly at the top like a mad fool & never connects.
](*,)

---

### Post by pdc on 2009-12-11
this has been a common problem with 9.10; many would suggest trying a live CD before changing a stable system  (ie changing from 9.04 to 9.10)

are you sure you are not using a Huawei E169

type

lsusb in a terminal

---

### Post by lpmb on 2009-12-13
Chaps;

I too am still having trouble with the Vodafone **Huawei E220 USB** modem with a fully patched Ubuntu 9.10 (**as of 13 Dec 2009**).

The catch with me is that I am *booting* from a full install on a USB drive (it's my first time and I'm experimenting on a work laptop where I have no admin rights to the HD, hence the USB stick boot).

My question is can I run these sudo commands that seem to affect the ability to recognize USB devices without actually interfering with my operating system which is, as I mention, running on a USB device itself?   Would hate to get this thing wrong (even if the cost of reinstalling is minimal).

Thanks.
LPMB.:D

---

### Post by daka on 2009-12-14
> **lpmb said:**
> Chaps;

I too am still having trouble with the Vodafone **Huawei E220 USB** modem with a fully patched Ubuntu 9.10 (**as of 13 Dec 2009**).

The catch with me is that I am *booting* from a full install on a USB drive (it's my first time and I'm experimenting on a work laptop where I have no admin rights to the HD, hence the USB stick boot).

My question is can I run these sudo commands that seem to affect the ability to recognize USB devices without actually interfering with my operating system which is, as I mention, running on a USB device itself?   Would hate to get this thing wrong (even if the cost of reinstalling is minimal).

Thanks.
LPMB.:D


Me too ... still having problems after kernel upgrade and booting from hard drive, not USB.  I am a bit frustrated after  a month of this drama.

I visited a Vodafone store and found out about a 3G wifi base for my huawei E220.  This converts the signal to a wifi signal and that signal is recognized as a wifi network connection.  Does anyone know if these 3g wifi base units are compatible with Ubuntu?  It seems like a simple solution to the usB dongle drama.

Daka

---

### Post by lpmb on 2009-12-15
deleted for inaccuracy - sorry... thought I had solved it.

---

### Post by alexfish on 2009-12-15
> **daka said:**
> Me too ... still having problems after kernel upgrade and booting from hard drive, not USB.  I am a bit frustrated after  a month of this drama.

I visited a Vodafone store and found out about a 3G wifi base for my huawei E220.  This converts the signal to a wifi signal and that signal is recognized as a wifi network connection.  Does anyone know if these 3g wifi base units are compatible with Ubuntu?  It seems like a simple solution to the usB dongle drama.

Daka

Some days better than others try changing the settings  // 

  try// one //at a time // handshake protocol may slow it down that's why they work faster on Linux  //  Tip get them unlocked ... above is good advice to // re network manager  /disable wireless

Have you Noticed How It Works With The Live CD // Re: you are Root// with the Live CD ;; When installed you are the user .May be A clue there ,Trying  to go through the Syslog to find it??

if it is a newer device then it has two names i will post that one soon

---

### Post by alexfish on 2009-12-15
The
default IP address provided is not a problem but the DNS (Domain Name Server) addresses of 10.11.12.13. and 10.11.12.14 seemingly coming from Vodafone are no use and their is no domain name resolution. The answer is to use fixed DNS servers and rather than use the Vodafone UK ones

OpenNic

Primary DNS 217.115.138.24 see attached
Alternative DNS 83.217.93.246 / No Ping 16 dec 2009

Pings show that the primary one is very fast although it is in Germany.


These can be set by using the Network Manager - System -> Administration -> Networking but they will not remain if you switch to an Ethernet or WiFi connection where new addresses are obtained so further work is needed. They are stored in /etc/resolv.conf which gets overwritten. so /etc/wvdial.conf also needs to be modified to have a line in the Default setting when using the Vodafone Connect Card is not providing DNS of

Auto DNS = 0 

TRY these settings

AT_OPSYS=0   #Only connect to GSM networks 
AT_OPSYS=1   #Only connect to UMTS networks 
AT_OPSYS=2   #If you have a choice - GPRS first 
AT_OPSYS=3   #If you have a choice &#8211; UMTS first 
AT_OPSYS=4   #Which ever network you connect to stay with it. 
AT_OPSYS=5   #Automatic &#8211; let V3G decide

Spot the difference  vodafone on the right

---

### Post by lpmb on 2009-12-15
Guys;

For the Vodafone UK / Huawei E220 modem (contract) in 9.10 (fully patched)

The solution is to use the following commands in terminal

sudo rmmod usb-storage (you will have to enter your login password)
sudo modprobe usbserial vendor=0x12d1 product=0x1003

Other products and vendors codes can be found at the sites cited earlier in the thread.


I can confirm two things:

1.  It does NOT work when booting 9.10 off a USB stick - the usb-storage is in use and cannot be rmmod out

2. it DOES work for me using a hard disk boot.  I'm online now with no popups and no disconnects.

So this gets me to where I need to be at least - with thanks to all who contributed to my eventual understanding.

Finally, as total noob to this, who is astounded every single time my new Ubuntu system boots up, I am pretty shocked at the moaning going on in this forum with threats of "never using Ubuntu again because of this".   Time for some people to grow up and ponder that this entire system/movement is FREE.  If you don't appreciate it, its definitely time to go back to Windows 7, which by all accounts is a perfectly acceptable system - but not free.  If you aren't prepared to put in the time, don't bother installing  - and don't whine - you might piss off the person who gave up time to develop it, for free.
:popcorn:

---

### Post by opentux on 2009-12-23
> **lpmb said:**
> 
For the Vodafone UK / Huawei E220 modem (contract) in 9.10 (fully patched)

The solution is to use the following commands in terminal

sudo rmmod usb-storage (you will have to enter your login password)
sudo modprobe usbserial vendor=0x12d1 product=0x1003

Thanks lpmb, your fix worked for my Vodafone Ireland / Huawei E220 modem with Ubuntu 9.10.

---

### Post by pdc on 2009-12-23
Hi OpenTux;

so do you have to enter these commands each time you turn your computer on again? .... to activate the modem?

---

### Post by alexfish on 2009-12-24
> **pdc said:**
> Hi OpenTux;

so do you have to enter these commands each time you turn your computer on again? .... to activate the modem?

Hi


    Here is a good part of a good guide to read
   

[LIST]
[*][SIZE=2][COLOR=Blue][User Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")[/COLOR][/SIZE]
[*][SIZE=2][COLOR=Blue][Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")[/COLOR][/SIZE]
[/LIST]

---

### Post by uidb4056 on 2010-01-04
Hi, I've found a solution that at least works for my E220, that worked flawlessly with previous releases but didn't work with Karmic x64 on my Lenovo W500 (kernel 2.6.31.16-generic). Found in Launchpad that this can be solved updating the firmware of modem this link will show you the way and includes a link on Launchpad with explanations ( [http://azizan.aiskosong.net/?p=458](http://azizan.aiskosong.net/?p=458) ).

I've switched to XP where the modem runs without problems, downloaded the firmware and applied it (only the firmware not the dashboard because Launchpad says is not necessary), after the update of firmware in XP I've checked if still runs on it and Yes! it still works and get as a side benefit that the connection now is at 7.2 GB instead of previous 3.6 GB.

Going back to Karmic again now at connection of the USB the internal disk is showed in desktop but , when starts the modem it was started OK but I was not able to navigate ...

Searching for a solution (apparently the problem was no DNS) I edited the wideband connection starting from terminal 'sudo nm-connection-editor' and in the Tab 'Adjusting IPV4' fill the field DNS Servers with the DNS used by XP and then this was solved.

I hope this can help

---

### Post by clearwood on 2010-01-23
Fellow ubuntu user

I had a similar problem tjeck this:
[http://www.glenscott.net/2009/12/01/how-to-fix-huawei-e620-usb-3g-modem-in-ubuntu-9-10-karmic-koala/](http://www.glenscott.net/2009/12/01/how-to-fix-huawei-e620-usb-3g-modem-in-ubuntu-9-10-karmic-koala/)

best regards

---

### Post by togril2010 on 2010-01-26
wow - I have spent a week trying to get my vodafone stick to work. I guess the problem is (to me) that there are many workarounds, and varying success rates.

This IS actually a big one for me, as I don't yet have the skill to know what I am safely:D doing in linux.

Can anyone suggest a USB mobile broadband (pre-paid NOT contract) available in Australia that plugs in to Karmic and just works? Is there a specific USB model? 

Thanks to everyone who has been trying top make it work. You are appreciated.

---

### Post by pdc on 2010-01-26
folks who have the latest kernel seem to stand the best chance; I understand;

so ...... I think 2.6.31.18 ............ I think?? 

so seems best to upgrade to latest kernel I suspect; as you may know, Karmic has had a chequered history;

I have personal success with older modems and operating systems: so a Huawei E220 and Vodafone Oz was fine with Ubuntu 8.10; as was a Huawei E160 (unlocked) with the 3 network; (the latter I bought from ebay_aus); you will find reports on this forum too of successful configurations with virgin oz; they need little tweaks as Virgin Oz uses PAP authentication rather than CHAP which all else seem to use;

Vodafone seem now to sell two types of modem: either by Huawei or ZTE; (the latter have -Z on their number);

tell us what you have done with your Australian Vodafone device ................

does lsusb give you 19d2:2000 ?

---

### Post by togril2010 on 2010-01-26
My vodafone dingle comes up as 12d1:1520 with lsusb. (a  K3765  ??)
I am on the latest update of Ubuntu as of yesterday, 2.6.31-17 generic.

I have basically tried a different version of usb_modeswitch, with some older libraries, altered my modeswitch.conf (betavine),  tried the commands at the start of this thread (I get** unrecognized option 'ttyUSB0'**  when i use the final command:*sudo ppd ttyUSB0* ,

 "altered a few other files" + broke my network manager completely (through ignorant  fiddling....:D!).

In the end went to a public library with wireless access and did a clean install of the OS yesterday from the live cd + all updates today.

The biggest issue is I need remote access for a Masters by Research - so  I would be happy changing my  dongle for anything that is known to work (pre paid).

---

### Post by togril2010 on 2010-01-27
OK -Still trying here:
lsusb reveals:
Bus 001    Device 007     ID 12d1:1520 Huawi Technologies blah.

So I ran the script by dj toonz as follows:

sudo rmmod usb-storage 
sudo modprobe -r option
sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=**0x1520** (as per my lsusb)
sudo pppd ttyUSB0 (or ttyUSB1?? as it is on bus 001??)
I get the unspecified option message.

Can anyone shed any light on this? Um...this is a nightmare, as have to come to another place just to write on this thread.

---

### Post by pdc on 2010-01-27
Hi togril;

so with linux, it sees your vodafone device as a CD-ROM; and you need to flip it:

if you plug the device in, does it create an icon on your desktop?

If so, RIGHT-CLICK on the icon;

select EJECT from the drop-down menu?

(if you have got this far, and now open a terminal, and type lsusb you should see your device has flipped and now has the ID of 

> 0x12d1:0x1465 

If so ............ it should ....... configure up with Network Manager;

this page tells you how to configure on NM if you need that help;

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

(half-way down: Create a mobile broadband ...............)

other options are install wvdial but see how you get on above

---

### Post by togril2010 on 2010-01-28
Thanks, I had no luck with any of it, maybe it's the product type - BUT - It was suggested by another user - steveneddy- I got a MiFi device, a little wireless hub that also contains the payg sim....It works a treat:D.

So it's not really solved technically for me, but anyone else reading this having concerns, maybe think about a little wifi modem like theE5832. It's just hassle free...just connected and not too expensive (esp if you are thinking of getting a dongle anyway).

---

### Post by davidtrounce on 2010-01-29
Dear John,

I followed your instructions for the same usb stick on my Ubuntu 9.04 and all installed well. However, my computer still sees my usb stick as a data stick and puts an icon on the desktop, rather than see it as a modem and have it appear in ym network manager.

Any suggestions?

---

### Post by pdc on 2010-01-29
.......... not sure who the "Dear John" is .......... !!!!!!!!!!!!!!

............ but if you go back to post #2 in this long thread ..

> open a terminal up

Applications , Accessory , Terminal

then copy & paste these

[B]sudo rmmod usb-storage

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001[/B]


and then type

> ls /dev/ttyUSB*

do you get any results like .... ttyUSB0 and ttyUSB1 and ttyUSB2

---

### Post by st0nes on 2010-03-01
Doesn't work for me.  This is enormously frustrating; internet access is absolutely critical!

I couldn't follow the terminal instructions because of the following errors:-
> mark@addy-laptop:~$ sudo rmmod usb-storage
[sudo] password for mark: 
mark@addy-laptop:~$ sudo modprobe -r option
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module option is in use.
mark@addy-laptop:~$ sudo modprobe -r usbserial
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module usbserial is in use.
mark@addy-laptop:~$ 
mark@addy-laptop:~$ sudo modprobe usbserial vendor=0x12d1 product=0x1001
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
mark@addy-laptop:~$ sudo pppd ttyUSB0
mark@addy-laptop:~$
According to network manager I am connected to Vodacom default, but I cannt access any web pages.  What Earthly use is that?  They really should not have released Karmic with such a critical component broken.  It's been 4 months since then and it still isn't fixed!

---

### Post by SecretCode on 2010-03-01
If Network Manager says you are connected, you may in fact be connected.

But you may not have got DNS servers. Vodacom is particularly unreliable on this - **on both Windows and Ubuntu**, I find that on 50% of days I have to try 5 to 10 times to connect before I (a) connect and (b) get DNS servers. 

If you can connect, type 
```
cat /etc/resolv.conf
```
to see what name servers were assigned. If it just says 'generated by networkmanager' with no IP addresses listed, disconnect and reconnect until Vodacom cooperates.

If IP addresses for name servers are shown, try a ping or two to see if names can be resolve and hosts reached.

---

### Post by st0nes on 2010-03-05
> **dj-toonz said:**
> My How To I must of posted at least 100 times and worked for every body

Not for me.  I've tried it with 3565-Z and E160, neither of which work at all.  Whenever I enter a modprobe command I get this:-
```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.

```

---

### Post by st0nes on 2010-03-07
> **SecretCode said:**
> If Network Manager says you are connected, you may in fact be connected.

OK, I can't get that far anymore.  I've tried so many "solutions" and workarounds I may have broken something else.  The modem is there and recognised as such--here is the output of lsusb:-
```
Bus 001 Device 008: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 002: ID 5986:0200 Acer, Inc OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
So how do I get network manager to use the damn thing?  Do you know what the correct settings for Vodacom are?  I'm getting incredibly frustrated by this.  If a solution has not been found by Wednesday, I'm going to reinstall windows because I REQUIRE internet access to do my work.

I can't believe the incompetence Canonical have demonstrated.  This bug was known before Karmic was released and four months later has STILL not been fixed!

---

### Post by SecretCode on 2010-03-07
> **st0nes said:**
> I'm getting incredibly frustrated by this.
I think that to survive with computers, you have to be a bigot one way or the other, so you can overlook the frustrations that any one supplier / architecture brings. ;)

> **st0nes said:**
> If a solution has not been found by Wednesday, I'm going to reinstall windows because I REQUIRE internet access to do my work.
I strongly recommend you install Windows one way or another - dual boot or virtualbox guest (I have both, and I use the vbox guest a lot - yes, my E220 works in it) - until you are absolutely confident in your Linux installation.



Now, to actual help ... can you run 
```
tail -f -n 50 /var/log/messages | egrep -i '(ppp)|(usb)'
```
(this will monitor and display new messages in the messages log)

- then plug in the E220, then (if it appears in the network manager drop down within a minute or so) try to connect. And post the output here.

If the mobile broadband option appears in the network manager menu at all, then I think you're in the same position as me, and it may be an intermittent Vodacom problem. If it doesn't (although it seems that it did before), then there are other options for getting it recognised.

---

### Post by dominic.rsa on 2010-03-15
I was having this problem on my desktop (Strangely not on my laptop) both running Karmic.

My temporary fix on the desktop is to open Places -> Computer when it tries to mount the dongle as a filesystem, then right click on the CDROM displayed and left click on Safely Remove....

Then try and connect the 3G via Network Manager.

Worked for me and a pretty easy and quick work around for now.

---

### Post by NiksaVel on 2010-04-03
Maybe a bit off topic, but I just thought I add that I've played around a bit with openSUSE 11.2 today and the modem works flawlessly there...  both as data medium and a 3g modem (mine is recognized as huawei e620)...

Maybe smeone can compare notes? :)

---

### Post by Goedman on 2010-04-15
Dear Linux gugu's,

I was happily using a Vodafone Huawei E220 modem to get connected to internet until I upgraded to ubuntu 9.10. 

Now, how embarresing is this, I am using XP to connect to the forum and beg for help. 

I have tried many of the suggestions on the forum short of extensive terminal progamming and nothing worked so far. The "pppoeconf" little wizard didn't pick up the modem either. 

I am running Karmic on an ACER laptop 5230E. I have read about upgrading to the latest Kernel - but how do I do that if my modem only works in XP? 

Also there is no connection icon top right of my screeen that everyone else tends to see.

Worried regards.

---

### Post by alexfish on 2010-04-15
hi goedman


first steps will be to see how it is configuring with Ubuntu



Boot up the computer without the modem connected

Open up a terminal and enter the following

Code:

tail -f /var/log/syslog

tail is a command which outputs the last 10 lines of a file, with the -f option it continues to monitor the file and keeps outputing any further additions appended to the file in real time.

now plug the modem in,and give the system time to settle and monitor any changes in the syslog

open up another terminal and enter this command

Code:

lsusb

then if a device or file etc shows up on the desktop, rightclick on the device and eject or safely remove the device

enter the lsusb command again ,
the device id's may have changed, 
if this is the case then you should be able to configure the device with the Network Manager

also check if the device has been detected and any ports allocated by using this command from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 

if the device is not configuring after the above then post all the results of the outputs from the terminals, from this it may be possible to determine what to do next

 do you have usb modeswitch or ozerocdoff installed or even possibly vmc
 can you give details of which method you where connecting to the internet prior to and after the upgrade, IE, PPP with the pon, wvdial,script etc

also could you say if this is a 3565 device or the E220 device

regards

alexfish

---

### Post by pdc on 2010-04-15
E220 works on some folks' computers .............


[http://ubuntuforums.org/showthread.php?t=1440587](http://ubuntuforums.org/showthread.php?t=1440587)

---

### Post by Goedman on 2010-04-15
Thanks very much alexfish, (you guru's are incredibly patient with us lower lifeforms)

Yes it is a Vodafone Huawei E220 modem.

I actually still can log onto the internet with my desktop, running Jaunty but I am away from home at the moment. On my laptop I only have 

Karmic (installed from the magazine DVD) and my old version of XP.

I did go to the Draisberghof website but got intimidated when I read all the instructions of how to download and install usb modeswitch and ozerocdoff. VMC I have never heard off, it sounds like a text editor.

I have run "tail -f -n 50 /var/log/messages | egrep -i '(ppp)|(usb)'" and if it is of any use these were the results:
jaco@jaco-laptop:~$ tail -f -n 50 /var/log/messages | egrep -i '(ppp)|(usb)'
Apr 15 14:21:39 jaco-laptop kernel: [  381.344072] usb 6-1: USB 

disconnect, address 4
Apr 15 14:21:39 jaco-laptop kernel: [  381.346049] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from 
ttyUSB0
Apr 15 14:21:39 jaco-laptop kernel: [  381.346141] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Apr 15 14:24:56 jaco-laptop kernel: [  578.248057] usb 6-1: new full speed USB device using uhci_hcd and address 5
Apr 15 14:24:57 jaco-laptop kernel: [ 578.406037] usb 6-1: configuration #1 chosen from 1 choice
Apr 15 14:24:57 jaco-laptop kernel: [  578.415860] scsi10 : SCSI emulation for USB 

Mass Storage devices
Apr 15 14:24:57 jaco-laptop kernel: [  578.416023] usb 6-1: USB disconnect, address 5
Apr 15 14:24:57 jaco-laptop kernel: [  579.240026] usb 6-1: new full speed USB device using uhci_hcd and address 6
Apr 15 14:24:58 jaco-laptop kernel: [  579.400056] usb 6-1: 

configuration #1 chosen from 1 choice
Apr 15 14:24:58 jaco-laptop kernel: [  579.410003] usb 6-1: GSM modem (1-port) converter now attached to 

ttyUSB0
Apr 15 14:24:58 jaco-laptop kernel: [  579.416027] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Apr 15 14:24:58 jaco-laptop kernel: [  579.418788] scsi13 : SCSI emulation for USB Mass Storage devices
Apr 15 14:33:04 jaco-laptop kernel: [ 1065.576053] usb 6-1: 

USB disconnect, address 6
Apr 15 14:33:04 jaco-laptop kernel: [ 1065.578142] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from 

ttyUSB0
Apr 15 14:33:04 jaco-laptop kernel: [ 1065.578235] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Apr 15 14:33:36 jaco-laptop kernel: [ 1097.560030] usb 6-1: new full speed USB device using uhci_hcd and address 7
Apr 15 14:33:36 jaco-laptop kernel: [ 1097.723105] usb 6-1: configuration #1 chosen from 1 choice
Apr 15 14:33:36 jaco-laptop kernel: [ 1097.734065] scsi14 : SCSI emulation for USB 

Mass Storage devices
Apr 15 14:33:36 jaco-laptop kernel: [ 1097.735155] usb 6-1: USB disconnect, address 7
Apr 15 14:33:37 jaco-laptop kernel: [ 

1098.552028] usb 6-1: new full speed USB device using uhci_hcd and address 8
Apr 15 14:33:37 jaco-laptop kernel: [ 1098.715097] usb 6-1: 

configuration #1 chosen from 1 choice
Apr 15 14:33:37 jaco-laptop kernel: [ 1098.727219] usb 6-1: GSM modem (1-port) converter now attached to 

ttyUSB0
Apr 15 14:33:37 jaco-laptop kernel: [ 1098.729234] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Apr 15 14:33:37 jaco-

laptop kernel: [ 1098.742261] scsi17 : SCSI emulation for USB Mass Storage devices
Apr 15 14:37:28 jaco-laptop kernel: [ 1329.448055] usb 6-1: 

USB disconnect, address 8
Apr 15 14:37:28 jaco-laptop kernel: [ 1329.450174] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from 

ttyUSB0
Apr 15 14:37:28 jaco-laptop kernel: [ 1329.450267] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1

"Once 

connected:" Apr 15 14:37:28 jaco-laptop kernel: [ 1329.448055] usb 6-1: USB disconnect, address 8
Apr 15 14:37:28 jaco-laptop kernel: [ 

1329.450174] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Apr 15 14:37:28 jaco-laptop kernel: [ 1329.450267] 

option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Apr 15 14:40:33 jaco-laptop kernel: [ 1514.448027] usb 6-1: new full 

speed USB device using uhci_hcd and address 9
Apr 15 14:40:33 jaco-laptop kernel: [ 1514.606154] usb 6-1: configuration #1 chosen from 1 choice
Apr 15 14:40:33 jaco-laptop kernel: [ 1514.616043] scsi18 : SCSI emulation for USB Mass Storage devices
Apr 15 14:40:33 jaco-laptop kernel: [ 

1514.616186] usb 6-1: USB disconnect, address 9
Apr 15 14:40:34 jaco-laptop kernel: [ 1515.440033] usb 6-1: new full speed USB device using 

uhci_hcd and address 10
Apr 15 14:40:34 jaco-laptop kernel: [ 1515.598156] usb 6-1: configuration #1 chosen from 1 choice
Apr 15 14:40:34 jaco-laptop kernel: [ 1515.608145] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
Apr 15 14:40:34 jaco-laptop kernel: [ 1515.613326] 

usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
Apr 15 14:40:34 jaco-laptop kernel: [ 1515.616398] scsi21 : SCSI emulation for USB 

Mass Storage devices

"When I safely remove the mass storage device:" there is no further communication?"



What I will do is follow your instructions and report back on those results when I get back.

Friendly regards,

Goedman

---

### Post by alexfish on 2010-04-15
hi

do try posting the outputs as mentioned, but do not install anything as yet , but also of note ,from your logs it shows

usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1

this would indicate the device has been configured as the modem, at this stage the network manager should see the device,i am presuming you have not yet ejected the device so try to make the connection with the network manager before doing so , although i am not sure if the correct port is been used, errors may occur whilst trying to connect

also which kernel are you using

regards

alexfish

---

### Post by Goedman on 2010-04-15
Hello friendly alexfish,

I installed Karmic directly from a DVD in the Ubuntu magazine and therefore not the latest kernel - also I am not sure how to check which kernel I have installed?

I did boot up the computer without the modem connected and opened up the first terminal to enter the following Code:


"jaco@jaco-laptop:~$ tail -f /var/log/syslog

Apr 15 19:33:52 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:33:53 jaco-laptop anacron[1866]: Anacron 2.3 started on 2010-04-15

Apr 15 19:33:53 jaco-laptop anacron[1866]: Normal exit (0 jobs run)

Apr 15 19:33:55 jaco-laptop console-kit-daemon[1184]: WARNING: Couldn't read /proc/918/environ: Failed to open file '/proc/918/environ': No such file or directory

Apr 15 19:33:56 jaco-laptop anacron[1983]: Anacron 2.3 started on 2010-04-15

Apr 15 19:33:56 jaco-laptop anacron[1983]: Normal exit (0 jobs run)

Apr 15 19:34:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:34:21 jaco-laptop NetworkManager: Tried to set deprecated property gsm/band

Apr 15 19:34:21 jaco-laptop NetworkManager: Tried to set deprecated property gsm/band

Apr 15 19:34:43 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:35:23 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

"

This when I went to get a copy of the text file with your instructions on:

"

Apr 15 19:35:49 jaco-laptop ntfs-3g[3007]: Version 2009.4.4 external FUSE 27

Apr 15 19:35:49 jaco-laptop ntfs-3g[3007]: Mounted /dev/sda3 (Read-Write, label "DATA", NTFS 3.1)

Apr 15 19:35:49 jaco-laptop ntfs-3g[3007]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077

Apr 15 19:35:49 jaco-laptop ntfs-3g[3007]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sda3,blkdev,blksize=4096

Apr 15 19:36:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:37:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS "

This is what I observed once I plugged in the usb modem:


Apr 15 19:40:04 jaco-laptop kernel: [  391.504048] usb 6-1: new full speed USB device using uhci_hcd and address 3

Apr 15 19:40:04 jaco-laptop kernel: [  391.663014] usb 6-1: configuration #1 chosen from 1 choice

Apr 15 19:40:04 jaco-laptop kernel: [  391.741504] Initializing USB Mass Storage driver...

Apr 15 19:40:04 jaco-laptop kernel: [  391.742967] scsi6 : SCSI emulation for USB Mass Storage devices

Apr 15 19:40:04 jaco-laptop kernel: [  391.743119] usbcore: registered new interface driver usb-storage

Apr 15 19:40:04 jaco-laptop kernel: [  391.743123] USB Mass Storage support registered.

Apr 15 19:40:04 jaco-laptop kernel: [  391.743818] usb-storage: device found at 3

Apr 15 19:40:04 jaco-laptop kernel: [  391.743822] usb-storage: waiting for device to settle before scanning

Apr 15 19:40:04 jaco-laptop kernel: [  391.760059] usb 6-1: USB disconnect, address 3

Apr 15 19:40:05 jaco-laptop kernel: [  392.496027] usb 6-1: new full speed USB device using uhci_hcd and address 4
Apr 15 19:40:05 jaco-laptop kernel: [  392.655012] usb 6-1: configuration #1 chosen from 1 choice

Apr 15 19:40:05 jaco-laptop kernel: [  392.671106] scsi9 : SCSI emulation for USB Mass Storage devices

Apr 15 19:40:05 jaco-laptop kernel: [  392.675739] usb-storage: device found at 4

Apr 15 19:40:05 jaco-laptop kernel: [  392.675743] usb-storage: waiting for device to settle before scanning

Apr 15 19:40:05 jaco-laptop kernel: [  392.710356] usbcore: registered new interface driver usbserial

Apr 15 19:40:05 jaco-laptop kernel: [  392.710369] USB Serial support registered for generic

Apr 15 19:40:05 jaco-laptop kernel: [  392.710398] usbcore: registered new interface driver usbserial_generic
Apr 15 19:40:05 jaco-laptop kernel: [  392.710400] usbserial: USB Serial Driver core

Apr 15 19:40:05 jaco-laptop kernel: [  392.723824] USB Serial support registered for GSM modem (1-port)

Apr 15 19:40:05 jaco-laptop kernel: [  392.723868] option 6-1:1.0: GSM modem (1-port) converter detected

Apr 15 19:40:05 jaco-laptop kernel: [  392.723945] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0

Apr 15 19:40:05 jaco-laptop kernel: [  392.723954] option 6-1:1.1: GSM modem (1-port) converter detected

Apr 15 19:40:05 jaco-laptop kernel: [  392.724022] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1

Apr 15 19:40:05 jaco-laptop kernel: [  392.724037] usbcore: registered new interface driver option

Apr 15 19:40:05 jaco-laptop kernel: [  392.724039] option: v0.7.2:USB Driver for GSM modems

Apr 15 19:40:05 jaco-laptop modem-manager: (ttyUSB0) opening serial device...

Apr 15 19:40:05 jaco-laptop modem-manager: (ttyUSB0): probe requested by plugin 'Generic'

Apr 15 19:40:05 jaco-laptop modem-manager: (ttyUSB1) opening serial device...
Apr 15 19:40:05 jaco-laptop modem-manager: (ttyUSB1): probe requested by plugin 'Generic'

Apr 15 19:40:07 jaco-laptop modem-manager: (ttyUSB0) closing serial device...

Apr 15 19:40:07 jaco-laptop modem-manager: do_grab_port: plugin 'Generic' claimed to support tty/ttyUSB0 but couldn't: (0) Could not get port's sysfs file.

Apr 15 19:40:07 jaco-laptop modem-manager: (ttyUSB1) closing serial device...

Apr 15 19:40:07 jaco-laptop modem-manager: do_grab_port: plugin 'Generic' claimed to support tty/ttyUSB1 but couldn't: (0) Could not get port's sysfs file.

Apr 15 19:40:10 jaco-laptop kernel: [  397.673967] usb-storage: device scan complete

Apr 15 19:40:10 jaco-laptop kernel: [  397.676959] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2

Apr 15 19:40:10 jaco-laptop kernel: [  397.698935] sr1: scsi-1 drive

Apr 15 19:40:10 jaco-laptop kernel: [  397.699059] sr 9:0:0:0: Attached scsi CD-ROM sr1

Apr 15 19:40:10 jaco-laptop kernel: [  397.699122] sr 9:0:0:0: Attached scsi generic sg2 type 5

Apr 15 19:40:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS" 



This happened when I safely disconnected the usb HUAWEI%20Mass%20Storage.drive:


"Apr 15 19:44:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:45:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS" in other words almost nothing...



Then I opened up another terminal to enter this command:


"jaco@jaco-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 006 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jaco@jaco-laptop:~$ 

"

No device or file showed up on the desktop or on Computer.

This was all that printed in the first terminal:

"
Apr 15 19:42:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:43:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:44:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:45:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS "

This was the second lsusb command, but it looks very similar to the first one:

"jaco@jaco-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 006 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jaco@jaco-laptop:~$" 



Still no signal indicated on the top right hand side of the desktop. I checked the Vodacom information in the Network Manager but still no joy with a logon. (bit disappointing)



To check if the device has been detected and any ports allocated I used this command on the second terminal:


"jaco@jaco-laptop:~$ dmesg | grep -e "modem" -e "tty"
[    0.001385] console [tty0] enabled
[  392.723824] USB Serial support registered for GSM modem (1-port)
[  392.723868] option 6-1:1.0: GSM modem (1-port) converter detected
[  392.723945] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
[  392.723954] option 6-1:1.1: GSM modem (1-port) converter detected
[  392.724022] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
[  392.724039] option: v0.7.2:USB Driver for GSM modems
jaco@jaco-laptop:~$ "


On the first terminal it detected the following:


"Apr 15 19:59:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 19:59:15 jaco-laptop NetworkManager: Tried to set deprecated property gsm/band

Apr 15 19:59:15 jaco-laptop NetworkManager: Tried to set deprecated property gsm/band

Apr 15 20:00:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS 

Apr 15 20:01:13 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS "



All new attempts to wake up the mobile broadband was unsuccessful. I rebooted the system and went through everything again with the same result.



Thankful regards,



Goedman

---

### Post by alexfish on 2010-04-16
hi
 

 from the information posted this is what I can determine  so far


    The dmesg | grep -e "modem" -e "tty"  shows the modem is registered at the two ports I have highlighted the important in blue, and also the driver has been configured  as in the last line, see below
 

 [ 0.001385] console [tty0] enabled
[ 392.723824] USB Serial support registered for GSM modem (1-port)
[ 392.723868] option 6-1:1.0: GSM modem (1-port) converter detected
[ 392.723945] usb 6-1: GSM modem (1-port) [COLOR=Blue]converter now attached to ttyUSB0[/COLOR]
[ 392.723954] option 6-1:1.1: GSM modem (1-port) converter detected
[ 392.724022] usb 6-1: GSM modem (1-port) [COLOR=Blue]converter now attached to ttyUSB1[/COLOR]
[ 392.724039] [COLOR=Blue]option: v0.7.2:USB Driver for GSM modems[/COLOR]
 

 so it would be reasonable to assume a connection can be made with the Network Manager, So when you see this, try to make the connection and do not eject anything from the desktop,

 

 Your outputs show the network manager trying to set the deprecated property
 

 this I would expect if the Network Manager has made the connection,s check the system/logfile viewer , messages . This is what I would expect to see in front of your outputs or something similar.

 

 kernel: [ 294.723705] usb 1-5: configuration #1 chosen from 1 choice

[COLOR=#000080]kernel: [ 294.746196] option 1-5:1.0: GSM modem (1-port) converter detected
kernel: [ 294.746512] usb 1-5: GSM modem (1-port) converter now attached to [/COLOR][COLOR=#000000][SIZE=2]**ttyUSB0**[/SIZE][/COLOR][COLOR=#000080]
[/COLOR]
[COLOR=#000080]kernel: [ 294.748622] option 1-5:1.1: GSM modem (1-port) converter detected
kernel: [ 294.748902] usb 1-5: GSM modem (1-port) converter now attached to [/COLOR][COLOR=#000000][SIZE=2]**ttyUSB1**[/SIZE][/COLOR]



kernel: [ 294.752541] scsi8 : SCSI emulation for USB Mass Storage devices
kernel: [ 294.754201] scsi9 : SCSI emulation for USB Mass Storage devices

[COLOR=#000080]kernel: [ 299.755772] scsi 8:0:0:0: [/COLOR][COLOR=#000000][SIZE=2]CD-ROM [/SIZE][/COLOR][COLOR=#000080]HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
kernel: [ 299.757881] scsi 9:0:0:0:[/COLOR][COLOR=#000000][SIZE=2]Direct-Access [/SIZE][/COLOR][COLOR=#000080]HUAWEI MMC Storage 2.31 PQ: 0 ANSI: 2[/COLOR]

[COLOR=#000080]kernel: [ 299.781429] sr2: scsi-1 drive
kernel: [ 299.781995] sr 8:0:0:0: Attached scsi generic sg4 type 5
kernel: [ 299.782669] sd 9:0:0:0: Attached scsi generic sg5 type 0
kernel: [ 299.802756] sd 9:0:0:0: [sdc] Attached SCSI removable dis[/COLOR]k

pppd[8879]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
pppd[8879]: pppd 2.4.5 started by root, uid 0
pppd[8879]: Using interface ppp0

pppd[8879]: Connect: ppp0 <--> [COLOR=#000000][SIZE=2]**/dev/ttyUSB0**[/SIZE][/COLOR] (or [COLOR=#000000][SIZE=2]**ttyUSB1 or 2**[/SIZE][/COLOR])

[COLOR=#000080]kernel: [ 324.448138] PPP BSD Compression module registered
kernel: [ 324.475252] PPP Deflate Compression module registered[/COLOR]

pppd[8879]: Could not determine remote IP address: defaulting to 10.64.64.64

pppd[8879]: local IP address 10.91.124.131
pppd[8879]: remote IP address 10.64.64.64
[COLOR=#000080]
pppd[8879]: [/COLOR][COLOR=#000000][SIZE=2]**primary.. **[/SIZE][/COLOR][COLOR=#000080]DNS address 10.206.65.68
pppd[8879]: [/COLOR][COLOR=#000000][SIZE=2]**secondary**[/SIZE][/COLOR][COLOR=#000080] DNS address 10.206.65.68
[/COLOR]

  then the following outputs may appear after the above,
 

 Apr 15 19:34:21 jaco-laptop NetworkManager: Tried to set deprecated property gsm/band
Apr 15 19:34:21 jaco-laptop NetworkManager: Tried to set deprecated property gsm/band
Apr 15 19:34:43 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS
Apr 15 19:35:23 jaco-laptop wpa_supplicant[1733]: CTRL-EVENT-SCAN-RESULTS



so do please check the logfile messages again , as what you are saying and what is been shown in the logfiles etc is not adding up / Or have you been using a different modem


I am going to shot in the dark here , if the connection is been attempted by the network manager and then appears to have made the connection, then there is a possibility the primary and secondary server addresses have not been returned, check this from the log file, there is a way around this, 


Added
There is one thing I have also noted , you mentioned vodacom and this thread relatates to vodafone, so double check your ISP connections in the network manager


regards


alexfish

---

