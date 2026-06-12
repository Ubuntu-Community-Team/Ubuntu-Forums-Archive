---
title: "wna 1000m wireless adapter keeps asking for wifi password"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by D2414 on 2013-01-16
64 bit. internal wifi works. trying to get the usb adapter to work on a desktop without internet connection


lspci -nn 
lsusb
ndiswrapper -l
rfkill list all                      

ubuntu@ubuntu:~$  lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 008: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 004: ID 064e:f203 Suyin Corp. 
Bus 001 Device 005: ID 0781:5530 SanDisk Corp. Cruzer
Bus 002 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 007: ID 08ec:0015 M-Systems Flash Disk Pioneers Kingston DataTraveler ELITE
ubuntu@ubuntu:~$ ndiswrapper -l
ubuntu@ubuntu:~$ rfkill list all 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$

---

### Post by chili555 on 2013-01-16
Probably the easiest way is, on the other PC, install linux-backports-modules-cw. The exact version depends on the Ubuntu version; if it's 12.10, then 3.6-quantal-generic.

Without an Internet connection will be very tough. Are you able to download and transfer files on a USB key or similar?

---

### Post by D2414 on 2013-01-16
Its not working on ubuntu 12.04 or 12.10. yes  i have the usb stick ready where do i download the quantal. I figured ill try to find the fix on this through this pc then copy what i did onto usb

---

### Post by D2414 on 2013-01-16
Ok so im now using 12.04 on both. i just made a 16 gb ubuntu 12.04 drive so any changes you help me with i can use on the other computer.

---

### Post by chili555 on 2013-01-16
So your new partition or drive is also 12.04 and 64-bit the same as the desktop PC? If so, we are going to try a slick trick. Please do:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic 
```Make careful note of all the packages it installs. Here is an example from my machine; yours *will* be different. All of them will be stored in /var/cache/apt/archives/.

> chili@Think410:~$ sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
[sudo] password for chili: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  [COLOR="Red"]linux-backports-modules-cw-3.6-3.5.0-21-generic[/COLOR]
The following NEW packages will be installed:
  [COLOR="Red"]linux-backports-modules-cw-3.6-3.5.0-21-generic
  linux-backports-modules-cw-3.6-quantal-generic[/COLOR]
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,973 kB of archives.
After this operation, 11.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

Next do:```
sudo nautilus /var/cache/apt/archives/
```Drag and drop all the packages that were installed by backports on to a USB drive. Now transfer them to the desktop of the other machine and install with:```
cd Desktop
sudo dpkg -i *.deb
```If there are any problems, post back soon as Mrs. Chili and I are going to lunch.

---

### Post by D2414 on 2013-01-16
So it wouldnt work so now i got a wna3100 and i am connected to internet via ethernet to download anything i need. i read all other threads for this adapter and nothing so now im hoping i can get it to work this way
lspci -nn 
lsusb
ndiswrapper -l
rfkill list all 			 		


deb@Home:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) [1022:9609]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200] [1002:9710]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
deb@Home:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
deb@Home:~$ ndiswrapper -l
deb@Home:~$ rfkill list all 
deb@Home:~$

---

### Post by chili555 on 2013-01-17
> So it wouldnt workThat's it? 'it wouldnt work' is all you can say? Have you decided there is no way that even Chili can fix what didn't work???

Frankly, the WNA3100 is even harder, especially on 64-bit. There are dozens of 100-post threads about WNA3100 and I suggest you start there.

If the computer with the NetGear WNA1000M is hooked up to the ethernet, then simply do:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```

---

### Post by bogan on 2013-01-18
Hi!, **D2414**,

When you get the Wifi Password requester on the computer with the two Realtek adapters, does it list them both on a drop-down menu in the requester?

If so, you need to select the correct one before clicking on the 'Connect' button.

Hi!, **chili555**,

I see from the OP's original listing that the WNA1000 is a Realtek RTL8188CUS, and that computer also has a Pci Realtek RTL8191SEvA.

Whereas the later listing does not show the Pci Adapter and a USB WNA 3100(v1) as a BCM43231.

