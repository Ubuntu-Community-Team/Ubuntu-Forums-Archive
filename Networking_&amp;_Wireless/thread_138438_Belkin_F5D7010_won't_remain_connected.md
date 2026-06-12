---
title: "Belkin F5D7010 won't remain connected"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by roachk71 on 2006-03-01
[LEFT]This is an irksome problem:

I just bought a Belkin F5D7010, version 5000 802.11g card, and even though I have it working with ndiswrapper, the connection is intermittent at best.

I have the latest drivers from the Belkin site. Should another driver be used? Also, after rebuilding ndiswrapper, it can't be modprobed (permission denied, even as root!)

Any help with these issues would be greatly appreciated.

Note: I have five years of experience with linux, but I'm neither nerd nor total geek. (chuckle) 

Addendum: Not using DHCP helps, albeit marginally... (Sighs) And I tried installing the driver from the CD instead of from their site; Maybe that'll make things better. We'll see...
[/LEFT]

---

### Post by Lambert on 2006-03-02
Post the output of these commands.

sudo lshw -C network

This one won't give output
sudo slocate -u

then

sudo slocate | grep ndiswrapper.ko

modinfo ndiswrapper


OPen a terminal and watch your syslog file for any errors during the intermitant time.

tail -f /var/log/syslog

---

### Post by roachk71 on 2006-03-02
[LEFT]Good Morning,

The first command's output:
```
*-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network DISABLED
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:31:44:a4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=natsemi driverversion=1.07+LK1.0.17 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:2400-24ff iomemory:d0004000-d0004fff irq:10
  *-network
       description: Wireless interface
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@02:00.0
       logical name: wlan0
       version: 01
       serial: 00:11:50:70:88:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper ip=192.168.1.128 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0100000-d010ffff irq:11


``` 
modinfo ndiswrapper code:

```

filename:       /lib/modules/2.6.12stack16k/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.1
license:        GPL
vermagic:       2.6.12stack16k SMP preempt PENTIUM4 16KSTACKS gcc-3.4
depends:        usbcore
srcversion:     13A3C1D1DB65F026DBFF725
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)

``` 

Of course, I had to burn the midnight oil until 3:30 this morning, as I waited for a custom kernel to be built. This has made it more reliable with the 16k kernel stacks patch, though it still has to disconnect and rescan the network.

Also, the output shows the device as having an AR5001 chipset; This card has an AR5211. I wonder if that's significant?
[/LEFT]

---

### Post by Lambert on 2006-03-02
add one more to run

sudo dpkg -s linux-restricted-modules-`uname -r`

---

### Post by roachk71 on 2006-03-02
```
Package `linux-restricted-modules-2.6.12stack16k' is not installed and no info is available.

```

Of course, I'm using ndiswrapper, so I had thought restricted modules wouldn't be required.

---

### Post by Lambert on 2006-03-02
It's not, just wanted to make sure it wasn't installed as two drivers for a device could cause a conflict.

---

### Post by roachk71 on 2006-03-02
[LEFT]Of course, I haven't retried DriverLoader with the new kernel yet. I probably will afterwhile, but it wouldn't even bring the card up with the stock kernel. Hmm... :-?

One more thing: I wonder if a member of the community would be willing to host the new kernel and headers in their repositories for people who can't afford to wait for the build process, since the 16k stack patch is very helpful... This one's for  P4 and Celeron  architectures,  but  solves  a  lot  of efficiency issues.

OOPS!!

I forgot to add that this kernel is DMA optimized as well. Some computers don't jive well with that optimization. Just a word of caution.

UPDATE: Just retried DriverLoader a few minutes ago. This is a no-go: it reports that the card is not present, or that either the device or driver is incompatible (which is utter baloney.)

A little something extra for ya found using dmesg|grep ndis:
```

[4294715.591000] ndiswrapper version 1.1 loaded (preempt=yes,smp=yes)
[4294715.725000] ndiswrapper: driver blkwgn (Belkin,06/01/2005,4.1.2.56) loaded
[4294716.210000] ndiswrapper: using irq 11
[4294716.312000] ndiswrapper (NdisAllocateMemory:200): Windows driver allocating too big a block at DISPATCH_LEVEL: 200336
[4294716.916000] ndiswrapper (NdisAllocateMemory:200): Windows driver allocating too big a block at DISPATCH_LEVEL: 200336
[4294716.921000] wlan0: ndiswrapper ethernet device 00:11:50:70:88:c4 using driver blkwgn, configuration file 168C:001A.5.conf
[4294716.925000] ndiswrapper (NdisAllocateMemory:200): Windows driver allocating too big a block at DISPATCH_LEVEL: 200336
[4294717.286000] ndiswrapper (NdisAllocateMemory:200): Windows driver allocating too big a block at DISPATCH_LEVEL: 200336
[4294717.296000] ndiswrapper (NdisAllocateMemory:200): Windows driver allocating too big a block at DISPATCH_LEVEL: 200336
[4294985.522000] ndiswrapper (NdisAllocateMemory:200): Windows driver allocating too big a block at DISPATCH_LEVEL: 200336

