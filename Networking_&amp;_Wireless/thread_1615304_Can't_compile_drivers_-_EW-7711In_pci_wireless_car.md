---
title: "Can't compile drivers - EW-7711In pci wireless card"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by gofes on 2010-11-06
I'm running 10.10 64bit 
It's a new build, but I chose the edimax EW-7711ln PCI adapter as it has Linux support.

I downloaded the drivers off their site, though only for 10.04.

When I try to compile them [sudo make] I get the error [Linux] Error 2
The full output is bellow.

Any ideas where I am going wrong?


```
make -C tools
make[1]: Entering directory `/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/tools'
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/tools/bin2h
cp -f os/linux/Makefile.6 /home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.o
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:219: warning: cast to pointer from integer of different size
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:306: warning: cast to pointer from integer of different size
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:324: warning: cast to pointer from integer of different size
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:341: warning: cast to pointer from integer of different size
/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:357: warning: cast to pointer from integer of different size
make[2]: *** [/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/ben/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
ben@due:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$ 

```

[http://edimax.co.uk/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=326&button=Go](http://edimax.co.uk/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=326&button=Go)

---

### Post by notnic on 2010-11-06
Hey.

I am having the exact same problem. Very similar error message too (cmm_mac_...)

It really is a shame because the packaging almost made me believe it would work with the Disk that came with it. Oh well. Any help would be great.

---

### Post by chili555 on 2010-11-06
The RT3070 chipset is driven by the native built-in driver rt2870sta. Here is what modinfo has to say:```
modinfo rt2870sta
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/[COLOR="Red"]RT3070[/COLOR] Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin

```Have either of you tried to get the native driver going? Do you want to try? Please post:```
lsusb
```

---

### Post by notnic on 2010-11-06
Hi, thanks for your help.

its a pci device so I get (for lspci)
> 
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
03:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
04:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
04:02.0 Network controller: RaLink Device 3060

---

### Post by chili555 on 2010-11-06
> 04:02.0 Network controller: RaLink Device 3060 Not quite enough information. Please run:```
lspci -nn
```Post that line again with the additional data, please.

---

### Post by notnic on 2010-11-06
This is what i get:

> 04:02.0 Network controller [0280]: RaLink Device [1814:3060]

---

### Post by chili555 on 2010-11-06
Ouch! This is actually driven by the often lousy rt2800pci. It's better to get this driver: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Get the driver marked RT3062PCI/etc. Download it to your desktop. Open System > Administration Synaptic and make sure the packages *build-essential* and *kernel-headers-generic* are installed.

Now open a terminal and do:```
cd Desktop
tar -xvf 2010_07_16_RT3062_Linux_STA_v2.4.0.0.tar.bz2
cd 2010_07_16_RT3062_Linux_STA_v2.4.0.0
make
sudo make install
```Now do the blacklists described here: [http://ubuntuforums.org/showpost.php?p=10071183&postcount=19](http://ubuntuforums.org/showpost.php?p=10071183&postcount=19)

Now do:```
sudo su
echo rt3562sta >> /etc/modules
exit
```Reboot and tell us if your wireless is working.

---

### Post by notnic on 2010-11-07
I did all that and its not working. Any other suggestions?

---

### Post by chili555 on 2010-11-07
Let's do a bit of diagnosis. Please post:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
iwconfig
```Thanks.

---

### Post by notnic on 2010-11-07
```
nic@Zeke:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             882847  0 
nic@Zeke:~$ dmesg | grep -e rt2 -e rt3
[   14.532450] rt2860 0000:04:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
nic@Zeke:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

---

### Post by chili555 on 2010-11-07
Dr. Chili snaps on his latex gloves.

It's time to do a full diagnostic work-up. There must be something more in there. Please insert the device, reboot and run:```
dmesg > notnic.txt
lsmod >> notnic.txt
ls /etc/Wireless/RT2860STA >> notnic.txt
ifconfig >> notnic.txt
zip notnic.zip notnic.txt
```You will find a file in your home directory called notnic.zip. Please attach it to your reply.

---

### Post by gofes on 2010-11-07
I seem to be in exactly the same place as notnic

Following the steps in post #7 doesn't remedy my troubles either.

```
ben@due:~$ lsmod | grep -e rt2 -e rt3
rt3562sta            1000812  0 
ben@due:~$ dmesg | grep -e rt2 -e rt3
[    6.004522] rt2860 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
ben@due:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

Cheers for the help so far

---

### Post by chili555 on 2010-11-07
For gofes, may I see:```
lsusb
```Thanks.

---

### Post by gofes on 2010-11-07
```
ben@due:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 090c:6200 Feiya Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Should it make any difference my blacklist currently reads

blacklist rt2870sta
blacklist rt3562sta
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib

blacklist rt2x00usb

thanks

---

### Post by chili555 on 2010-11-07
I am sorry; I should have requested:```
lspci -nn | grep Network
```Do both of you have 64-bit systems? I don't believe the drivers downloadable at Ralink, nor the drivers on the included CD are 64-bit compatible. There are a lot of posts around that say they are not. I have not found your exact device listed yet, either way.

You could email Ralink to ask if they have a 64-bit version: Jett Chen <jett_chen@ralinktech.com>

We could try to trick the built-in rt2860sta driver to run your card. 

You could re-install a 32-bit system.

You could try the Windows drivers with ndiswrapper.

I will be glad to help any way I can.

---

### Post by gofes on 2010-11-07
```
ben@due:~$ lspci -nn | grep Network
03:05.0 Network controller [0280]: RaLink Device [1814:3060]

```

And yes I'm running 64 bit.

Not sure what the best way to proceed is then.

---

### Post by notnic on 2010-11-07
hi Chili, im using 32-bit already. I should have mentioned that before.

I cannot find the .inf windows driver on the CD they gave because its a silly utility. Edimax website gives the same. is there an alternative windows driver i could try?

im gonna boot into ubuntu now and do the zip file for you.

---

### Post by notnic on 2010-11-07
back again, heres the zip file.

---

### Post by chili555 on 2010-11-08
Here is a snip from your *dmesg*:> [   14.462014] [COLOR="Red"]rt2860[/COLOR] 0000:04:02.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   14.462313] 
[   14.462315] 
[   14.462316] === pAd = f9792000, size = 528236 ===
[   14.462317] 
[   14.462360] <-- RTMPAllocTxRxRingMemory, Status=0
[   14.462424] <-- RTMPAllocAdapterBlock, Status=0
[   14.462427] pAd->CSRBaseAddress =0xf9780000, csr_addr=0xf9780000!
[   14.469702] [COLOR="Red"]ndiswrapper[/COLOR] version 1.56 loaded (smp=yes, preempt=no)We don't want two wireless drivers loading and fighting each other. First, let's remove ndiswrapper and see if rt3562sta comes to life:```
sudo gedit /etc/modules
```If the word ndiswrapper is there, remove it. Proofread, save and close gedit. Next, do:```
ndiswrapper -l
```It will output something like:> Installed ndis drivers:
  {name of driver} driver present, hardware presentThe output may vary slightly. Whatever the name of the driver is, let's erase it:```
sudo ndiswrapper -e {name of driver}
```Obviously, substitute the actual name, such as rt8733 or whatever the -l command said it was.

Now, reboot and give me a report. If your wireless is not working now, let me have the same diagnostic report, but this time, name it notnic2.

Thanks.

---

### Post by notnic on 2010-11-08
Hello again.

well, still not working. I had already removed the driver from ndiswrapper before i posted on this forum, but now i have taken it out of the startup list too.

It really is a shame this isnt working, but I am definitely enjoying all your help. Thanks again.

---

### Post by chili555 on 2010-11-08
This is my favorite kind of problem: it all looks perfect, except it just doesn't work. 

Were there any errors when you compiled? Would you please do:```
sudo rmmod -f rt3562sta
cd Desktop/2010_07_16_RT3062_Linux_STA_v2.4.0.0
```Substitute the location you downloaded the file if it's not as above.```
make clean
make
sudo make install
```Note any errors, not warnings. You can copy and paste from the terminal into a text document to post here. If there are no errors, do:```
sudo modprobe rt3562sta
iwconfig
```Any improvement?

If not, let's try Plan B (not from outer space.)

---

### Post by gofes on 2010-11-08
Right what would my options be?

The edimax EW-7711ln PCI isn't down as working with ndiswrapper but there is a XP 64bit driver on their website.

Is this likely to work where should I start?

How likely is a solution going to be. As this is a new build is it worth returning my Edimax wifi card and getting a differnt one?

---

### Post by chili555 on 2010-11-08
I have no idea how likely it is to work; we'll only know when it actually works, or not.

I suggest you remove the compiled driver (sudo make uninstall from the install directory), change the /etc/modules line to read rt2860sta and then we'll do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="pci", ATTR{idVendor}=="1814", ATTR{idProduct}=="3060", RUN+="/sbin/modprobe -qba rt2860sta"
```Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```
install rt2860sta /sbin/modprobe --ignore-install rt2860sta $CMDLINE_OPTS; /bin/echo "1814 3060" > /sys/bus/pci/drivers/rt2860/new_id
```Proofread twice, save and close gedit.

Reboot and cross your fingers and toes. As I am sure you can see, this is very experimental.

Give me a report if it's not working with notnic3.

A simple 'Woohoo!' if it is working.

---

### Post by notnic on 2010-11-08
Im sorry chili, no whooho yet :( I feel it is coming soon though.

Ubuntu has a wireless interface now, and the ability to enable/disable wireless networking (which i never had before), but no networks signal etc. But here is my zip file none the less.

I do not get any errors when compiling the driver you told me to use. But i have attached the errors that I get when i try to make the drivers from the edimax website (in the zip).

---

### Post by chili555 on 2010-11-09
Please post:```
sudo iwconfig wlan0 power on
iwconfig wlan0
sudo iwlist wlan0 scan
```If there are errors or warnings, it will be instructive to see what they are. Your files look pretty healthy, actually, especially this:> wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:aa:d3:7e  
          inet6 addr: fe80::21f:1fff:feaa:d37e/64 Scope:Link
          [COLOR="Red"]UP[/COLOR] BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          [COLOR="Red"]TX packets:208[/COLOR] errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 It suggests that there is a flicker of life!

---

### Post by gofes on 2010-11-09
I too now have the wireless interface back, but I'm also not getting any signal.

Cheers again.

---

### Post by notnic on 2010-11-09
Samsies!

---

### Post by chili555 on 2010-11-09
Thanks, guys. gofes, from now on, if it's necessary, please name your diagnostic files gofes.zip. It helps me keep the right person in mind.

---

### Post by chili555 on 2010-11-09
Deleted.

---

### Post by chili555 on 2010-11-09
We compiled rt3562sta which did nothing for us. However, it did place it's own version of RT2860STA.dat on file. I would like to see if it is the culprit. We will make a backup in case we have to...well, back up. Please do:```
sudo su
rmmod -f rt2860sta
mv /etc/Wireless/RT2860STA/RT2860STA.dat /etc/Wireless/RT2860STA/RT2860STA.dat.bak
echo Default > /etc/Wireless/RT2860STA/RT2860STA.dat
modprobe rt2860sta
exit
```Any improvement?

I am going to another machine that has a stock, fresh from the Ubuntu factory /etc/Wireless/RT2860STA/RT2860STA.dat file and we will try it if the above doesn't work for us.

---

### Post by chili555 on 2010-11-09
My factory fresh install has*** NO*** RT2860STA.dat! The plot thickens.

---

### Post by notnic on 2010-11-11
Hey, i did that and still no luck. Do you know where i could get a windows driver to try and use in ndiswrapper? is there a reason why i shouldnt?

---

### Post by gofes on 2010-11-11
I've still had no luck either.

The [Edimax drivers are here.]("http://www.edimax.com/en/support_detail.php?pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pl1_id=1&pd_id=344&button=Go")

Or would it be best [to use on on the Ralink drivers?]("http://www.ralinktech.com/support.php?s=1")

---

### Post by chili555 on 2010-11-11
My first preference would be the Ralink XP drivers appropriate to your architecture; i.e.32- or 64-bit.

---

### Post by notnic on 2010-11-12
I dont know if im being a noob or what, but they are all utilities. i.e. no inf files. but the only one i tried is > PCI/mPCI/CB (RT2860 /RT2760 /RT2890 /RT2790 /RT306X /RT309X /RT35X2)

---

### Post by gofes on 2010-11-12
^ I've just noticed the same thing.

---

### Post by chili555 on 2010-11-12
Hang in there, guys (or gals), I'm trying to get it worked out now. I'll be back soon.

---

### Post by chili555 on 2010-11-12
Please try these files. Let me know how it goes.

---

### Post by chili555 on 2010-11-12
Oops! Those files are probably wrong.  Try these instead.

Soory for my mis-step.

---

### Post by coulson on 2010-11-14
Hi all

Latecomer to this thread. I am experiencing the same problems as described in the original post. Given that there are a multitude of tests which haven't worked yet, and there is a solution pending testing, what should I start with?

This whole thing is so frustrating. I wish I'd paid more attention when I bought this wireless card! (originally it didn't say it was Ubuntu compatible, but now the Edimax site says it is it just makes me even more annoyed!)

---

### Post by chili555 on 2010-11-14
The only remaining solution is ndiswrapper using the files in the post just above. We have not yet heard if it works.

I have not yet heard from gofes or notnic; either it worked or they returned their cards.

---

### Post by notnic on 2010-11-14
WOOHOOO!!!! Finally it works. I am writing this from my Ubuntu installation. Thanks so Much Chili

So just to clarify for anyone looking for the solution, Use ndiswrapper with the drivers provided by Chili (a few post up).

---

### Post by chili555 on 2010-11-14
Awesome! I am glad it's finally working and glad you have good news to share with the searchers.

---

### Post by coulson on 2010-11-14
Sorry to be a thickie, but can you provide a step-by-step for using ndiswrapper?

---

### Post by chili555 on 2010-11-14
I don't believe the ndiswrapper suite is installed by default, therefor, please open System > Administration > Synaptic and select Settings > Repositories. You will see the option to install software from the install CD. Drop the CD into the tray and press the button 'Reload.' It will index the packages available on the CD. Search for *ndisgtk* and install it and its dependencies. 

Close Synaptic and download the rt**2860**.zip file above to your desktop. Right-click the file and select 'Extract Here.' Open System > Administration > Windows Wireless Drivers. Select 'Install new driver.' Navigate to your desktop and to the folder called *rt2860*. Select rt2860.inf and install it. 

It may take a reboot, but your wireless should be working. Post back if you need further guidance.


- - - - - -

Whew! I amazed myself! I got through a whole post and never used the terminal!!!

---

### Post by coulson on 2010-11-14
It worked here too after a reboot. Thanks for your help and persistence! I shall now be steadily increasing my Ubuntu usage. Indeed, this is being posted from it now :-)

---

### Post by gofes on 2010-11-14
I'm still not having any luck. I just have a greyed out wireless networks section .

Nsdwrapper is showing as RT2860 hardware installed yes

```
ben@due:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

But I guess this is as I still have

/etc/udev/rules.d/network_drivers.rules
/etc/modprobe.d/network_drivers.conf
 as bellow?

Deleting them leaves me with no wireless network manager at all.


> **chili555 said:**
> I have no idea how likely it is to work; we'll only know when it actually works, or not.

I suggest you remove the compiled driver (sudo make uninstall from the install directory), change the /etc/modules line to read rt2860sta and then we'll do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="pci", ATTR{idVendor}=="1814", ATTR{idProduct}=="3060", RUN+="/sbin/modprobe -qba rt2860sta"
```Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```
install rt2860sta /sbin/modprobe --ignore-install rt2860sta $CMDLINE_OPTS; /bin/echo "1814 3060" > /sys/bus/pci/drivers/rt2860/new_id
```Proofread twice, save and close gedit.

Reboot and cross your fingers and toes. As I am sure you can see, this is very experimental.

Give me a report if it's not working with notnic3.

A simple 'Woohoo!' if it is working.

---

### Post by chili555 on 2010-11-14
Let's see if we can tweak a few things. Please do:```
sudo mv /etc/udev/rules.d/network_drivers.rules /etc/udev/rules.d/network_drivers.rules.bak
sudo mv /etc/modprobe.d/network_drivers.conf /etc/modprobe.d/network_drivers.conf.bak
sudo gedit /etc/modules
```If rt2860sta is there, please remove it and add:```
ndiswrapper
```Proofread carefully, save and close gedit. Now do:```
sudo modprobe ndiswrapper
iwconfig
ndiswrapper -l
```l is for 'list.' Please post the result.

---

### Post by gofes on 2010-11-15
Hello, I'm not showing any Wireless again!

```
ben@due:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

ben@due:~$ ndiswrapper -l
rt2860 : driver installed
	device (1814:3060) present (alternate driver: rt2800pci)
ben@due:~$ 


```

Still no luck, but cheers for all the help.

---

### Post by chili555 on 2010-11-15
> alternate driver: rt2800pciLet's fix that and see if your wireless wakes up. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines:```
blacklist rt2800pci
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2800lib
```Proofread carefully, save and close gedit. Reboot and run the tests above again.

---

### Post by gofes on 2010-11-15
It looks like the 64 bit OS is causing the problem.

When I boot up, before the Ubuntu splash I get the error text along the lines of:
Kernel is 64bit but windows driver is not. Couldn't prepare driver.

---

### Post by chili555 on 2010-11-15
Indeed. We must search for the 64-bit rt2860.inf and .sys files.

Googling now...

---

### Post by chili555 on 2010-11-15
You will need to erase the drivers you have now:```
sudo ndiswrapper -e rt2860.inf
```Since the 64-bit version has the same name, you may need to expunge your old files:```
sudo rm -rf /etc/ndiswrapper/*
```Now install these 64-bit files as previously explained.

EDIT: I am not sure these are going to work, but try and we'll find out.

---

### Post by gofes on 2010-11-15
Cheers for all the help, but I've still not got any wireless option. 

In the ndswrapper GUI the 64bit drivers I just installed show as Hardware present: no.

Although they did work the earlier 32bit version did detect the hardware.

---

### Post by chili555 on 2010-11-15
Erase those as well and do:```
sudo rm /etc/modprobe.d/ndiswrapper.conf 
```I am close to working out a fix.

---

### Post by TheRussMan on 2010-12-06
Any update on this?  I get the same issue.

---

### Post by jonpon on 2011-01-13
Fantastic, I wish Id found this thread earlier! 
Well Done Chilli

---

### Post by Dragon Lord on 2011-01-26
chili555 - thank you for the driver! (page 4).
Another V for me.

---

### Post by Neptunium on 2011-02-04
Thanks from me as well chilli555, for posting the drivers and instructions.

Pleased to have got my EW-7711ln wireless adaptor working with Ubuntu, having read this thread.

---

### Post by teyster2 on 2011-02-08
> **chili555 said:**
> Oops! Those files are probably wrong.  Try these instead.

Soory for my mis-step.

Thanks so much for this.  I was pulling my hair out.

---

### Post by norm.h on 2011-03-24
> **chili555 said:**
> 
 Open System > Administration > ......Windows Wireless Drivers. Select 'Install new driver.' Navigate to your desktop and to the folder called *rt2860*. Select rt2860.inf and install it.

I've been trying to follow this thread from the beginning, as I can't get my EW-7711ln card to work either.
Goodness knows what I've got installed now!
Anyway, trying to resort to ndiswrapper, which is installed, I don't have Windows Wireless Drivers facility on System > Admin.

I'm running Ubuntu 10.10, 32 bit.

---

### Post by TheRussMan on 2011-03-24
I found the wrapper to be a bit poor and ended up downloading the sourcecode and compiling them myself.  It's actually pretty straight forward and you can pretty much follow the instructions on the manufacturers website.  Only really annoyance is I have to recompile everytime a new kernel comes out.  Only takes a few mins though.

---

### Post by norm.h on 2011-03-25
I recently purchased an EDIMAX EW-7711 PCI wireless adapter, which I have installed on a Foxconn 945G7AD MB.
I am running Linux Ubuntu 10.10  with the 2.6.35-28-generic kernel, and can't get a connection to my ZyXEL P660HW router.

I get exactly the same as Notnic as far as Post 6, and in Post 7 I find that &#8220;build-essential&#8221; isn't loaded.

I have downloaded the &#8220;DPO_RT3070_LinuxSTA_V2.3.0.2_20100412.tar&#8221; driver and tried to run the &#8220;How to install Edimax EW-7711xxx (3070) on Linux Ubuntu (9.10 & 10.4) &#8221; from the EDIMAX website.

At Step 5: Copy the RT2870STA.dat to RT3070STA.dat, and then copy the 
RT3070STA.dat into the driver folder on the Desktop. $ sudo mv RT2870STA.dat RT3070STA.dat but get:
norm@norm-desktop:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$ sudo mv RT2870STA.dat RT3070STA.dat 
mv: cannot stat `RT2870STA.dat': No such file or directory 

*iwconfig* originally showed:
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 

Now it shows:
ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

*lshw* shows: 
*-network 
                description: Wireless interface 
                product: RaLink  vendor: RaLink 
                &#8230;..
                configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-28-generic firmware=N/A latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn 

*lsusb *shows:
norm@norm-desktop:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 046d:09a4 Logitech, Inc. QuickCam E 3500 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
Whereas *lspci* shows:
04:02.0 Network controller: RaLink Device 3060 


Where am I going wrong? Will I have to reconnect via ethernet to download &#8220;build-essential&#8221;?
Sorry this is a bit of a jumble of information! (and I don't know where the smilies came from)

---

### Post by chili555 on 2011-03-26
> Whereas lspci shows:
04:02.0 Network controller: RaLink Device 3060
Please let us see:```
lspci **-nn**
```We need the pci.id code for your device.

---

### Post by norm.h on 2011-03-27
Apologies for the delay.

lspci -nn shows:  
04:02.0 Network controller [0280] : RaLink Device [1814 : 3060]

---

### Post by bkratz on 2011-03-27
See post 3 of this thread

[http://ubuntuforums.org/showthread.php?t=1664883](http://ubuntuforums.org/showthread.php?t=1664883)


It links to another of Dr. Chili threads!

---

### Post by norm.h on 2011-03-27
With respect, your link goes to earlier posts in *this *thread.

I haven't got "Windows Wireless Devices" on the machine I'm trying to get wifi for, but it *is* on this laptop.
Is there a way to copy it to the other machine, maybe using a memory stick?

---

### Post by norm.h on 2011-03-29
I'm still struggling with this.
I've made sure that all the requirements are available on the machine, (including the Windows Wireless Drivers app).
I've tried  the procedure detailed in Post 7, and get this:

norm@norm-desktop:~$ cd /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ make
make -C tools
make[1]: Entering directory `/home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.o
see include/linux/module.h for more information
  LD [M]  /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
cp -f /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko /tftpboot
cp: cannot create regular file `/tftpboot': Permission denied
make: *** [LINUX] Error 1
norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ 

I've also tried the EDIMAX "How to install...", and the ndiswrapper route. All to no avail.

lspci -nn shows: 04:02.0 Network controller [0280]: RaLink Device [1814:3060]

iwconfig shows: norm@norm-desktop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

Please, please can somebody help?

---

### Post by notnic on 2011-03-29
Hi norm. I cant help you with all that much. But I thought I would show you the driver I am using in ndiswrapper. It has worked flawlessly for me since the last time I was on this thread. If there is anything else I can dig up for you to compare your own setup, just ask.

ndiswrapper -l
rt2860 : driver installed
	device (1814:3060) present (alternate driver: rt2800pci)

---

### Post by norm.h on 2011-03-29
Since installing the rt2860 driver in ndiswrapper I'm now back to square one, ie, device not associating with the router.
I *have* allowed the device MAC in the router's MAC filter.

norm@norm-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:72 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

norm@norm-desktop:~$ ndiswrapper -l
WARNING: /etc/modprobe.d/blacklist.conf line 41: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist.conf line 53: ignoring bad line starting with 'sudo'
rt2860 : driver installed
	device (1814:3060) present (alternate driver: rt2800pci)
norm@norm-desktop:~$ 

Are these two warnings significant?

Don't know where the smilies came from.

EDIT:
After a reboot, I now get:

norm@norm-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by norm.h on 2011-03-29
Is this of any use to helpers?

norm@norm-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:15:58:8d:19:b7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.33 latency=0 multicast=yes
       resources: irq:43 ioport:de00(size=256) memory:fdeff000-fdefffff memory:fdd00000-fdd1ffff
  *-network
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=rt2860 latency=64 maxlatency=4 mingnt=2
       resources: irq:17 memory:fd9f0000-fd9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:1f:1f:a5:fe:df
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 multicast=yes wireless=Ralink STA
norm@norm-desktop:~$

---

### Post by chili555 on 2011-03-29
Just to be a bit too blunt, you can't jump back and forth between ndiswrapper and a compiled driver. We need to pick one and fine tune it. Which do you prefer?> WARNING: /etc/modprobe.d/blacklist.conf line 41: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist.conf line 53: ignoring bad line starting with 'sudo'Let's try to fix this. Please post:```
cat /etc/modprobe.d/blacklist.conf
```We'll identify and repair the lines in question.

There are a few minor problems in your compile, but let's solve those only if you decide on the native driver. Please post:```
lsmod | grep -e ndis -e rt2 -e rt3
```

---

### Post by notnic on 2011-03-29
Again, may not be any help. But this is the relevant section from my blacklist:
blacklist rt2800usb
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib

---

### Post by chili555 on 2011-03-29
> **notnic said:**
> Again, may not be any help. But this is the relevant section from my blacklist:
blacklist rt2800usb
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800libIt is not of any help. There is a problem on lines 41 and 53 of the file. May I see the *whole* file?

---

### Post by norm.h on 2011-03-29
I was beginning to suspect I'd muddled things up.
It happens when I don't really know what I'm doing!

I don't really mind which driver I have as long as it works, but if in the future, a kernel has a working native driver for the card, what happens if I'm using ndiswrapper? (Just a thought)

Anyway:

norm@norm-desktop:~$ cat /etc/modprobe.d/blacklist.conf
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2sudo gedit /etc/modprobe.d/blacklist.conf
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps

sudo gedit /etc/modprobe.d/blacklist.conf

blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr

sudo gedit /etc/modprobe.d/blacklist.conf

blacklist amd76x_edac
blacklist rt2800pci
norm@norm-desktop:~$ 

norm@norm-desktop:~$ lsmod | grep -e ndis -e rt2 -e rt3
rt3562sta             916662  0 
ndiswrapper           184207  0 
norm@norm-desktop:~$

---

### Post by chili555 on 2011-03-29
Wow.

Please amend the file to read as I have indicated.```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps

blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr

blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread twice, carefully. Save and close gedit.> if in the future, a kernel has a working native driver for the card, what happens if I'm using ndiswrapper?You'll have a conflict and have to resolve it by blacklisting the native driver.

Let's see:```
ndiswrapper -l
```If it looks healthy, we'll concentrate on ndiswrapper.> I was beginning to suspect I'd muddled things up.Indeed...

By the way, I notice you have a wired ethernet connection. Network Manager is designed to *disallow* a wireless connection if you have wired. Before we try to connect, please detach the wire. We are a few steps away before we can connect.

---

### Post by norm.h on 2011-03-29
norm@norm-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt2860 : driver installed
	device (1814:3060) present (alternate driver: rt2800pci)
norm@norm-desktop:~$ 

I was going to ask about Network Manager disallowing wireless if wired.

Going for tea now. Back in an hour.

---

### Post by chili555 on 2011-03-29
> rt2860 : driver installed
device (1814:3060) present ([COLOR="Red"]alternate driver: rt2800pci[/COLOR])After you corrected the blacklist file, did you reboot? How was the tea?

---

### Post by norm.h on 2011-03-29
> **chili555 said:**
> After you corrected the blacklist file, did you reboot? How was the tea?
No, I didn't reboot, should I have done?
Tea - fish & chips, luverly!

EDIT: Have just rebooted, but haven't disconnected ethernet connection. Am waiting for your say so.
(quote:"*We are a few steps away before we can connect*".)

---

### Post by chili555 on 2011-03-29
I love fish and chips; it's hard to get decent fish and chips in South Carolina. They think fish is catfish overcooked in a giant vat of stale grease. Ugh!

Please detach the wire, reboot and tell me how much you love your wireless.

---

### Post by norm.h on 2011-03-29
Where do we go from here?

No connection - 
norm@norm-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

norm@norm-desktop:~$ 

Anyway, enough for tonight, it's my bedtime.
Thanks so much for all your help and patience.

---

### Post by norm.h on 2011-03-30
I've had another try, but get the same results as last evening, so I downloaded the card's User Manual in which it refers to LEDs on the card which light when a button is pressed to activate WPS security.
Neither light is lit, and as my router doesn't support WPS anyway, I've left well alone.
I simply don't know where to go with this (unless it's back to the shop with a "not fit for purpose" item).

For information:
norm@norm-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:15:58:8d:19:b7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.34 latency=0 multicast=yes
       resources: irq:43 ioport:de00(size=256) memory:fdeff000-fdefffff memory:fdd00000-fdd1ffff
  *-network
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=rt2860 latency=64 maxlatency=4 mingnt=2
       resources: irq:17 memory:fd9f0000-fd9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:1f:1f:a5:fe:df
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 multicast=yes wireless=Ralink STA
norm@norm-desktop:~$ 

Should I perhaps be looking in the BIOS?

Isn't this: driver=RALINK WLAN driverversion=2.4.1.1 a driver referred to earlier in the thread, different from the ndis wrapper driver we're trying to use?

---

### Post by norm.h on 2011-03-31
With reference to my previous post, this is an extract from Post 68 after I had downloaded a (presumably) newer driver version:

norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_***V2.4.1.1***_20101217$ make

Extract from lshw -C Network:

*-network DISABLED
description: Wireless interface
physical id: 1
logical name: ra0
serial: 00:1f:1f:a5:fe:df
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=RALINK WLAN ***driverversion=2.4.1.1*** multicast=yes wireless=Ralink STA
norm@norm-desktop:~$ 

norm@norm-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
***rt2860 : driver installed***
device (1814:3060) present (alternate driver: rt2800pci)
norm@norm-desktop:~$ 

Could this be a conflict which is preventing a wireless connection, and if so, how do I overcome it, please?

---

### Post by chili555 on 2011-03-31
> Could this be a conflict which is preventing a wireless connection, and if so, how do I overcome it, please?It is absolutely a problem. Sorry for the delay in my reply; flu has kept me in bed for a couple of days.

Please do:```
cd Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
sudo make uninstall
sudo rmmod -f rt3562sta
sudo modprobe ndiswrapper
iwconfig
```Your interface should now be wlan0 and not ra0. Does it connect as expected?

---

### Post by norm.h on 2011-03-31
Sorry to hear about the flu, hope you're better.
This is what I get from your commands:

norm@norm-desktop:~$ cd /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make uninstall
[sudo] password for norm: 
make -C /home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 uninstall
make[1]: Entering directory `/home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt3562sta.ko
/sbin/depmod -a 2.6.35-28-generic
make[1]: Leaving directory `/home/norm/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo rmmod -f rt3562sta
norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

norm@norm-desktop:~/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$

---

### Post by chili555 on 2011-03-31
Please show me:```
ndiswrapper -l
```That's a lower-case L for 'list.'

---

### Post by norm.h on 2011-03-31
norm@norm-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt2860 : driver installed
	device (1814:3060) present (alternate driver: rt2800pci)
norm@norm-desktop:~$

---

### Post by norm.h on 2011-03-31
norm@norm-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt2860 : driver installed
	device (1814:3060) present (alternate driver: rt2800pci)
norm@norm-desktop:~$ 

Question: should it not have removed 3592 and 3062 as well, or did it?

rm -rf /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt3562sta.ko

---

### Post by chili555 on 2011-03-31
Please let me see:```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```We need to consolidate (and check) these files.> Question: should it not have removed 3592 and 3062 as well, or did it?Those are simply device designations that are driven by rt3562sta. Not a problem.

---

### Post by norm.h on 2011-03-31
norm@norm-desktop:~$ cat /etc/modprobe.d/blacklist
blacklist RALINK

norm@norm-desktop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
# replaced by e100
blacklist eepro100
# replaced by tulip
blacklist de4x5
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
norm@norm-desktop:~$

---

### Post by chili555 on 2011-03-31
Your file without .conf attempts to blacklist RALINK. There is no such module. Moreover, you have everything needed blacklisted in .conf. Let's remove the unneeded file:```
sudo rmmod -f /etc/modprobe.d/blacklist
```Now, let's see what the problem might be with ndiswrapper:```
dmesg | grep ndiswrapper
```Where did you get the .inf file you are using with ndiswrapper? From the CD that came with the device?

---

### Post by norm.h on 2011-03-31
Just been called for my tea. Back soon
N

---

### Post by norm.h on 2011-03-31
Before you ask, omelette with tomatoes and spring onions.:)

I got the inf. file from the driver you recommended in Post 39 (rt2860)

norm@norm-desktop:~$ sudo rmmod -f /etc/modprobe.d/blacklist
[sudo] password for norm: 
ERROR: Removing 'blacklist': No such file or directory

norm@norm-desktop:~$ dmesg | grep ndiswrapper
[   16.265201] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   16.614539] usbcore: registered new interface driver ndiswrapper
norm@norm-desktop:~$

Edit: the CD that came with the device doesn't support Linux. 

Off topic a mo.
When I leave the thread open, I don't see if you've replied unless I go out and back in.
Is this right?

---

### Post by chili555 on 2011-03-31
> sudo rmmod -f /etc/modprobe.d/blacklist
[sudo] password for norm:
ERROR: Removing 'blacklist': No such file or directory
Rats. I made a mistake and I'm sorry. Must be the flu. I meant to remove the file, not the module:```
sudo [COLOR="Red"]rm[/COLOR] -f /etc/modprobe.d/blacklist
```I remember on my old performance evaluations, I could hardly ever get higher than, "Occasionally makes an understandable error."

I believe the .inf file is correct for your device. I don't understand why it doesn't run. Please let me see:```
sudo cat /var/log/syslog | grep ndis
```If there are repeats, just post the last ten or so lines.> When I leave the thread open, I don't see if you've replied unless I go out and back in.
Is this right? No. Just press Reload or Refresh on your browser.

---

### Post by bkratz on 2011-03-31
@Chili555, should that have been blacklist.conf or doesn't that matter?

---

### Post by norm.h on 2011-03-31
This doesn't look right.
anyway, nearly bedtime, I'll check back in the morning.


norm@norm-desktop:~$ sudo rm -f /etc/modprobe.d/blacklist
[sudo] password for norm: 
norm@norm-desktop:~$ sudo cat /var/log/syslog | grep ndis
norm@norm-desktop:~$

---

### Post by chili555 on 2011-03-31
> **bkratz said:**
> @Chili555, should that have been blacklist.conf or doesn't that matter?blacklist is correct; see post #91.

---

### Post by bkratz on 2011-03-31
Dr. Chili

Thanks, I saw that post but apparently it didn't sink in!!!

---

### Post by norm.h on 2011-04-01
10.30 am UK time.

There's a saying that goes:
"He who doesn't do any work, doesn't make any mistakes"!!!!

> **chili555 said:**
> Rats."Occasionally makes an understandable error."
. Please let me see:```
sudo cat /var/log/syslog | grep ndis
```If there are repeats, just post the last ten or so lines.No. Just press Reload or Refresh on your browser.

norm@norm-desktop:~$ sudo rm -f /etc/modprobe.d/blacklist
[sudo] password for norm: 
norm@norm-desktop:~$ sudo cat /var/log/syslog | grep ndis
Apr  1 10:10:13 norm-desktop kernel: [    7.898379] ndiswrapper version 1.56 loaded (smp=yes, preempt=no), but I haven't got the Network icon in the panel.
Apr  1 10:10:13 norm-desktop kernel: [    9.643923] ndiswrapper: driver rt2860 (Ralink Technology, Corp.,07/06/2010, 3.01.08.0001) loaded
Apr  1 10:10:13 norm-desktop kernel: [    9.644443] ndiswrapper 0000:04:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  1 10:10:14 norm-desktop kernel: [   10.172547] ndiswrapper 0000:04:02.0: setting latency timer to 64
Apr  1 10:10:14 norm-desktop kernel: [   10.175891] ndiswrapper: using IRQ 17
Apr  1 10:10:15 norm-desktop kernel: [   11.625393] usbcore: registered new interface driver ndiswrapper
Apr  1 10:10:19 norm-desktop NetworkManager[1049]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
norm@norm-desktop:~$ 

norm@norm-desktop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions., but I haven't got the Network icon in the panel.
wlan0     IEEE 802.11g  ESSID:"V1_n0rm"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:CF:72:0F:C6   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:100/100  Signal level:-22 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Disconnected the cable and rebooted. Now I'm doing this with a wireless connection.

Apologies for yet another "off-topic" query:
How do you quote part of a post, in a box as you have done several times?  

Anyway, thank you most sincerely for all your help and patience.
N

---

### Post by chili555 on 2011-04-01
> Apologies for yet another "off-topic" query:
How do you quote part of a post, in a box as you have done several times?
^^^You mean like this? At the top of the reply box, there is a button towards the right that looks sort of like a text ballon used in cartoons. If you hover over it, it says, 'wrap [QUOTE] tags around selected text.' I copy and paste the text into my reply, highlight it and click the balloon. If you become a hard-core terminal/command-line/emacs geek; you can learn to write UUB code directly.

Glad it's finally working! I shall hoist a Guinness and celebrate!

---

### Post by norm.h on 2011-04-01
You mean like this?

> If you become a hard-core terminal/command-line/emacs geek; you can learn to write UUB code directly.

I don't think that's at all likely.

> I shall hoist a Guinness and celebrate!
Have it on me:D

Once again, my sincere thanks.

---

### Post by snake_865 on 2011-04-10
> **gofes said:**
> Cheers for all the help, but I've still not got any wireless option. 

In the ndswrapper GUI the 64bit drivers I just installed show as Hardware present: no.

Although they did work the earlier 32bit version did detect the hardware.

i m in the same situation as gofes,did anybody find a solution?

---

### Post by mariana.malta on 2012-09-07
> **chili555 said:**
> I don't believe the ndiswrapper suite is installed by default, therefor, please open System > Administration > Synaptic and select Settings > Repositories. You will see the option to install software from the install CD. Drop the CD into the tray and press the button 'Reload.' It will index the packages available on the CD. Search for *ndisgtk* and install it and its dependencies. 

Close Synaptic and download the rt**2860**.zip file above to your desktop. Right-click the file and select 'Extract Here.' Open System > Administration > Windows Wireless Drivers. Select 'Install new driver.' Navigate to your desktop and to the folder called *rt2860*. Select rt2860.inf and install it.

It may take a reboot, but your wireless should be working. Post back if you need further guidance.

I have made all you say. I dont understand where the  .sys file enters (what to do with it).

My wireless does not work....I have this problem since 11.10 (which I could get it to work with this [http://askubuntu.com/questions/84959/how-do-i-get-a-ralink-rt3060-wireless-card-working](http://askubuntu.com/questions/84959/how-do-i-get-a-ralink-rt3060-wireless-card-working) .

But now I am stuck!

CAn anyone help me? I am almost giving up and looking for another wireless card....any hint on what card we should buy to have it working out of the box?

Thank you Chilli for ALL YOUR AMAZING HELP AND EFFORTS AND WORK. 

Mariana

---

### Post by chili555 on 2012-09-07
> **mariana.malta said:**
> I have made all you say. I dont understand where the  .sys file enters (what to do with it).

My wireless does not work....I have this problem since 11.10 (which I could get it to work with this [http://askubuntu.com/questions/84959/how-do-i-get-a-ralink-rt3060-wireless-card-working](http://askubuntu.com/questions/84959/how-do-i-get-a-ralink-rt3060-wireless-card-working) .

But now I am stuck!

CAn anyone help me? I am almost giving up and looking for another wireless card....any hint on what card we should buy to have it working out of the box?

Thank you Chilli for ALL YOUR AMAZING HELP AND EFFORTS AND WORK. 

MarianaThis thread is geting long, old and tough to navigate. Please start a new thread and send me a Private Message with the link if I don't catch it right away.

I'll be very happy to help.

---

