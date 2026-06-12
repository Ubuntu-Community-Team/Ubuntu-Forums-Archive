---
title: "No wireless. Driver conflict? Can't blacklist ath_hal."
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by sina94 on 2009-05-29
My wireless stopped working yesterday. The day before I did some cleaning up from my Jaunty upgrade. GRUB had never gotten updated for whatever reason, so I updated GRUB... whichever option I chose switched the root hard drive from sda1 to hda1, so I had to fix that (may have also changed other things). I also re-selected "Important security updates" and "Recommended updates" in Software Sources (which had apparently been deselected when I upgraded to Jaunty). I then upgraded the ~120 packages that came up with those options selected. I also upgraded intel drivers as instructed on the Ubuntu AspireOne wiki 

> *Optional* You can get latest version of Intel driver (v. 2.7.0) by adding the following ppa to your sources: deb [http://ppa.launchpad.net/glasen/ppa/ubuntu](http://ppa.launchpad.net/glasen/ppa/ubuntu) jaunty main

Those are the only major changes that I can recall from the last few days. My wireless went down mid-session with no apparent cause (it had been working after all of the aforementioned changes and just stopped working randomly).

Network manager initially said that there was no wireless device. Something I did in the process of trying to fix the problem fixed this problem (recompiling drivers, blacklisting modules, etc.). However, it still can't detect any networks (it usually finds about 10, including mine).

When I perform

> lsmod |grep ath

I get the following:

> ath_rate_sample        21120  1 
ath_pci               218296  0 
wlan                  238064  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312160  3 ath_rate_sample,ath_pci

My first thought is that it's a conflict between ath_pci and ath_hal. However, ath_hal has been added to /etc/modprobe.d/blacklist.conf. But, it still comes up when I boot. I don't know what else might be causing it to load in spite of it being blacklisted (I'm relatively new to linux). And when I perform
> 
sudo modprobe -r ath_hal

I get
> 
FATAL: Module ath_hal is in use.

Very frustrating. I have a feeling that if I could get rid of ath_hal it would remedy my wireless woes... but I don't know how to.

Any help would be appreciated. Here's some additional info that might be helpful.

dmesg | grep -e ath -e wlan

> [    3.028790] device-mapper: multipath: version 1.0.5 loaded
[    3.028796] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.449312] ath_hal: module license 'Proprietary' taints kernel.
[    6.658642] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.658669] ath_pci 0000:03:00.0: setting latency timer to 64
[    7.153564] MadWifi: ath_attach: Switching rfkill capability off.
[    7.601973] ath_pci: wifi0: Atheros 5424/2424: mem=0x75200000, irq=18
[   24.684069] ath0: no IPv6 routers present

lshw -C Network

> WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:be:59:88
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.51 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:22:69:22:0a:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ba:6d:27:37:69:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

ifconfig

> ath0      Link encap:Ethernet  HWaddr 00:22:69:22:0a:85  
          inet6 addr: fe80::222:69ff:fe22:a85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:be:59:88  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:febe:5988/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5187626 (5.1 MB)  TX bytes:2580680 (2.5 MB)
          Interrupt:251 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-22-69-22-0A-85-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:1702 (1.7 KB)
          Interrupt:18 



iwconfig

> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


---

### Post by Chris_no on 2009-05-29
I'm not sure if you have a driver conflict or not.

Your wifi interrupt ( 18 ) does not conflict with your 
eth0 interrupt ( 251 ).

Your ath has not been assigned an ip address as one would
expect from your description of the problem.

You describe ALOT of stuff that may be responsible.

I assume that reboot didn't do the trick.

You may want to disable your wireless card and/or remove all packages
and modules that can be responsible and install them again as a last resort
if no one else has a better answer.

---

### Post by sina94 on 2009-05-29
Nope. Reboot definitely didn't help.

How do I remove the modules if it comes to that? Simply delete them from a directory (and if so, which one?)?

---

### Post by Chris_no on 2009-05-29
Before you start to do anything big and drastic.

Let me see if I get what you are trying to do correct here.

You have tried to install Jaunty and somehow after update
your wireless card stopped working?

If that is the case you may be better of backing up all your info
and reinstalling ubuntu. 

Trying to untangle broken modules/packages when you don't even know
which one is responsible is NO FUN!

I don't know your situation well enough to advice a specific cure.
It might be helpful to see the output of lsdev and/or procinfo.

However wait a day or two before you do anything big, someone else may
have the answer.

---

### Post by sina94 on 2009-05-29
Here's the output of procinfo:

> Memory:        Total        Used        Free     Buffers                       
RAM:         1532472     1060796      471676      150020                       
Swap:              0           0           0                                   

Bootup: Thu May 28 20:33:18 2009   Load average: 0.72 0.48 0.31 4/229 11840    

user  :   00:22:20.23   6.7%  page in :           569356                       
nice  :   00:00:18.83   0.1%  page out:           255268                       
system:   00:05:24.25   1.6%  page act:            91000                       
IOwait:   00:10:12.71   3.1%  page dea:                0                       
hw irq:   00:00:21.05   0.1%  page flt:          5030590                       
sw irq:   00:00:06.16   0.0%  swap in :                0                       
idle  :   04:54:10.15  88.4%  swap out:                0                       
uptime:   02:43:07.62         context :          4678178                       

irq   0:    1051787  timer                irq  15:      57392  ata_piix         
irq   1:      11373  i8042                irq  16:     646639  ehci_hcd:usb1, uh
irq   8:          1  rtc0                 irq  17:          0  uhci_hcd:usb3    
irq   9:      13422  acpi                 irq  18:         74  uhci_hcd:usb4, at
irq  12:    1312602  i8042                irq  19:        303  uhci_hcd:usb5, mm
irq  14:          0  ata_piix            irq 2299:     129821  eth0             

sda            43205r           14187w   mmcblk0              92r              
sda1           43149r           14187w   mmcblk0p1              85r            
sda2              35r               0w                                         

lo          TX 240.00B       RX 240.00B       wlan0       TX 0.00B         RX 0.00B        
eth0        TX 6.53MiB       RX 14.14MiB      pan0        TX 0.00B         RX 0.00B        
wmaster0    TX 0.00B         RX 0.00B 

And, apparently ath_hal is loaded with ath_pci. I was under the impression that it was an unrelated module.

And it was about 3 weeks ago that I upgraded to Jaunty from Intrepid. It was just GRUB that hadn't been updated since then.

---

### Post by t0mppa on 2009-05-29
Ath_hal is indeed used by ath_pci and the driver won't work, if you kill ath_hal away.

What's important on Jaunty though, is that ath5k was changed to be the default driver for Atheros cards, as its development is finally far enough to surpass the older madwifi driver (ath_pci). Ath5k and ath9k are the new drivers developed by madwifi, whereas ath_pci was the original one and is on the process of being replaced by the newer ones.

Your procinfo shows wlan0 and wmaster0, which are what ath5k calls its interfaces (rather than ath0 and wifi0 with ath_pci & friends), so that suggest ath5k might be doing something as well and it could be the one creating conflicts. Also Jaunty creates a /etc/modprobe.d/blacklist-ath_pci.conf file, which does just that, blacklists ath_pci. Should probably comment out the blacklisting from there, if you plan to use the ath_pci.

So, summa summarum, I'd crawl through the blacklists and make sure that ath5k is blacklisted and none of the ath_pci related modules aren't. Or if you want to try something different, could just try letting ath5k run your interface by doing the opposite.

---

### Post by sina94 on 2009-05-29
Sorry. I've been going back and forth between the madwifi and the ath5k drivers. Must've loaded the ath5k before I did the procinfo. Here's the one with the madwifi drivers.

> Memory:        Total        Used        Free     Buffers                       
RAM:         1532472      657332      875140       38384                       
Swap:              0           0           0                                   

Bootup: Thu May 28 23:58:46 2009   Load average: 0.92 0.58 0.52 2/227 8482     

user  :   00:21:06.51   8.6%  page in :           257086                       
nice  :   00:00:18.92   0.1%  page out:           145476                       
system:   00:05:17.02   2.2%  page act:            32558                       
IOwait:   00:06:09.79   2.5%  page dea:                0                       
hw irq:   00:00:17.44   0.1%  page flt:          3604720                       
sw irq:   00:02:11.47   0.9%  swap in :                0                       
idle  :   03:29:21.79  85.6%  swap out:                0                       
uptime:   01:58:29.60         context :          4832069                       

irq   0:    1363653  timer                irq  15:      26668  ata_piix         
irq   1:       1400  i8042                irq  16:     442910  ehci_hcd:usb1, uh
irq   8:          1  rtc0                 irq  17:          0  uhci_hcd:usb3    
irq   9:       9898  acpi                 irq  18:      31864  uhci_hcd:usb4, wi
irq  12:     819948  i8042                irq  19:        262  uhci_hcd:usb5, mm
irq  14:          0  ata_piix            irq 2299:      51247  eth0             