Does your recommended install of:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
``` serve to deal with the stated problem of the title with the Realtek Adapter or the Broadcom?.

The reason I ask is that with 12.10 I continue to have unpredictable difficulties with both connecting and dropping the network connection with a setup similar to the first and using the r8172 driver that comes with the kernal installation.

Would it help to install the backports module in my case?

My internal Adapter is a Realtek USB RTL8191SU and the USB Dongle is a Realtek RTL8188S [According to the Network manager, and a RTL8188SU according to lshw].

Chao!,** bogan**.
[ If I should start another thread, please say so.

---

### Post by chili555 on 2013-01-18
> Does your recommended install of:
Code:

sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic

serve to deal with the stated problem of the title with the Realtek Adapter or the Broadcom?.
It was to install a better and, hopefully, working driver for his Realtek RTL8188CUS. It would probably fix his internal Realtek RTL8191SEvA as well, actually.

The Broadcom is a whole different nightmare that has been discussed quite a few times elsewhere on this forum. While the Realteks are difficult, the Broadcom is super-extra maddeningly difficult.

---

### Post by bogan on 2013-01-18
Hi!, **chili555**,

Thanks for the PM, ffrustrating, isn't it?

After installing the backports-module with apt-get, do I need to run 'dpkg -i' to activate it? as you described, or is that only if copying it to a PC without internet?

My RTL8191SU sometimes, but not often, is already connected before I log-in, other times, more often, it takes 5 minutes of scanning and asking for the Wifi password, before connecting.

Chao!.** bogan**.

---

### Post by chili555 on 2013-01-18
> After installing the backports-module with apt-get, do I need to run 'dpkg -i' to activate it? Nope,that's already done.> as you described, or is that only if copying it to a PC without internet?Exactly.

Does a reboot help? Now that backports is installed, do you have the same symptom? If so, we're probably at the point where your own new thread is in order.

---

### Post by bogan on 2013-01-18
Hi!, **chili555**,

You Posted:```
Does a reboot help? Now that backports is installed, do you have the same symptom? 
```I have run into a problem, unconnected with Networking, which makes my HDD unacessable, with the result I have only been able to try the backports procedure on my 12.10 USB.

From 7 reboots with the backports installed, 4 connected within 6 seconds of logging in, 1 was already connected, and 1 gave a: " none - disconnected" message, followed by a request for the Password and connected 25 seconds later. [ These were all without the USB dongle].
 The 7th was with the dongle plugged in and it crashed on log-in, the launcher, Desktop background and top panel disappearing. except for the clock & calender. I have no idea what the cause of the last was, and the "none" message instead of "network" or " CYBERGRANS" I have never seen before. [B]

sudo lshw -C network[/B] shows the r8712u driver still in use. Is that what you expected?

The above summary is certainly better than I have previously managed to average, and I will Post again when I get the HDD sorted out.

Chao! and Thanks!, **bogan**.

---

### Post by bogan on 2013-01-22
Hi!,** chili555**,

Having sorted my HDD problem i have installed the backports procedure in three 12.10 installations and one 12.04.

Whilst i have had what seems to be fewer problems connecting and 'dropping' with all of them, I have still had some.

The difficulty I have is that the performance of both the internal RTL8191SU and the RTL8188U Dongle has always been very variable and unpredictable. { I only use the later to force recognition of both, when it fails to recognize the RTL8191.}

So, as my impression is that things are better, I am going to leave them for a week or two before deciding whether to open a new thread.

Thanks for the aid. 
Could you explain what 'backports-modules-cw' actually does, should it still be using the r8712u driver ??

Chao!, **bogan.**

---

### Post by chili555 on 2013-01-22
> Could you explain what 'backports-modules-[COLOR="Red"]cw[/COLOR]' actually does, should it still be using the r8172u driver ??There is a package of newer updated drivers, including Realtek, called compat-wireless. This is just the Ubuntu-customized version.>  I only use the later to force recognition of both, when it fails to recognize the RTL8191Wow! You shouldn't have to use one device to force recognition of another. The internal ought to be recognized and start automatically. If you'd care to trouble-shoot, reboot without the USB and post:```
lsmod | grep rtl
dmesg | grep rtl
```

---

### Post by bogan on 2013-01-22
Hi!, **chili55**5,

'lsmod | grep rtl' gives no output.```
alan@alan-MS-7616:~$ dmesg | grep rtl
[   17.430623] r8712u: register rtl8712_netdev_ops to netdev_ops
[   18.023491] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
alan@alan-MS-7616:~$ lsmod | grep -e rt -e r8
parport_pc             31969  0 
r8712u                162516  0 
parport                40754  3 parport_pc,ppdev,lp
r8169                  55977  0 
alan@alan-MS-7616:~$ 
``` 

Edit: I used the Dongle to force a re-connection after it was dropped, from the bug in recovering from 'Sleep', that's how I found it worked.
 
Chao!, **bogan.**

---

### Post by chili555 on 2013-01-22
Let's see some details about the internal:```
lspci -nn | grep 0280
```

---

### Post by bogan on 2013-01-22
Hi!, **chili55**5,

'lspci -nn | grep 0280' gave no output, it is a USB device. ```
:~$ lsusb | grep  -i wlan
Bus 002 Device 006: ID 13d3:3306 IMC Networks Mediao 802.11n WLAN [Realtek RTL8191SU]
```I think "Mediao" is a typo for "Median" it is a Median computer.```
:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
      ......
     driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw 
      ......
