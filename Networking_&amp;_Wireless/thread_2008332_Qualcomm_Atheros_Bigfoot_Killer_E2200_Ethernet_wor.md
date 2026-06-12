---
title: "Qualcomm Atheros Bigfoot Killer E2200 Ethernet working in linux"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by Mahler122 on 2012-06-22
Hi All,

I have found a way to get the Qualcomm Atheros Bigfoot Killer E2200 ethernet card to work with existing Atheros linux drivers. Following in the footsteps of this post: [http://ubuntuforums.org/showthread.php?p=12028162](http://ubuntuforums.org/showthread.php?p=12028162). I have basically 'stolen' the driver of a related card with existing linux drivers.

I have created a patch to be applied to the compat-wireless kernel modules. After application of this patch and procedure, my ethernet card worked.

The module which will be modified is alx, and after I told the kernel to load it explicitly by editing /etc/modules, My ethernet card was discovered at startup and properly suspended and hibernated. I can verify that gigabit speeds are possible with this 'stolen' driver.

I haven't had any probles yet, but I will post a reply to this thread if a problem appears at some later date, or Atheros releases a proper driver for this card.

You will need to install a few packages

```
sudo apt-get install build-essential linux-headers
```

You will need to download the compat-wireless-2012-05-10-p tarball from here: [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-05-10-p.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-05-10-p.tar.bz2)

And download the attached compat-patch.txt.

Untar the tarball into a convenient location, and apply the patch making sure to use the --dry-run option to make sure there are no errors.

```
tar -xvf /path/to/compat-wireless-2012-05-10-p.tar.bz2
cd ./compat-wireless-2012-05-10-p.tar.bz2
patch --dry-run -p2 < /path/to/compat-patch.txt
patch -p2 < /path/to/compat-patch.txt
```

Now make and assuming no errors arise, install the package.

```
make
sudo make install
```

Now test that the module works by inserting it into the running kernel.

```
sudo modprobe alx
```

Your ethernet card should be discovered, and assuming you have the ethernet plugged into a working jack with dhcp, you should become connected to ethernet.

Assuming this is the case, modify your /etc/modules file so that this module is loaded at startup by adding the following lines at the end.

```
#E2200 support
alx
```

And you're good to go. Let me know how this works out for you.

---

### Post by Paddy Landau on 2012-06-23
Thank you for posting this for others to see.

If you [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), it will help others find it.

---

### Post by Mahler122 on 2012-06-23
No problem!, Done.

---

### Post by belnac on 2012-06-25
Awesome, Mahler! Many thanks for this - will try it out at once.

---

### Post by belnac on 2012-06-25
Using Kernel 3.5.0-rc3, compilation fails on ./net/bluetooth/rfcomm/tty.c

Attached is a simple patch I've just created that fixes the compilation error, which is caused by different function definitions for tty_unlock and tty_lock; current version of tty.c expects the two (mutex) functions to accept an argument, which they now don't anymore.

Mahler, thanks again for this - the NIC has now been brought to life!

---

### Post by Mahler122 on 2012-06-25
Just so I'm clear on this, this patch is meant to be applied after my patch correct?

I tested my patch with the 3.2.0 kernel. It's good to know about this compilation error with the 3.5-rc's.

---

### Post by belnac on 2012-06-25
> **Mahler122 said:**
> Just so I'm clear on this, this patch is meant to be applied after my patch correct?

Yes, correct. Applying just your patch results in the compilation error mentioned above - and that was whilst compiling with kernel 3.5.0-rc3; haven't tested with other kernels. Applying the second patch fixes it and compilation proceeds nicely.

---

### Post by Mahler122 on 2012-06-26
Just so everyone knows, I suspect that I'm experiencing the first issues related to this 'stolen' driver. It seems that everything simply freezes after ~ 2.5 days or so of use. The only route to recovery seemed to be a hard boot. However it might just be the graphical interface. Next time it happens I'm going to see whether my machine responds to ssh. (It's happened twice so far)

Please let me know if you experience this as well, and try not to have essential documents and what not loaded into ram to avoid losing them if this happens and you need to hard boot.

Of course, Atheros needs to release a legitimate driver which won't crash the kernel, but in the meantime, for me the NIC working is worth worrying about the crashing.

---

### Post by chili555 on 2012-06-26
> It seems that everything simply freezes after ~ 2.5 days or so of use. The only route to recovery seemed to be a hard boot.What does /var/log/syslog suggest the origin of the lock-up is?

---

### Post by Mahler122 on 2012-06-26
I'd say nothing. There is just a time gap between when the last message was issued, and when the first kenel boot message appears.

Here are the lines surrounding the gap which I suspect is the lock-up.

```
Jun 26 16:31:07 sibelius AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/0b6a845712d54ef2854d86ddae157393
Jun 26 16:31:08 sibelius AptDaemon.PackageKit: INFO: Get updates()
Jun 26 16:31:09 sibelius AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/0b6a845712d54ef2854d86ddae157393
Jun 26 16:37:08 sibelius AptDaemon: INFO: Quitting due to inactivity
Jun 26 16:37:08 sibelius AptDaemon: INFO: Quitting was requested
Jun 26 16:52:29 sibelius kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 26 16:52:29 sibelius rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1017" x-info="http://www.rsyslog.com"] start
Jun 26 16:52:29 sibelius rsyslogd: rsyslogd's groupid changed to 103
Jun 26 16:52:29 sibelius rsyslogd: rsyslogd's userid changed to 101
Jun 26 16:52:29 sibelius rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun 26 16:52:29 sibelius kernel: [    0.000000] Initializing cgroup subsys cpuset
```

Thanks for letting me know about this log. I was looking for something like this. I'll post another if I see it happen again.

---

### Post by chili555 on 2012-06-26
> Jun 26 16:31:09 sibelius AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/0b6a845712d54ef2854d86ddae157393
Jun 26 16:37:08 sibelius AptDaemon: INFO: Quitting due to inactivity
Jun 26 16:37:08 sibelius [COLOR="Red"]AptDaemon:[/COLOR] INFO: Quitting was requested
Jun 26 16:52:29 sibelius kernel: imklog 5.8.6, log source = /proc/kmsg started.There is a well-known bug in aptd in 12.04. I wonder if it has anything to do with anything. You might change Update Manager to *NEVER* check for updates for a while and see if it helps. You can always do updates the old-fashioned way:```
sudo apt-get update && sudo apt-get -y upgrade
```I am a bit suspicious of my own advice because I have no lock-ups.

---

### Post by belnac on 2012-06-27
Prior to applying Mahler's patch I too was suffering freezes running the latest 3.2 Kernel. I never actually found out what exactly was causing the freezes as I was never able to find any information in the logs, however I'm pretty sure it was kernel related; possibly a driver.

The reason why I'm pretty certain of this is the freezes were completely gone once I built the latest kernel from git. I'm currently running kernel 3.5.0-rc4, with the ethernet nic enabled and handling pretty intense torrent traffic - several dozens of GB up/down stream every day - and I'm yet to encounter _any_ issues at all. It runs beautifully.

I would say, then, that if you have a Killer E2200 (released a few months ago, if I'm not mistaken) then chances are your hardware is probably new too. As I say, in my case upgrading to the latest kernel solved all stability issues (my setup includes i7-3720QM Ivy Bridge, HM77 chipset, Nvidia 670M GPU.) Then again, the longer I've ran my laptop was for just slightly over 22h, whereas you seem to use your machine as a server.

Hope this helps though.

---

### Post by Mahler122 on 2012-06-27
I'm glad to hear that you're not having any problems. I'll try the 3.5-rc4 kernel now.

My setup is

MSI GT70
gtx 675m
i7-3610QM

I use it more as a workstation during the day, but I don't really run it over night. The internet connection is too poor where I live for it to be useful the moment.

Now all we have to wait for is the kernel and NVIDIA people to figure out what they're doing for optimus support.

---

### Post by belnac on 2012-06-28
> **Mahler122 said:**
> Now all we have to wait for is the kernel and NVIDIA people to figure out what they're doing for optimus support.

I *believe* I've just now found a way to:

[LIST]
[*]install the latest official (and obviously _proprietary_) NVidia driver that fully supports my GPU (670M)
[*]enable full 3d hardware acceleration
[*]enable Optimus optmizations
[/LIST]


**HOW**

Support for NVidia Optimus is provided by the open-source project Bumblebee, which can be found [[COLOR="RoyalBlue"]here[/COLOR]](http://bumblebee-project.org/) [1]. Install instructions for Ubuntu at the bottom of the page [[COLOR="RoyalBlue"]here[/COLOR]](http://bumblebee-project.org/install.html) [2].
 
Latest proprietary NVidia drivers can be installed by first adding the [[COLOR="RoyalBlue"]x-swat repository[/COLOR]](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) [3].


**STEPS** *(using sudo or as root)*

```

# apt-get purge nvidia-current
# add-apt-repository ppa:bumblebee/stable
# add-apt-repository ppa:ubuntu-x-swat/x-updates
# apt-get update
# apt-get install bumblebee bumblebee-nvidia
```

Everything seems stable so far and I now have full 3d acceleration! Still early to say anything about battery consumption as I haven't run the laptop for long yet; also [FONT="Courier New"]optirun[/FONT] isn't running for some reason.


-----
[1] [http://bumblebee-project.org/](http://bumblebee-project.org/)
[2] [http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html)
[3] [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by chili555 on 2012-06-28
I wonder if the Nvidia and Optimus part wouldn't be better on General Help. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by Mahler122 on 2012-07-02
> **belnac said:**
> I too was suffering freezes running the latest 3.2 Kernel. I never actually found out what exactly was causing the freezes as I was never able to find any information in the logs, however I'm pretty sure it was kernel related; possibly a driver.

So, It's been 5 days since I switched to 3.5.0-rc{4,5}, and I've had no issues. Looks like belnac was right! And the fake NIC driver is working great!

As far as the Optimus stuff is concerned, I suspect that our situation is a bit more complicated, and I'm starting a thread [here]("http://ubuntuforums.org/showthread.php?t=2014681") to gather information and figure out what needs to be done to get our discrete chips working.

---

### Post by OrionFL79 on 2012-08-01
Its alive!  I'm another one who's got an MSI GT70.  I was stuck in the evil parallel universe for a few months waiting for NVidia to come out with a linux driver until Windows - being the virus bait that it is caught something then imploded on itself.  

Anywho, your patch worked flawlessly on my "Killer" card - and now I'm off to figure out this whole Bumblebee thing to get my graphics working.

Thank you and good job! :)

**Bows to your awesomeness**

 - Orion

---

### Post by leenmie on 2012-09-04
I have a MSI GE60 and the guide works very well.
However, we should install only alx module, not all compat modules. We can do that by executing "driver-select alx" (the script in scripts folder) after the patching job.
Thanks,

---

### Post by belnac on 2012-09-22
Letting everybody know that I just tried to connect the NIC to a gigabit switch but it refuses to negotiate a 1000Mb link.

I'm pretty sure it's a driver issue as I tried forcing it with the following command,

```
# ethtool -s eth0 speed 1000 duplex full autoneg off
```

but I lose the link each time, and then have to manually unload and reload the alx driver.

This is the only issue I've had since using the fake driver BTW.

--

Also, the following is found is the syslog after issuing the ethtool command:

```
[ 2205.379034] alx 0000:02:00.0: error when reset phy
[ 2205.379034] eth0: speed = 0x20, autoneg = 1
```

---

### Post by chili555 on 2012-09-22
> I'm pretty sure it's a driver issue as I tried forcing it Perhaps you'll have better luck with the later alx driver outlined at post #4 here: [http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx](http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx)

---

### Post by allstar00001 on 2012-10-05
This article helps me a  lot. Many thanks.

---

### Post by belnac on 2012-10-10
> **belnac said:**
> Letting everybody know that I just tried to connect the NIC to a gigabit switch but it refuses to negotiate a 1000Mb link.

Just to let everyone know that this is **not** a driver issue! Turns out the Cat5e cable I was using was faulty. Replaced it with a cat6 and now have a super fast 1gpbs link.

---

### Post by keesvandieren on 2012-10-18
> **belnac said:**
> Using Kernel 3.5.0-rc3, compilation fails on ./net/bluetooth/rfcomm/tty.c

Attached is a simple patch I've just created that fixes the compilation error, which is caused by different function definitions for tty_unlock and tty_lock; current version of tty.c expects the two (mutex) functions to accept an argument, which they now don't anymore.

Mahler, thanks again for this - the NIC has now been brought to life!

This patch also needs to be applied when using Ubuntu 12.04 and [Kernel 3.4-precise]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/").

With that I got things working with Ubuntu 12.04, Ivy bridge processor (that needs kernel 3.4) and LAN. 

Thanks for sharing this!

Edit: it works directly after install. But Ubuntu does not start up any more with 3.4 kernel. So still looking for a solution (will see if Ubuntu 12.10 makes it work without customizations)

---

### Post by keesvandieren on 2012-10-18
Can someone confirm that this Network card is supported in Ubuntu 12.10? (with our without custom driver)?

---

### Post by chili555 on 2012-10-18
It isn't supported directly, but can be done with modification of compat-wireless.

---

### Post by Mahler122 on 2012-10-19
Hi All, just letting everybody know that this modification with the patch mentioned still works for ubuntu 12.10 when using the stock kernel. At this time, the network card is still not officially supported.

I'd also like to let everyone know that the patch mentioned above also works for 3.6.x kernels. You may upgrade to these and still have your network card working.

---

### Post by dn1nj4 on 2012-10-19
Mahler122: Pulled the latest drivers from [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2) and applied your patch.  Everything seems to be working amazingly well on Ubuntu 12.04.  Thanks so much!

---

### Post by keesvandieren on 2012-10-25
Finally got it working, with Intel Ivy Bridge processor and Ubuntu 12.04 and Kernel 3.6

Steps:

[LIST]
[*] Installed kernel 3.6 (as described here: [http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html](http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html) )
[*] Downloaded drivers from [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2) and apply both patches 
[*] Extract archive and chdir into it
[*] run: sudo su
[*] run: ./scripts/driver-select alx
[*] run: make
[*] run: make install
[*] run: make unload
[*] reboot
[/LIST]
The topic start post does not mention the step: [FONT="Courier New"]/scripts/driver-select alx[/FONT], linuxwireless.org [does]("http://linuxwireless.org/en/users/Download/stable/#Building_and_installing"). Should it be listed there as well?

---

### Post by SnakeHaveYou on 2012-10-27
Hello all!

I want to make Linux my daily OS, but i've an E2100.. Is there anyway to make this patch works for my card?

Thanks!

---

### Post by chili555 on 2012-10-27
> **SnakeHaveYou said:**
> Hello all!

I want to make Linux my daily OS, but i've an E2100.. Is there anyway to make this patch works for my card?

Thanks!If you have the same device, there is no reason why not. Please verify:```
lspci -nn | grep 0200
```

---

### Post by SnakeHaveYou on 2012-10-27
Nothing.. But "grep Ath"shows:

```
06:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0037] (rev 01)
```


The NIC seems to be different (E2200 vs my E2100), but maybe modifying the Patch file..

---

### Post by chili555 on 2012-10-27
> Atheros Communications Inc. Device [168c:0037] (rev 01)This is a wireless device using the driver *ath9k*. It is not the famous Killer. Let's see:```
lspci -nn
```

---

### Post by SnakeHaveYou on 2012-10-27
Here it goes:

```
00:00.0 Host bridge [0600]: Intel Corporation Xeon E5/Core i7 DMI2 [8086:3c00] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 1a [8086:3c02] (rev 07)
00:02.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 2a [8086:3c04] (rev 07)
00:03.0 PCI bridge [0604]: Intel Corporation Xeon E5/Core i7 IIO PCI Express Root Port 3a in PCI Express Mode [8086:3c08] (rev 07)
00:05.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Address Map, VTd_Misc, System Management [8086:3c28] (rev 07)
00:05.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Control Status and Global Errors [8086:3c2a] (rev 07)
00:05.4 PIC [0800]: Intel Corporation Xeon E5/Core i7 I/O APIC [8086:3c2c] (rev 07)
00:11.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Virtual Root Port [8086:1d3e] (rev 05)
00:16.0 Communication controller [0780]: Intel Corporation C600/X79 series chipset MEI Controller #1 [8086:1d3a] (rev 05)
00:1a.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #2 [8086:1d2d] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 1 [8086:1d10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 2 [8086:1d12] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 3 [8086:1d14] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 4 [8086:1d16] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 5 [8086:1d18] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 6 [8086:1d1a] (rev b5)
00:1c.6 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 7 [8086:1d1c] (rev b5)
00:1c.7 PCI bridge [0604]: Intel Corporation C600/X79 series chipset PCI Express Root Port 8 [8086:1d1e] (rev b5)
00:1d.0 USB controller [0c03]: Intel Corporation C600/X79 series chipset USB2 Enhanced Host Controller #1 [8086:1d26] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation C600/X79 series chipset LPC Controller [8086:1d41] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation C600/X79 series chipset 6-Port SATA AHCI Controller [8086:1d02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation C600/X79 series chipset SMBus Host Controller [8086:1d22] (rev 05)
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
02:00.1 Audio device [0403]: NVIDIA Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
03:00.1 Audio device [0403]: NVIDIA Corporation GF104 High Definition Audio Controller [10de:0beb] (rev a1)
05:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller [1b4b:9172] (rev 11)
06:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0037] (rev 01)
08:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller [1b4b:9172] (rev 11)
09:00.0 Power PC [0b20]: Freescale Semiconductor Inc Device [1957:c006] (rev 10)
0a:00.0 USB controller [0c03]: Fresco Logic Device [1b73:1009] (rev 02)
0b:00.0 USB controller [0c03]: Fresco Logic Device [1b73:1009] (rev 02)
0c:00.0 Audio device [0403]: Creative Labs X-Fi Titanium series [EMU20k2] [1102:000b] (rev 03)
ff:08.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 0 [8086:3c80] (rev 07)
ff:08.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 [8086:3c83] (rev 07)
ff:08.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 0 [8086:3c84] (rev 07)
ff:09.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link 1 [8086:3c90] (rev 07)
ff:09.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 [8086:3c93] (rev 07)
ff:09.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 QPI Link Reut 1 [8086:3c94] (rev 07)
ff:0a.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 0 [8086:3cc0] (rev 07)
ff:0a.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 1 [8086:3cc1] (rev 07)
ff:0a.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 2 [8086:3cc2] (rev 07)
ff:0a.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Power Control Unit 3 [8086:3cd0] (rev 07)
ff:0b.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Interrupt Control Registers [8086:3ce0] (rev 07)
ff:0b.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Semaphore and Scratchpad Configuration Registers [8086:3ce3] (rev 07)
ff:0c.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
ff:0c.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
ff:0c.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 0 [8086:3cf4] (rev 07)
ff:0c.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 System Address Decoder [8086:3cf6] (rev 07)
ff:0d.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
ff:0d.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Unicast Register 0 [8086:3ce8] (rev 07)
ff:0d.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller System Address Decoder 1 [8086:3cf5] (rev 07)
ff:0e.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Processor Home Agent [8086:3ca0] (rev 07)
ff:0e.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Processor Home Agent Performance Monitoring [8086:3c46] (rev 07)
ff:0f.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Registers [8086:3ca8] (rev 07)
ff:0f.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller RAS Registers [8086:3c71] (rev 07)
ff:0f.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 0 [8086:3caa] (rev 07)
ff:0f.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 1 [8086:3cab] (rev 07)
ff:0f.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 2 [8086:3cac] (rev 07)
ff:0f.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 3 [8086:3cad] (rev 07)
ff:0f.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Target Address Decoder 4 [8086:3cae] (rev 07)
ff:10.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 0 [8086:3cb0] (rev 07)
ff:10.1 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 1 [8086:3cb1] (rev 07)
ff:10.2 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 0 [8086:3cb2] (rev 07)
ff:10.3 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 1 [8086:3cb3] (rev 07)
ff:10.4 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 2 [8086:3cb4] (rev 07)
ff:10.5 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller Channel 0-3 Thermal Control 3 [8086:3cb5] (rev 07)
ff:10.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 2 [8086:3cb6] (rev 07)
ff:10.7 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Integrated Memory Controller ERROR Registers 3 [8086:3cb7] (rev 07)
ff:11.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 DDRIO [8086:3cb8] (rev 07)
ff:13.0 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 R2PCIe [8086:3ce4] (rev 07)
ff:13.1 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to PCI Express Performance Monitor [8086:3c43] (rev 07)
ff:13.4 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 QuickPath Interconnect Agent Ring Registers [8086:3ce6] (rev 07)
ff:13.5 Performance counters [1101]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 0 Performance Monitor [8086:3c44] (rev 07)
ff:13.6 System peripheral [0880]: Intel Corporation Xeon E5/Core i7 Ring to QuickPath Interconnect Link 1 Performance Monitor [8086:3c45] (rev 07)

```


I've a Gigabyte G1.Assassin2 motherboard, with integrated Killer E2100 and a PCIE WLAN/BT

---

### Post by chili555 on 2012-10-27
> I've a Gigabyte G1.Assassin2 motherboard, Yikes! I don't know whether to be envious or afraid!!! That's quite a mobo. > with integrated Killer E2100I'm old and it's late here, but so far I don't see it. Could it be one of those rare devices attached to a USB bus?```
lsusb
```Is it enabled or not in the BIOS? Let's look at:```
sudo lshw -C network
```>  PCIE WLAN/BT That we *do* see.

---

### Post by SnakeHaveYou on 2012-10-27
Well, i'm starting over! (sorry about my bad english!)

After you said "USB", i remembered that the PCIE WLAN/BT Atheros AR1111 ("made" by Gigabyte) was connected by the Mini PCIE AAANDD by an USB conection.. ([http://vmodtech.com/main/wp-content/uploads/northbridge/wb150300/10.jpg](http://vmodtech.com/main/wp-content/uploads/northbridge/wb150300/10.jpg))

You were right! The Atheros in "lspci -nn" was the WLAN one..
In lsusb, the WLAN Atheros appeared again..

So i took out the WLAN card and disconected it from the PCIE and the USB..

But, nothing appeared in lsusb or lspci..


In lshw (well, i'm using openSUSE)), you can see this:

```
47: PCI 900.0: 0b20 Power PC
  [Created at pci.319]
  Unique ID: x1VA.0hqDZebGQi4
  Parent ID: QSNP.Z7pQLQCVET7
  SysFS ID: /devices/pci0000:00/0000:00:1c.4/0000:09:00.0
  SysFS BusID: 0000:09:00.0
  Hardware Class: unknown
  Model: "Freescale Power PC"
  Vendor: pci 0x1957 "Freescale Semiconductor Inc"
  Device: pci 0xc006 
  SubVendor: pci 0x1a56 "Bigfoot Networks, Inc."
  SubDevice: pci 0x1201 
  Revision: 0x10
  Memory Range: 0xfa400000-0xfa4fffff (rw,non-prefetchable)
  Memory Range: 0xfa500000-0xfa50ffff (rw,non-prefetchable)
  Memory Range: 0xdd000000-0xddffffff (ro,non-prefetchable)
  Memory Range: 0xfa510000-0xfa513fff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00001957d0000C006sv00001A56sd00001201bc0Bsc20i00"
  Config Status: cfg=no, avail=yes, need=no, active=unknown
  Attached to: #32 (PCI bridge)
```

This is the only reference to the E2100!




(As for the Motherboard, is very good! But, as you can see, they don't support Linux based systems :( )

---

### Post by chili555 on 2012-10-28
I have done a lot of digging including downloading and extracting the LAN driver at Gigabyte's site for your awesome mobo. Here is a snip from the .inf file with some highlighting:> [BFOOT]
; DisplayName        Section        DeviceId
; -----------        -------        --------
;%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B4&SUBSYS_11011A56
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B4         ;MPC8315E
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B5         ;MPC8315
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B6         ;MPC8314E
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_1957&DEV_00B7         ;MPC8314
%Xeno831x.DRVDESC%=Xeno831x_Inst, PCI\VEN_[COLOR="Red"]1957[/COLOR]&DEV_[COLOR="Red"]C006 [/COLOR]        ;MPC8308The name of the .inf file is XenoXP.inf.

I have Googled your pci.id and the others listed in the .inf file; 1957:00B4 for example, and found nothing. I am fairly confident this isn't an *alx* device and isn't an Atheros; it identifies itself as:> Vendor: pci 0x1957 "[COLOR="Red"]Freescale Semiconductor Inc[/COLOR]"
  Device: pci 0xc006 
  SubVendor: pci 0x1a56 "Bigfoot Networks, Inc."
  SubDevice: pci 0x1201 Frankly, and I hate to say this ever, I have no further suggestions.

---

### Post by SnakeHaveYou on 2012-10-28
No problem man!! Thank you for your help!!

I think that my NIC is a Bigfoot Networks E2100(Win7 and Gigabyte's page says that :P), but, this one is manufactured by Freescale Semiconductor Inc., maybe because it's an on-board NIC is not manufactured directly by Atheros nor Bigfoot, and that makes the things more complicated..

I don't have any driver experience, so i hope someday, someone make a "fake" driver like the OP, but for my NIC!

Again, thanks for your help and for your time!!! :)





**
PD: I'll try to patch the Kernel to use the Atheros AR1111 WLAN card!

---

### Post by chili555 on 2012-10-28
> Atheros Communications Inc. Device [[COLOR="Red"]168c:0037[/COLOR]] I don't remember much from my Suse days, but in Ubuntu, it's already present:```
sudo modprobe ath9k
```If that doesn't do it, start a new thread and I'll be happy to help.

---

### Post by jobmail on 2012-10-28
> **keesvandieren said:**
> Finally got it working, with Intel Ivy Bridge processor and Ubuntu 12.04 and Kernel 3.6

Steps:

[LIST]
[*] Installed kernel 3.6 (as described here: [http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html](http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html) )
[*] Downloaded drivers from [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2) and apply both patches
[*] Extract archive and chdir into it
[*] run: sudo su
[*] run: ./scripts/driver-select alx
[*] run: make
[*] run: make install
[*] run: make unload
[*] reboot
[/LIST]
The topic start post does not mention the step: [FONT=Courier New]/scripts/driver-select alx[/FONT], linuxwireless.org [does]("http://linuxwireless.org/en/users/Download/stable/#Building_and_installing"). Should it be listed there as well?

 On my MSI GT70, Ubuntu 12.10, Kernel 3.6.3 work fine! Thank you! :-)

---

### Post by benliberty on 2012-10-28
> **chili555 said:**
> I have done a lot of digging including downloading and extracting the LAN driver at Gigabyte's site for your awesome mobo. Here is a snip from the .inf file with some highlighting:The name of the .inf file is XenoXP.inf.

I have Googled your pci.id and the others listed in the .inf file; 1957:00B4 for example, and found nothing. I am fairly confident this isn't an *alx* device and isn't an Atheros; it identifies itself as:Frankly, and I hate to say this ever, I have no further suggestions.

Thanks for looking into this. I've followed this thread closely over the last few hours trying to get the E2100 working on a gigabyte motherboard with an onboard E2100 NIC; I've upgraded to the 3.6.3 kernel, applied both patches to the network drivers, created the make file, built and loaded the alx module, but the ethernet nic is not recognized.

I can confirm that the only thing seen is the Freescale PPC hardware.

---

### Post by Dracomage on 2012-11-01
Hi,

I've got a MSI GT60 with a Killer E2200. I tried following the instructions alas there is an error during the compilation :

```
make -C /lib/modules/3.6.4-1-ARCH/build M=/home/guigui/Build/compat-wireless-2012-05-10-p modules
make[1]: Entering directory `/usr/src/linux-3.6.4-1-ARCH'
  CC [M]  /home/guigui/Build/compat-wireless-2012-05-10-p/net/mac80211/led.o
/home/guigui/Build/compat-wireless-2012-05-10-p/net/mac80211/led.c: In function 'ieee80211_stop_tpt_led_trig':
/home/guigui/Build/compat-wireless-2012-05-10-p/net/mac80211/led.c:279:3: error: implicit declaration of function 'led_brightness_set' [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/guigui/Build/compat-wireless-2012-05-10-p/net/mac80211/led.o] Error 1
make[2]: *** [/home/guigui/Build/compat-wireless-2012-05-10-p/net/mac80211] Error 2
make[1]: *** [_module_/home/guigui/Build/compat-wireless-2012-05-10-p] Error 2
make[1]: Leaving directory `/usr/src/linux-3.6.4-1-ARCH'
make: *** [modules] Error 2
```

I applied the two patches before compilation.
I have the newest kernel : 3.6.4, could it be due to this ?

---

### Post by chili555 on 2012-11-01
> compat-wireless-2012-05-10-pI think you need a later version of compat-wireless. Please see post #28.

---

### Post by Dracomage on 2012-11-01
Thanks, now it works.

---

### Post by lothei on 2012-12-08
I just tried the method in the first post (+ applying the second patch) on a fresh 12.10 installation (3.5 kernel), and it worked perfectly (so far)

Now ubuntu recognize the network card for my MSI GE60, Thanks ! I really didn't want to stick to wifi :KS

---

### Post by discojesus425 on 2012-12-22
Just used this on my new MSI GT70, and it worked perfectly following the original post for 12.04.  Thanks very much for this one!

---

### Post by thunder130990 on 2013-01-08
Oh my! Thanks! It was so frustrating until now! 

Surprisingly working on MSI GE70. "Surprisingly" because while checking the thread from where this all comes ( [http://ubuntuforums.org/showthread.php?p=12028162](http://ubuntuforums.org/showthread.php?p=12028162)), I realized my .inf files in the windows driver do not look like the ones there. 

However, it finally worked. If I may, I would suggest to announce that the second patch has to be applied with patch -p1 instead of patch -p2 . The ones like me that do not know what they're doing (I had never used patch) will apreciate it. By the way, someone could explain me in a non-man way what the -pNUMBER option does? I already read through that part of the manual and I still don't have a clue.

Thank you again!

---

### Post by ayush000 on 2013-01-18
Got this error while doing "make"
/lib/modules/3.5.0-17-generic/build: No such file or directory.

succesfully did these(as on first post):
sudo apt-get install build-essential linux-headers-3.5.0-22 3.5.0-22

tar -xvf compat-wireless-2012-05-10-p.tar.bz2 
patch --dry-run -p2 < compat-patch.txt 
patch -p2 < compat-patch.txt

I've GT70 laptop with killer e2200 & UBUNTU 12.10

It works.. I had to use generic version of linux-headers

---

### Post by ayush000 on 2013-01-21
Is there any way to get it to work with kernel 3.7.3?

---

### Post by chili555 on 2013-01-21
> **ayush000 said:**
> Is there any way to get it to work with kernel 3.7.3?You might try compiling a later version of compat-wireless, this, for example: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1.tar.bz2)

---

### Post by WarFireTheSecond on 2013-02-22
Hi everyone!

This method worked for the kernel 3.5.0-23 pretty good but since the kernel 3.5.0-24 the driver is somehow not assigned to the ethernet controller. Someone else with the same problem? If booting with the old kernel it still works...

Anyone an idea what I could do?

Edit:

```
$ lsmod |grep alx
alx                    81293  0 
compat                 13100  7 bnep,rfcomm,bluetooth,iwlwifi,mac80211,cfg80211,alx

```

but linux detects the ethernet controller (however without saying which module to load). 
hwinfo:
```

23: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: svHJ.XvAJki0A184
  Parent ID: qTvu.5uQaTDY9My8
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Attansic Ethernet controller"
  Vendor: pci 0x1969 "Attansic Technology Corp."
  Device: pci 0xe091 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x10c7 
  Revision: 0x13
  Memory Range: 0xf7d00000-0xf7d3ffff (rw,non-prefetchable)
  I/O Ports: 0xc000-0xcfff (rw)
  IRQ: 3 (no events)
  Module Alias: "pci:v00001969d0000E091sv00001462sd000010C7bc02sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

```

---

### Post by thunder130990 on 2013-02-22
It's weird. For me since we got to 3.5.0-24 I need to reboot it for it to work propperly. 

I would recommend you install only the ethernet drivers (alx), anyway by running:

scripts/driver-select alx

Then doing make clean, make, and sudo make install. This is my current configuration with kernel 3.5.0-25 (just updated today) and the only oddity is that I need to reboot just after the sudo make install step because for some reason the sudo modprobe alx does not make the ethernet work, even if it, of course, loads the module.

I attach my hwinfo so you see if you can use it for something:
```
35: PCI 300.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.dciuKhvHIn9
  Parent ID: qTvu.Bby94CRHdbE
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Attansic Ethernet controller"
  Vendor: pci 0x1969 "Attansic Technology Corp."
  Device: pci 0xe091 
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x10cd 
  Revision: 0x13
  Driver: "alx"
  Driver Modules: "alx"
  Device File: eth0
  Memory Range: 0xf7d00000-0xf7d3ffff (rw,non-prefetchable)
  I/O Ports: 0xc000-0xcfff (rw)
  IRQ: 45 (736289 events)
  HW Address: 8c:89:a5:07:03:ab
  Link detected: yes
  Module Alias: "pci:v00001969d0000E091sv00001462sd000010CDbc02sc00i00"
  Driver Info #0:
    Driver Status: alx is active
    Driver Activation Cmd: "modprobe alx"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (PCI bridge)

```

---

### Post by WarFireTheSecond on 2013-02-22
Thank you for your answer. Unfortunately it didn't worked. I also updated the kernel to  3.5.0-25, but still I have the same issues :cry:

Edit: I just saw that indeed they changed something in the kernel 3.5.0-24 for the Atheros cards as one may see [here]("http://www.ubuntuupdates.org/package/canonical_kernel_team/quantal/main/base/linux-headers-3.5.0-25-generic")... but I don't understand the changes.

---

### Post by chili555 on 2013-02-22
Let's troubleshoot. What is your device?```
lspci -nn | grep 0200
```Does the new *alx* cover your device?```
modinfo alx
``` Does the ethernet start if you simply load the module?```
sudo modprobe alx
ifconfig
```Is there an error or warning in the message logs?```
dmesg | grep -e alx -e eth0
```Thanks.

---

### Post by WarFireTheSecond on 2013-02-22
Ok, let's do it

```
lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:e091] (rev 13)

```

```
modinfo alx
filename:       /lib/modules/3.5.0-25-generic/updates/drivers/net/ethernet/atheros/alx/alx.ko
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     8DFA4CF8AB3E985CBE6B84F
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v00001969d00002060sv*sd*bc*sc*i*
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v00001969d00001073sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        compat
vermagic:       3.5.0-25-generic SMP mod_unload modversions 

```

```
sudo modprobe alx
ifconfig
```

ifconfig shows only the wifi, even after loading the module alx

```
dmesg | grep -e alx -e eth0
```

shows no message.

---

### Post by chili555 on 2013-02-22
> Atheros Communications Inc. Device [1969:[COLOR="Red"]e091[/COLOR]]However, we see no e091 or, more properly E091 here:> alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v00001969d00002060sv*sd*bc*sc*i*
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v00001969d00001073sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*I think you'll need to patch and then compile compat-wireless as outlined in post #1. I've examined the patch and your device is covered.> #define ALX_DEV_ID_AR8161               0x1091   /* l1f */
 #define ALX_DEV_ID_AR8162               0x1090   /* l2f */
+#define ALX_DEV_ID_E2200                0x[COLOR="Red"]e091[/COLOR]   /* l1f */
 
 #define ALX_REV_ID_AR8152_V1_0          0xc0
 #define ALX_REV_ID_AR8152_V1_1          0xc1
 #define ALX_REV_ID_AR8152_V2_0          0xc0Please post back if you need additional guidance.

---

### Post by WarFireTheSecond on 2013-02-22
Thank you very much! It worked! I dont really understand why, because I already did everything in post #1 with the kernel 3.5.0-23. I guess those drivers where somehow overwritten with the new kernel?

Note: I had to reboot to be able to load the module, as was stated in post #51

---

### Post by chili555 on 2013-02-22
> **WarFireTheSecond said:**
> Thank you very much! It worked! I dont really understand why, because I already did everything in post #1 with the kernel 3.5.0-23. I guess those drivers where somehow overwritten with the new kernel?

Note: I had to reboot to be able to load the module, as was stated in post #51That's always the case with drivers compiled from source code. They are built for your currently running kernel only. When a newer kernel, also known as linux-image, is installed, re-compile:```
cd Desktop/compat-wireless-version-whatever
./scripts/driver-select restore
./scripts/driver-select alx
sudo su
make clean
make
make install
modprobe alx
exit
```The linux-backports-modules-cw package includes alx but it likewise doesn't cover your device 1969:e091.

---

### Post by thesplus on 2013-03-13
Hi Mahler122,

I had installed Bigfoot killer E2200 ethernet driver for your help.
Thank you!!!

---

### Post by operez002 on 2013-04-01
Im having trouble putting in the line of code i typed in 


tar -xvf /path/to/compat-wireless-2012-05-10-p.tar.bz2 
where the path was my home folder and it untared it then i get stuck because the second line after that says there is no such directory.
 Can anyone explain it to me I'm sort of new to this

---

### Post by chili555 on 2013-04-01
> **operez002 said:**
> Im having trouble putting in the line of code i typed in 


tar -xvf /path/to/compat-wireless-2012-05-10-p.tar.bz2 
where the path was my home folder and it untared it then i get stuck because the second line after that says there is no such directory.
 Can anyone explain it to me I'm sort of new to thisSo, if I am correct, you did:```
tar -xvf /home/operez002/compat-wireless-2012-05-10-p.tar.bz2 
```...or whatever your user name is? If you need to recover the exact command, please do in a terminal:```
history | grep tar
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

That command means, roughly, list the last thousand or so commands I've issued. The pipe symbol means roughly, pipe the results through another command; in this case grep, which looks for a pattern, in this case 'tar.' So any commands you issued using the word tar will be shown. 

Once we know where the file is located, we can change directories into it:```
cd /wherever/compat-wireless-2012-05-10-p
```And then we can proceed with the remaining steps.>  I'm sort of new to this All of us were new at one time; even Linus and me. No worries.

---

### Post by sauyon on 2013-04-14
I decided that I wanted to update this for the newest version of compat-drivers, and so I did - the patch is attached.

Also, I forked the alx repo and patched that: [https://github.com/Sauyon/alx/](https://github.com/Sauyon/alx/)

hopefully, my pull request will be approved :P

---

### Post by stef_204 on 2013-04-15
@sauyon

> **sauyon said:**
> I decided that I wanted to update this for the newest version of compat-drivers, and so I did - the patch is attached.

Also, I forked the alx repo and patched that: [https://github.com/Sauyon/alx/](https://github.com/Sauyon/alx/)

hopefully, my pull request will be approved :P

Hi,

Really struggling with my Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller [1969:e091]; have tried various packages/patches but no luck yet.
I am on kernel 3.8.6-1.

I think your patch should work; however, I am not clear on how to apply the procedure you described.

Can I use your patch with any of these here:
[http://drvbp1.linux-foundation.org/~mcgrof/rel-html/compat-drivers/]("http://drvbp1.linux-foundation.org/~mcgrof/rel-html/compat-drivers/")

Or do I need to use git as desribed here: [https://github.com/Sauyon/alx/blob/master/README.md]("https://github.com/Sauyon/alx/blob/master/README.md") ?

If I do need to use instructions as in link above (git), do I still need to apply the patch or is it already in your alx version?

Sorry, I'm new at this.

---

### Post by sauyon on 2013-04-15
I built the patch to work with [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2) :)

then, in the same directory as the bz2 file:
```
tar -xjvf compat-drivers-3.9-rc2-2-su.tar.bz2
cd compat-drivers-3.9-rc2-2-su
```

then copy the alx-patch file into the compat-drivers directory

then:
```
patch --dry-run -p1 < alx-patch.txt
```
and if no errors:
```
patch -p1 < alx-patch.txt
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

and you should be done :)

if you want to patch a different version of compat-drivers for whatever reason, just move the alx-patch file into drivers/net/ethernet/atheros/alx, cd to it, and instead of patch -p1, patch -p6.

---

### Post by stef_204 on 2013-04-16
> **sauyon said:**
> 
and you should be done :)

Indeed I am!

Nicely done, you really nailed it! :)

It just works; didn't even need to reboot, just downloaded the compat-driver package referenced, applied the patch, loaded alx and ..... card recognized on the fly.
Tested it and pings perfectly.

Thanks, saved me a lot of grief, most appreciated.

If that's alright, I will post a thread in my distro's forum referencing your solution here with a link (will try to make it a sticky, if not, at the very least a SOLVED thread with the reference link to here.)

---

### Post by Volta500 on 2013-04-18
Hello, when i try to run any of the patches, I get these errors:
Im running Kubuntu 12.10 on a MSI GT60.

```

root@Pelle-GT60:/home/pelle/Documents/compat-wireless-2012-05-10-p# patch --dry-run -p2 < tty.c.patch.txt
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- ./net/bluetooth/rfcomm/tty.c       2012-05-10 21:52:29.000000000 +0100
|+++ ./net/bluetooth/rfcomm/tty.c       2012-06-25 14:32:38.494450009 +0100
--------------------------
File to patch: ^C



```
How can I solve this problem?
I am still kinda new with linux but learning fast :P
If you need any more information please ask

EDIT:
Never mind!
The fix on page 7 worked like a charm! 
Thank you.

---

### Post by sauyon on 2013-04-20
Ok, so quick tutorial on patching things:

[LIST=1]
[*]Figure out which driver is most appropriate for patching; in this case it was the alx driver, as the E2200 appears to be a rebrand of the AR1816. 
[*]Download the source and add the hardware id's where they seem to fit 
[*]Make sure that any references to the closest card also reference the new card 
[*]Build; if there are errors, debug 
[*]Hurrah, you've built a (hopefully) working patch :P 
[*]To build a patch file (if you're using git), do a git diff 
[/LIST]

Weird.... that post was a lot shorter than I imagined it to be, but now that I think about it, that's all it really is. I think it's about as long as the message that I wrote saying that It would be difficult for me to write it because it was a little difficult for me to read, lol.
 I'm also kind of depressed that this took me twenty hours to do -_-

But anyhow, hopefully this is useful in some way :P

---

### Post by 070 on 2013-04-23
> **sauyon said:**
> I built the patch to work with [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2) :)

then, in the same directory as the bz2 file:
```
tar -xjvf compat-drivers-3.9-rc2-2-su.tar.bz2
cd compat-drivers-3.9-rc2-2-su
```

then copy the alx-patch file into the compat-drivers directory

then:
```
patch --dry-run -p1 < alx-patch.txt
```
and if no errors:
```
patch -p1 < alx-patch.txt
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

and you should be done :)

if you want to patch a different version of compat-drivers for whatever reason, just move the alx-patch file into drivers/net/ethernet/atheros/alx, cd to it, and instead of patch -p1, patch -p6.

Thank u, now my gt60 can use the ethernet!

---

### Post by thunder130990 on 2013-04-23
> **sauyon said:**
> I built the patch to work with [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2) :)

then, in the same directory as the bz2 file:
```
tar -xjvf compat-drivers-3.9-rc2-2-su.tar.bz2
cd compat-drivers-3.9-rc2-2-su
```

then copy the alx-patch file into the compat-drivers directory

then:
```
patch --dry-run -p1 < alx-patch.txt
```
and if no errors:
```
patch -p1 < alx-patch.txt
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

and you should be done :)

if you want to patch a different version of compat-drivers for whatever reason, just move the alx-patch file into drivers/net/ethernet/atheros/alx, cd to it, and instead of patch -p1, patch -p6.

Thank you, I had been some months now that the old driver + patch did not work. Now it's working for me in 3.8.0-19. However, I still have to reboot for it to work, when I do the installation and try it with modprobe it doesn't work, but when I reboot (with the changes in the configuration file to load alx each time) it does.

Any ideas on why?

Thank you again!

---

### Post by Mr.EJ on 2013-04-29
> **thunder130990 said:**
> Thank you, I had been some months now that the old driver + patch did not work. Now it's working for me in 3.8.0-19. However, I still have to reboot for it to work, when I do the installation and try it with modprobe it doesn't work, but when I reboot (with the changes in the configuration file to load alx each time) it does.

Any ideas on why?

Thank you again!

you might need to do a **rmmod alx** first then do **modprobe alx**

---

### Post by PadreAdamo on 2013-04-30
[COLOR=#000000]I have the Killer Xeno Pro. The E2100, I believe, is the other name for it.  How do I use your fix for my NIC? I'm new to Linux but finding my way around very well utilizing the documentation out there. Thank you.

[/COLOR][HR][/HR][COLOR=#000000]
0a:00.0 Power PC [0b20]: Freescale Semiconductor Inc Device [1957:00b6] (rev 12)[/COLOR]
[COLOR=#000000]Subsystem: Bigfoot Networks, Inc. Device [1a56:1101][/COLOR]
[COLOR=#000000]Flags: bus master, fast devsel, latency 0, IRQ 255[/COLOR]
[COLOR=#000000]Memory at f2c00000 (32-bit, non-prefetchable) [size=1M][/COLOR]
[COLOR=#000000]Memory at f2dff000 (32-bit, non-prefetchable) [size=4K][/COLOR]
[COLOR=#000000]Memory at f1000000 (64-bit, prefetchable) [size=16M][/COLOR]
[COLOR=#000000]Memory at f2df8000 (64-bit, non-prefetchable) [size=16K][/COLOR]
[COLOR=#000000]Capabilities: <access denied>[/COLOR]

---

### Post by saruz on 2013-05-04
> **sauyon said:**
> I built the patch to work with [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2) :)

then, in the same directory as the bz2 file:
```
tar -xjvf compat-drivers-3.9-rc2-2-su.tar.bz2
cd compat-drivers-3.9-rc2-2-su
```

then copy the alx-patch file into the compat-drivers directory

then:
```
patch --dry-run -p1 < alx-patch.txt
```
and if no errors:
```
patch -p1 < alx-patch.txt
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

and you should be done :)

if you want to patch a different version of compat-drivers for whatever reason, just move the alx-patch file into drivers/net/ethernet/atheros/alx, cd to it, and instead of patch -p1, patch -p6.

Got this to work with my MSI GE60. Thanks a lot :)

---

### Post by lazybean on 2013-05-07
Hi Guys,

I bought the MSI GE60, installed Ubuntu and followed **sauyon's **guide to install my Network but it doesn't work.

dmesg prints out the following:

> 
[  290.927981] Compat-drivers backport release: compat-drivers-v3.9-rc2-2-su
[  290.927990] Backport based on linux-stable.git v3.9-rc2
[  290.927991] compat.git: linux-stable.git
[  290.943179] Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver


---

### Post by tazzy2k on 2013-05-07
If anyone is interested in doing the patch for the current (May 7, 2013) stock kernel of Ubuntu 13.04, this is what worked for me:

0. Get the kernel build stuff:
```
sudo apt-get install build-essential linux-headers-3.8.0-19-generic
```

1. Get and unpack this driver package: 
[https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/compat-drivers-3.8-1-u.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/compat-drivers-3.8-1-u.tar.bz2)

2. Place the alx-patch.txt here (relative to base dir of unpacked driver): 
```
./drivers/net/ethernet/atheros/alx/alx-patch.txt
```

3. Patch, but use -p1, -p6 would NOT work, probably because I used it wrong: 
```
patch -p1 < ./drivers/net/ethernet/atheros/alx/alx-patch.txt
```
Patch will complain that the alx-patch.txt doesn't match perfectly but it can figure out the right places to patch the code on its own.

4. Continue as **sauyon** wrote:
```

./scripts/driver-select alx
...

```

5. Enjoy your Gbit LAN :-]

Tested it real quick (writing this post using the driver) and it seems to work.

---

### Post by k3malb3y on 2013-05-16
[LIST=1]
[*]hi I'm following this thread from beggining to the end. Have the same ethernet card (Killer e2200 on MSI GE60) 
[*]Using Debian** 3.7.2-0+kali6** x86_64 GNU/Linux 
[*]I tried all the ways and many things before to install my eth0 (all patches I've found) 
[*]finally I downloaded [compat-drivers-**3.9-rc2-2-su**.tar.bz2 ]("http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2")and patched with "**alx-patch.txt**" found in this thread. 
[/LIST]

my problem is when I try to enter "modprobe alx" I get this msg 
*"ERROR: could not insert 'alx': Unknown symbol in module, or unknown parameter (see dmesg)"*
[B]
dmesg | grep alx[/B]
```
[ 1267.756495] alx: Unknown symbol backport_dependency_symbol (err 0)
```

here some info:
[LIST]
[*]** cat /etc/network/interfaces** 
[/LIST]
```
auto lo eth0
iface lo inet loopback
```

[LIST]
[*]**ifconfig** 
[/LIST]
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4080 (3.9 KiB)  TX bytes:4080 (3.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 0c:d2:92:3e:46:f3  
          inet addr:172.18.58.137  Bcast:172.18.58.255  Mask:255.255.255.0
          inet6 addr: fe80::ed2:92ff:fe3e:46f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18613 errors:0 dropped:1 overruns:0 frame:0
          TX packets:12083 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9804372 (9.3 MiB)  TX bytes:1657278 (1.5 MiB)

```
[LIST]
[*]**lspci -d :e091 -vnn** 
[/LIST]
```
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:10c7]
    Flags: bus master, fast devsel, latency 0, IRQ 3
    Memory at f7d00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at c000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable- Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable- Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-08-31-ca-8c-89-a5-ff

```

[LIST]
[*]**modinfo alx** 
[/LIST]
```
filename:       /lib/modules/3.7-trunk-amd64/updates/src/alx.ko
version:        1.2.3
license:        Dual BSD/GPL
description:    Qualcomm Atheros Gigabit Ethernet Driver
author:         Qualcomm Corporation, <nic-devel@qualcomm.com>
srcversion:     FC6555DA3CF93CC52DE0322
alias:          pci:v00001969d000010A0sv*sd*bc*sc*i*
alias:          pci:v00001969d000010A1sv*sd*bc*sc*i*
alias:          pci:v00001969d00001090sv*sd*bc*sc*i*
alias:          pci:v00001969d00001091sv*sd*bc*sc*i*
depends:        compat,mdio
vermagic:       3.7-trunk-amd64 SMP mod_unload modversions 

```


[LIST]
[*]and of course "alx" is not in the ***lspci*** list :( 
[/LIST]

Thank you..

---

### Post by sauyon on 2013-05-16
> **tazzy2k said:**
> 
2. Place the alx-patch.txt here (relative to base dir of unpacked driver): 
```
./drivers/net/ethernet/atheros/alx/alx-patch.txt
```

3. Patch, but use -p1, -p6 would NOT work, probably because I used it wrong: 
```
patch -p1 < ./drivers/net/ethernet/atheros/alx/alx-patch.txt
```
Patch will complain that the alx-patch.txt doesn't match perfectly but it can figure out the right places to patch the code on its own.


Sorry I wasn't completely clear, you need to cd into drivers/net/ethernet/atheros/alx as per below before you -p6.

> **sauyon said:**
> if you want to patch a different version of compat-drivers for whatever reason, just move the alx-patch file into drivers/net/ethernet/atheros/alx, cd to it, and instead of patch -p1, patch -p6.

Also, you actually don't have to do this every version, only if they change the directory system for whatever reason. I honestly don't know why I said that, lol.

Finally do a patch with --dry-run if you want to be extra safe and confirm what changes the patch is going to make.

---

### Post by sauyon on 2013-05-16
> **k3malb3y said:**
> finally I downloaded [compat-drivers-**3.9-rc2-2-su**.tar.bz2 ]("http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2")and patched with "**alx-patch.txt**" found in this thread.

Did you use my patch file or the original patch file? That's all I can think of, sorry.

---

### Post by k3malb3y on 2013-05-16
no I used your patch file , and I've done lots of 'alx' installation with different patches before. used 'ATL1C' to define ethernet card too and tried config edits like this;
```
  modprobe atl1c 
echo 1969 e091 > /sys/bus/pci/drivers/atl1c/new_id
than;

modprobe alx 
echo 1969 e091 > /sys/bus/pci/drivers/alx/new_id
ifconfig 
```
maybe because of these some files and packages has been corrupted. I tried to clean-update and fix again but I think that wasn't success
when I try to 'modprobe alx'
I still get "ERROR: could not insert 'alx': Unknown symbol in module, or unknown parameter"

:( don't wanna re-install the system. (sorry about my bad English)

---

### Post by k3malb3y on 2013-05-16
also still got the biggest Nvidia issue too. Never seen GTX660M working on deb/linux system.
when I was using Backtrack 3.2.xx allways had "No screens found" error. the xorg.conf file took my hours literally.
 now in Kali Linux 3.7.2-0 it found the screen somehow. but it is blackscreen, you racist Nvidia!

---

### Post by k3malb3y on 2013-05-17
oke I wanna learn how to compile a patch can u advice me some decument  to read

---

### Post by sauyon on 2013-05-18
> **k3malb3y said:**
> oke I wanna learn how to compile a patch can u advice me some decument  to read

Do you mean create the patch? Look at the file - it's essentially the output of a diff command.

---

### Post by jcryselz33 on 2013-05-21
I did a software update the other day and it updated my linux headers thus getting rid of my ethernet drivers. I went through the same process as before but could not get them installed. Any solutions?

---

### Post by chili555 on 2013-05-21
Were there errors when you did the 'make' and/or 'make install' steps? It will be helpful if you could post them.

---

### Post by jcryselz33 on 2013-05-21
I was following tazzy2k's post on how he got it working on ringtail. 

Code:

joey@joey-CZ-17:~/Downloads/compat-drivers-3.8-1-u$ patch -p1 < ./drivers/net/ethernet/atheros/alx/alx-patch.txt
patching file drivers/net/ethernet/atheros/alx/alx_ethtool.c
patching file drivers/net/ethernet/atheros/alx/alx_main.c
Hunk #1 succeeded at 55 (offset -2 lines).
Hunk #2 succeeded at 1016 (offset 5 lines).
patching file drivers/net/ethernet/atheros/alx/alx_reg.h
joey@joey-CZ-17:~/Downloads/compat-drivers-3.8-1-u$ ./scripts/driver-select alx
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/ethernet/broadcom/Makefile.bk
Backing up makefile: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
joey@joey-CZ-17:~/Downloads/compat-drivers-3.8-1-u$ 


After all that my ethernet card is still not being detected

---

### Post by chili555 on 2013-05-21
> **jcryselz33 said:**
> I was following tazzy2k's post on how he got it working on ringtail. 

Code:

joey@joey-CZ-17:~/Downloads/compat-drivers-3.8-1-u$ patch -p1 < ./drivers/net/ethernet/atheros/alx/alx-patch.txt
patching file drivers/net/ethernet/atheros/alx/alx_ethtool.c
patching file drivers/net/ethernet/atheros/alx/alx_main.c
Hunk #1 succeeded at 55 (offset -2 lines).
Hunk #2 succeeded at 1016 (offset 5 lines).
patching file drivers/net/ethernet/atheros/alx/alx_reg.h
joey@joey-CZ-17:~/Downloads/compat-drivers-3.8-1-u$ ./scripts/driver-select alx
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/ethernet/broadcom/Makefile.bk
Backing up makefile: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
joey@joey-CZ-17:~/Downloads/compat-drivers-3.8-1-u$ 


After all that my ethernet card is still not being detectedYou also need to do:```
make
sudo make install
sudo modprobe alx
```Now is it working? If there are errors or warnings, please post them.

---

### Post by sirLethe on 2013-05-23
Before alx starts to work, it is better to 
$ sudo make unload

and then,
$ sudo modprobe alx

Mine just works fine with sauyon's method.

---

### Post by Volta500 on 2013-05-30
Suddenly my ethernet card stopped working.
Weird thing is that it just stopped working. One day it was fine and the next it stopped. Reboot doesn't help. Unloading and reloading has no effect. Could it have been some update that is giving problems?
 
But this is not the first time the Ethernet became unresponsive but all other times reinstalling the driver solved it.
But now for some reason am unable to build the driver.

This is what I did:

unpack, cd to directory, copy patch to  ./drivers/net/ethernet/atheros/alx/
then apply patch:

```

pelle@GT60:~/compat-drivers-3.9-rc2-2-su$ cd ./drivers/net/ethernet/atheros/alx/pelle@GT60:~/compat-drivers-3.9-rc2-2-su/drivers/net/ethernet/atheros/alx$ patch --dry-run -p1 < alx-patch.txt
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/net/ethernet/atheros/alx/alx_ethtool.c b/drivers/net/ethernet/atheros/alx/alx_ethtool.c
|index 074c640..b19950e 100644
|--- a/drivers/net/ethernet/atheros/alx/alx_ethtool.c
|+++ b/drivers/net/ethernet/atheros/alx/alx_ethtool.c
--------------------------
File to patch: ^C
pelle@GT60:~/compat-drivers-3.9-rc2-2-su/drivers/net/ethernet/atheros/alx$ patch --dry-run -p6 < alx-patch.txt
patching file alx_ethtool.c
patching file alx_main.c
Hunk #2 succeeded at 1017 (offset 6 lines).
patching file alx_reg.h

pelle@GT60:~/compat-drivers-3.9-rc2-2-su/drivers/net/ethernet/atheros/alx$ patch -p6 < alx-patch.txt
patching file alx_ethtool.c
patching file alx_main.c
Hunk #2 succeeded at 1017 (offset 6 lines).
patching file alx_reg.h



pelle@GT60:~/compat-drivers-3.9-rc2-2-su$ ./scripts/driver-select alx
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/ethernet/broadcom/Makefile.bk
Backing up makefile: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk

``` 


So far so good but when I try to make
```

pelle@GT60:~/compat-drivers-3.9-rc2-2-su$ make
./scripts/gen-compat-autoconf.sh /home/pelle/compat-drivers-3.9-rc2-2-su/.config /home/pelle/compat-drivers-3.9-rc2-2-su/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.5.0-31-generic/build M=/home/pelle/compat-drivers-3.9-rc2-2-su modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-31-generic'
  CC [M]  /home/pelle/compat-drivers-3.9-rc2-2-su/compat/main.o
In file included from /home/pelle/compat-drivers-3.9-rc2-2-su/include/linux/compat-2.6.h:71:0,
                 from <command-line>:0:
/home/pelle/compat-drivers-3.9-rc2-2-su/include/linux/compat-3.8.h:49:32: error: redefinition of ‘kref_get_unless_zero’
In file included from include/linux/kobject.h:24:0,
                 from include/linux/slub_def.h:13,
                 from include/linux/slab.h:185,
                 from include/linux/textsearch.h:8,
                 from include/linux/skbuff.h:28,
                 from include/linux/if_ether.h:134,
                 from include/linux/netdevice.h:29,
                 from /home/pelle/compat-drivers-3.9-rc2-2-su/include/linux/compat-2.6.29.h:5,
                 from /home/pelle/compat-drivers-3.9-rc2-2-su/include/linux/compat-2.6.h:52,
                 from <command-line>:0:
include/linux/kref.h:113:32: note: previous definition of ‘kref_get_unless_zero’ was here
make[3]: *** [/home/pelle/compat-drivers-3.9-rc2-2-su/compat/main.o] Error 1
make[2]: *** [/home/pelle/compat-drivers-3.9-rc2-2-su/compat] Error 2
make[1]: *** [_module_/home/pelle/compat-drivers-3.9-rc2-2-su] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-31-generic'
make: *** [modules] Error 2

```
What could cause this and how can I solve the problem?
Im running Kubuntu 12.10 but plan to update to 13.04 when I get my ethernet working as updating on my ****** wifi could take a few days :(

dmesg | grep alx comes up empty, unloading and reloading alx has no effect.

---

### Post by chili555 on 2013-05-30
Since you are running kernel 3.**5**.0-xx, I suggest you try an earlier compat-wireless package than 3.**9**.xx. Perhaps this: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.4-1-snpc.tar.bz2) 

You will need the patch; please try it and let us hear your report.

---

### Post by Volta500 on 2013-05-30
Thanks for the input, but now Im unable to patch with both patch files on this thread.
Output:
```
pelle@GT60:~/compat-wireless-3.5.4-1-snpc/drivers/net/ethernet/atheros/alx$ patch --dry-run -p1 < alx-patch.txtcan't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/net/ethernet/atheros/alx/alx_ethtool.c b/drivers/net/ethernet/atheros/alx/alx_ethtool.c
|index 074c640..b19950e 100644
|--- a/drivers/net/ethernet/atheros/alx/alx_ethtool.c
|+++ b/drivers/net/ethernet/atheros/alx/alx_ethtool.c
--------------------------
File to patch: ^C
pelle@GT60:~/compat-wireless-3.5.4-1-snpc/drivers/net/ethernet/atheros/alx$ patch --dry-run -p6 < alx-patch.txt
patching file alx_ethtool.c
Hunk #1 succeeded at 431 with fuzz 2 (offset -300 lines).
patching file alx_main.c
Hunk #1 succeeded at 34 with fuzz 2 (offset -23 lines).
Hunk #2 succeeded at 3695 with fuzz 2 (offset 2684 lines).
can't find file to patch at input line 37
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/net/ethernet/atheros/alx/alx_reg.h b/drivers/net/ethernet/atheros/alx/alx_reg.h
|index 58177f3..0788aa8 100644
|--- a/drivers/net/ethernet/atheros/alx/alx_reg.h
|+++ b/drivers/net/ethernet/atheros/alx/alx_reg.h
--------------------------
File to patch: ^C
pelle@GT60:~/compat-wireless-3.5.4-1-snpc/drivers/net/ethernet/atheros/alx$ patch --dry-run -p6 < compat-patch.txt.txt
bash: compat-patch.txt.txt: No such file or directory
pelle@GT60:~/compat-wireless-3.5.4-1-snpc/drivers/net/ethernet/atheros/alx$ patch --dry-run -p6 < compat-patch.txt
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur ./compat-wireless-2012-05-10-p-Original/drivers/net/ethernet/atheros/alx/alf_cb.c ./compat-wireless-2012-05-10-p-New/drivers/net/ethernet/atheros/alx/alf_cb.c
|--- ./compat-wireless-2012-05-10-p-Original/drivers/net/ethernet/atheros/alx/alf_cb.c  2012-05-10 22:52:30.000000000 +0200
|+++ ./compat-wireless-2012-05-10-p-New/drivers/net/ethernet/atheros/alx/alf_cb.c       2012-06-22 17:47:23.293252558 +0200
--------------------------
File to patch: ^C
pelle@GT60:~/compat-wireless-3.5.4-1-snpc/drivers/net/ethernet/atheros/alx$ patch --dry-run -p1 < compat-patch.txt
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur ./compat-wireless-2012-05-10-p-Original/drivers/net/ethernet/atheros/alx/alf_cb.c ./compat-wireless-2012-05-10-p-New/drivers/net/ethernet/atheros/alx/alf_cb.c
|--- ./compat-wireless-2012-05-10-p-Original/drivers/net/ethernet/atheros/alx/alf_cb.c  2012-05-10 22:52:30.000000000 +0200
|+++ ./compat-wireless-2012-05-10-p-New/drivers/net/ethernet/atheros/alx/alf_cb.c       2012-06-22 17:47:23.293252558 +0200
--------------------------
File to patch: ^C

```

---

### Post by chili555 on 2013-05-30
Let's go back to basics and start by identifying your device:```
lspci -nn | grep 0200
```

---

### Post by Volta500 on 2013-05-30
Here you go.
```

pelle@GT60:~$ lspci -nn | grep 0200
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:e091] (rev 13)

```

Note that the device HAS worked before using the same method but probably an update went along and caused problems

---

### Post by chili555 on 2013-05-30
Please try this instead. If this doesn't succeed, we'll take the patches apart. Big fun for a Bigfoot!

[http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2)

---

### Post by Volta500 on 2013-05-30
Nope. Sorry to say but no luck with that package either.
Output:
```
pelle@GT60:~/compat-wireless-3.6.2-1-snpc/drivers/net/ethernet/atheros/alx$ patch --dry-run -p1 < alx-patch.txtcan't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/net/ethernet/atheros/alx/alx_ethtool.c b/drivers/net/ethernet/atheros/alx/alx_ethtool.c
|index 074c640..b19950e 100644
|--- a/drivers/net/ethernet/atheros/alx/alx_ethtool.c
|+++ b/drivers/net/ethernet/atheros/alx/alx_ethtool.c
--------------------------
File to patch: ^C
pelle@GT60:~/compat-wireless-3.6.2-1-snpc/drivers/net/ethernet/atheros/alx$ patch --dry-run -p6 < alx-patch.txt
patching file alx_ethtool.c
Hunk #1 succeeded at 431 with fuzz 2 (offset -300 lines).
patching file alx_main.c
Hunk #1 succeeded at 34 with fuzz 2 (offset -23 lines).
Hunk #2 succeeded at 3695 with fuzz 2 (offset 2684 lines).
can't find file to patch at input line 37
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/net/ethernet/atheros/alx/alx_reg.h b/drivers/net/ethernet/atheros/alx/alx_reg.h
|index 58177f3..0788aa8 100644
|--- a/drivers/net/ethernet/atheros/alx/alx_reg.h
|+++ b/drivers/net/ethernet/atheros/alx/alx_reg.h
--------------------------
File to patch: ^C



```
If it would solve the problem it would be possible to update to Kubuntu 13.04 at work where the WiFi is much better.

---

### Post by chili555 on 2013-05-30
> If it would solve the problem it would be possible to update to Kubuntu 13.04 It should work perfectly.

---

### Post by Volta500 on 2013-05-30
Then I will install the upgrade tomorrow, install the driver and see how many other problems surface ;)

But thanks for your input anyways.

EDIT:
[COLOR=#000000]It took a few tries and a reboot but it works![/COLOR]
[COLOR=#000000]But after going to sleep and waking up it is necessary to unload and reload (modprobe -r alx, modprobe alx from root konsole). I could turn that into a script and set it to run at wakeup but is that a good solution or are there better ways to do that?[/COLOR]

---

### Post by chili555 on 2013-05-31
> It took a few tries and a reboot but it works!Awesome! Great news.> But after going to sleep and waking up it is necessary to unload and reload (modprobe -r alx, modprobe alx from root konsole). I could turn that into a script and set it to run at wakeup but is that a good solutions or are there better ways to do that?Please try this:```
gksudo gedit /etc/pm/config.d/config
```Add a single line:```
SUSPEND_MODULES="alx"
```Proofread, save and close gedit. Reboot, suspend and let us have your report.

---

### Post by Volta500 on 2013-06-05
My apologies for the late response but everything is working perfectly!
Again thanks for your assistance. Both for getting my wired ethernet working and learning more of Linux. It really is a great OS

---

### Post by chili555 on 2013-06-05
> **Volta500 said:**
> My apologies for the late response but everything is working perfectly!
Again thanks for your assistance. Both for getting my wired ethernet working and learning more of Linux. It really is a great OSGlad to hear it's working. Have fun!

---

### Post by senine on 2013-06-11
> **sauyon said:**
> I built the patch to work with [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2) :)

then, in the same directory as the bz2 file:
```
tar -xjvf compat-drivers-3.9-rc2-2-su.tar.bz2
cd compat-drivers-3.9-rc2-2-su
```

then copy the alx-patch file into the compat-drivers directory

then:
```
patch --dry-run -p1 < alx-patch.txt
```
and if no errors:
```
patch -p1 < alx-patch.txt
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

and you should be done :)

