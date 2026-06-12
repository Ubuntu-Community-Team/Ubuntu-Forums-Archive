---
title: "Gateway laptop wireless problems!"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by XSAINTS on 2010-10-20
Dear all,
I used to have windows Vista. I decided to install ubuntu and successfully installed Ubuntu 10.04 LTS. Everything is running ok, but wireless! There is no indication of wireless at all.
Following some forum answers I thought this would be useful for you to look at the problem:
                     p { margin-bottom: 0.08in; }  lshw -C Network  
 WARNING: you should run this program as super-user.  
   *-network UNCLAIMED      
        description: Ethernet controller 
        product: Marvell Technology Group Ltd.  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        version: 03  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=0  
        resources: memory:f6000000-f600ffff memory:f4000000-f400ffff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:06:00.0  
        logical name: eth0  
        version: 01  
        serial: 00:e0:b8:e4:a4:00  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list rom ethernet physical  
        configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=10.101.28.13 latency=0 multicast=yes  
        resources: irq:28 ioport:4000(size=256) memory:fa200000-fa200fff memory:c0000000-c001ffff(prefetchable)  
 

 lspci -nn  
 00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)  
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)  
 00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)  
 00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)  
 00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)  
 00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)  
 00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)  
 00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)  
 00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)  
 00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)  
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)  
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)  
 00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)  
 00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)  
 00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)  
 02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a08] (rev 03)  
 06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01) 



Please give your suggestions what to do here.
Thank you in advance

---