*-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.4.2
       logical name: wlan0
       serial: 1c:4b:d6:47:82:96
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.2.2 multicast=yes 
       wireless=IEEE 802.11bg
``````
~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"CYBERGRANS"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:BF:09:3D:7C   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=84/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:47:82:96  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe47:8296/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:925898 (925.8 KB)  TX bytes:80883 (80.8 KB)
```Hope this helps.

Edit: If I enter```
lsusb -v | grep WLAN
``` it shows:
> Couldn't open device, some information will be missing9 times before the normal output plus the idproduct.

Chao!, **bogan.**

---

### Post by chili555 on 2013-01-22
> ID 13d3:3306 IMC Networks Mediao 802.11n WLAN [Realtek RTL8191SU]The correct driver for this device is, indeed, r8712u. I wonder if the device doesn't start and run as expected because the driver isn't loading automatically on boot. Let's try to rectify that:```
sudo su
echo r8712u >> /etc/modules
exit
```Now with that device *ONLY* inserted, reboot and tell us if it's working properly.

---

### Post by D2414 on 2013-01-22
Hey Chilli I apologize for the change. Im sorry for asking about the wna3100, just thought it'd be easier. I followed your steps and it didn't seem to work. Whats next if your still willing to help me.

---

### Post by bogan on 2013-01-23
> **chili555 said:**
> The correct driver for this device is, indeed, r8712u. I wonder if the device doesn't start and run as expected because the driver isn't loading automatically on boot. Let's try to rectify that:```
sudo su
echo r8712u >> /etc/modules
exit
```Now with that device *ONLY* inserted, reboot and tell us if it's working properly.Done! with two 12.10 installations - no detectable difference on a couple of reboots each.

Edit: UPDATE:
After ten successful rebooted connections with this installation -  all completed within 15 seconds of logging in - the 11th one called for two Password entries and showed two 'Network disconnected: You are offline' messages. The first Password requester being inactive for 50 secs. -  not responding to keystrokes - before getting focus.

I do not know if the following problem with 'sudo nvidia install -f' is relevant, but I never had it before installing the backport-CW module: [ This downloads the latest recommended driver and forces a re-install after un-installing the existing one.]

In 10 or 12 attempts with both  'sudo nvidia install -f' and  'sudo sh NVIDIA-Linux-x86-304.51.run -f' [which uses the pre-downloaded .run file if the driver is not already installed] only once did it get to 50% download before hanging without any error message, the rest hung before 25%, some at as little as 1%.

A normal direct download from the nvidia.com site ran correctly, without problems.

Chao!,** bogan**.

---

### Post by chili555 on 2013-01-23
> **D2414 said:**
> Hey Chilli I apologize for the change. Im sorry for asking about the wna3100, just thought it'd be easier. I followed your steps and it didn't seem to work. Whats next if your still willing to help me.Probably not as sorry as you are going to be when you see how very difficult your new device is going to be! Since the title of this thread is WNA1000M, please start a new thread and reference WNA3100. Tell me what you've tried so far. Include this information:```
lsusb
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by chili555 on 2013-01-23
> In 10 or 12 attempts with both 'sudo nvidia install -f' and 'sudo sh NVIDIA-Linux-x86-304.51.run -f' [which uses the pre-downloaded .run file if the driver is not already installed] only once did it get to 50% download before hanging without any error message, the rest hung before 25%, some at as little as 1%.
It seems apparent that you have an issue with your video driver. I have very little experience in such things. I suggest you start a new thread and reference your Nvidia driver.