if you want to patch a different version of compat-drivers for whatever reason, just move the alx-patch file into drivers/net/ethernet/atheros/alx, cd to it, and instead of patch -p1, patch -p6.


This is also doable on ubuntu 13.04, thanks a lot!

---

### Post by Berillions on 2013-06-13
Hi,

I have two questions :
- Which driver-compat version i must to use with my Debian Wheezy with the kernel 3.2.41 ?
- Why this drivers is not implemented directly in the kernel ? (Even in the staging driver)

Thanks

---

### Post by HomeDread on 2013-06-13
Hi guys !

Thank for this post. If just receive my GE60 few days ago and just notice today that ethernet do not work. 
I've look the diff patch, nothing herd. But I would like to apply it on 3.9.5 kernel. Here i am in [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/) I cannot find the compat-drivers-3.9-5-2.tar.xz file. 
Do you have any idea of how get ot ? If I apply the patch as is on kernel 3.9.5 will it works ?

Thank again and in hope to read you.

Regards

---

### Post by HomeDread on 2013-06-14
Ok, I've apply the patch over the 3.9.6 kernel and it work fine.
Thank again. In hope this will be included in next satndard kernel it will be cool.

---

### Post by Volta500 on 2013-06-19
Hey again

After installing updates my ethernet stopped working again! Ive attatched the updates that were installed in the attatchment.
Will reinstalling the driver solve it or is there more to it?

