---
title: "Intel 82579LM card"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by Matt_C. on 2013-08-15
I'm about to lose my mind over here. . . I've been digging around forever with this.  I have a Lenovo T520 running Ubuntu 12.10, I just upgrade from 12.04 (the current ethernet issue happens with both).

Basically, I'm seeing the behavior described here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1176370](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1176370), although I'm seeing it with the 12.x versions not 13.x which is where that behavior was first reported.  Also, I have an Intel 82579LM gigabit card not an Atheros card as described in that bug report.

But, yes, the same thing happens, my ethernet (I don't use wireless) connection seems fine at boot up, then several minutes later, just appears to die.  If I restart the network connection, it's fine again. . . for a while, then it dies again eventually.  It's absolutely driving me crazy.

What I've done thus far:
1) installed the latest e1000e driver from Intel.
2) Modifed and then finally disabled Network Manager, I'm currently using ifup/ifdown to manage the ethernet connection
3) enabled and disabled my wireless connection, doesn't seem to make a difference at all, but as I mentioned I don't need or want to use wireless on this Ubuntu machine
4) the laptop is dual boot with Windows 7, from Windows 7, the ethernet connection seems fins
5) set up a static IP address for this laptop
6) I use Synergy to share a keyboard/mouse with my other laptop running Windows (not by choice!), I've tried disabling that too, doesn't make a difference
7) switched my laptops ethernet cable to a different port on my cable modem/router
8) I often connect to a Cisco VPN at work, whether I'm connected to the VPN also makes no difference for my wired connection

Any help is greatly appreciated!  Thanks in advance.

Current configuration, please let me know if any other diagnostic info would be helpful.  I didn't include the output from nm-tool because, as I've mentioned, I've disabled the Network Manager.
--------------------------------
lspci -nn | grep 0200


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
dmesg | grep -e eth0 -e e100

[    0.000000] ACPI: SSDT 00000000bafe1000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.652087] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
[    0.652091] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    0.652135] e1000e 0000:00:19.0: setting latency timer to 64
[    0.652201] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.652236] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    0.844876] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:d1:28:a4
[    0.844880] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    0.844945] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[   14.345580] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.576050] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   14.679801] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   14.680568] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.420082] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   17.420588] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1601.627016] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 1601.727836] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 1601.728762] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1604.990997] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 1604.991536] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3208.855652] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 3208.959083] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 3208.959812] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3211.695394] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 3211.695937] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4545.711609] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 4545.812213] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[ 4545.815076] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4548.536478] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 4548.537019] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
---------------------------------------------------------------------------------------------------------------------------------------
cat /etc/network/interfaces

auto lo
iface lo inet loopback
auto eth0 
iface eth0 inet static
address 192.168.0.5 
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.1
broadcast 192.168.0.255
dns-nameservers 209.18.47.61 209.18.47.62
------------------------------------------------------------------------------------------------------------------------------------------
cat /sys/devices/pci0000\:00/0000\:00\:19.0/power/control

on

---

### Post by chili555 on 2013-08-15
Let's have a look at:```
modinfo e1000e | grep version
```Please confirm this address is outside the DHCP pool in the router:> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address [COLOR="#FF0000"]192.168.0.5[/COLOR]
netmask 255.255.255.0
network 192.168.0.0
gateway 192.168.0.1
broadcast 192.168.0.255
dns-nameservers 209.18.47.61 209.18.47.62Also, I think your interfaces file is a bit busy. I suggest:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 209.18.47.61 209.18.47.62
```Also, would you please try:```
sudo modprobe -r e1000e
sudo modprobe e1000e EEE=0
```If it helps, we'll write one file to make it persistent.

---

### Post by Matt_C. on 2013-08-15
OK, output from comands:
----------------------------------------------------
modinfo e1000e | grep version


version:        2.0.0-k
srcversion:     8BE4A65E2266A2193761AAA
vermagic:       3.5.0-37-generic SMP mod_unload modversions 


--------------------------------------------------------------------------------------------
sudo modprobe -r e1000e


It seemed to print a bunch of empty strings to the console, I saw my shell prompt print a bunch of times, but no actual text was written to stdout.  That also seemed to disable my ethernet connection, when I run ifup eth0, it reports that the device can't be found.