### Post by chili555 on 2010-10-20
Here is your wireless device:> 02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a08] (rev 03) Here is a series of posts that describe using ndiswrapper and the Windows XP driver to get it going: [http://wwww.ubuntuforums.org/showthread.php?t=575785](http://wwww.ubuntuforums.org/showthread.php?t=575785)

Please post back if you need additional guidance.

---

### Post by XSAINTS on 2010-12-26
> **chili555 said:**
> Here is your wireless device:Here is a series of posts that describe using ndiswrapper and the Windows XP driver to get it going: [http://wwww.ubuntuforums.org/showthread.php?t=575785](http://wwww.ubuntuforums.org/showthread.php?t=575785)

Please post back if you need additional guidance.

Hi, sorry for quite a late reply!
I went through the link that you gave, but I couldn't do anything!
Could you please, just quote here what to do step by step!
I would highly appreciate it!
thanks a lot...

---

### Post by chili555 on 2010-12-28
Do you still have the install CD you used to install Ubuntu? We might need it. First, open Applications > Accessories > Terminal and do:```
ndiswrapper -v
```If it reports the version, we are halfway done! Here is an example:> $ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.35-24-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       2.6.35-24-generic SMP mod_unload modversions 686 

Next, do you have the driver CD that came with your wireless device? What is on it? When you drop the CD in the tray when booted into Ubuntu, drag and drop the files to your desktop. What kind of file is it? If it's a zip file, right-click it and select 'Extract Here.' We are looking for a folder containing the .inf file. Please tell us what you have.

---

### Post by XSAINTS on 2010-12-29
Thanks a lot for your reply!
after the command ndswrapper -v I got the following:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.35-24-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       2.6.35-24-generic SMP mod_unload modversions 686 

and when I followed your next directions I got a folder for wireless drivers:

1st folder had .pdf, 2 .txt and 1 .exe files
2nd folder had 1 .txt and 1 .exe

thats it, no .inf file!

Any other suggestions mate?
cheers!:p

---

### Post by chili555 on 2010-12-30
Here is a file that contains the items you need. Place the file on your desktop. Right-click it and select 'Extract Here.' Now, in a terminal, do:```
cd Desktop/WN511T-ver30
sudo ndiswrapper -i NetMW14x.inf
sudo ndiswrapper -a 11ab:2a08 netmw14x
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
```Now is your wireless working?

---

### Post by XSAINTS on 2011-01-03
Thanks a lot foe guidance! 
The driver is installed. But I don't know still, whether my wireless working or not...

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:e4:a4:00  
          inet addr:10.101.179.69  Bcast:10.101.179.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fee4:a400/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:204997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:199042244 (199.0 MB)  TX bytes:26388138 (26.3 MB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10176 (10.1 KB)  TX bytes:10176 (10.1 KB)

I got this in terminal for ifconfig. does it say anything...
Thanks bro!

---

### Post by chili555 on 2011-01-04
What does this tell us?```
ndiswrapper -l
```

---

### Post by XSAINTS on 2011-01-05
> **chili555 said:**
> What does this tell us?```
ndiswrapper -l
```

 ndiswrapper -l
agrmdv32 : driver installed
autorun : invalid driver!
netmw14x : driver installed
osfilter : invalid driver!
sfpat : invalid driver!
sfpat2k : invalid driver!
sfpatlh : invalid driver!
sfpatxp : invalid driver!


heheh, I got the driver now! thanks a looooooooooooooooooooooooooooooooooooot!:lolflag:

---

### Post by XSAINTS on 2011-01-05
BUT STILL  NOT WORKING.....!:popcorn:

---

### Post by chili555 on 2011-01-05
So, do I take that to mean you've fixed it and you are now another satisfied client?

---

### Post by chili555 on 2011-01-05
Please do:```
sudo ndiswrapper -r autorun
sudo ndiswrapper -r osfilter
sudo ndiswrapper -r sfpat
sudo ndiswrapper -r sfpat2k 
sudo ndiwrapper -r sfpatlh
sudo ndiswrapper -r sfpatxp 
sudo ndiswrapper -r agrmdv32
```Now insert the device and run and post:```
ndiswrapper -l
```

---

### Post by XSAINTS on 2011-02-03
Dear, I did as u said: and got the following:


~$ sudo ndiswrapper -r autorun
couldn't delete /etc/ndiswrapper/autorun: No such file or directory
xsaints@xsaints-laptop:~$ sudo ndiswrapper -r osfilter
xsaints@xsaints-laptop:~$ sudo ndiswrapper -r sfpat
xsaints@xsaints-laptop:~$ sudo ndiswrapper -r sfpat2k 
xsaints@xsaints-laptop:~$ sudo ndiwrapper -r sfpatlh
sudo: ndiwrapper: command not found
xsaints@xsaints-laptop:~$ sudo ndiswrapper -r sfpatxp 
xsaints@xsaints-laptop:~$ sudo ndiswrapper -r agrmdv32
xsaints@xsaints-laptop:~$ sudo ndiwrapper -l
sudo: ndiwrapper: command not found
xsaints@xsaints-laptop:~$

---

### Post by XSAINTS on 2011-02-03
> **chili555 said:**
> So, do I take that to mean you've fixed it and you are now another satisfied client?

Hummm, not so much! But still learning Ubuntu, step by step!
With a help of people like you!...appreciate it very much!
Thanks anyway

---

### Post by jhargis1012 on 2011-02-03
This is crazy, I'm having this same issue. I even had the wireless working on my machine in a previous installation of Ubuntu. But now, using the same instructions and same driver, no luck. I think it might have something to do with running in 64 bit now.

---

### Post by chili555 on 2011-02-04
> xsaints@xsaints-laptop:~$ sudo ndiwrapper -l
sudo: ndiwrapper: command not found
It's not ndiwrapper; it's ndi[COLOR="Red"]**s**[/COLOR]wrapper. In order to diagnose what is going wrong, I need to see:```
sudo ndiswrapper -l
```That's a lower case L for 'list.' Please run and post.

---

### Post by chili555 on 2011-02-04
> **jhargis1012 said:**
> This is crazy, I'm having this same issue. I even had the wireless working on my machine in a previous installation of Ubuntu. But now, using the same instructions and same driver, no luck. I think it might have something to do with running in 64 bit now.Perhaps. Did you use the 64-bit XP .inf file? What does this tell us?```
sudo ndiswrapper -l
```Thanks.

---

### Post by sahilsameer on 2011-02-04
if u are having the wireless driver for windows
download attachments
install them by double click
if any errors
then install all other packages and finally install the error file
after the three files are installed in system administration u will find Windows Wireless Drivers
then insert driver cd or open the driver file
there will be a.inc file
click install driver and locate all the.inc file ( as much as there are)
insert the device
finally see whether hardware present is yes in windows wireless drivers
then remove all other drivers other than it
restart
have fun
download from 
[http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download)

---

### Post by jhargis1012 on 2011-02-07
```
jeremy@jeremy-MT6458:~$ sudo ndiswrapper -l
netmw14x : invalid driver!
jeremy@jeremy-MT6458:~$ 
```


Yeah, I've tried working with several other driver downloads (64 bit specific ones), but none of them were helpful because they were setup executables rather than self-extracting archives.

Any tips would be greatly appreciated, thanks.

---

### Post by rsperson on 2011-12-10
I am having the same result
netw14x : invalid driver

I am also running 64bit Ubuntu 11.10

The device is built in - not something to "insert"  :)

---

### Post by chili555 on 2011-12-11
Do the system logs tell us why it's invalid?```
sudo cat /var/log/syslog | grep ndis
```May I see:```
lspci -nn | grep 0280
```Thanks.

---