The interface does not show up in the network manager GUI but I can see it in lspci. My switch the computer is connected to indicates 100Mbit connection in stead of 1Gbit, but it does report connection

Thanks

---

### Post by chili555 on 2013-06-19
> Will reinstalling the driver solve it It should:```
cd Desktop/driver_file/wherever
sudo su
make clean
make
make install 
modprobe alx
exit
```

---

### Post by Volta500 on 2013-06-19
Jap, that worked! Thank you.
Just the modprobe was not enough, it required a reboot but now everything seems to be good.

---

### Post by krasmussen on 2013-06-26
For some reason I wasn't able to get the patch to work with my E2200 in my MSI GT70 running the 3.9.6 kernel so I created my own patch maybe this will work for someone else too.

Step by Step instructions for applying the patch and compiling/installing alx:

1) wget [http://www.kernel.org/pub/linux/kern...2-20-u.tar.bz2]("http://www.kernel.org/pub/linux/kernel/projects/backports/2013/02/20/compat-drivers-2013-02-20-u.tar.bz2")

2) Save the contents of this pastebin as e2200support.patch [http://pastebin.com/FU7zVmhr](http://pastebin.com/FU7zVmhr)   # The file upload didn't want to work for me.

3) tar -xjf compat-drivers-2013-02-20-u.tar.bz2