-------------------------------------------------------------------------------------
sudo modprobe -r e1000e EEE=0


FATAL: Module EEE=0 not found.


Not sure if this is helpful after running the second command, perhaps this is the problem?


------------------------------------------------------------------------------------------------------------------------------


I cleaned up my interfaces file and rebooted as well.  Thanks for helping with this!

---

### Post by chili555 on 2013-08-15
> version: 2.0.0-kThat's not the latest version available for download. I suggest you retrace your steps and compile at least 2.3.2 which works well on my 13.04 system. [http://sourceforge.net/projects/e1000/files/e1000e%20stable/](http://sourceforge.net/projects/e1000/files/e1000e%20stable/) 
> sudo modprobe -r e1000e


It seemed to print a bunch of empty strings to the console, I saw my shell prompt print a bunch of times, but no actual text was written to stdout. That also seemed to disable my ethernet connection, when I run ifup eth0, it reports that the device can't be found.

We are trying to unload e1000e and reload it to include a driver parameter. Unloading (-r) is not in itself a fix for anything. It is merely the first step of a two-step process.> sudo modprobe -r e1000e EEE=0That's not the command I requested. Please try again.```
sudo modprobe -r e1000e 
sudo modprobe e1000e EEE=0
```

EDIT: 2.3.2 compilles perfectly on my 12.10 system and I suspect will fix your problem.

---

### Post by Matt_C. on 2013-08-15
Command output:
sudo modprobe -r e1000e
sudo modprobe e1000e EEE=0
FATAL: Error inserting e1000e (/lib/modules/3.5.0-37-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko): Invalid argument

That, of course, looks bad.  

I downloaded the latest driver from Intel's site: [https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&keyword=82579&lang=eng](https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&keyword=82579&lang=eng), but it appears that I did something wrong.  I'll try reinstalling it from SourceForge.

Thanks!

---

### Post by Matt_C. on 2013-08-15
The new driver's in place, I will see if it works better:
modinfo e1000e | grep version
version:        2.4.14-NAPI
srcversion:     E08BFA31FFBE6A8F2869CB9
vermagic:       3.5.0-37-generic SMP mod_unload modversions

Also, with this driver, I get no output from the two modprobe commands, which I'm going to assume is better than the error message I saw with the old driver.

Thanks again.

---

### Post by chili555 on 2013-08-15
> Also, with this driver, I get no output from the two modprobe commands, which I'm going to assume is better than the error message I saw with the old driver.Oh, yes! In this context, no response means, roughly, 'command accepted and executed. There are no errors or warnings to report.'

I will be interested in your report.

---

### Post by Matt_C. on 2013-08-16
Hey chili555, so far, so good.  I've been running all morning and I typically see the connection errors within 30 minutes or so.

So. . . fingers crossed/knock on wood, it looks like it's fixed. 

Thank you very much!

I'll update this thread if the issue recurs.

---

### Post by chili555 on 2013-08-16
> **Matt_C. said:**
> Hey chili555, so far, so good.  I've been running all morning and I typically see the connection errors within 30 minutes or so.

So. . . fingers crossed/knock on wood, it looks like it's fixed. 

Thank you very much!

I'll update this thread if the issue recurs.Great news. Glad it's working. If you feel that it is, please mark this thread Solved so that the searchers will see the solution.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Matt_C. on 2013-08-16
Will do, I'm going to wait until the end of the day though. . . just to be sure.  :)

---

### Post by Matt_C. on 2013-08-16
Uggh, nope it's still happening.  My other laptop (running Windows) is on the same wired network and has great performance.  My Ubuntu laptop's network connection has slowed down to a crawl again.

What should I try next?

---

### Post by Matt_C. on 2013-08-16
EDIT: didn't mean to post this a second time, I didn't realize that my response succeeded (it was during the network sluggishness) and was posted to page 2 of this thread.

Unfortunately, this did not fix the issue.  It just happened again.  My Windows laptop was fine while my Ubunut laptop's internet connection slowed down to a crawl.  

What should I try next?

---

### Post by chili555 on 2013-08-16
I suggest this:```
sudo modprobe -r e1000e 
sudo modprobe e1000e EEE=0
```See if it is stable. If so, we'll write a quick file and make it persistent. If not, let's check the logs:```
cat /var/log/syslog | grep -e e100 -e eth0 | tail -n20
```If the result is sparse, then try:```
cat /var/log/syslog.1 | grep -e e100 -e eth0 | tail -n20
```

---

### Post by Matt_C. on 2013-08-16
OK, I was able to get it back into the slow state fairly easily, I just opened about 6 tab in my browser window to various pages and refreshed each several times.  Anyway, yes the ethernet driver/connection appeared stable in that the modprobe commands didn't generate any output.  Here's the output from the next two commands:
--------------------------------------------------------------------------------------------------------------------------------------------------
cat /var/log/syslog | grep -e e100 -e eth0 | tail -n20

Aug 16 14:23:23 localhost kernel: [21921.297360] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 14:23:23 localhost kernel: [21921.397781] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 14:23:23 localhost kernel: [21921.398694] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 16 14:23:26 localhost kernel: [21924.688833] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Aug 16 14:23:26 localhost kernel: [21924.689400] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug 16 22:09:05 localhost kernel: [49800.188064] e1000e: Intel(R) PRO/1000 Network Driver - 2.4.14-NAPI
Aug 16 22:09:05 localhost kernel: [49800.188066] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
Aug 16 22:09:05 localhost kernel: [49800.188100] e1000e 0000:00:19.0: setting latency timer to 64
Aug 16 22:09:05 localhost kernel: [49800.188162] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
Aug 16 22:09:05 localhost kernel: [49800.188164] e1000e 0000:00:19.0: EEE Support Disabled
Aug 16 22:09:05 localhost kernel: [49800.188195] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 22:09:05 localhost kernel: [49800.377935] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:d1:28:a4
Aug 16 22:09:05 localhost kernel: [49800.377939] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Aug 16 22:09:05 localhost kernel: [49800.378005] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
Aug 16 22:09:05 localhost kernel: [49800.566111] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 22:09:05 localhost kernel: [49800.666863] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 22:09:05 localhost kernel: [49800.667794] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 16 22:09:08 localhost kernel: [49803.527721] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Aug 16 22:09:08 localhost kernel: [49803.528254] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready



--------------------------------------------------------------------------------------------------------------------------------------------------
I don't know if the above qualifies as sparse, so here's the output from the second command as well:
cat /var/log/syslog.1 | grep -e e100 -e eth0 | tail -n20

Aug 15 17:16:46 localhost kernel: [  250.964613] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 15 17:16:46 localhost kernel: [  251.068148] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 15 17:16:46 localhost kernel: [  251.068961] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 15 17:16:49 localhost kernel: [  253.932940] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Aug 15 17:16:49 localhost kernel: [  253.933678] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug 16 08:17:26 localhost kernel: [    0.000000] ACPI: SSDT 00000000bafe1000 00996 (v01  PmRef    CpuPm 00003000 INTL 20061109)
Aug 16 08:17:26 localhost kernel: [    0.647637] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
Aug 16 08:17:26 localhost kernel: [    0.647641] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
Aug 16 08:17:26 localhost kernel: [    0.647690] e1000e 0000:00:19.0: setting latency timer to 64
Aug 16 08:17:26 localhost kernel: [    0.647765] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
Aug 16 08:17:26 localhost kernel: [    0.647801] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 08:17:26 localhost kernel: [    0.843641] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:d1:28:a4
Aug 16 08:17:26 localhost kernel: [    0.843645] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Aug 16 08:17:26 localhost kernel: [    0.843711] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
Aug 16 08:17:26 localhost kernel: [   14.359280] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 16 08:17:26 localhost kernel: [   14.651498] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 08:17:26 localhost kernel: [   14.754078] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
Aug 16 08:17:26 localhost kernel: [   14.754702] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 16 08:17:29 localhost kernel: [   18.049032] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Aug 16 08:17:29 localhost kernel: [   18.049469] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


I'm not familiar with any of this really, but the IPv6 lines look suspicious, could they be related to this issue?

---

### Post by Matt_C. on 2013-08-19
Hmmm. . . running out of ideas here.  I just changed my network cable, modem/router port and I just disabled IPV6.  The issue is still happening.  Not sure what to try next.  I might just boot into my Windows partition and see if I can reproduce the issue there.  

I'm thinking that maybe this is related to hibernate/suspend. . .  I've disabled both.

---

### Post by chili555 on 2013-08-19
This parameter goes away on reboot:```
sudo modprobe -r e1000e 
sudo modprobe e1000e EEE=0
```When you implement it temporarily, is the speed improved? I really don't see anything suspicious in your message log.

---

### Post by Matt_C. on 2013-08-19
Yes, that seems to bring it back from the dead.  So does running sudo ifdown eth0;sudo ifup eth0.  As did restarting the connection via the Network Manager before I disabled it.

My next ideas are to try not using Synergy with my Ubuntu laptop and to try booting into Windows for the whole day to see if the wired internet connection will be slow with those configurations as well.  I've booted into Windows and looked at the network card's properties and it appears fine.

It does feel like Synergy might be at play here - I have no idea why though.  It appears that this problem always happens with I switch my keyboard/mouse back to Ubuntu from Windows.  It could be a red herring.

Here's the output from route -v
----------------------------------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0


I'm not sure why the subnet mask is 0.0.0.0 on the first line, I'd expect it to be 255.255.255.0.  Not sure if this makes a difference here or not.

---

### Post by chili555 on 2013-08-19
If it seems to help, I suggest you make it persistent:```
gksudo gedit /etc/modprobe.d/e1000e.conf
```Add a single line:```
options e1000e EEE=0
```Proofread carefully, save and close gedit.

The parameter will now load on boot automagically.

I look forward to the results of your further experiments.

---

### Post by Matt_C. on 2013-08-19
-----------------------------------------------------------------------------
cat /etc/modprobe.d/e1000e.conf
options e1000e EEE=0



It actually seems worse after making this change.  What I'm considering now is running a full day in Windows to see if it's only happening with Ubuntu and then if it is only a Unbuntu issue, I might just wipe out my hard drive and install 13.04.

Thanks for the help.  I'm thoroughly baffled at this point.

---

### Post by Matt_C. on 2013-08-19
Don't know if it makes a big difference but I had a carriage return after the[COLOR=#000000] "options e1000e EEE=0".  I've since removed it, I'll try it out a bit longer and then try my day long Windows experiment.[/COLOR]

---

### Post by Matt_C. on 2013-08-20
OK, just as I suspected, this is a problem only with Ubuntu.  I've been running Windows all day from the same laptop and my internet connection has been fine.  Not sure what to do next. . . contemplating reinstalling Unbuntu from scratch, probably 13.04 at this point.

---

### Post by chili555 on 2013-08-20
> **Matt_C. said:**
> OK, just as I suspected, this is a problem only with Ubuntu.  I've been running Windows all day from the same laptop and my internet connection has been fine.  Not sure what to do next. . . contemplating reinstalling Unbuntu from scratch, probably 13.04 at this point.That's certainly a reasonable approach. The driver e1000e is still not working well in 13.04 and you'll probably need to compile at least 2.3.2 for it to work at all.

You could try the live CD first and even compile the later e1000e driver to test.

---

### Post by Matt_C. on 2013-08-20
Live CD's probably the smart approach to take first.  Thanks!

---

### Post by Matt_C. on 2013-08-29
So. . . as it turns out, my problem was with my ISP's modem/router.  I have a Cisco router that I use for my wireless hosts and when I plug my Ubuntu laptop's ethernet cable into the Cisco router, I no longer see this problem.  Unfortunately, I found this out after I wiped my hard drive and reinstalled Ubuntu.  :(  Not the end of the world though because I wanted to upgrade to 13.04 anyway.

My internet connection is a bit slower going through my personal router which makes sense because there's a second device involved.  I have no idea why my ISP's router was doing what it did.  I suppose it could be a bug/config issue with their router.  At this point, I've wasted enough time and I have a good enough workaround that I'm not going to worry about it anymore.

---

### Post by chili555 on 2013-08-30
Glad it's working by whatever means.

---

### Post by Matt_C. on 2013-09-04
Me too.   Thanks for the help.

---