```
[/LEFT]

---

### Post by csevcik on 2006-03-04
Would it be possible that your router is asssigning channels dynamically (in auto mode) and your card is set to a fixed channel (say 11)?

If so if your router is serving another user through say, channel 6, your card may not connect.

I tried to solve this (with root priviledges) as:

**iwconfig wlan0 channel auto**

only to get

[B]Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.[/B]

So I edited by hand the F5D7010 configuration file /etc/ndiswrapper/**bcmwl5**/14E4:4320:1799:7010.5.con in my system. The bcmwl5 part of the path may be diferent (I do not know if the name of the config file would be different too) if you are not using the original Belkin MS W drivers. The part I changed determines channel scanning and in my case now looks like this:

.
.
.
antdiv|-1
BadFramePreempt|0
[B]Channel|1
Channel|11
Channel|1
[/B]EnableAutoConnect|0
.
.
.

the bold part means something like "start scanning from channel 1 upto channel 11 incrementing in steps of 1". Originally was Channel|11 only once in the cf file which set the card to read only Channel 11. My card now works great in home and in my office, my home router is in auto mode and my office router is set fixed to channel 11.

I hope this helps you

Carlos

---

### Post by roachk71 on 2006-03-05
[LEFT]I'd already checked into that. This version of DD-WRT won't support dynamic channel assignment (and to my knowledge, neither will the router's hardware.) The router is a WRT54G.

I'm typing this reply using an older tower, with Breezy installed. The card installed in this one has only one problem: too many obstructions, affecting throughput. (At least it did before i pulled it off of the floor.) I _really_ had to recompile the kernel for this one, since it was too slow running any of the stock kernels.

The card is a WMP11 version 2.7, which has a Broadcom BCM4301. It's having absolutely no problems since the machine was moved. :cool:

I had forgotten to add that the notebook now usually sits atop the desk since its VGA port has bent pins. The problem remains: even close to the router, it has problems remaining connected.

Of course, it isn't too much of a problem now; I've removed an ndiswrapper reference in /etc/modules, since it's not needed by the recompiled kernel. It mainly has problems after boot: it initially associates, then, two minutes later, disconnects and scans for networks and associates again more reliably.
[/LEFT]

---

### Post by roachk71 on 2006-03-05
[LEFT]Update to the last reply:

Turns out the WMP11 card has a bad antenna, as well. It had gotten broken two weeks ago while everything was being moved around (It just started having problems an hour ago.)

Oh well... :neutral:
[/LEFT]

---

### Post by roachk71 on 2006-03-07
[LEFT]***HUGE UPDATE***[/LEFT]
    
I downloaded the latest NDISWrapper source last week (version 1.10). I had apparently not followed all of the compilation instructions.
 
The source has just been built and the driver installed, and with the 16k Stacks option in my custom kernel (this information is for those new to the thread), the interface no longer drops off after booting, and it really flies!!!
 
I can't really call the problem solved, until I've thoroughly tested the new configuration for at least a few days. I'm still quite happy the installation worked out though! \\:D/
 
Special Note: For those of you who need a newer wireless card to work correctly under Ubuntu (Breezy), please check out the top two links in my signature; These are a must-read (you'll have to compile a custom kernel before the NDISWrapper source can be compiled, and not all cards will work anyway.) However, you should learn as much as you can about kernel compilation before proceeding. This can either give you great satisfaction, or lots of headaches, depending on your experience.

---

### Post by roachk71 on 2006-03-07
[LEFT]Hey, Y'all,

Day 1:

All is working quite well. Link quality's unavailable, but the ndiswrapper site told me to expect that.

The card's still fast and reliable, and judging by performance the link is quite strong. Apparently, the card is a quality product. I simply had the wrong 'wrapper.

Later!  :KS
[/LEFT]

---

### Post by roachk71 on 2006-03-11
[LEFT]I Feel like an idiot, and I guess I should.

Apparently, this card is already supported quite well by the ath_pci driver. No lights on the card, but the network monitor tells all, and so do the network tools.

I had to do a clean installation to find out I was taking the wrong advice myself!

However, I'll leave those links in my signature for those who really do need 'em...

Later...:mrgreen:
[/LEFT]

---

### Post by roachk71 on 2006-03-14
[LEFT]UH OH!!

It would appear that my post about having to recompile the kernel with the stack patch and compiling ndiswrapper were correct...

The ath_pci module detects the card as an AR5212, when it's an AR5211, and the card keeps dropping packets, so I'm gonna redo the original operation.

Note to those who own an F5D7010 version 5 (5000) card: You just might have to go through all of those steps anyway. The ath_pci module is experimental (and in my opinion unstable.) :mad:

Unfortunately, I'll have to reinstall Ubuntu using a file system other than XFS through LVM, which I'll do later.

It's either ath_pci, or our DSL modem's almost had it.
[/LEFT]

---

### Post by roachk71 on 2006-03-15
[LEFT]I'm back...

Using the configuration I had before temporarily reinstalling windows, with a custom kernel (without having to make a clean installation!!) and a more reliable NDisWrapper.

Happy camper now! :-D
[/LEFT]

---

