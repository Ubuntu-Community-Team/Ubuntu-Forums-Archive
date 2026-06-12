---
title: "Networking disabled after using/installing VPN"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by atomicben on 2011-08-07
Everything was working fine today and for many days before today. (this is a pretty fresh install of 10.10 Maverick).

I installed a VPN connection (PPTP) to connect to work.

That worked fine.  i connected, remoted into the machine I wanted and did what I had to do.  Here's where it gets weird.

I was ABOUT to disconnect from the VPN and when I clicked on the network manager icon BAM it said DISCONNECTED.  I figured, thanks... saved me another click or 2.  But now I have no networking at all.

The network manager icon says "Networking disabled"

I tried:
warm booting a couple times
cold booting a couple times

I also tried:

```
service restart networking
```

and

```
sudo /etc/init.d/networking restart
```

when I first did 'service restart networking' I got:

> $ service networking start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.40" 
(uid=1000 pid=1610 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" 
requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

Now, it doesn't matter what I do I get "unknown instance"

I tried booting from a LiveCD and the network works just fine.  So I don't think it's hardware.  Here's my lspci if you need it:

> $ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
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
**01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)**
03:02.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
03:02.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

This is a wired connection and the activity lights are on.


I would really just like to delete/uninstall anything that has to do with VPN's and see if that works.  Or maybe reinstall network manager.  Are those reasonable places to start?

This is so weird.  Please advise!

---

### Post by atomicben on 2011-08-07
Weird, on the forums there are 2 almost brand new threads that sound a lot like mine:

[B]Ethernet port suddenly stopped working
[/B][http://ubuntuforums.org/showthread.php?t=1820471](http://ubuntuforums.org/showthread.php?t=1820471)

and 

**Network Disabled**
[http://ubuntuforums.org/showthread.php?t=1819811](http://ubuntuforums.org/showthread.php?t=1819811)


my lshw also says :

> *-network DISABLED


What's going on?  COuld we all have the same problem at the same time?  What are the odds?

---

### Post by atomicben on 2011-08-07
Damn, I am making things worse.

I figured that I'd reinstall network-manager.  Without even thinking I ran:

sudo apt-get remove network-manager

but now I can't reinstall because I have no internet.  I'm a total stoop.

---

### Post by atomicben on 2011-08-07
OMG I can't believe this.

So after all that nightmare I found a page that had a similar problem and all it was was right clicking network manager and clicking Enable Networking.

I think I know what happened now.  I went to disconnect but I must have right clicked and somehow i clicked Enable Networking.  I didn't catch it because I had thought it just disconnected itself.  How embarrassing.

Well.  I've got egg on my face.  I think I'm going to go drink and cry now.

---

