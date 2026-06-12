---
title: "Wireless not working on RaLink RT3090 with Ubuntu 10.04"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by nlj on 2010-05-21
I am running Ubuntu 10.04 (64-bit) on a SONY VAIO M (Model VPCM111AX/W (Atom N450)) which appears to have a RaLink RT3090 wireless card. So far everything seems to work except the WLAN.

The problem is that the wireless does not appear to be switched on. This computer doesn't have a key combination to toggle the wireless. Instead it has a physical switch on the front. The switch is in the "on" position, and the green LED is on. (It isn't a toggle switch with a spring like on an Aspire One, rather it has an "on" position and an "off" position and a green LED turns on when it is on, so you'd think it would be pretty obvious if it were off.) 

At the bottom of this post I have appended diagnostic messages from a variety of utilities that seemed more or less relevant.

Can anyone tell me the status of the RaLink RT3090 with Ubuntu 10.04? I have looked through various posts here about getting this card working with earlier versions of the OS, where complicated procedures with mixed and apparently intermittent results are described. Do these measures also need to be followed with 10.04?

How can I tell if an old solution (say from some of the posts here from last autumn) is still valid for 10.04? (I don't really want to superstitiously keep trying things in the hopes that something might work. I'd prefer to diagnose what the real problem is and address that specifically. Although I'm not sure how much time it would be worth spending on it. Possibly better to take the computer back to the store and get a different one?)

Thank you in advance to anyone who can point me in the right direction towards getting this working.

A few notes/clarifications:

Note 1: I have not installed Ubuntu to my hard drive yet because I want to be sure it'll work first. I'm running from a bootable USB flashdrive set up from the ISO by Unetbootin (as described in [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)). Is there any reason to expect that wireless might work if the OS is booted from a HDD if it doesn't work when booted from USB?

Note 2: I also briefly tried running Ubuntu 10.04 Netbook Edition from the USB and that has the same problem with the wireless.

Note 3: Wired Ethernet works fine.

Note 4: Is it odd that the device is wlan0 rather than ra0? And is it odd that wlan0 seems to be associated with "RT2860 Wireless” and "RT2860STA" rather than with names with "RT3090" in them?

Note 5: The wireless works fine in Windows 7 and I make sure it is turned on when I shut down the system prior to booting from the USB.

Note 6: (Possibly irrelevant) The SONY VAIO update utility had me update the Windows driver for the RT3090. The reason given was that the factory installed driver causes problems with audio playback during boot.

===

nm-tool gives:

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt3090
  State:             unavailable
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            jme
  State:             connected
  Default:           yes

. . . plus more details on eth0.

===

lspci -v reports:

01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Flags: bus master, fast devsel, latency 0, IRQ 16.
	Memory at fe900000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt3090
	Kernel modules: rt3090sta

===

ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:24:be:ba:21:69  
          inet addr:192.168.10.107  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::224:beff:feba:2169/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3163 (3.1 KB)  TX bytes:4506 (4.5 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3312 (3.3 KB)  TX bytes:3312 (3.3 KB)

===

iwconfig reports:

lo        no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

===

"sudo lshw -C network" gives:

  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff
  *-network
       description: Ethernet interface
       product: JMC260 PCI Express Fast Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 02
       serial: 00:24:be:ba:21:69
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd  
autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=full ip=192.168.10.107  
latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:fe800000-fe803fff ioport:e100(size=128) ioport:e000(size=256)

===

"ifconfig wlan0 up" gives:
SIOCSIFFLAGS: Permission denied

"sudo ifconfig wlan0 up" gives:
SIOCSIFFLAGS: Operation not permitted

---

### Post by chili555 on 2010-05-22
> How can I tell if an old solution (say from some of the posts here from last autumn) is still valid for 10.04?What is it? We'll give you our opinion.> Is it odd that the device is wlan0 rather than ra0? And is it odd that wlan0 seems to be associated with "RT2860 Wireless” and "RT2860STA" rather than with names with "RT3090" in them?Nope. The various rtxxsta drivers are built by the same guy on, more or less, the same template. The native kernel versions all use wlanX rather than raX, as the compiled version uses. The RT2860 is just a placeholder until you connect with an actual access point.

You have a valid driver in place. Compiling another is not likely to change anything.

Several things come to mind. First, Network Manager is designed to not allow a wireless connection if wired is available. You have a wired connection now:> eth0 Link encap:Ethernet HWaddr 00:24:be:ba:21:69
inet addr:192.168.10.107 Please detach the wire and run:```
sudo lshw -C network
```Is wireless still shown as disabled?

Next, we'd love to see the result of:```
rfkill list all
rfkill unblock all
rfkill list all
```Finally, I wonder if the special driver *sony-laptop* is doing it's job correctly. Is it loaded?```
lsmod | grep sony
```Does it help to unload it?```
sudo rmmod -f sony-laptop
```Now move the switch and see if the wireless comes to life.

---

### Post by nlj on 2010-05-22
Thank you chili555. I followed your steps (details below), but no wireless yet.

Sorry. I didn't know that Network Manager disallows wireless if a wire is connected. I had plugged in the wired connection when I discovered that the wireless didn't work, but I see now that I should have run the reports first. However, even with no ethernet cable plugged in and after a restart, "sudo lshw -C network" still shows the Wireless interface as "DISABLED".

I tried "rfkill list all", "rfkill unblock all", "rfkill list all" but there was no output; the first one had nothing to list and I suppose the second one had nothing to unblock (or couldn't unblock it but reported no error) and for the third one there was still nothing to list. So all three commands just returned me to the command prompt.

"lsmod | grep sony" gave: "sony_laptop	33756	0". "sudo rmmod -f sony-laptop" produced no output, but repeating "lsmod | grep sony" now listed nothing so I guess the discrepancy between the underscore and the hyphen don't matter? (In any case, I ran through all these procedures several times (restarting in between) and the time I tried "sudo rmmod -f sony_laptop" the results were the same.)

The "sudo rmmod -f sony-laptop" seemed to have no effect on the wireless (or anything else that I noticed), and turning the wireless off and on with the physical switch and toggling "Enable Networking" and "Enable Wireless" in the Network Manager aplet in various orders didn't bring up the wireless (as far as I could tell from the status listed in Network Manager.

So where to I go from here. Are there more steps I can take to pinpoint the problem? Failing that, am I best to go with the ndis wrapper route, or rebuild the kernel with the newest RaLink driver? (The revision history on the lastest driver just says the change was to fix something on Apples, so possibly not useful. However, am I correct that the driver Ubuntu is currently using is not a Linux driver supplied by RaLink but is one written by the Linux team?)

---

### Post by orangenick on 2010-05-23
try this workaround, it worked for me (MSI L2300 - RT3090 on ubuntu 10.04):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

quote:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

HTH...

---

### Post by chili555 on 2010-05-23
May I see:```
dmesg | grep -i RT3
dmesg | grep -i RT2
```Thanks.

---

### Post by nlj on 2010-05-24
Thank you orangenick and chili555. That sorts out the problem. I now have wireless working on the RT3090 in my SONY VAIO M with Ubuntu 10.04 (64-bit).

The report from chili555's commands was as follows:

ubuntu@ubuntu:~$ dmesg | grep -i RT3
[   38.443096] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   38.545357] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   38.545410] rt3090 0000:01:00.0: setting latency timer to 64

ubuntu@ubuntu:~$ dmesg | grep -i RT2
[   39.363324] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   39.363335] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   39.368619] !!! rt28xx Initialized fail !!!
[   39.708075] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   39.708086] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   39.713495] !!! rt28xx Initialized fail !!!

So I checked for the file in question and as expected, it did not exist:
ubuntu@ubuntu:~$ ls /etc/Wireless/RT2860STA
ls: cannot access /etc/Wireless/RT2860STA: No such file or directory
ubuntu@ubuntu:~$ ls /etc/Wireless
ls: cannot access /etc/Wireless: No such file or directory

So I followed orangenick's procedure from Ubuntu >“linux” package > Bugs > Bug #541620 ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)), and created an empty file of the right name and in the right location and after restarting the Network Manager, there was my wireless working just fine. For future reference the steps that did the job were:

sudo mkdir -p /etc/Wireless/RT2860STA/
sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
sudo service network-manager restart

Note that because I was booting from USB and the filesystem reverted to it's pristine state every time I rebooted, the fix was not persistent over a reboot and I had to enter those three commands each time I started.

But I have now installed onto my hard drive and the fix is permanent.

Thank you very much for your assistance.

---

### Post by chili555 on 2010-05-24
Good job. Glad it's working.> However, am I correct that the driver Ubuntu is currently using is not a Linux driver supplied by RaLink but is one written by the Linux team?)In fact, the Ralink folks are a part of the Linux team and they do write the driver you are using:```
$ modinfo rt2870sta
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
[COLOR="Red"]alias:          rt3070sta[/COLOR]
version:        2.0.1.0
license:        GPL
description:    RTxx70 Wireless LAN Linux Driver
[COLOR="Red"]author:         Paul Lin <paul_lin@ralinktech.com>[/COLOR]
```

---

### Post by gargok on 2010-06-09
To me on my Asus eeePC 1001ha, this worked
> as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

wireless is active and looks for wireless networks... BUT
I cannot connect to my own hidden network with WPA

What did I do wrong? What should I do?

---

### Post by chili555 on 2010-06-09
Did you select 'Hidden Network' and fill in the details? Is your router set to WPA or WPA2 or the funny mixed WPA ***and*** WPA2 mode? Many here cannot connect in mixed mode. Please select WPA or WPA2 but not both.

---

### Post by gargok on 2010-06-09
Chilli555 thanks for your answer.
Yes, I selected 'Hidden Network' and filled in the details
> Is your router set to WPA or WPA2 or the funny mixed WPA ***and***  WPA2 mode? Many here cannot connect in mixed mode.
Router is in WPA-PSK mode with TKIP WPA encription.

shall you help me without loosing security??

---

### Post by flopfish on 2010-06-10
> **nlj said:**
> I am running Ubuntu 10.04 (64-bit) [with a] RaLink RT3090 wireless card. So far everything seems to work except the WLAN.
...
How can I tell if an old solution (say from some of the posts here from last autumn) is still valid for 10.04?

Yes, the old solution still works: The rt3090 driver packaged for Karmic in [this PPA]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") still works fine for me in Lucid.

That package ought to be rather portable.  Because it is built using [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support"), it contains the source code for the rt3090 kernel module (not some fragile binary), and it gets compiled automatically for your kernel at install time.  Any trouble due to using it in Lucid ought to be minimized.

Nevertheless, the rt3090 package mentioned above is a bit stale.  It hasn't been rebuild explicitly for Lucid (not that this should matter), and, more importantly, it is a version behind the most recent upstream driver release from RaLink.

I have built my own up-to-date rt3090 driver package based on the PPA mentioned above.  It's really easy to do, and I recommend that you give it a try.

I have written a guide on how to build your own rt3090 driver package for Ubuntu 10.04.  I have also posted my own pre-built rt3090 package for Lucid; you're free to download it and use it if you don't want to bother build it yourself.

Here is the guide to installing the rt3090 driver on Ubuntu 10.04 (Lucid):

[http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/)

---

### Post by sastowers on 2010-06-29
> **orangenick said:**
> try this workaround, it worked for me (MSI L2300 - RT3090 on ubuntu 10.04):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

quote:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

HTH...

Thank You! Thank You! Thank You! I've been stumped by this issue since I bought my Averatec N1200 Netbook....I have a dual boot Win7 and Ubuntu 10.04 and would prefer to use Ubuntu over 7 for everything but my audio recording, but was at the point that I was going to uninstall Ubuntu until I found this answer. If yer ever out in here in the hills, I'll give ya a good snort of grannies rheumatiz medicine fer yer kindness.....

:guitar:

---

### Post by padiamon on 2010-07-01
orangenick thank you so much . your post's so great........
it works very fine thank u again

---

### Post by philosopher2003@gmail.com on 2010-08-11
Ok I had this very problem to start when I first in stalled 9.10 and then when I installed 10.04.  I got drivers installed and had been working till the latest up date in may I believe.  I have been trying the various fixes and work arounds that I have been seeing but I'm not getting similar results.  Maby that is cause I'm still a nub!  

It is showing my card and the driver installed.  Except it says it is unclaimed.  
laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feaf0000-feafffff

As for other results I got this
dragonone@dragonone-laptop:~$ sudo mkdir -p /etc/Wireless/RT2860STA/
dragonone@dragonone-laptop:~$ sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
dragonone@dragonone-laptop:~$ dmesg | grep -i RT3
[   16.953316] rt3090sta: disagrees about version of symbol module_layout
dragonone@dragonone-laptop:~$ dmesg | grep -i RT2
dragonone@dragonone-laptop:~$ ls /etc/Wireless/RT2860STA
RT2860STA.dat


Help please

---

### Post by mylo9000 on 2010-08-12
i don't know why this worked but it did for my wife's laptop, so i'm not complaining.

sudo mkdir -p /etc/Wireless/RT[COLOR="Red"]3090[/COLOR]STA/
sudo touch /etc/Wireless/RT3090STA/RT[COLOR="Red"]3090[/COLOR]STA.dat
sudo service network-manager restart

for some reason the folder and and filename had to match the device exactly. i kept the previous folder RT2860STA as well. Just in case the drive decides to fall back on what did work before for no reason.

just wanted to let you know what worked for me.
:D\\:D/

---

### Post by shashi859 on 2010-08-15
> **orangenick said:**
> try this workaround, it worked for me (MSI L2300 - RT3090 on ubuntu 10.04):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

quote:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

HTH...


Thank you very much...

My new HCL Laptop was unable to connect to my home wifi using rt3090 driver and after trying lots of stuff this worked for me.

---

### Post by Julian2010 on 2010-08-24
Hello everyone here,

This is just to report my personal experience about setting to work the RT3090 Wifi device on a Compaq CQ10-410SF netbook, in case it may help someone else with the same machine..and the same WIFI problem.
I installed today Ubuntu 10.04 from the free CD and performed the on-line updates (through wired LAN of course) before trying to setup the WIFI link.
It took some time, as "only" 250 files were updated in the repo. between the CD release and today.
So I expected that everything would then just run fine..but the WIFI link did not.Although the WIFI LED was ON, the WIFI link could not be set up.
I followed the guidelines given in previous messages of this thread and checked the /etc/Wireless folder.It was not empty ( as it was for some users here) but the sub-folder was RT2860A (empty), not the expected RT2860STA.
I did not check anything else than that.
So I executed in terminal the 3 command lines given by orangenick on May 24th:
[B]"sudo mkdir -p /etc/Wireless/RT2860STA/
 sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
 sudo service network-manager restart"[/B]
  I left the existing and useless RT2860A subfolder as it was.
Then the WIFI link (WPA protected) could be easily set up and works fine.
So, many thanks to orangenick for his efficient solution.

---

### Post by ChrisZeh on 2010-09-04
> **orangenick said:**
> try this workaround, it worked for me (MSI L2300 - RT3090 on ubuntu 10.04):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

quote:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

HTH...


This worked for me, many thanks!!

For the record I have the Acer Aspire AX3400-U2022.
(lspci says I have a  RaLink RT3090 Wireless 802.11n 1T/1R PCIe)

It boggles my mind why just creating the folders and adding a blank file lets the wireless card start working?

But it is finally working, so maybe I shouldn't ask questions ;-)

---

### Post by Anxst on 2010-09-13
This worked for me, as well! MSI CX700 laptop.

Silly drivers looking for folders it didn't take the time to create.

Thanks, everyone!

---

### Post by pchampin on 2010-09-20
Hi all,

I have a Sony Vaio VPC M12M1E, and encountered the same problem: I could see the interface with iwcondig, but couldn't detect any network. Note also that the wireless LED never turned on, even when I used the hardware switch.

At first, orangenick's trick (creating /etc/Wireless/RT2860STA/RT2860STA.dat) didn't work for me. But then I realized that I had disabled wireless **from windows**, using sony-provided tools.

I rebooted on windows, re-enabled the wireless. When rebooting back to ubuntu, the wireless worked perfectly (i.e. hardware switch, LED, access to the network).

I just post this in case other people run into the same trouble. Thanks for this very useful thread.

---

### Post by milarepa12 on 2010-12-03
Thank you orangenick. 

> as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

worked on my Asus Eeepc 1001AH. With Karmic, I had to compile my kernel. That's great and saves a lot of time at each kernel upgrade...

---

### Post by raul.ya on 2011-01-03
I have an HP Pavilion Elite HPE-141es computer with Ubuntu 10.04.01 LTS (server version) 64 bit with gnome-desktop installed.

The wlan0 doesn't up and apears to be disabled. Could anyone help me? Thanks.

If I try **ifconfig wlan0 up** I get the message
[B]
SIOCSIFFLAGS: Operation not permitted[/B]

I paste here some information about my system:




**cat /etc/lsb-release **
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"


**lshw -c network**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 03
       serial: 40:61:86:f5:96:8e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=161.111.229.137 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:35 ioport:d800(size=256) memory:fbaff000-fbafffff memory:f6ffc000-f6ffffff(prefetchable) memory:fbac0000-fbadffff(prefetchable)
[B]  *-network DISABLED
       description: Wireless interface
       product: RT3092 Wireless 802.11n 2T/2R PCIe[/B]
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:fbff0000-fbffffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
**lsmod | grep rt**
rt3090sta             751243  0 
parport                37160  2 ppdev,lp

**iwlist scanning**
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

wlan0     No scan results

vboxnet0  Interface doesn't support scanning.
[B]
sudo iwconfig[/B]
lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

**dmesg | grep -i rt3**
[   20.620036] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   20.623426] rt3090 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.623488] rt3090 0000:05:00.0: setting latency timer to 64

**dmesg | grep -i rt2**
[   22.988374] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   22.988377] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   22.993545] !!! rt28xx Initialized fail !!!
[   23.005913] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   23.005914] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   23.011081] !!! rt28xx Initialized fail !!!

---

### Post by chili555 on 2011-01-03
> [ 23.005914] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[ 23.011081] !!! rt28xx Initialized fail !!!Did you try the fix in post #21?

---

### Post by raul.ya on 2011-01-03
I will try...

---

### Post by raul.ya on 2011-01-03
Wow !!!! It works fine !!!!!

Thansk.

---

### Post by ineedhelpplz on 2011-01-03
I had this problem a couple of months ago, i solved this by updating ubuntu. By this i mean 
you have to go to:

System>Administration>Update Manager.

then update and this worked for me.

---

### Post by datacrusher on 2011-03-25
the all arround quoted solution in creatint the .dat dummy file brought back to life the wireless in my cheap *** "qbex" brazilian brand of netbooks. 

wired eth works like a charm. wirelles works at home wpa2 network, but at work in wap2-enterprise, eap non certified network it dont work, when it gets in it works for about 1 minute and then simply stop transfering data. 

we have a LOT of cpters here working (1200 wireless users) with all sort of devices / cpters... very odd that 10.04 means to have long term support and dont work common drivers like this, reported longe ago in bug reports, with a solution quite clumsy to simply create a file and get it working. 

i downloaded and installed 10.04 netbook.iso and managed to get the wireless going by this very helpful post, but yet still ill be happy to see the 10.04 lts working on such popular pcs like these as soon as possible, and if does would be awesome that it worked here in the university :D

o/

---

### Post by Jiawen on 2011-03-29
With the latest kernel update (2.6.32-30), I can't get my wireless working. In fact, only 2.6.32-28 gives me wireless. The .deb I have installed is, I think, the most recent one. Trying to work through the RaLink driver's piles of config settings is beyond me. It's all very confusing. Has anyone figured this out?

---

### Post by Skybinary on 2011-04-13
> **orangenick said:**
> try this workaround, it worked for me (MSI L2300 - RT3090 on ubuntu 10.04):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

quote:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

HTH...

Worked for me for the acer aspire revo R3700 with RT3090 wlan module
Thanks :)

---

### Post by atlee on 2011-06-03
open terminal
sudo gedit /etc/modprobe.d/blacklist.conf
add blacklist rt2800pci to the bottom of file
save
exit, reboot
everything should work.

---

### Post by a.sarkar on 2011-06-24
Hi all,

Here's my experience to install ralink driver rt3090 on ubuntu 10.04.

**[COLOR=black]Option 1:[/COLOR]**
User orangenick's post. #4 in the list.

```
sudo mkdir -p /etc/Wireless/RT2860STA/
sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
sudo service network-manager restart
```Works. However, on my laptop, time taken to connect to any network is slow. The
network also goes up and down from time to time, even though other laptops show
full connectivity. Have to run the command
    ```
sudo service network-manager restart
```from time to time, to re-connect to available wireless. 

[B]Option 2:
[/B]Post #11 by user flopfish 
[http://www.halibutdepot.org/how_to_b..._ubuntu_lucid/]("http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/")

Either rebuild it as given by the instructions in the above post or download the 
pre-build deb package for ubuntu lucid with ralink driver 2.3.1.4 from the link below. (also posted in the above link)
[http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb]("http://stat.case.edu/%7Ejrt32/how_to_build_rt3090_for_ubuntu_lucid/rt3090-dkms_2.3.1.4-0ubuntu0%7Eppa1_all.deb")

This works. Now connection to network is really fast. I didn't install 
the prebuilt version. I followed the instructions to build it on my own.
Found out I had also to install the dpatch package on my system
as a pre-requisite
```
sudo apt-get install dpatch
``` Also, after, installation of the driver, via the command 
```
sudo dpkg -i rt3090-dkms_2.3.1.4-0ubuntu0~ppa1_all.deb
```I had to install the dkms package via the command
    ```
sudo apt-get install -f
``` Don't know if kernel update will break it or not. 
[B]
Option 3:[/B]
Post #30 by user atlee.

```
open terminal
sudo gedit /etc/modprobe.d/blacklist.conf
add blacklist rt2800pci to the bottom of file
save
exit, reboot
everything should work.
```Don't know if this works. Have not tried it. Will try it if kernel update
breaks option2 solution.

---

### Post by redmaniac on 2011-06-25
> **a.sarkar said:**
>  I didn't install 
the prebuilt version. I followed the instructions to build it on my own.


Which sources did you use? The 2.4.0.4 Version currently available on Ralink's website? Those did not compile for me and I wonder if that was because I did not use the patch mentioned in the HOWTO. 

cheers
redmaniac

---

### Post by a.sarkar on 2011-06-25
Dear @redmaniac, 
I used the pre-saved Ralink tar ball from this site

[http://stat.case.edu/~jrt32/how_to_build_rt3090_for_ubuntu_lucid/RT3090_LinuxSTA_V2.3.1.4_20100222.tar.bz2]("http://stat.case.edu/%7Ejrt32/how_to_build_rt3090_for_ubuntu_lucid/RT3090_LinuxSTA_V2.3.1.4_20100222.tar.bz2")

The above link is given in the HOWTO by flopfish. The driver in the 
above link is version 2.3.1.4 - not the latest one. But it works. Also I 
followed the HOWTO and applied the patches. Hope this helps.

---

### Post by a.sarkar on 2011-06-26
I thought after compiling and installing the RT3090 wireless driver version 2.3.1.4, as given in [this]("http://stat.case.edu/%7Ejrt32/how_to_build_rt3090_for_ubuntu_lucid/") website (Option 2 of post #31), wireless connection would be stable. However it isn't, even if the wireless signal strength is good.

So I decided to install the latest driver from the [Ralink website]("http://eng.ralinktech.com.tw/support.php?s=2") since the "Release Notes" of the latest driver version 2.4.0.4 says that auto-reconnect feature has been added in version 2.4.0.0.

Here are the steps that I followed.

Visited the [Ralink website]("http://eng.ralinktech.com.tw/support.php?s=2") and downloaded the [RT3090PCIe]("http://eng.ralinktech.com.tw/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09URTJORFF5TWpreU9TNTZhWEE5UFQweU1ERXdYekV5TVRkZlVsUXpNRGt3WDB4cGJuVjRVMVJCWDFZeUxqUXVNQzQwWDFkcFJtbENWRU52YldKdlgwUlFUdz09Qw%3D%3D") driver. (Before downloading the website asks for your name and email id).

Since I would be installing from src, I also installed gpaco
```
sudo apt-get install gpaco
```Paco keeps a log of the files installed manually via "make install" command. This way it is easy to uninstall manually installed files. 

Unzipped the downloaded Ralink driver file and used the following commands

```
cd 20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo paco -lD make
sudo paco -lD+ make install

```Note that usually the "make" command doesn't require root privileges. However, this driver package requires it. 

Hopefully now the connection would be stable. Will report back with results.

If one wants to uninstall the driver file, the command would be 
```
sudo gpaco
```if you have installed via paco.

---

### Post by redmaniac on 2011-06-26
@a.sarkar

I am curious to hear your results. I messed my system up pretty bad with that driver. It didn't compile from scratch and I "fixed" the sources. Should have used your gpaco tool I guess :D

---

### Post by a.sarkar on 2011-06-26
@redmaniac

Compiling the src from scratch worked without a glitch in my system.
Sorry to hear that it didn't workout for your system.
Could you post how exactly you fixed the source - could help others with the same problem as yours.

Yes gpaco works great in uninstalling if you are installing via paco. :D

---

### Post by redmaniac on 2011-06-27
> **a.sarkar said:**
> 
Could you post how exactly you fixed the source - could help others with the same problem as yours.


Well I put "fixed" in quotation marks because I'm sure that I screwed up the driver that way. So I'd rather not put it here. The fact that you compiled the sources without any trouble seems to indicate that there is something on your system that I do not have. The problem I face is this:  

In the folder where the driver sources are located there is a file 
```
os/linux/cfg80211.c
```This file will not compile on my system, since in the method 
```
TxPwrSet
```the type 
```
enum tx_power_setting
```is undefined.

But why is it defined for you? If I was missing a header file I think it would tell me so. I have now seen two or three posts by people who can compile this driver and all claim to use 10.10 (or haven't updated their profile). I am using 11.04. This still leaves me puzzled.

Oh, and before anyone asks: Linux headers are all installed, kernel is 2.6.38-8.

---

### Post by redmaniac on 2011-06-27
Well I'll be damned. I just checked the header cfg80211.h (/usr/src/linux-headers-*/include/net/cfg80211.h) here on my machine at work (kernel 2.6.32-32) and sure enough it contains an enum named tx_power_settings. I am sure I checked that file last night at home and found nothing of the sort (as I mentioned in my previous post, that's a different kernel). I'll double check later when I'm back home, but according to the files I just downloaded from here [http://packages.ubuntu.com/natty/linux-headers-2.6.38-8-generic](http://packages.ubuntu.com/natty/linux-headers-2.6.38-8-generic) there really is no definition of this enum in that header file.

Does anyone know whether this is a bug or a feature?  

EDIT: It's a feature [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fa61cf70a6ae1089e459e4b59b2e8d8e90d8535e](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fa61cf70a6ae1089e459e4b59b2e8d8e90d8535e)

So everybody with a newer kernel has to either patch the sources or wait....

---

### Post by a.sarkar on 2011-06-27
@redmaniac

I am using 10.04 and my kernel is 2.6.32-32. Since you are using 11.04, I guess, the updated kernel is incompatible with the ralink driver. Like you said, 

> **redmaniac said:**
> 
everybody with a newer kernel has to either patch the sources or wait...


until ralink releases a new compatible driver. Sorry couldn't help you much.

---

### Post by unixlinuxos on 2011-07-01
you can do a kernel update it i use a sony vaio m series netbook model vpcm111ax you can do a kernel update the reboot your pc and your wifi might work

---

### Post by unixlinuxos on 2011-07-01
do you use 11.04? does the wifi work? you want to do this in the terminal:
sudo add-apt-repository ppa:kernel-ppa/ppa

sudo apt-get update

then 
apt-cache showpkg linux-headers

after that 
sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing
I hope it helps

---

### Post by gnusci on 2011-07-02
I have seen zillions of problems with RaLink. Did you try wicd?

---

### Post by amorriso on 2011-07-02
Hey all

Can anyone lend an insight into what is occurring here?? The annoying symptom I'm trying to get rid of is random disconnects. I'm using the latest driver supplied by: 

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages)

I also have blacklisted a bunch of drivers

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
As described here:

[http://www.techytalk.info/2011/05/ralink-rt3090-ubuntu-driver-ppa/](http://www.techytalk.info/2011/05/ralink-rt3090-ubuntu-driver-ppa/)



Any info is greatly appreciated! 


I include the log file and info regarding the wireless device. 

**This is some of the output from /var/log/daemon.log**

Jul  2 07:54:32 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Jul  2 07:54:32 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 07:54:34 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 07:54:34 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 07:54:34 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 07:54:34 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 07:54:34 enceladus wpa_supplicant[1103]: Associated with 00:26:5a:16:cc:d9
Jul  2 07:54:34 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated
Jul  2 07:54:35 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake
Jul  2 07:54:35 enceladus wpa_supplicant[1103]: WPA: Key negotiation completed with 00:26:5a:16:cc:d9 [PTK=CCMP GTK=TKIP]
Jul  2 07:54:35 enceladus wpa_supplicant[1103]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:16:cc:d9 completed (reauth) [id=0 id_str=]
Jul  2 07:54:35 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake
Jul  2 07:54:35 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed
Jul  2 07:56:52 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:56:52 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:56:52 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Jul  2 07:56:52 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 07:56:54 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 07:56:54 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 07:56:54 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 07:56:54 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 07:56:54 enceladus wpa_supplicant[1103]: Associated with 00:26:5a:16:cc:d9
Jul  2 07:56:54 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated
Jul  2 07:56:54 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake
Jul  2 07:56:54 enceladus wpa_supplicant[1103]: WPA: Key negotiation completed with 00:26:5a:16:cc:d9 [PTK=CCMP GTK=TKIP]
Jul  2 07:56:54 enceladus wpa_supplicant[1103]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:16:cc:d9 completed (reauth) [id=0 id_str=]
Jul  2 07:56:54 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake
Jul  2 07:56:54 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed
Jul  2 07:57:14 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:57:14 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:57:14 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Jul  2 07:57:14 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 07:57:16 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 07:57:16 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 07:57:16 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 07:57:16 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 07:57:17 enceladus NetworkManager: <debug> [1309589837.000880] periodic_update(): Roamed from BSSID 00:26:5A:16:CC:D9 (virginjab) to (none) ((none))
Jul  2 07:57:19 enceladus wpa_supplicant[1103]: Associated with 00:26:5a:16:cc:d9
Jul  2 07:57:19 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated
Jul  2 07:57:19 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake
Jul  2 07:57:19 enceladus wpa_supplicant[1103]: WPA: Key negotiation completed with 00:26:5a:16:cc:d9 [PTK=CCMP GTK=TKIP]
Jul  2 07:57:19 enceladus wpa_supplicant[1103]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:16:cc:d9 completed (reauth) [id=0 id_str=]
Jul  2 07:57:19 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake
Jul  2 07:57:19 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed
Jul  2 07:57:23 enceladus NetworkManager: <debug> [1309589843.003421] periodic_update(): Roamed from BSSID (none) ((none)) to 00:26:5A:16:CC:D9 (virginjab)
Jul  2 07:58:33 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:58:33 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:58:33 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Jul  2 07:58:33 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 07:58:35 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 07:58:35 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 07:58:35 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 07:58:35 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 07:58:36 enceladus wpa_supplicant[1103]: Associated with 00:26:5a:16:cc:d9
Jul  2 07:58:36 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated
Jul  2 07:58:36 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake
Jul  2 07:58:36 enceladus wpa_supplicant[1103]: WPA: Key negotiation completed with 00:26:5a:16:cc:d9 [PTK=CCMP GTK=TKIP]
Jul  2 07:58:36 enceladus wpa_supplicant[1103]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:16:cc:d9 completed (reauth) [id=0 id_str=]
Jul  2 07:58:36 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake
Jul  2 07:58:36 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed
Jul  2 07:59:57 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:59:57 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 07:59:57 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Jul  2 07:59:57 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 07:59:59 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 07:59:59 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 07:59:59 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 07:59:59 enceladus wpa_supplicant[1103]: Associated with 00:26:5a:16:cc:d9
Jul  2 07:59:59 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated
Jul  2 07:59:59 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake
Jul  2 07:59:59 enceladus wpa_supplicant[1103]: WPA: Key negotiation completed with 00:26:5a:16:cc:d9 [PTK=CCMP GTK=TKIP]
Jul  2 07:59:59 enceladus wpa_supplicant[1103]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:16:cc:d9 completed (reauth) [id=0 id_str=]
Jul  2 07:59:59 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake
Jul  2 07:59:59 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed
Jul  2 08:02:38 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 08:02:38 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 08:02:38 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Jul  2 08:02:38 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 08:02:40 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 08:02:40 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 08:02:40 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 08:02:41 enceladus NetworkManager: <debug> [1309590161.000557] periodic_update(): Roamed from BSSID 00:26:5A:16:CC:D9 (virginjab) to (none) ((none))
Jul  2 08:02:44 enceladus wpa_supplicant[1103]: Associated with 00:26:5a:16:cc:d9
Jul  2 08:02:44 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated
Jul  2 08:02:44 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associated -> 4-way handshake
Jul  2 08:02:44 enceladus wpa_supplicant[1103]: WPA: Key negotiation completed with 00:26:5a:16:cc:d9 [PTK=CCMP GTK=TKIP]
Jul  2 08:02:44 enceladus wpa_supplicant[1103]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:16:cc:d9 completed (reauth) [id=0 id_str=]
Jul  2 08:02:44 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake
Jul  2 08:02:44 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed
Jul  2 08:02:47 enceladus NetworkManager: <debug> [1309590167.002552] periodic_update(): Roamed from BSSID (none) ((none)) to 00:26:5A:16:CC:D9 (virginjab)
Jul  2 08:03:40 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 08:03:40 enceladus wpa_supplicant[1103]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jul  2 08:03:40 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  completed -> disconnected
Jul  2 08:03:40 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 08:03:42 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 08:03:42 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 08:03:42 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 08:03:42 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 08:03:47 enceladus NetworkManager: <debug> [1309590227.002844] periodic_update(): Roamed from BSSID 00:26:5A:16:CC:D9 (virginjab) to (none) ((none))
Jul  2 08:03:47 enceladus wpa_supplicant[1103]: Authentication with 00:26:5a:16:cc:d9 timed out.
Jul  2 08:03:47 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected
Jul  2 08:03:47 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 08:03:49 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 08:03:49 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 08:03:49 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 08:03:49 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 08:03:54 enceladus wpa_supplicant[1103]: Authentication with 00:26:5a:16:cc:d9 timed out.
Jul  2 08:03:54 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected
Jul  2 08:03:54 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 08:03:56 enceladus NetworkManager: <info>  (ra0): device state change: 8 -> 3 (reason 11)
Jul  2 08:03:56 enceladus NetworkManager: <info>  (ra0): deactivating device (reason: 11).
Jul  2 08:03:56 enceladus NetworkManager: <info>  (ra0): canceled DHCP transaction, dhcp client pid 7239
Jul  2 08:03:56 enceladus NetworkManager: <WARN>  check_one_route(): (ra0) error -34 returned from rtnl_route_del(): Sucess#012
Jul  2 08:03:56 enceladus avahi-daemon[974]: Withdrawing address record for 192.168.1.7 on ra0.
Jul  2 08:03:56 enceladus avahi-daemon[974]: Leaving mDNS multicast group on interface ra0.IPv4 with address 192.168.1.7.
Jul  2 08:03:56 enceladus avahi-daemon[974]: Interface ra0.IPv4 no longer relevant for mDNS.
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0) starting connection 'virginjab'
Jul  2 08:03:56 enceladus NetworkManager: <info>  (ra0): device state change: 3 -> 4 (reason 0)
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  2 08:03:56 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> disconnected
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Jul  2 08:03:56 enceladus NetworkManager: <info>  (ra0): device state change: 4 -> 5 (reason 0)
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0/wireless): connection 'virginjab' has security, and secrets exist.  No new secrets needed.
Jul  2 08:03:56 enceladus NetworkManager: <info>  Config: added 'ssid' value 'virginjab'
Jul  2 08:03:56 enceladus NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jul  2 08:03:56 enceladus NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Jul  2 08:03:56 enceladus NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Jul  2 08:03:56 enceladus NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul  2 08:03:56 enceladus NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul  2 08:03:56 enceladus NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Jul  2 08:03:56 enceladus NetworkManager: <info>  Config: set interface ap_scan to 1
Jul  2 08:03:56 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 08:03:58 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 08:03:58 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 08:03:58 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 08:03:58 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 08:04:03 enceladus wpa_supplicant[1103]: Authentication with 00:26:5a:16:cc:d9 timed out.
Jul  2 08:04:03 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> disconnected
Jul  2 08:04:03 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Jul  2 08:04:05 enceladus wpa_supplicant[1103]: WPS-AP-AVAILABLE 
Jul  2 08:04:05 enceladus wpa_supplicant[1103]: Trying to associate with 00:26:5a:16:cc:d9 (SSID='virginjab' freq=2462 MHz)
Jul  2 08:04:05 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  scanning -> associating
Jul  2 08:04:05 enceladus wpa_supplicant[1103]: Association request to the driver failed
Jul  2 08:04:05 enceladus wpa_supplicant[1103]: Associated with 00:26:5a:16:cc:d9
Jul  2 08:04:05 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  associating -> associated
Jul  2 08:04:05 enceladus NetworkManager: <info>  (ra0): supplicant connection state:Association request to the driver failed  associated -> 4-way handshake
Jul  2 08:04:05 enceladus wpa_supplicant[1103]: WPA: Key negotiation completed with 00:26:5a:16:cc:d9 [PTK=CCMP GTK=TKIP]
Jul  2 08:04:05 enceladus wpa_supplicant[1103]: CTRL-EVENT-CONNECTED - Connection to 00:26:5a:16:cc:d9 completed (reauth) [id=0 id_str=]
Jul  2 08:04:05 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  4-way handshake -> group handshake
Jul  2 08:04:05 enceladus NetworkManager: <info>  (ra0): supplicant connection state:  group handshake -> completed
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'virginjab'.
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) started...
Jul  2 08:04:05 enceladus NetworkManager: <info>  (ra0): device state change: 5 -> 7 (reason 0)
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0) Beginning DHCP transaction (timeout in 45 seconds)
Jul  2 08:04:05 enceladus NetworkManager: <info>  dhclient started with pid 8259
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) started...
Jul  2 08:04:05 enceladus NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP6 Configure Get) complete.
Jul  2 08:04:05 enceladus dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jul  2 08:04:05 enceladus dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jul  2 08:04:05 enceladus dhclient: All rights reserved.
Jul  2 08:04:05 enceladus dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jul  2 08:04:05 enceladus dhclient: 
Jul  2 08:04:05 enceladus NetworkManager: <info>  DHCP: device ra0 state changed normal exit -> preinit
Jul  2 08:04:05 enceladus dhclient: Listening on LPF/ra0/e0:2a:82:13:aa:7d
Jul  2 08:04:05 enceladus dhclient: Sending on   LPF/ra0/e0:2a:82:13:aa:7d
Jul  2 08:04:05 enceladus dhclient: Sending on   Socket/fallback
Jul  2 08:04:07 enceladus dhclient: DHCPREQUEST of 192.168.1.7 on ra0 to 255.255.255.255 port 67
Jul  2 08:04:07 enceladus dhclient: DHCPACK of 192.168.1.7 from 192.168.1.1
Jul  2 08:04:07 enceladus dhclient: bound to 192.168.1.7 -- renewal in 34344 seconds.
Jul  2 08:04:07 enceladus NetworkManager: <info>  DHCP: device ra0 state changed preinit -> reboot
Jul  2 08:04:07 enceladus NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul  2 08:04:07 enceladus NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Jul  2 08:04:07 enceladus NetworkManager: <info>    address 192.168.1.7
Jul  2 08:04:07 enceladus NetworkManager: <info>    prefix 24 (255.255.255.0)
Jul  2 08:04:07 enceladus NetworkManager: <info>    gateway 192.168.1.1
Jul  2 08:04:07 enceladus NetworkManager: <info>    hostname 'dhcppc5'
Jul  2 08:04:07 enceladus NetworkManager: <info>    nameserver '192.168.1.1'
Jul  2 08:04:07 enceladus NetworkManager: <info>  Activation (ra0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul  2 08:04:07 enceladus NetworkManager: <info>  Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul  2 08:04:07 enceladus NetworkManager: <info>  Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Jul  2 08:04:07 enceladus avahi-daemon[974]: Joining mDNS multicast group on interface ra0.IPv4 with address 192.168.1.7.
Jul  2 08:04:07 enceladus avahi-daemon[974]: New relevant interface ra0.IPv4 for mDNS.
Jul  2 08:04:07 enceladus avahi-daemon[974]: Registering new address record for 192.168.1.7 on ra0.IPv4.
Jul  2 08:04:08 enceladus NetworkManager: <info>  (ra0): device state change: 7 -> 8 (reason 0)
Jul  2 08:04:08 enceladus NetworkManager: <info>  Policy set 'virginjab' (ra0) as default for routing and DNS.
Jul  2 08:04:08 enceladus NetworkManager: <info>  Activation (ra0) successful, device activated.
Jul  2 08:04:08 enceladus NetworkManager: <info>  Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Jul  2 08:04:08 enceladus ntpdate[8307]: adjust time server 91.189.94.4 offset -0.046766 sec


And ... 

**lshw -C network**
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       serial: e0:2a:82:13:aa:7d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.7 ip=192.168.1.7 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:c3400000-c340ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 64:31:50:55:af:98
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:2000(size=256) memory:c1404000-c1404fff(prefetchable) memory:c1400000-c1403fff(prefetchable) memory:c1410000-c141ffff(prefetchable)

---

### Post by unixlinuxos on 2011-07-08
a lot of the drivers are fighting for control of the pci card O.o you need to black list some of the drivers

---

### Post by a.sarkar on 2011-07-08
@amorriso

Are you using ubuntu 10.04 - if yes, then you can try to follow my post (#34) to download the latest driver from Ralink and compile it. The one from 

[https://launchpad.net/~markus-tisoft...3090/+packages]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+packages")

isn't the latest one. In my laptop, after installing the driver from src, frequency of random disconnects has gone down significantly. After reading your post I have also blacklisted a bunch of drivers (same as you). Hopefully this will completely stop the random disconnects.

---

### Post by amorriso on 2011-07-16
Hey all

So, I appear to have reduced/modified my problem (the current state is certainly less annoying than the previous). 

Current symptoms are: totally random freezes/disconnects of wicd with different errors to those produced with network-manager. I'll post more when I've worked out what is occurring. 

Semi-solution:

Unfortunately starts with ... 
1. replaced my 32 bit version of 10.04 with the 64 bit version (although I'm not sure if this really had any effect). 

2. installed the ra3090 driver from:
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages)
Just the standard lucid build (built 2010-08-27)

3. installed wicd (NOTE!!! don't update anything, updating for me really broke network-manager/wpa_supplicant/something - I don't know why)
4. service network-manager stop
5. At this stage I had to manually start the wicd daemon because it will failed to start b.c. network-manager was running (applications -> internet -> wicd)
6. Connected to my WPA network (I had to wait a couple of seconds -> minute before networks showed up)
7. I've since removed network-manager 

This is not a total solution but the situation is MUCH improved.

---

### Post by Flymo on 2011-08-30
Thanks, orangenick!

This worked just fine in U/Xubuntu 10.04.3 on the little eMachines ER1401, which has the Ralink RT3090 WiFi - and the AMD K325, nVidia 9200 graphics etc.

Nice simple solution....

Ben

> **orangenick said:**
> try this workaround, it worked for me (MSI L2300 - RT3090 on ubuntu 10.04):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

quote:

as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

HTH...

---

### Post by andoras on 2011-09-09
> **chili555 said:**
> 
Several things come to mind. First, Network Manager is designed to not allow a wireless connection if wired is available. You have a wired connection now:Please detach the wire and run:```
sudo lshw -C network
```Is wireless still shown as disabled?


That was a good opinion... well it works for me now :P
Thanks guys. I don't know how, because I followed more threads, but finally I got the signal.
Yeah!

---

### Post by ioan123 on 2011-09-18
I had major issues with the rt3090 driver, but eventually made it work - this is what I did, step by step. Before starting - it works fine with 10.04 32/64 bits and 11.04 32 bits (doesn't work with 11.04 64 bits - get a kernel error panic message as soon as I get connected to a WPA wireless network)

1 - Blacklist rt2800pci
a) sudo gedit /etc/modprobe.d/blacklist.conf
b) Insert this line at end of file --> blacklist rt2800pci

2 - Install driver
a) Add a ppa with rt3090 drivers, all instructions here [https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)
b) Open Synaptic, click on refresh repositories, search for 3090 & install (this will load the latest rt3090 sources and compile the driver)

3 - Load module when system starts
a) sudo gedit /etc/modules
b) Insert this line at end of file --> add rt3090sta

4 - reboot
--> Click on the network & you should see the list of wireless networks available

NOTE - make sure the wireless is hardware turned on!

Enjoy :p

Ioan

---

### Post by venkatams on 2011-11-11
After following these steps of "orangenick" with a slight difference of calling the directory and folder RT3090* as follows:
as root (or sudo before each line):
[COLOR="Blue"]mkdir -p /etc/Wireless/RT3090STA/
touch /etc/Wireless/RT3090STA/RT3090STA.dat
service network-manager restart[/COLOR]

on my acer veriton VN281G it still didn't work until I followed the steps provided by "atlee" in posting #30 it worked perfectly well. 

Many thanks.

---

### Post by nick4mony on 2012-05-19
> **orangenick said:**
> as root (or sudo before each line):
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart

HTH...

This also works on a HP Pavilion DV6 (but check the [font=courier][color=blue]lspci | grep -i ralink[/color][/font] to ensure the expected hardware is actually there), running Lucid 10.04, 64-bit.

---