sda            15561r           11105w   sdb              121r               6w
sda1           15498r           11105w   sdb1              73r               6w
sda2              42r               0w   sdb2               4r               0w
mmcblk0              92r                 sdb5              18r               0w
mmcblk0p1              85r                                                     

lo          TX 240.00B       RX 240.00B       ath0        TX 0.00B         RX 0.00B        
eth0        TX 2.61MiB       RX 41.67MiB      pan0        TX 0.00B         RX 0.00B        
wifi0       TX 1.40MiB       RX 0.00B 

With both drivers I get "No scan results" from iwlist scan.

---

### Post by t0mppa on 2009-05-29
Ok then, long as they aren't both loaded, either one should work. At least something is happening with this one, since it shows wifi0 with 1.4MiB transmitted. If dmesg doesn't offer any clues to what might be wrong, I'm afraid I'm out of ideas then as well.

It's starting to resemble what Chili55 labeled as his favorite problem: everything looks correct, but it still doesn't work.

---

### Post by sina94 on 2009-05-29
Sounds like a good favorite problem to have. Haha.

Any chance that it's a hardware issue? Especially with the way it cut out mid-session. Any way to test if the hardware is faulty?

---

### Post by Chris_no on 2009-05-29
I use madwifi and it works like a charm on my acer aspire one.

Another option you have is to get linux4one.
It is tailormade for the aspire one.

As t0mppa pointed out though no need to blacklist anything
since it is the same driver.

I assume you havn't changed the other network settings (dhcp, static, ip address stuff) you may need to reload that and restart networking after you
have set the modules back in place.

sudo /etc/init.d/networking restart

---

### Post by Chris_no on 2009-05-29
Something has changed since you downloaded your drivers.

*Optional* You can get latest version of Intel driver (v. 2.7.0) by adding the following ppa to your sources: deb [http://ppa.launchpad.net/glasen/ppa/ubuntu](http://ppa.launchpad.net/glasen/ppa/ubuntu) jaunty main [Edit: The more recent and complete updates might be available here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/])

---

### Post by sina94 on 2009-05-29
> **Chris_no said:**
> 
I assume you havn't changed the other network settings (dhcp, static, ip address stuff) you may need to reload that and restart networking after you
have set the modules back in place.

sudo /etc/init.d/networking restart

I haven't changed network settings. I have done a "sudo /etc/init.d/networking restart" at several points... I don't know exactly what you mean by "reload that" and restart networking.

> **Chris_no said:**
> [Edit: The more recent and complete updates might be available here: [https://launchpad.net/~ubuntu-x-swat...ve/x-updates/]](https://launchpad.net/~ubuntu-x-swat...ve/x-updates/])

That was technically a part of my options when I installed the intel drivers from the other repository. Since it said they "might be available here" I went ahead and went with the option that was tried and true. And it fixed my video problems, so I figured I'd stick with that. Don't know that video drivers have much effect on my wireless issues... but went ahead and installed the updates from the ubuntu-x repository anyways. No improvement.

---

### Post by Chris_no on 2009-05-29
By reloading I mean that you change your ip address and other settings to something other than what you had and then change them back again and pray that something just magically fall into place somewhere.

Other than that I have zero new ideas. Good luck.

---

### Post by t0mppa on 2009-05-29
> **Chris_no said:**
> By reloading I mean that you change your ip address and other settings to something other than what you had and then change them back again and pray that something just magically fall into place somewhere.

Ah, the good old "restart and while the computer is busy with that change the order of your coats on the rack" fix that so often miraculously works its magic and fixes computer problems.

---

### Post by Chris_no on 2009-05-30
Alot of people have alot of issues with wireless on Jaunty (9.04).

[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

I use Hardy (8.04) and I'm sticking with it until I know for a fact
that all the issues have been sorted out.
I did the same when I had Feisty (7.04). It is ALWAYS alot of issues when they issue a new version.

---

### Post by sina94 on 2009-06-02
> **t0mppa said:**
> Ah, the good old "restart and while the computer is busy with that change the order of your coats on the rack" fix that so often miraculously works its magic and fixes computer problems.

Yup... that's pretty much how it happened. My roommate had Knoppix on a flash drive... so plugged that in to see if I got any results. He was like "lemme see!"... ifconfig down, ifconfig up, dmesg... and the piece of crap starts working.

Of course, this is the same day that I blow a circuit running a TV, microwave, A/C, and computer all on the same circuit... after resetting the breaker I got no results. He does it... everything starts working.

I swear... the kid has magic powers.

---

### Post by t0mppa on 2009-06-02
Sounds like a very handy roommate to have though. No need to worry about breaking anything, when you can just have mr. Magic touch fix it. :D

---