4) patch --dry-run -p0 < ./e2200support.patch    # Not really needed but lets you check the patch

5) patch -p0 < ./e2200support.patch

6) cd compat-drivers-2013-02-20-u

7) make

8) sudo make install

9) reboot or modprobe alx

---

### Post by Fusxfaranto on 2013-06-29
Having some trouble with this, hope someone can help.  Everything compiles and installs without error, but when I modprobe it and add it to /etc/modules and reboot, it still doesn't seem to do anything.  The model of mine is E2205, lspci still gives me [1969:e091] but that might be the issue.

---

### Post by chili555 on 2013-06-29
> **Fusxfaranto said:**
> Having some trouble with this, hope someone can help.  Everything compiles and installs without error, but when I modprobe it and add it to /etc/modules and reboot, it still doesn't seem to do anything.  The model of mine is E2205, lspci still gives me [1969:e091] but that might be the issue.By 'everything' do you mean the procedure in the post just above yours or which? This is over 100 posts long and there are several methods proposed.

By the way, lspci will never change, whether the driver works or not, unless you change devices. lspci is a listing of the details of your device only.

---

### Post by Fusxfaranto on 2013-06-29
> **chili555 said:**
> By 'everything' do you mean the procedure in the post just above yours or which? This is over 100 posts long and there are several methods proposed.

