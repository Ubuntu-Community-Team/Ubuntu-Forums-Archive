---
title: "wireless interface won't enable - fresh install of ubuntu 8.10"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by anng on 2009-01-01
I'd sure like some help.  I bought my son a used laptop from ebay and it came with PCLinuxOS and vmware.  After about 2 days I ditched that and decided to go with Ubuntu and wine.  I downloaded a CD ISO file last night and installed Ubuntu.  However, I've tried everything I can think of and everything I've found though googling but I can't get the wireless interface up.  There is no ethernet NIC on the laptop, so it has no other access to the internet.

----- 

Dell latitude D600
Ubuntu 8.10 (installed last night)
previous os: PCLinuxOS 2007 - wireless worked then
no ethernet card so wireless only option (I'm on another computer to post this)

lspci output:  Croadcom Corporation BCM4306 802.11b/g 
               Wireless LAN COntroller (rev 02)

lshw -C network output  (forgive any typo's please)
    *-network
      description: Network controller
      product: BCM4306 802.11b/g Wireless LAN Controller
      vendor: Broadcom Corporation
      physical id: 3
      bus info: pci@000:02:03:0
      version: 02
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list
      configuration: driver:b43-pci-bridge latency=32 module=ssb
    *-network DISABLED
      description: Wireless interface
      physical id: 1
      logical name: wlan0
      serial: 00:90:4b:6b:bd:de
      capatilities: ethernet physical wireless
      configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

/etc/network/interfaces
   auto lo
   iface lo inet loopback
    
Thanks,
anng

---

### Post by anng on 2009-01-01
any ideas?  I haven't gotten any reply.

---

### Post by kevdog on 2009-01-01
You are in a little bit of a pickle.  The b43 driver requires installation of the closed source broadcom firmware in order to make a fully functional wireless driver.  I believe the firmware can be downloaded here:
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

Notice firmware is dependent on your kernel version which you may check by typing
uname -r 
at the command line.
If you had an ethernet connection -- this would be fully automated for you.  However the way you need to do it is the way we used to all have to do it -- so a little bit of history for you!!

---

### Post by anng on 2009-01-01
Thanks!  I don't mind the command line route at all.  I'll give it a try.

---

### Post by melojo on 2009-01-01
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by kevdog on 2009-01-01
melojo

That's a very good link written by a credible source.

The only change I would make to the guide is that at the end of the process you edit your /etc/apt/sources.list and remove the cd-rom as one of the repositories.  I would also verify that you are downloading the correct version of the firmware by cross-referencing on the b43 page.  That would be about all.

---

### Post by Mac Jingles on 2009-01-01
anng,

Please post your progress. I believe I'm having the same problem.

---

### Post by anng on 2009-01-02
> **Mac Jingles said:**
> anng,

Please post your progress. I believe I'm having the same problem.

Mac Jingles - I'm at work today so it will probably be tomorrow before I can look at it again.  I did try manually configuring it last night per the first post, but the interface is still determined to be disabled.

The frustrating thing is I talked my son into using linux because I feel completely lost with Windows.  You'd think I could at least get a network interface up.  But... from looking at the myriad of similar posts here, it seems that getting the wireless interface up may actually be a pain, not just me being inept.

On Wednesday I did actually have it up, but 1) it did not stay up after I rebooted, 2) for the life of me I don't know what I actually did to finally get it up, and 3) at that time even though the interface was up, I didn't have dhcp correctly configured so I could get lookups working.

---

### Post by anng on 2009-01-02
Thanks melojo!!!

The best part about working with folks who are way bigger techies than you are is that the best and the nicest can really make your life easier.  Needless to say, a coworker helped me out today.  We followed this link from melojo: [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72) .  The wireless now works!

On another good note, the coworker discovered that I actually do have an ethernet nic, it was just disabled in the bios so it didn't even show up with commands like dmesg and ifconfig.  Enabling that in the bios gave us an internet connection which made life oh so much easier. (I had seen the nic receptor, but couldn't find anything in dmesg or ifconfig to indicate that the nic actually existed).

I'm going to have one happy son when I get home.  Now on to installing wine and a few of his games.

Have a good weekend all and Happy New Year.

anng

---

### Post by Mac Jingles on 2009-01-02
Unfortunately, melojo's link and the instructions from it did not get my wireless working.

I'm using Xubuntu 8.04.1
Kernel 2.6.24-19 Generic

Similar information appears:

CODE
> 
mike@Jingles:~$ sudo lshw -C network
*-network
 description: Network Controller
 product: BCM4306 802.11b/g Wireless LAN Controller
 vendor: Broadcom Corporation
 physical id: b
 bus info: pci@0000:00:0b.0
 version: 03
 width: 32 bits
 clock: 33MHz
 capabilities: bus_master
 configuration: driver=b43-pci-bridge latency=32 module=ssb
*-network DISABELED
 description: Wireless interface
 physical id: 1
 logical name: wlan0
 serial: 00:11:50:1f:31:0a
 capabilities: ethernet physical wireless
 configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

The whole process was successful until i got to the last line of command:

code
> sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device

I know I'm missing something here. Any help or direction to links/threads would be most helpful.

Best,

-MJ

---

### Post by anng on 2009-01-06
MJ,

That's the error I was getting at first.  Did you get any errors or messages when you got to this part of the instructions?

  cd
  sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
  tar xfvj broadcom-wl-4.150.10.5.tar.bz2
  sudo b43-fwcutter --unsupported -w /lib/firmware  
  broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
  sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

- Ann

---

### Post by lord_lethris on 2009-01-06
I know this isn't the answer your looking for, but most "broadcom" chipset wireless devices are actual not supported very well under any distro of linux.

Almost everyone I know, just gave up and purchaced wireless dongle/card without the broadcom chipset.

You CAN try this ->

[I]enable 3rd party software, then under "add/remove..." search for "ndiswrapper" and select the software called "Windows Wireless driver" (or somthing like that)

Once installed, you will find it under "Applications->System->Admin" (I think, if I can remember)

Download an older set of broadcom drivers (the version pre current version usually works best), for WIN2000 or WINXP for you hardware ([COLOR="Red"]**NOTE:** NOT linux driver[/COLOR]) and use this tool to install them.[/I]

If that doesn't work, dont loose heart, as I said before, a sh*te load of people have the same issue, and more often than not, these Broadcom drivers are impossable to install.

Good luck.

---

### Post by Mac Jingles on 2009-01-12
Thanks for the support!

I still haven't gotten it to work on that computer. I'll try a couple more times, but its not worth getting to frustrated over. The broadcom just doesn't seem worth it.

I installed Ubuntu 8.10 on my new laptop and the internet worked perfectly the first time... but would like to get wireless working on my desktop as well.

Best,

-MJ

---