---

### Post by bogan on 2013-01-23
Hi!, **chili555**,
> **chili555 said:**
> It seems apparent that you have an issue with your video driver. I have very little experience in such things. I suggest you start a new thread and reference your Nvidia driver.The problem with the video driver is already sorted.

It was in doing so I cropped up against this downloading trouble,for which I had - and have - no explanation. In the many times I have used 'nvidia-installer -f' in the past, I have never had an interruption of the nvidia download process.

As the only difference I know of, that might affect it, was the installation of the backports-CW module, I thought I should mention it, in case you recognized the symptom.

Evidently you do not; but thanks for the response, anyway. 

 Chao!,** bogan.**

---

### Post by chili555 on 2013-01-23
If you don't have a video card issue, I wonder why you tried to re-install the Nvidia drivers 10-12 times. Is it because it never fully downloaded because of the suspect wireless driver?

---

### Post by bogan on 2013-01-24
> **chili555 said:**
> If you don't have a video card issue, I wonder why you tried to re-install the Nvidia drivers 10-12 times. Is it because it never fully downloaded because of the suspect wireless driver?Sorry for the confusion. I** did **have a video driver problem following the recent kernel update, but I sorted it out, and no longer have a problem.

It was part of the sorting out process that I had to purge all the video driver and Xorg components and re-install them, and used the nvidia download to check out that the process was complete. The '10-12 times' was indeed due to the interrupted download.

Although it was only a minor kernal update, it was the worst video mess up I have encountered, and the most difficult to correct.

 It was due to a driver called "nvidia-current-dev-304.51.really.304.43"which when  the module was updated to 304.51, left behind the 304.43 elements, and that gave a kernel conflict and a fatal Xorg error.

Chao!,** bogan**.

---

### Post by bogan on 2013-01-26
HI1, **chili555**,

I see there is an update for 'backports-modules-cw-; together with a fresh install and the Quantal 3.5.0-23 #35 kernal update in the 'Proposed' ppa.

it is from 3.5.0.22.28 to 3.5.0.23.9 for Quantel.

Whatever it does, I think it can be counted a success, at least as far as I am concerned, with the Realtek RTL8191SU and the r8712u driver.

From more than 20 reboots & cold restarts I have had only one erroneos password requestor, all the others connected within 15 seconds of entering the Log-in password.

Equally for a few boots with the RTL8188U Usb Dongle , and plugging it in after booting.

Chao!, & Thanks again, **bogan**.

---

### Post by chili555 on 2013-01-26
Awesome news! Glad it's working.

---

### Post by bogan on 2013-01-26
Hi!, **chili555,**

**Even better news:**

The compat wireless modules having set-up the Realtek RTL8191SU Wifi Adapter in my main Win7 computer, I set about my secondary Vista desktop, which has given even more connection problems with its Ralink RT2501/RT2573 Adapter, using the rt73usb driver.

This recently has even given trouble with Windows, though at the moment is OK.

Before installing the backports I updated to the Proposed Quantal kernal, which in this case did not include the backports update.

It took me most of half an hour to get a connection, even with the USB dongle plugged in as well, repeatedly asking for a network password, and then it dropped out about 10 seconds after finishing the download!!

With a second restart after installing the Linux-backports-modules-cw-3.6-precise-generic in the 12.04 installation, as well as the quantal version in 12.10, both booted and made the connection almost immediately, and did not drop-out.

So success number two!!

That leaves the 10.04 installation. The Ubuntu Software Center of 10.04 lists lots of versions, though called "compat-wireless-2.6...", rather than "cw"; and none of them with version numbers to match the kernal version.

I tried both ```
sudo apt-get install linux-backports-modules-cw-3.6-lucid-generic #and also:
sudo apt-get install linux-backports-modules-cw* # as well as :
sudo apt-get install linux-backports-modules-cw-2.6-lucid-generic 
```All returned " not found "; and I did not know which of the versions in the software center to try.