By the way, lspci will never change, whether the driver works or not, unless you change devices. lspci is a listing of the details of your device only.

I tried the method outlined in the first post (along with the second  patch posted a little bit later), then after that failed to do anything I  upgraded my kernel to 3.9.8 and tried the method posted above, with the  same result.

EDIT: Nevermind, I got it working.  Not so good with Linux networking... >.>

---

### Post by Brazen on 2013-07-02
Would it be possible to use dkms with this to compile it automatically on kernel upgrades?

---

### Post by Napseis on 2013-07-02
hello,I succeeded some time ago to use the patch with the post of sauyon on page 7, but I updated my fedora (I know this is ubuntu forum but...), and now I get this error upon modprobe: 
```
 modprobe: ERROR: could not insert 'alx': Unknown symbol in module, or unknown parameter (see dmesg) 
```
I also tried with Krassmussen post, same problem. 

I have kernel 3.9.6-200.fc18.x86_64 

Edit: and this time i don't even see the wifi on my GE-60 :/ ...


Any idea please ?
Thanks

---

### Post by Berillions on 2013-07-03
Hi,

It seems that the driver for Killer E2200 appears in the kernel 3.10, see : 
[https://www.lwn.net/Articles/555179/]("https://www.lwn.net/Articles/555179/")

:)

---

### Post by fredericoschardong on 2013-07-15
> **Berillions said:**
> Hi,

It seems that the driver for Killer E2200 appears in the kernel 3.10, see : 
[https://www.lwn.net/Articles/555179/](https://www.lwn.net/Articles/555179/)

:)


Have anyone tried this?

---

### Post by fcassin on 2013-07-18
Hi,

Recent owner of a MSI GE60 2OE here. A quick message to thank Mahler122 and sauyon.
The patch described on page 7 by sauyon worked with no reboot needed.

For information I use Ubuntu 13.04 amd64.

Thanks !

---

### Post by zloe on 2013-07-19
[SIZE=1]Can someone make a patch for 3.10.1 vanilla kernel? 
drivers/net/ethernet/atheros/alx/* in attachment.
Thank you![/SIZE]
**UPD**: oh, it worsk without patching. Just enable **Qualcomm Atheros AR816x/AR817x support** in  **> Device Drivers > Network device support > Ethernet driver support**.

---

### Post by Brazen on 2013-07-19
Anyone know how to add this to dkms?  This patch and compat-drivers works great for me, but it's a hassle having to rebuild it on every kernel update.

Here is what I have so far.  I grabbed the compat-drivers-3.8.3-2-snpu from [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/) , applied the alx patch described earlier (the one of page 7 of this forum thread I think) and did the driver-select so it only compiles the alx driver.  Now all I have to do is "make && sudo make install" to get the driver.  This is on Ubuntu 12.04, btw.

Here is what I think I need to do:

1. copy the  compat-drivers-3.8.3-2-snpu folder to /usr/src/alx-3.8.3-2-snpu/
2. put a dkms.conf file in that alx-3.8.3-2-snpu folder with this in it:

    MAKE="make -C compat-drivers-3.8.3-2-snpu/"
    BUILT_MODULE_NAME=alx
    BUILT_MODULE_LOCATION=compat-drivers-3.8.3-2-snpu/drivers/net/ethernet/atheros/alx/
    PACKAGE_NAME=alx
    PACKAGE_VERSION=3.8.3-2-snpu
    AUTOINSTALL=yes
    REMAKE_INITRD=no

3. run "sudo dkms add -m alx -v 3.8.3-2-snpu"

At that point I get an error that says it needs a DEST_MODULE_LOCATION which I think may just be "/updates".

Looking through the kernel modules built by the "make install" makes me think I may also need to do something with compat.ko, but I'm pretty lost at this point and need to get back to studying.

**BTW: for anyone else getting to this point in the thread**, if you just got the 3.10 compat drivers (now called "backports") from my link in this post, you probably don't even need to patch.  Just driver-select, make, and sudo make install.

---

### Post by Brazen on 2013-07-19
I gave it another quick try and was able to get dkms to add it with this dkms.conf:

```
MAKE="make -C compat-drivers-3.8.3-2-snpu/"
BUILT_MODULE_NAME[0]=compat
BUILT_MODULE_LOCATION[0]=compat-drivers-3.8.3-2-snpu/compat/
DEST_MODULE_LOCATION[0]=/updates
BUILT_MODULE_NAME[1]=alx
BUILT_MODULE_LOCATION[1]=compat-drivers-3.8.3-2-snpu/drivers/net/ethernet/atheros/alx/
DEST_MODULE_LOCATION[1]=/updates
PACKAGE_NAME=alx
PACKAGE_VERSION=3.8.3-2-snpu
AUTOINSTALL=yes
REMAKE_INITRD=no
```

I'll have to wait for the next kernel update to see if it works.

UPDATE: installed an older kernel and it would not compile.  The make log says "make: *** No targets.  Stop." even though when I run it manually it works fine.

---

### Post by jsffan on 2013-07-20
I have an MSI Xpower and the patch described on page 7 by sauyon worked with no reboot needed.

---

### Post by paulvarjak on 2013-08-27
Works for me with the instructions in post 63 and the patch attached to post 61.
Ubuntu 13.04 kernel 3.8.0-30-generic x86_64.

My HW is: Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)
The laptop is an MSI GE60 - 259ES

Thanks a lot.

---

### Post by Mandy_Bradshaw on 2013-08-27
Thanks for this! I have been finding out how to use [COLOR=#000000]Qualcomm Atheros Bigfoot Killer E2200 to my linux. followed your tutorial and it really works! thanks again, dude.[/COLOR]

---

### Post by chili555 on 2013-08-27
Please see post #4 and following here. No patch is required. [http://ubuntuforums.org/showthread.php?t=2166562&highlight=E2200](http://ubuntuforums.org/showthread.php?t=2166562&highlight=E2200)

---

### Post by amlittle042 on 2013-09-04
> **krasmussen said:**
> For some reason I wasn't able to get the patch to work with my E2200 in my MSI GT70 running the 3.9.6 kernel so I created my own patch maybe this will work for someone else too.

Step by Step instructions for applying the patch and compiling/installing alx:

1) wget [http://www.kernel.org/pub/linux/kern...2-20-u.tar.bz2]("http://www.kernel.org/pub/linux/kernel/projects/backports/2013/02/20/compat-drivers-2013-02-20-u.tar.bz2")

2) Save the contents of this pastebin as e2200support.patch [http://pastebin.com/FU7zVmhr](http://pastebin.com/FU7zVmhr)   # The file upload didn't want to work for me.

3) tar -xjf compat-drivers-2013-02-20-u.tar.bz2

4) patch --dry-run -p0 < ./e2200support.patch    # Not really needed but lets you check the patch

5) patch -p0 < ./e2200support.patch

6) cd compat-drivers-2013-02-20-u

7) make

8) sudo make install

9) reboot or modprobe alx

This worked for my MSI GT70 -- thanks a ton!

---

### Post by rakoun2 on 2013-09-04
> **keesvandieren said:**
> Finally got it working, with Intel Ivy Bridge processor and Ubuntu 12.04 and Kernel 3.6

Steps:

[LIST]
[*] Installed kernel 3.6 (as described here: [http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html](http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html) ) 
[*] Downloaded drivers from [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2) and apply both patches 
[*] Extract archive and chdir into it 
[*] run: sudo su 
[*] run: ./scripts/driver-select alx 
[*] run: make 
[*] run: make install 
[*] run: make unload 
[*] reboot 
[/LIST]
The topic start post does not mention the step: [FONT=Courier New]/scripts/driver-select alx[/FONT], linuxwireless.org [does]("http://linuxwireless.org/en/users/Download/stable/#Building_and_installing"). Should it be listed there as well?
that works for my computer (GE60 )but &#305; couldnt make the patch2 (tty...) but this computers bluethooth doesnt working also in windows. 
so thanks for your solution

---

### Post by Regis_Wang on 2013-10-15
> **sauyon said:**
> I built the patch to work with [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc2/compat-drivers-3.9-rc2-2-su.tar.bz2) :)

then, in the same directory as the bz2 file:
```
tar -xjvf compat-drivers-3.9-rc2-2-su.tar.bz2
cd compat-drivers-3.9-rc2-2-su
```

then copy the alx-patch file into the compat-drivers directory

then:
```
patch --dry-run -p1 < alx-patch.txt
```
and if no errors:
```
patch -p1 < alx-patch.txt
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

and you should be done :)

if you want to patch a different version of compat-drivers for whatever reason, just move the alx-patch file into drivers/net/ethernet/atheros/alx, cd to it, and instead of patch -p1, patch -p6.[FONT=arial]
Mahler122 and Sauyon ([/FONT][FONT=arial]page 7)[/FONT][FONT=arial]
[/FONT][FONT=arial][SIZE=2]thx a lot!!! 
[/SIZE][/FONT][COLOR=#000000][FONT=arial]I appreciate it[/FONT][/COLOR][FONT=arial][SIZE=2]
you take all the pains that [/SIZE][SIZE=2]I feel!
you know, the wireless network speed is too slow.[/SIZE]

first I uesd the method in page 1,but i faildt.
then i try the method in page7,it works!

PC:MSI GE60 2OC-051XCN
[/FONT][COLOR=#333333][FONT=arial]System version:Ubuntu 13.04[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Kernel:3.8.0-31-generic[/FONT][/COLOR][FONT=arial]
HW: [/FONT]```
03:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)    Subsystem: Micro-Star International Co., Ltd. Device 10e6
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f7a00000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at d000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: alx

```
[FONT=arial]

[/FONT]

---

### Post by komeyl_dalaei on 2013-10-23
hi guys!
i followed the structure explaind in post #1 and after trying the first code i received this output:
```
[SIZE=3]komeyl@komeyl:~$ sudo apt-get install build-essential linux-headersReading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers is a virtual package provided by:
linux-headers-3.5.0-17 3.5.0-17.28
linux-headers-3.5.0-17-generic 3.5.0-17.28
You should explicitly select one to install.
E: Unable to locate package build-essential
E: Package 'linux-headers' has no installation candidate[/SIZE]

```

does this error influence the procedure to install driver?

thx a lot!

---

### Post by chili555 on 2013-10-24
> **komeyl_dalaei said:**
> hi guys!
i followed the structure explaind in post #1 and after trying the first code i received this output:
```
[SIZE=3]komeyl@komeyl:~$ sudo apt-get install build-essential linux-headersReading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers is a virtual package provided by:
linux-headers-3.5.0-17 3.5.0-17.28
linux-headers-3.5.0-17-generic 3.5.0-17.28
You should explicitly select one to install.
E: Unable to locate package build-essential
E: Package 'linux-headers' has no installation candidate[/SIZE]

```

does this error influence the procedure to install driver?

thx a lot!Please try linux-headers[COLOR="#FF0000"]-generic[/COLOR].

---

### Post by komeyl_dalaei on 2013-10-25
> **chili555 said:**
> Please try linux-headers[COLOR=#FF0000]-generic[/COLOR].

i received this output:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package build-essentiall

```

:-k   ](*,)

---

### Post by chili555 on 2013-10-25
> E: Unable to locate package build-essentiallIt is not build-essentiall; it is build-essential with *one* trailing L. For your convenience, you can simply copy and paste the commands into your terminal.```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by komeyl_dalaei on 2013-10-25
> **chili555 said:**
> It is not build-essentiall; it is build-essential with *one* trailing L. For your convenience, you can simply copy and paste the commands into your terminal.```
sudo apt-get install build-essential linux-headers-generic
```

i received same error again. does this command needs to internet to work properly?

---

### Post by chili555 on 2013-10-25
> **komeyl_dalaei said:**
> i received same error again. does this command needs to internet to work properly?Yes, indeed, it does. Can you get, beg, borrow or steal a wireless connection, even for just a few moments?

---

### Post by komeyl_dalaei on 2013-10-26
finally i passed the first command ):P

but after trying "make" command, i received this output with some errors:

komeyl@komeyl:~/Desktop/compat-wireless-2012-05-10-p$ make```

make -C /lib/modules/3.5.0-17-generic/build M=/home/komeyl/Desktop/compat-wireless-2012-05-10-p modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/alx/alx_main.o
  CC [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/alx/alx_ethtool.o
  CC [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/alx/alc_cb.o
  CC [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/alx/alc_hw.o
  CC [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/alx/alf_cb.o
  CC [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/alx/alf_hw.o
  LD [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/alx/alx.o
  CC [M]  /home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm/tty.o
/home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm/tty.c: In function ‘rfcomm_tty_open’:
/home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm/tty.c:713:3: error: too many arguments to function ‘tty_unlock’
In file included from /home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm/tty.c:30:0:
include/linux/tty.h:609:24: note: declared here
/home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm/tty.c:715:3: error: too many arguments to function ‘tty_lock’
In file included from /home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm/tty.c:30:0:
include/linux/tty.h:608:24: note: declared here
make[4]: *** [/home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm/tty.o] Error 1
make[3]: *** [/home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth/rfcomm] Error 2
make[2]: *** [/home/komeyl/Desktop/compat-wireless-2012-05-10-p/net/bluetooth] Error 2
make[1]: *** [_module_/home/komeyl/Desktop/compat-wireless-2012-05-10-p] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [modules] Error 2
komeyl@komeyl:~/Desktop/compat-wireless-2012-05-10-p$
```

---

### Post by chili555 on 2013-10-26
For your 3.5.0-xx kernel, try this package instead: [http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046](http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046)

---

### Post by komeyl_dalaei on 2013-10-28
> **chili555 said:**
> For your 3.5.0-xx kernel, try this package instead: [http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046](http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046)

my ubuntu version was 12.10, and that method worked very well. thanke you very vey very much [COLOR=#ff0000]chili555[/COLOR]!

---

### Post by bert.creemers on 2013-11-09
and Yes, besides some missing related libraries (all solvable with simple logic), your instructions rode me right to a working e2200 on a 1000Mbs ...
very grateful for your effort/post.

Thanks Chili !!!

---

### Post by swdonline2 on 2013-11-11
Thanks for all the hard work chili555!  Posting this for others who encounter the same problem.

Several weeks ago, when the 3.2.0-55 64-bit kernel for Ubuntu 12.04 was released, this solution stopped working for me (after working for over a year).  I could no longer make the compat-wireless-3.6.2-1-snpc drivers, receiving the following errors: 

[I]make[1]: Entering directory `/usr/src/linux-headers-3.2.0-56-generic'
  CC [M]  /usr/local/src/compat-wireless-3.6.2-1-snpc/compat/main.o
In file included from /usr/local/src/compat-wireless-3.6.2-1-snpc/include/linux/compat-2.6.h:64:0,
                 from <command-line>:0:
/usr/local/src/compat-wireless-3.6.2-1-snpc/include/linux/compat-3.4.h:32:21: error: redefinition of ‘kmalloc_array’
include/linux/slab.h:243:21: note: previous definition of ‘kmalloc_array’ was here[/I]

However*,* as of kernel 3.2.0-56, I can now use the backports solution posted at [http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046](http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046).  This is working for me with kernel 3.2.0-56 and backports 3.11.6-1.

---

### Post by chris131 on 2013-11-20
Hello everyone! I wanted to say that solution from thunder130990 which can be found on page 7 solved my problems with MSIGE070ND laptop. I owe you a brew guys.

---

### Post by chris131 on 2013-11-20
Hello everyone! I wanted to say that solution from thunder130990 which can be found on page 7 solved my problems with MSIGE070ND laptop. 
3.7-trunk-amd64   
I owe you a brew guys. And big thank to you thunder130990
Thank u, now my gt60 can use the ethernet!

---

### Post by curtistheiii on 2013-12-22
Hey,

I have just purchased a new mother board [SIZE=2]GIGABYTE GA-G1.Sniper M5. It says it has a Atheros Killer E2201. Im not sure if this makes a difference or not but i have not been able to get any of the patches to work. Is there anyway you guys can help me out. Im new to this kind of stuff so just tell me what to do. Im running [/SIZE]Ubuntu Server 12.04.3 LTS, but if theres another version of ubuntu server I should run i have no problem installing a new os.

---

### Post by chili555 on 2013-12-22
I strongly suspect that, since this is a Bigfoot E2201 and not an E2200, that it's a different new device. I love new devices! I suggest you start a new thread and post:```
lspci -nn | grep 0200
```If I don't catch it right away, please send me a private message.

---

### Post by cokex on 2014-02-13
Thanks! This worked perfectly for me .. using BAMT 1.5 and ASRock Fatal1ty Z87 killer mother board.

I booted up the BAMT on usb, plugged in another usb drive with the drivers and patches, I only applied the first patch from the first page here.

My steps: 

copy driver and patch to usb drive, plug into BAMT server, copy the files to the user directory, open up a terminal, change into the directory, and then run the commands below.

# tar -xvf /path/to/compat-wireless-2012-05-10-p.tar.bz2
# cd ./compat-wireless-2012-05-10-p.tar.bz2
# patch --dry-run -p2 < /path/to/compat-patch.txt
# patch -p2 < /path/to/compat-patch.txt

and then run what is below .. 

# ./scripts/driver-select alx (what this does is setup the config to only compile the alx driver, saves time)
# make
# make install
# make unload
# reboot 

came right up after reboot .. 

I did add 'auto eth0, and setup dhcp' in /etc/network/interfaces before I found out about needing this driver so this might need to be added if ifconfig doesn't show eth0.

Thanks again for the great work on this patch .. 

> **keesvandieren said:**
> Finally got it working, with Intel Ivy Bridge processor and Ubuntu 12.04 and Kernel 3.6

Steps:

[LIST]
[*] Installed kernel 3.6 (as described here: [http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html](http://www.upubuntu.com/2012/10/install-linux-kernel-363-in-ubuntu.html) ) 
[*] Downloaded drivers from [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.2-1-snpc.tar.bz2) and apply both patches 
[*] Extract archive and chdir into it 
[*] run: sudo su 
[*] run: ./scripts/driver-select alx 
[*] run: make 
[*] run: make install 
[*] run: make unload 
[*] reboot 
[/LIST]
The topic start post does not mention the step: [FONT=Courier New]/scripts/driver-select alx[/FONT], linuxwireless.org [does]("http://linuxwireless.org/en/users/Download/stable/#Building_and_installing"). Should it be listed there as well?

---

### Post by chili555 on 2014-02-13
> tar -xvf /path/to/compat-wireless-[COLOR="#FF0000"]2012-05-10[/COLOR]-p.tar.bz2An old, old package. There are more efficient ways to do this and without a patch. I hope the next searcher that comes along will try this instead: [http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046](http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046)

---

### Post by cokex on 2014-02-13
> **chili555 said:**
> An old, old package. There are more efficient ways to do this and without a patch. I hope the next searcher that comes along will try this instead: [http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046](http://ubuntuforums.org/showthread.php?t=2166562&p=12752046#post12752046)

Ahh.. much cleaner way to do this .. nice

---

### Post by ckyong on 2014-06-15
thanks a lot..it's work like charm :)

---

### Post by cavensben on 2014-08-08
thank you. 
Your solution worked out great on my machine. My eth0 driver was not to be found in ifconfig -a. Your patch made is appear! 

Machine: ubuntu 12.04 on a MSI GE60, Qualcomm Atheros Killer E2200 ethernet controller

---

### Post by el-rayado-verde on 2015-05-14
Hi!

I've just installed Ubuntu 15.04 and cannot connect to the internet via Ethernet, I've tried several tutorials detailed in some of these threads but I get errors. I don't know what to do. I'm kind of new to Linux, so please I beg for your patience and collaboration.
The moment I get errors is after executing the first 'make' command. What can I do?

---

### Post by chili555 on 2015-05-14
This old and very long thread contains information that was probably very valid when written but is quite stale for today's newer kernels. I suggest you start a new thread and include:```
lspci -nn | grep 0200
nm-tool
```Thanks.

---