Do you know which, or if there is a 'Lucid' version??

Chao!, [B]bogan.
[/B]

---

### Post by chili555 on 2013-01-26
> Do you know which, or if there is a 'Lucid' version??Searching here suggests there is none: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You could install linux-headers and build-essential and compile from source: [http://linuxwireless.org/en/users/Download/stable/#compat-wireless_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_stable_releases)

Depending on your exact kernel version, I might try 2.6.39-1. If you get it to 'make' without error, proceed to 'sudo make install.' If not, delete it and try another version. 'Make' makes no changes to your system.

Would you like some guidance as to how to compile from source?

---

### Post by bogan on 2013-01-27
Hi!, **chili555,**

Thanks for your suggestion and offer.

The 10.04 LTS I have installed is:
"Linux  2.6.32-45-generic #102-Ubuntu SMP Wed Jan 2 21:53:06 UTC 2013 i686 GNU/Linux".

In 10.04 Ubuntu Software Center, of 42 different versions, the nearest to that I can find are not an exact match:> compat-wireless Linux modules for version 2.6.32 on x86
linux-backports-modules-compact-wireless-2.6.34-2.6.32-45-generic-pae

compat-wireless Linux modules for version 2.6.32 on x86/x86_64
linux-backports-modules-compact-wireless-2.6.34-2.6.32-45-genericFor some reason the RT2501/2573USB Adapter, with the rt73usb driver, has always worked better on 10.04 than on later distributions, ever since you first helped me set it up in 9.1. ['lsmod' also shows the rt2x00usb & rt2x00lib as present as well as rt73usb.  I do not understand the reference to rt2500usb.] ```

desktop:~$ lsmod | grep -i rt7
rt73usb                22402  0 
crc_itu_t               1371  1 rt73usb
rt2x00usb               9639  2 rt73usb,rt2500usb
rt2x00lib              27573  3 rt73usb,rt2500usb,rt2x00usb
```So, as, at 88, I do not feel inclined to start delving into compiling source code [beyond ' make, make install,] I am going to decline your kind offer, and leave it as it is.

It is worth noting that on two occasions when I installed the backports modules, on the first reboot I got a password requester; after a cold restart and with further reboots, connection was fast; even, in some cases, with 12.10, completing before I had entered the Log-in password.

Chao!, [B]bogan.

[/B]

---

### Post by chili555 on 2013-01-27
88 and too old to compile from source? I hardly think so. Don't tell anyone, bogan, but I've been retired since the '90s. I have a great-grandson. I'm not exactly a kid.

I wonder, as well, why rt73usb and rt2500usb are loaded. As the kids say, you know, the kids who are only 60, that can't be good. Let's find out which driver you need, make sure only that driver is loaded and see if the performance improves. Please insert the device you intend to use and run and post:```
lsusb
```We will also check to see what, if any, drivers load automatically:```
cat /etc/modules
ls /etc/modprobe.d
```Before we fully explore the compat-wireless avenue, let's sort out the correct driver.

---

### Post by bogan on 2013-01-28
Hi!, **chili555**,

Come Monday morning and [COLOR=Red]BAD[/COLOR] news:
Not only has my 12.10 Update manager failed with a broken daemon & I am getting scholes of system errors, but see below, and it just started asking for Passwords again.

Booting my Win7 m/c after being switched off for 2 days and I got five password requesters before it connected. Booting the Vista m/c from 12.10 and from 10.04 I was unable to get a connection at all, and gave up after about half an hour each.

On 12.04, similarly; but eventually I was able to get a connection by plugging in the RT8188usb Dongle.
Booting to Windows and, surprisingly as I had had previously had problems, It connected at once and worked OK, downloading a Firefox update.

This evening all three installations booted and connected almost at once. So, presumably, which day, what time of day, the ISP signal strength, and who is connected to the Network are effect connectivity. [ But see later comment above.]

So, to respond to your Post: { This is all from the Vista m/c.} ```
desktop:~$ lsusb | grep -ie wireless
Bus 001 Device 007: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 001 Device 006: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
``` ```
-MS-7318Vista-12.10:~$ lsmod | grep -e rt7 -e rt2 -e comp
rt73usb                26624  0 
rt2x00usb              19980  1 rt73usb
rt2x00lib              48602  2 rt73usb,rt2x00usb
mac80211              470383  2 rt2x00usb,rt2x00lib
cfg80211              183967  2 rt2x00lib,mac80211
compat                 14558  6 bnep,rfcomm,bluetooth,rt73usb,mac80211,cfg80211
crc_itu_t              12628  2 rt73usb,firewire_core
```Excerpts from /etc/modprobe.d/Blacklist.conf & etc//modules
```
# for ralink rt2573
# blacklist rt2x00usb
# blacklist rt2x00
cat /etc//modules
lp
```Vista-12.04: ~$ lsmod >> as above but no 'compat' shown though it is installed; no blacklists

Vista-10.04:  /etc/modules >> 'lp' only;  no blacklists
```
desktop:~$ lsmod |grep -e rt7 -e rt2 -e comp
rt73usb                22402  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18173  0 
rt2x00usb               9639  2 rt73usb,rt2500usb
rt2x00lib              27573  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205434  2 rt2x00usb,rt2x00lib
v4l1_compat            13251  1 videodev
cfg80211              126528  2 rt2x00lib,mac80211
``````
desktop:~$ lsusb | grep -ie wireless
Bus 001 Device 007: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 001 Device 006: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
```It also shows as : RT2501/2573USB, but I don't remember where; in Windows it is shown as: 'RT73'.
'nm-tool' shows the driver as 'rt73usb', but for some reason lshw>configuration does not show a driver.

The commented out Blacklists are a relic of the update from 11.10 to 12.04 when I tried them out, remembering your original advise way back, but they did not seem to make any difference, so I left them commented.

Chao!, **boga**n.

---

### Post by bogan on 2013-01-28
Hi!, **chili555**,

I just tried blacklisting 'rt2x00usb' & 'rt2x00lib', and rebooting, but it made no difference, and they still show up in 'lsmod'.

Now I have got Synaptic refusing to run, and 'apt-get -f install' crashing with a Segmentation fault. Looks like serious trouble.

Luckily I have a separate /home. and another 12.10 as well as the one on a Usb.

Chao!,** bogan.**

---

### Post by chili555 on 2013-01-28
It sounds to me like there are other, bigger problems here. You may get a clue by, for example, starting Synaptic in a terminal:```
sudo synaptic
```Note the errors and warnings in the terminal and Google them or search the forum.> 148f:2573 Ralink Technology, Corp. RT2501USB Wireless AdapterThe correct driver for your device is rt73usb:```
chili@Think410:~$ modinfo rt73usb | grep 2573
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]2573[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```rt73usb depends on rt2x00lib, rt2x00usb and crc-itu-t, so it's not improper to see them loaded. rt2[COLOR="Red"]5[/COLOR]00usb, on the other hand, should not be loading. We don't see it called in /etc/modules. 

Here it appears *NOT* to be loading: > -MS-7318Vista-12.10:~$ lsmod | grep -e rt7 -e rt2 -e comp
rt73usb                26624  0 
rt2x00usb              19980  1 rt73usb
rt2x00lib              48602  2 rt73usb,rt2x00usb
mac80211              470383  2 rt2x00usb,rt2x00lib
cfg80211              183967  2 rt2x00lib,mac80211
compat                 14558  6 bnep,rfcomm,bluetooth,rt73usb,mac80211,cfg80211
crc_itu_t              12628  2 rt73usb,firewire_core...but here it does:> desktop:~$ lsmod | grep -i rt7
rt73usb                22402  0 
crc_itu_t               1371  1 rt73usb
rt2x00usb               9639  2 rt73usb,[COLOR="Red"]rt2500usb[/COLOR]
rt2x00lib              27573  3 rt73usb,rt2500usb,rt2x00usbAre these from different machines? Is there a typo? Am I too old and confused???

---

### Post by bogan on 2013-01-28
Hi!, **chili555,**
I just tried to run Synaptic from a terminal as you suggested, and it did exactly the same as from the GUI. That is, the Synaptic window flashed open and immediately closed again, but there were no added messages, so no clues.

But that is off topic and I will Post separately about that.

I have re-commented the two rt2x00 blacklists.

 The rt2500usb is still there in the lsmod list from 10.04, the list headed: "Vista-10.04:":
```
,,,,,,,
rt2x00usb                  9639    2 rt73usb,rt2500usb
rt2x00lib                   27573  3 rt73usb,rt2500usb,rt2x00usb
......
```It's gone 1 am here and i am no longer thinking straight.

So Chao!,** bogan.**

---

### Post by bogan on 2013-01-29
Hi!, **chili555,**

Well, the good news is back!!

This morning 'sudo apt-get update' ran OK, so did: 'sudo apt-get install --reinstall update-manager', and then both the later and Synaptic ran OK as well. Plus, the 12.10, which was flakey yesterday, connected to the Internet straight away.

I have long suspected an intermittent hardware fault in this computer, and even quit using it for a couple of months, it was giving more trouble than it was worth. But when I restarted it, to try and update Windows, it was running reasonably well.

That suspicion seems to be confirmed.

Edit: I just tried blacklisting rt2500usb in 10.04,and it restarted & connected OK, so 'lsmod' no longer shows it:```
Vista-10.04-desktop:~# lsmod | grep -e rt2 -e rt7 -e comp
rt73usb                22402  0 
crc_itu_t               1371  1 rt73usb
rt2x00usb               9639  1 rt73usb
rt2x00lib              27573  2 rt73usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205434  2 rt2x00usb,rt2x00lib
v4l1_compat          13251  1  videodev
cfg80211              126528  2 rt2x00lib,mac80211
-desktop:~# 

```But 'compat' now shows up!!

Chao!.** bogan.**

---

### Post by chili555 on 2013-01-29
'compat' is not there; there is no module, at least on my 12.10 system, named compat. You have v4l_compat, a part of the Video for Linux system. Evidently you have a video capture device, perhaps even a part of your video card. It's unrelated to wireless.

Just as a nervous nellie precaution, let's blacklist rt2800usb *ONLY*. You can manually edit the file if you wish, or we can shoot it in from the command line:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Now, I suggest you watch the wireless and see if it performs a bit more reliably.

---

### Post by bogan on 2013-01-29
> **chili555 said:**
> 
Just as a nervous nellie precaution, let's blacklist rt2800usb *ONLY*. You can manually edit the file if you wish, or we can shoot it in from the command line:```
sudo su
echo "blacklist[COLOR=Red] [COLOR=Blue]rt2[COLOR=Red]8[/COLOR]00usb[/COLOR][/COLOR]" >> /etc/modprobe.d/blacklist.conf
exit
```Now, I suggest you watch the wireless and see if it performs a bit more reliably.Did you mean "rt2[COLOR=Red]8[/COLOR]00usb"??

I thought it was[COLOR=Red] rt2[COLOR=Blue]5[/COLOR]00usb[/COLOR] in the 10.04 installation that was the interloper, and I have already blacklisted that.

I have started another thread on my Updater-Manager problems:
[http://ubuntuforums.org/showthread.php?t=2110132](http://ubuntuforums.org/showthread.php?t=2110132) .
EDIT: Do not have 'compat' ????
What about this:> compat                 14558  6 rfcomm,bnep,bluetooth,rt73usb,mac80211,cfg80211From 12.10 lsmod. Posts #32 & 34.

Everything connecting OK at the moment. Many Thanks.

Chao!,** bogan.**

---

### Post by chili555 on 2013-01-29
Wow! I did mean rt2[COLOR="Red"]5[/COLOR]00usb. Good catch. That's what I get for working on several cases at the same time: confused. :confused:

---

### Post by bogan on 2013-01-29
> **chili555 said:**
> Wow! I did mean rt2[COLOR=Red]5[/COLOR]00usb. Good catch. That's what I get for working on several cases at the same time: confused. :confused:OK. I know how you feel.

Re: 'compat has no module', Please see my last Post, I added an Edit.

Chao!, **bogan**.

---

### Post by chili555 on 2013-01-29
> Re: 'compat has no module', Please see my last Post, I added an Edit.I believe it is part of the compat-wireless package, known in Ubuntu as linux-backports-modules-cw. You have it and I don't. At this point, I think it's needed.

---

