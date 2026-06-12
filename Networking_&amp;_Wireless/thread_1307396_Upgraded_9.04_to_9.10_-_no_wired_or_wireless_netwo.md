---
title: "Upgraded 9.04 to 9.10 - no wired or wireless networking"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by syntonic on 2009-10-31
Hi all,

Yes, another person having problems with networking after upgrading from 9.04 to 9.10. Have also tried a fresh install of 9.10 and it still doesn't work. I've tried a number of solutions that seem to be working for some other people to no avail so here's the standard things ppl are asking for :

```
lshw -C network
  *-network               
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: driver=iwlagn latency=0
       resources: irq:16 memory:be000000-be001fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 16
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:be100000-be103fff ioport:3000(size=256) memory:be200000-be21ffff(prefetchable)
``````
lsmod | grep iwlagn
iwlagn                109052  0 
iwlcore               112508  1 iwlagn
mac80211              181236  2 iwlagn,iwlcore
cfg80211               93052  3 iwlagn,iwlcore,mac80211
```dmesg says :

```
[   11.368516] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input10
[   11.386059] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[   11.528313] cfg80211: World regulatory domain updated:
[   11.528316]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.528318]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.528320]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.528322]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.528324]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.528326]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.815266] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   11.815269] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.815324] iwlagn 0000:02:00.0: enabling device (0000 -> 0002)
[   11.815332] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.815344] iwlagn 0000:02:00.0: setting latency timer to 64
[   11.815363] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0xFF00FFFF
[   11.966532] iwlagn 0000:02:00.0: Failed, HW not ready
[   11.966542] iwlagn 0000:02:00.0: PCI INT A disabled
[   11.975846] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.415953] ppdev: user-space parallel port driver
```It's a Toshiba Satellite Pro P300 and as I mentioned before everything was working fine in 9.04 (and 8.10 before that).

The "HW not ready" message suggests if there's a way to increase the wait period it might fix the problem with wireless.

Wired is totally broken - where as it worked out of the box in 8.10 and 9.04 it doesn't seem to have a valid driver in 9.10. Suggestions welcome though.

Any suggestions would be much appreciated.

Thanks in advance,
Paul.

---

### Post by lapate on 2009-10-31
+1 I have exactly same problem, same config:(

---

### Post by dougallen on 2009-10-31
I have the same problem with a Toshiba Satellite Pro P300.  No ethernet or wireless.  /etc/network/interfaces contains only the auto lo entry.  If I edit it to include auto eth0 and iface eth0 inet dhcp and then restart the network with /etc/init.d/networking restart, I get an error message saying eth0: ERROR while getting interface flags: No such device.  It seems the ethernet and wireless cards are not being detected at all.  The wired card is a Marvell 88E8040 PCI-E Fast Ethernet Controller and the wireless card is an Intel Wireless WiFi Link 5100.  Everything worked fine with Ubuntu 9.04, Kubuntu 9.04 and openSUSE 11.1.  There is no network at all with Ubuntu 9.10, Kubuntu 9.10 or openSUSE 11.2 RC2, irrespective of whether I do a network upgrade or a clean install from a liveCD.  I'd appreciate help, since this is a showstopper for me and I suspect for many others.

---

### Post by syntonic on 2009-10-31
thanks for expanding on the Marvell side dougallen. 

From all the posts on here with similar topics I have a feeling this is a pretty widespread problem. Especially for it to not support an intel wireless device (which is essentially centrino since it's a core 2 duo laptop).

I did find one reference on canonical where they encountered this problem during beta ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all)). Tried the kernel on the link at the bottom but the image deb package didn't install (headers installed ok). If anyone else can get it working let me know.

---

### Post by madsmaddad on 2009-10-31
Me too.   Upgraded to 9.10 Kubuntu over the wireless, now I have no connection. I had to reconfigure the wireless connection in knetwork manager. Dmesg gives wlan0: device not ready message. 

Note to others, with 9.04 I ALWAYS had to enter the kwallet password to start wireless link, access other hard disks etc. Got used to this extra level of security. But If I didn't do the wireless password quite quickly, the connection failed.

---

### Post by dougallen on 2009-10-31
Thanks for the rapid response, especially the link you gave in your message, syntonic.  It must be a widespread problem, and the bug report seems to confirm it is a kernel issue.  Because I am on 64-bit, I downloaded the 3 64-bit .deb files from the canonical link at the end of the reference.  I tried installing the headers file (683K) but it wouldn't.  I then installed firstly the all headers file (9.3M), then the headers file (683K), and finally the image file (27.7M).  This all worked fine.  After a reboot, the wired network came up like a charm.  Then I configured the wireless network from the system tray icon, and it too popped into life correctly.  So, the image patch did the trick for me.  Maybe you'd like to try redoing your image update, syntonic, in the order that worked for me.  I hope it solves your problem too.  I see from your previous reference URL that it has been signed off, but didn't make it into the release.  My own view is that that was a terribly bad judgement.  Anyway, I'd be interested to hear how you get on.  Goodness knows what will happen to those people who can't connect to the internet, won't be aware of the patch, maybe aren't technical enough to patch it themselves anyway, and will be locked out of the official release when it arrives.

---

### Post by syntonic on 2009-10-31
Glad to know it worked for you dougallen. I was using the 32bit image and that doesn't seem to work (headers install correctly, but the image doesn't). I'll try installing 64bit version and see how I go.

Cheers,
Paul

---

### Post by bluisana on 2009-11-01
Hey Syntonic or dougallen, 

I also have a Toshiba laptop that I just installed 9.10 on.  I think I have this same problem you all had.  

Can you give me some more details about how to install the image and header files.  I am somewhat of a linux newb.  I downloaded the linux 2.6........ (signed by linus) kernel files that were referenced in your link but they don't have any .deb files in them and I don't know where to go from here.  

Any help would be greatly appreciated.

---

### Post by dougallen on 2009-11-01
Hi there.  Sorry you are experiencing the problem too.  The link you need is [http://people.canonical.com/~apw/lp386468-karmic/](http://people.canonical.com/~apw/lp386468-karmic/)   This will give you a directory page with the files you need.  Click on the linux-headers line which ends in pwl_all.deb and save it to your desktop.  The file is about 9.3M.  Then make sure whether you have the 32-bit or the 64-bit Ubuntu.  Click on the linux-headers line ending amd64.deb or i386.deb and save to the desktop.  The file is about 680K.  Click on the linux-image line ending with the corre3sponding amd64.deb or i386.deb and save to the desktop.  Then install them by selecting your desktop and clicking on the first file first.  When it's installed, click on the second file.  When installed, click on the third image file.  Then reboot, being careful to select the 2.6.31-12 line rather than the original top line on the grub menu.  It should bring up your network fine.  Hope this is clear enough, and works for you.  Doug

---

### Post by bluisana on 2009-11-01
Hey Doug, 

thanks for the response.  I have already reinstalled because I made so many system changes I was afraid I might have screwed something else up.  I ended up finding all of the deb files and succesfully installing them off of a usb key but still no love.  I never saw an option that would allow me to "select the 2.6.31-12 line rather than the original top line on the grub menu".  Is that someone on commandline before I get to the login page? 

Update: 

I ended up changing the timeout setting in grub so that it shows me all of the installed Kernels on boot.  I chose the 2.6.31-12 kernel to boot into but I still have no eth0 or wireless.  

lshw -C network 

says that I have "AR50001 Wireless Network Adapter" and using driver=ath5k

This is pretty interesting to me because ubuntu 9.40 told me that the wireless card in this laptop was an ar242.  Wireless didn't work on 9.04 either but atleast I had ethernet.  Where can I go from here? 

Thanks

---

### Post by stevene on 2009-11-02
I'm seeing exactly the same problems, Toshiba Satellite P300-1C9. Problem seen when upgrading from 9.04 to 9.10, but also exists if I boot into the live 9.10 desktop i386 CD. 

lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

Everything works fine under 9.04, looking at the loaded kernel modules under 9.04 I see I have "sky2" for my wired ethernet, and "mac80211" for wireless. On the live CD I did an rmmod sky2 && modprobe sky2 and got the following in kern.log

```
Nov  2 08:31:46 ubuntu kernel: [  389.005506] sky2 driver version 1.23                                           
Nov  2 08:31:46 ubuntu kernel: [  389.005582] sky2 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17      
Nov  2 08:31:46 ubuntu kernel: [  389.005610] sky2 0000:03:00.0: setting latency timer to 64                     
Nov  2 08:31:46 ubuntu kernel: [  389.005649] sky2 0000:03:00.0: unsupported chip type 0x2e                      
Nov  2 08:31:46 ubuntu kernel: [  389.005670] sky2 0000:03:00.0: PCI INT A disabled                              
Nov  2 08:31:46 ubuntu kernel: [  389.005685] sky2: probe of 0000:03:00.0 failed with error -95    
```Doing the same on the same with mac80211, iwlcore and iwlagn I get
```
Nov  2 08:35:57 ubuntu kernel: [  639.992930] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov  2 08:35:57 ubuntu kernel: [  639.992932] iwlagn: Copyright(c) 2003-2009 Intel Corporation                 
Nov  2 08:35:57 ubuntu kernel: [  639.992980] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
Nov  2 08:35:57 ubuntu kernel: [  639.992991] iwlagn 0000:02:00.0: setting latency timer to 64                 
Nov  2 08:35:57 ubuntu kernel: [  639.993019] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x4AA707A                                                                                                        
Nov  2 08:35:57 ubuntu kernel: [  639.996005] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x941212FF                                                                                                              
Nov  2 08:35:57 ubuntu kernel: [  640.012156] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x941212FF                                                                                                              
<repeats>                                                                                                        
Nov  2 08:36:04 ubuntu kernel: [  647.600042] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x941212FF                                                                                                              
Nov  2 08:36:04 ubuntu kernel: [  647.615186] iwlagn 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x941212FF                                                                                                              
Nov  2 08:36:04 ubuntu kernel: [  647.626344] iwlagn 0000:02:00.0: Time out reading EEPROM[0]                    
Nov  2 08:36:04 ubuntu kernel: [  647.626347] iwlagn 0000:02:00.0: Unable to init EEPROM                         
Nov  2 08:36:04 ubuntu kernel: [  647.626368] iwlagn 0000:02:00.0: PCI INT A disabled
Nov  2 08:36:04 ubuntu kernel: [  647.626875] iwlagn: probe of 0000:02:00.0 failed with error -110

```

---

### Post by dougallen on 2009-11-02
Hi again.  I'm sorry both of you are still having problems.  I'm afraid I've run out of other ideas for you, but maybe others with more knowledge can jump in and help.  There are several other posts on the forum about wireless issues, and it would be worth reviewing them for possible solutions.  I'm not aware of any other solutions for the wired network problem.  For me, tinkering with configuration files was no use since the ethernet interface was not detected at all.  I'm really sorry I can't help further, but wish you luck elsewhere.  Hopefully Canonical will come up with an update to fix the bugs before too long.  Doug

---

### Post by syntonic on 2009-11-02
Stevene. Load the 64bit version of Karmic and try the patched kernel I linked to earlier. It worked for Dougallen.  I'm downloading the 64bit version now to try myself. (32bit image appears corrupt).

---

### Post by bluisana on 2009-11-02
I have the 64 bit version.  Ethernet is still not even recognized and I can't scan or manually setup a connection through wireless.  I am going to give it another day of searching around for a solution then it will be time to move to another linux distro or maybe even windows :(.

---

### Post by syntonic on 2009-11-02
> **bluisana said:**
> I have the 64 bit version.  Ethernet is still not even recognized and I can't scan or manually setup a connection through wireless.  I am going to give it another day of searching around for a solution then it will be time to move to another linux distro or maybe even windows :(.

Or you can just use 9.04 until they fix the issues (using windows is a bit drastic isn't it? :)  )

---

### Post by stevene on 2009-11-02
Unfortunately I'm unable to do that, I need this laptop for work and have backed out the Karmic upgrade (which took several hours to apply over the weekend). I can reboot into the install CDs, but that won't allow me to build a new kernel. I can probably try again this weekend/next week, when I can afford to not have the laptop as I'll have access to another machine.


Thanks

---

### Post by bobcollard on 2009-11-02
I fought it too,  For me it has been two steps forwards one step back.  I tried 9.10, could not connect.  Don't know why, wicd don't work, won't recognize my router.  My solution is on the following page, actually went back to a distro that is like 9.04 using debian and ubuntu with a different flavor.  Check it out if you like.::
[http://forums.linuxmint.com/viewtopic.php?f=109&t=35164](http://forums.linuxmint.com/viewtopic.php?f=109&t=35164)

---

### Post by KayakJim on 2009-11-02
Encountering the same problems with 9.10 fresh on a Toshiba Satellite P505-S8950 with Atheros Ethernet and Intel 5100 wireless.

At startup I have a screen roll of about 9 seconds of "MAC in deep sleep" messages before the Ubuntu splash page appears. Once logged in I have no Ethernet or Wireless.

I did try downloading and compiling the Atheros Linux drivers but encountered a ton of errors. Apparently they will only compile on Linux headers prior to Ubuntu 9.10.

I am going to try 8.10 Intrepid and see if that will work until 9.10 gets things sorted out.

---

### Post by drhjvyas on 2009-11-02
In my desktop also same problem. If u can not connect to internet u can not download any 'patch' for ur system. I have dual boot system with windows.Windows working fine. can someone tell me what file to download on window-machine and how to transfer to ubuntu9.1 partion and install so that internet connection works....???
How can i revert back to ubuntu9.04? by reinstalling from preserved cd of ubuntu9.04? DSL-wired connection was working fine in ubuntu9.04. Why this mess after upgrading?
Kindly reply.

---

### Post by KayakJim on 2009-11-02
> **drhjvyas said:**
> In my desktop also same problem. If u can not connect to internet u can not download any 'patch' for ur system. I have dual boot system with windows.Windows working fine. can someone tell me what file to download on window-machine and how to transfer to ubuntu9.1 partion and install so that internet connection works....???
How can i revert back to ubuntu9.04? by reinstalling from preserved cd of ubuntu9.04? DSL-wired connection was working fine in ubuntu9.04. Why this mess after upgrading?
Kindly reply.

9.10 is using a newer Linux kernel than 9.04 did causing a need for the drivers to be updated for the newer kernel.

---

### Post by xyzt on 2009-11-02
Same problem on an ASUS desktop: no network/internet access, be it cabled or wireless, but for console [FONT="Courier New"]ping[/FONT]. No e-mail, no browser, *no repository access*. Both with a lenghty upgrade, then a fresh install.

That happened to me before with some version (7.10? 8.04?) and was only solved with a new version.

---

### Post by chandru on 2009-11-02
This bug might be relevant.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all)

Short version of the workaround:

Try booting with acpi=off. Networking works but no battery support etc. 
I used to boot with that option, download the kernel mentioned in that thread from people.canonical.com, download startupmanager and set that kernel as the default. Now everything works.

Hope that works.

---

### Post by bluisana on 2009-11-02
Hey Chandru, 

Thanks for try.  I just appended acpi=off noacpi to the end of the [I][B]GRUB_CMDLINE_LINUX_DEFAULT 
[/B][/I]line in my grub config, but I still have no eth or wireless :(.  I am booting off of the 2.6.31.12-generic kernel now. 

Ug, I may have to take the drastic step of 

Any other possible suggestions would be greatly appreciated.

---

### Post by chandru on 2009-11-02
This might help to identify the problem, but may not.

In a console try
dmesg (or dmesg | less) and scan for any relevant lines about your card and error messages.

You can also try
sudo modprobe ath5k 
and look for error messages. There might be something specific that might be useful.

Regards

---

### Post by bluisana on 2009-11-02
sudo modprobe ath5k returned with no errors. 

do you see anything interesting with this output from dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-12-generic (root@chloe) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu1) ) #41lp386468apw1 SMP Thu Oct 8 15:58:00 UTC 2009 (Ubuntu 2.6.31-12.41lp386468apw1-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-12-generic root=UUID=175f2c8e-1914-4f14-a808-fcffcb27f379 ro quiet splash acpi=off noacpi
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037e70000 (usable)
[    0.000000]  BIOS-e820: 0000000037e70000 - 0000000037e84000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037e84000 - 0000000037e86000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037e86000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x37e70 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CDFFF write-protect
[    0.000000]   CE000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037e70000 (usable)
[    0.000000]  modified: 0000000037e70000 - 0000000037e84000 (ACPI data)
[    0.000000]  modified: 0000000037e84000 - 0000000037e86000 (ACPI NVS)
[    0.000000]  modified: 0000000037e86000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037e70000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0037e00000 page 2M
[    0.000000]  0037e00000 - 0037e70000 page 4k
[    0.000000] kernel direct mapping tables up to 37e70000 @ 8000-b000
[    0.000000] RAMDISK: 29793000 - 29f134df
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000037e70000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000037e70000
[    0.000000]   NODE_DATA [0000000000009000 - 000000000000dfff]
[    0.000000]   bootmap [000000000000e000 -  0000000000014fcf] pages 7
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0037e70000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019dbbcc]    TEXT DATA BSS ==> [0001000000 - 00019dbbcc]
[    0.000000]   #3 [0029793000 - 0029f134df]          RAMDISK ==> [0029793000 - 0029f134df]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00019dc000 - 00019dc108]              BRK ==> [00019dc000 - 00019dc108]
[    0.000000]   #6 [0000008000 - 0000009000]          PGTABLE ==> [0000008000 - 0000009000]
[    0.000000] found SMP MP-table at [ffff8800000f7380] f7380
[    0.000000]  [ffffea0000000000-ffffea0000dfffff] PMD -> [ffff880001e00000-ffff880002bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00037e70
[    0.000000] On node 0 totalpages: 228872
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3834 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3075 pages used for memmap
[    0.000000]   DMA32 zone: 221805 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: AMD     
[    0.000000] MPTABLE: Product ID: POOH        
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #2 Version 33 at 0xFEC00000.
[    0.000000] Processors: 2
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages at ffff8800019e7000, static data 89952 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 225639
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-12-generic root=UUID=175f2c8e-1914-4f14-a808-fcffcb27f379 ro quiet splash acpi=off noacpi
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 514a000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 882996k/915904k available (5291k kernel code, 416k absent, 32492k reserved, 3005k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1795.519 MHz processor.
[    0.000013] spurious 8259A interrupt: IRQ7.
[    0.000765] Console: colour VGA+ 80x25
[    0.000768] console [tty0] enabled
[    0.004772] allocated 9175040 bytes of page_cgroup
[    0.004775] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010008] Calibrating delay loop (skipped), value calculated using timer frequency.. 3591.03 BogoMIPS (lpj=17955190)
[    0.010042] Security Framework initialized
[    0.010067] AppArmor: AppArmor initialized
[    0.010183] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010853] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.011172] Mount-cache hash table entries: 256
[    0.011334] Initializing cgroup subsys ns
[    0.011339] Initializing cgroup subsys cpuacct
[    0.011343] Initializing cgroup subsys memory
[    0.011352] Initializing cgroup subsys freezer
[    0.011355] Initializing cgroup subsys net_cls
[    0.011369] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.011372] CPU: L2 Cache: 512K (64 bytes/line)
[    0.011376] CPU 0/0x0 -> Node 0
[    0.011378] tseg: 0037f00000
[    0.011380] CPU: Physical Processor ID: 0
[    0.011382] CPU: Processor Core ID: 0
[    0.011385] using C1E aware idle routine
[    0.011387] Performance Counters: AMD PMU driver.
[    0.011392] ... version:                 0
[    0.011394] ... bit width:               48
[    0.011396] ... generic counters:        4
[    0.011398] ... value mask:              0000ffffffffffff
[    0.011400] ... max period:              00007fffffffffff
[    0.011402] ... fixed-purpose counters:  0
[    0.011404] ... counter mask:            000000000000000f
[    0.013279] Setting APIC routing to flat
[    0.013351] ExtINT not setup in hardware but reported by MP table
[    0.013460]   alloc irq_desc for 16 on node 0
[    0.013463]   alloc kstat_irqs on node 0
[    0.013466]   alloc irq_desc for 17 on node 0
[    0.013468]   alloc kstat_irqs on node 0
[    0.013471]   alloc irq_desc for 18 on node 0
[    0.013473]   alloc kstat_irqs on node 0
[    0.013476]   alloc irq_desc for 19 on node 0
[    0.013478]   alloc kstat_irqs on node 0
[    0.013481]   alloc irq_desc for 20 on node 0
[    0.013482]   alloc kstat_irqs on node 0
[    0.013488]   alloc irq_desc for 21 on node 0
[    0.013489]   alloc kstat_irqs on node 0
[    0.013492]   alloc irq_desc for 22 on node 0
[    0.013494]   alloc kstat_irqs on node 0
[    0.013633] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=0 pin2=2
[    0.020000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.020000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.020000] ..... (found apic 0 pin 2) ...
[    0.113710] ....... works.
[    0.113712] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.230245] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3591.12 BogoMIPS (lpj=17955619)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.390163] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.390177] Brought up 2 CPUs
[    0.390180] Total of 2 processors activated (7182.16 BogoMIPS).
[    0.390233] CPU0 attaching sched-domain:
[    0.390236]  domain 0: span 0-1 level MC
[    0.390239]   groups: 0 1
[    0.390245] CPU1 attaching sched-domain:
[    0.390247]  domain 0: span 0-1 level MC
[    0.390250]   groups: 1 0
[    0.390325] Booting paravirtualized kernel on bare hardware
[    0.390325] regulator: core version 0.5
[    0.390325] Time: 20:57:28  Date: 11/02/09
[    0.390325] NET: Registered protocol family 16
[    0.390325] node 0 link 0: io port [1000, fffff]
[    0.390325] TOM: 0000000040000000 aka 1024M
[    0.390325] node 0 link 0: mmio [f8100000, ffffffff]
[    0.390325] node 0 link 0: mmio [f8000000, f80fffff]
[    0.390325] node 0 link 0: mmio [f8000000, f7ffffff]
[    0.390325] node 0 link 0: mmio [f0000000, f7ffffff]
[    0.390325] node 0 link 0: mmio [a0000, bffff]
[    0.390325] node 0 link 0: mmio [f0000000, efffffff]
[    0.390325] node 0 link 0: mmio [e0000000, efffffff]
[    0.390325] node 0 link 0: mmio [40000000, dfffffff]
[    0.390325] bus: [00,ff] on node 0 link 0
[    0.390325] bus: 00 index 0 io port: [0, ffff]
[    0.390325] bus: 00 index 1 mmio: [40000000, fcffffffff]
[    0.390325] bus: 00 index 2 mmio: [a0000, bffff]
[    0.390363] PCI: Using configuration type 1 for base access
[    0.391324] bio: create slab <bio-0> at 0
[    0.391324] ACPI: Interpreter disabled.
[    0.391324] SCSI subsystem initialized
[    0.391324] libata version 3.00 loaded.
[    0.391324] usbcore: registered new interface driver usbfs
[    0.391324] usbcore: registered new interface driver hub
[    0.391324] usbcore: registered new device driver usb
[    0.391324] PCI: Probing PCI hardware
[    0.391324] PCI: Probing PCI hardware (bus 00)
[    0.391324] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.391324] pci 0000:00:05.0: PME# disabled
[    0.391324] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.391324] pci 0000:00:07.0: PME# disabled
[    0.391324] pci 0000:00:12.0: reg 10 io port: [0x8440-0x8447]
[    0.391324] pci 0000:00:12.0: reg 14 io port: [0x8434-0x8437]
[    0.391324] pci 0000:00:12.0: reg 18 io port: [0x8438-0x843f]
[    0.391324] pci 0000:00:12.0: reg 1c io port: [0x8430-0x8433]
[    0.391324] pci 0000:00:12.0: reg 20 io port: [0x8400-0x840f]
[    0.391324] pci 0000:00:12.0: reg 24 32bit mmio: [0xf8609000-0xf86093ff]
[    0.391324] pci 0000:00:12.0: set SATA to AHCI mode
[    0.391324] pci 0000:00:13.0: reg 10 32bit mmio: [0xf8404000-0xf8404fff]
[    0.391324] pci 0000:00:13.1: reg 10 32bit mmio: [0xf8405000-0xf8405fff]
[    0.391324] pci 0000:00:13.2: reg 10 32bit mmio: [0xf8406000-0xf8406fff]
[    0.391324] pci 0000:00:13.3: reg 10 32bit mmio: [0xf8407000-0xf8407fff]
[    0.391324] pci 0000:00:13.4: reg 10 32bit mmio: [0xf8408000-0xf8408fff]
[    0.391324] pci 0000:00:13.5: reg 10 32bit mmio: [0xf8609400-0xf86094ff]
[    0.391324] pci 0000:00:13.5: supports D1 D2
[    0.391324] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.391324] pci 0000:00:13.5: PME# disabled
[    0.391324] pci 0000:00:14.0: reg 10 io port: [0x8410-0x841f]
[    0.391324] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.391324] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.391324] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.391324] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.391324] pci 0000:00:14.1: reg 20 io port: [0x8420-0x842f]
[    0.391324] pci 0000:00:14.2: reg 10 64bit mmio: [0xf8400000-0xf8403fff]
[    0.391324] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.391324] pci 0000:00:14.2: PME# disabled
[    0.391324] pci 0000:01:05.0: reg 10 64bit mmio: [0xf0000000-0xf7ffffff]
[    0.391324] pci 0000:01:05.0: reg 18 64bit mmio: [0xf8100000-0xf810ffff]
[    0.391324] pci 0000:01:05.0: reg 20 io port: [0x9000-0x90ff]
[    0.391324] pci 0000:01:05.0: reg 24 32bit mmio: [0xf8000000-0xf80fffff]
[    0.391324] pci 0000:01:05.0: supports D1 D2
[    0.391324] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.391324] pci 0000:00:01.0: bridge 32bit mmio: [0xf8000000-0xf81fffff]
[    0.391324] pci 0000:00:01.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.391324] pci 0000:00:05.0: bridge io port: [0x00-0xfff]
[    0.391324] pci 0000:00:05.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.391345] pci 0000:14:00.0: reg 10 64bit mmio: [0xf8200000-0xf820ffff]
[    0.391456] pci 0000:00:07.0: bridge 32bit mmio: [0xf8200000-0xf82fffff]
[    0.391513] pci 0000:1a:04.0: reg 10 32bit mmio: [0xf8300000-0xf8300fff]
[    0.391541] pci 0000:1a:04.0: supports D1 D2
[    0.391543] pci 0000:1a:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.391549] pci 0000:1a:04.0: PME# disabled
[    0.391598] pci 0000:1a:04.1: reg 10 32bit mmio: [0xf8302000-0xf83027ff]
[    0.391609] pci 0000:1a:04.1: reg 14 32bit mmio: [0xf8304000-0xf8307fff]
[    0.391671] pci 0000:1a:04.1: supports D1 D2
[    0.391673] pci 0000:1a:04.1: PME# supported from D0 D1 D2 D3hot
[    0.391679] pci 0000:1a:04.1: PME# disabled
[    0.391729] pci 0000:1a:04.2: reg 10 32bit mmio: [0xf8301000-0xf8301fff]
[    0.391796] pci 0000:1a:04.2: supports D1 D2
[    0.391798] pci 0000:1a:04.2: PME# supported from D0 D1 D2 D3hot
[    0.391804] pci 0000:1a:04.2: PME# disabled
[    0.391852] pci 0000:1a:04.3: reg 10 32bit mmio: [0xf8302800-0xf83028ff]
[    0.391917] pci 0000:1a:04.3: supports D1 D2
[    0.391920] pci 0000:1a:04.3: PME# supported from D0 D1 D2 D3hot
[    0.391926] pci 0000:1a:04.3: PME# disabled
[    0.391989] pci 0000:00:14.4: transparent bridge
[    0.391996] pci 0000:00:14.4: bridge 32bit mmio: [0xf8300000-0xf83fffff]
[    0.392768] pci 0000:00:05.0: BAR 13: can't allocate resource
[    0.392770] pci 0000:00:05.0: BAR 14: can't allocate resource
[    0.420009] Bluetooth: Core ver 2.15
[    0.420034] NET: Registered protocol family 31
[    0.420034] Bluetooth: HCI device and connection manager initialized
[    0.420034] Bluetooth: HCI socket layer initialized
[    0.420034] NetLabel: Initializing
[    0.420034] NetLabel:  domain hash size = 128
[    0.420034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.420043] NetLabel:  unlabeled traffic allowed by default
[    0.422236] pnp: PnP ACPI: disabled
[    0.422431] AppArmor: AppArmor Filesystem Enabled
[    0.422499] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.422503] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.422507] pci 0000:00:01.0:   MEM window: 0xf8000000-0xf81fffff
[    0.422511] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.422516] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    0.422519] pci 0000:00:05.0:   IO window: disabled
[    0.422522] pci 0000:00:05.0:   MEM window: disabled
[    0.422525] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.422529] pci 0000:00:07.0: PCI bridge, secondary bus 0000:14
[    0.422532] pci 0000:00:07.0:   IO window: disabled
[    0.422536] pci 0000:00:07.0:   MEM window: 0xf8200000-0xf82fffff
[    0.422539] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.422545] pci 0000:1a:04.0: CardBus bridge, secondary bus 0000:1b
[    0.422549] pci 0000:1a:04.0:   IO window: 0x001000-0x0010ff
[    0.422555] pci 0000:1a:04.0:   IO window: 0x001400-0x0014ff
[    0.422561] pci 0000:1a:04.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.422567] pci 0000:1a:04.0:   MEM window: 0x54000000-0x57ffffff
[    0.422573] pci 0000:00:14.4: PCI bridge, secondary bus 0000:1a
[    0.422578] pci 0000:00:14.4:   IO window: 0x1000-0x1fff
[    0.422584] pci 0000:00:14.4:   MEM window: 0xf8300000-0xf83fffff
[    0.422590] pci 0000:00:14.4:   PREFETCH window: 0x50000000-0x53ffffff
[    0.422604] pci 0000:00:05.0: setting latency timer to 64
[    0.422610] pci 0000:00:07.0: setting latency timer to 64
[    0.422634] pci 0000:1a:04.0: PCI->APIC IRQ transform: INT A -> IRQ 20
[    0.422643] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.422646] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.422649] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.422652] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xf81fffff]
[    0.422655] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.422659] pci_bus 0000:08: resource 0 mem: [0x0-0xfff]
[    0.422661] pci_bus 0000:08: resource 1 mem: [0x0-0xfffff]
[    0.422665] pci_bus 0000:14: resource 1 mem: [0xf8200000-0xf82fffff]
[    0.422668] pci_bus 0000:1a: resource 0 io:  [0x1000-0x1fff]
[    0.422671] pci_bus 0000:1a: resource 1 mem: [0xf8300000-0xf83fffff]
[    0.422674] pci_bus 0000:1a: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.422677] pci_bus 0000:1a: resource 3 io:  [0x00-0xffff]
[    0.422680] pci_bus 0000:1a: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.422684] pci_bus 0000:1b: resource 0 io:  [0x1000-0x10ff]
[    0.422687] pci_bus 0000:1b: resource 1 io:  [0x1400-0x14ff]
[    0.422690] pci_bus 0000:1b: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.422693] pci_bus 0000:1b: resource 3 mem: [0x54000000-0x57ffffff]
[    0.422737] NET: Registered protocol family 2
[    0.422869] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.423562] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.424687] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.425222] TCP: Hash tables configured (established 131072 bind 65536)
[    0.425226] TCP reno registered
[    0.425337] NET: Registered protocol family 1
[    0.425422] Trying to unpack rootfs image as initramfs...
[    0.644103] Freeing initrd memory: 7681k freed
[    0.648272] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.648385] Scanning for low memory corruption every 60 seconds
[    0.648548] audit: initializing netlink socket (disabled)
[    0.648564] type=2000 audit(1257195448.640:1): initialized
[    0.658871] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.660729] VFS: Disk quotas dquot_6.5.2
[    0.660729] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.660770] fuse init (API version 7.12)
[    0.660770] msgmni has been set to 1739
[    0.660770] alg: No test for stdrng (krng)
[    0.660770] io scheduler noop registered
[    0.660770] io scheduler anticipatory registered
[    0.660770] io scheduler deadline registered
[    0.660770] io scheduler cfq registered (default)
[    0.830034] pci 0000:01:05.0: Boot video device
[    0.830169]   alloc irq_desc for 24 on node 0
[    0.830169]   alloc kstat_irqs on node 0
[    0.830169] pcieport-driver 0000:00:05.0: irq 24 for MSI/MSI-X
[    0.830169] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    0.830169]   alloc irq_desc for 25 on node 0
[    0.830169]   alloc kstat_irqs on node 0
[    0.830169] pcieport-driver 0000:00:07.0: irq 25 for MSI/MSI-X
[    0.830169] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    0.830169] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.830169] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.831501] Linux agpgart interface v0.103
[    0.831508] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.832711] brd: module loaded
[    0.833217] loop: module loaded
[    0.833308] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.833465] ahci 0000:00:12.0: version 3.0
[    0.833486] ahci 0000:00:12.0: PCI->APIC IRQ transform: INT A -> IRQ 22
[    0.833610] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.833614] ahci 0000:00:12.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    0.834050] scsi0 : ahci
[    0.834050] scsi1 : ahci
[    0.834050] scsi2 : ahci
[    0.834050] scsi3 : ahci
[    0.834050] ata1: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609100 irq 22
[    0.834050] ata2: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609180 irq 22
[    0.834050] ata3: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609200 irq 22
[    0.834050] ata4: SATA max UDMA/133 abar m1024@0xf8609000 port 0xf8609280 irq 22
[    0.834050] pata_atiixp 0000:00:14.1: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.834050] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    0.834050] scsi4 : pata_atiixp
[    0.834050] scsi5 : pata_atiixp
[    0.834050] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    0.834050] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    0.834050] Fixed MDIO Bus: probed
[    0.834050] PPP generic driver version 2.4.2
[    0.834050] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.834050] ehci_hcd 0000:00:13.5: PCI->APIC IRQ transform: INT D -> IRQ 19
[    0.834050] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.834050] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.834050] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.834050] ehci_hcd 0000:00:13.5: debug port 1
[    0.834050] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf8609400
[    0.850009] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.850085] usb usb1: configuration #1 chosen from 1 choice
[    0.850121] hub 1-0:1.0: USB hub found
[    0.850130] hub 1-0:1.0: 10 ports detected
[    0.850239] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.850272] ohci_hcd 0000:00:13.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.850272] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.850272] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.850272] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf8404000
[    0.910079] usb usb2: configuration #1 chosen from 1 choice
[    0.910111] hub 2-0:1.0: USB hub found
[    0.910125] hub 2-0:1.0: 2 ports detected
[    0.910193] ohci_hcd 0000:00:13.1: PCI->APIC IRQ transform: INT B -> IRQ 17
[    0.910193] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.910193] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.910193] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf8405000
[    0.970079] usb usb3: configuration #1 chosen from 1 choice
[    0.970110] hub 3-0:1.0: USB hub found
[    0.970124] hub 3-0:1.0: 2 ports detected
[    0.970189] ohci_hcd 0000:00:13.2: PCI->APIC IRQ transform: INT C -> IRQ 18
[    0.970189] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.970189] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.970189] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf8406000
[    1.010499] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WT03, max UDMA/33
[    1.030086] usb usb4: configuration #1 chosen from 1 choice
[    1.030115] hub 4-0:1.0: USB hub found
[    1.030128] hub 4-0:1.0: 2 ports detected
[    1.030384] ohci_hcd 0000:00:13.3: PCI->APIC IRQ transform: INT B -> IRQ 17
[    1.030397] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    1.030437] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    1.030457] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf8407000
[    1.050448] ata5.00: configured for UDMA/33
[    1.090084] usb usb5: configuration #1 chosen from 1 choice
[    1.090112] hub 5-0:1.0: USB hub found
[    1.090126] hub 5-0:1.0: 2 ports detected
[    1.090195] ohci_hcd 0000:00:13.4: PCI->APIC IRQ transform: INT C -> IRQ 18
[    1.090195] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    1.090195] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    1.090195] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf8408000
[    1.150083] usb usb6: configuration #1 chosen from 1 choice
[    1.150112] hub 6-0:1.0: USB hub found
[    1.150125] hub 6-0:1.0: 2 ports detected
[    1.150213] uhci_hcd: USB Universal Host Controller Interface driver
[    1.150341] PNP: No PS/2 controller found. Probing ports directly.
[    1.180004] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.180017] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.180050] ata2: SATA link down (SStatus 0 SControl 300)
[    1.180099] ata4: SATA link down (SStatus 0 SControl 300)
[    1.180125] ata3: SATA link down (SStatus 0 SControl 300)
[    1.180135] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.180237] mice: PS/2 mouse device common for all mice
[    1.180331] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    1.180357] rtc0: alarms up to one day, 114 bytes nvram
[    1.180498] device-mapper: uevent: version 1.0.3
[    1.182722] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.182722] device-mapper: multipath: version 1.1.0 loaded
[    1.182722] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.182722] cpuidle: using governor ladder
[    1.182722] cpuidle: using governor menu
[    1.182722] TCP cubic registered
[    1.182722] NET: Registered protocol family 10
[    1.182722] lo: Disabled Privacy Extensions
[    1.182722] NET: Registered protocol family 17
[    1.182722] Bluetooth: L2CAP ver 2.13
[    1.182722] Bluetooth: L2CAP socket layer initialized
[    1.182722] Bluetooth: SCO (Voice Link) ver 0.6
[    1.182722] Bluetooth: SCO socket layer initialized
[    1.182722] Bluetooth: RFCOMM TTY layer initialized
[    1.182722] Bluetooth: RFCOMM socket layer initialized
[    1.182722] Bluetooth: RFCOMM ver 1.11
[    1.182722] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[    1.182722] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.182722] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.182722] PM: Resume from disk failed.
[    1.182722] registered taskstats version 1
[    1.182722]   Magic number: 1:744:1002
[    1.182722] rtc_cmos rtc_cmos: setting system clock to 2009-11-02 20:57:30 UTC (1257195450)
[    1.182722] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.182722] EDD information not available.
[    1.200586] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.330442] usb 1-1: configuration #1 chosen from 1 choice
[    1.360006] ata1: softreset failed (device not ready)
[    1.360045] ata1: applying SB600 PMP SRST workaround and retrying
[    1.450011] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.540022] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.540032] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[    1.540032] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.540038] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.540044] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.540044] ata1.00: configured for UDMA/133
[    1.560114] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[    1.560243] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.560330] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.560338] sd 0:0:0:0: [sda] Write Protect is off
[    1.560341] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.560367] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.560509]  sda:
[    1.560807] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WT03 PQ: 0 ANSI: 5
[    1.570794] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.570794] Uniform CD-ROM driver Revision: 3.20
[    1.570794] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.570794] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.580029]  sda1 sda2 < sda5 >
[    1.600260] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.611116] usb 1-8: configuration #1 chosen from 1 choice
[    1.730091] Freeing unused kernel memory: 660k freed
[    1.730425] Write protecting the kernel read-only data: 7556k
[    1.932530] [drm] Initialized drm 1.1.0 20060810
[    1.959982] [drm] radeon default to kernel modesetting DISABLED.
[    1.960577] pci 0000:01:05.0: can't find IRQ for PCI INT B; probably buggy MP table
[    1.960729] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    1.965568] Initializing USB Mass Storage driver...
[    1.966050] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.966173] usbcore: registered new interface driver usb-storage
[    1.966177] USB Mass Storage support registered.
[    1.969580] usb-storage: device found at 2
[    1.969585] usb-storage: waiting for device to settle before scanning
[    1.981564] ohci1394 0000:1a:04.1: PCI->APIC IRQ transform: INT B -> IRQ 21
[    2.040127] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8302000-f83027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.910775] PM: Starting manual resume from disk
[    2.910781] PM: Resume from partition 8:5
[    2.910783] PM: Checking hibernation image.
[    2.910841] PM: Resume from disk failed.
[    2.938171] EXT4-fs (sda1): barriers enabled
[    2.957812] kjournald2 starting: pid 389, dev sda1:8, commit interval 5 seconds
[    2.957812] EXT4-fs (sda1): delayed allocation enabled
[    2.957812] EXT4-fs: file extents enabled
[    2.997459] EXT4-fs: mballoc enabled
[    2.997478] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.360184] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f76c0411b2d]
[    3.593201] type=1505 audit(1257195452.910:2): operation="profile_load" pid=412 name=/usr/share/gdm/guest-session/Xsession
[    3.594785] type=1505 audit(1257195452.910:3): operation="profile_load" pid=413 name=/sbin/dhclient3
[    3.594785] type=1505 audit(1257195452.910:4): operation="profile_load" pid=413 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.594785] type=1505 audit(1257195452.910:5): operation="profile_load" pid=413 name=/usr/lib/connman/scripts/dhclient-script
[    3.641513] type=1505 audit(1257195452.960:6): operation="profile_load" pid=414 name=/usr/bin/evince
[    3.646740] type=1505 audit(1257195452.960:7): operation="profile_load" pid=414 name=/usr/bin/evince-previewer
[    3.649880] type=1505 audit(1257195452.970:8): operation="profile_load" pid=414 name=/usr/bin/evince-thumbnailer
[    3.675911] type=1505 audit(1257195452.990:9): operation="profile_load" pid=416 name=/usr/lib/cups/backend/cups-pdf
[    3.675911] type=1505 audit(1257195452.990:10): operation="profile_load" pid=416 name=/usr/sbin/cupsd
[    4.770841] Adding 2610520k swap on /dev/sda5.  Priority:-1 extents:1 across:2610520k 
[    5.209285] EXT4-fs (sda1): internal journal on sda1:8
[    5.327017] udev: starting version 147
[    6.727462] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    6.921299] lp: driver loaded but no devices found
[    6.960043] usb-storage: device scan complete
[    6.960629] scsi 6:0:0:0: Direct-Access     C-ONE    001GB Tiny       1.00 PQ: 0 ANSI: 2
[    6.960983] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.962556] sd 6:0:0:0: [sdb] 2031616 512-byte logical blocks: (1.04 GB/992 MiB)
[    6.962556] sd 6:0:0:0: [sdb] Write Protect is off
[    6.962556] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    6.962556] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.962556] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.962556]  sdb: sdb1
[    6.970858] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.970858] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.024956] EDAC MC: Ver: 2.1.0 Oct  8 2009
[    7.032550] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[    7.516191] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.682053] EDAC amd64_edac:  Ver: 3.2.0 Oct  8 2009
[    7.689502] EDAC amd64: This node reports that Memory ECC is currently disabled.
[    7.689502] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[    7.689502] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[    7.689502]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[    7.689502]     Might be a BIOS bug, if BIOS says ECC is enabled
[    7.689502]     Use of the override can cause unknown side effects.
[    7.689502] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    7.711723] sdhci: Secure Digital Host Controller Interface driver
[    7.711727] sdhci: Copyright(c) Pierre Ossman
[    7.912224] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.953722] Linux video capture interface: v2.00
[    7.956422] tifm_7xx1 0000:1a:04.2: PCI->APIC IRQ transform: INT C -> IRQ 20
[    7.990126] cfg80211: Calling CRDA to update world regulatory domain
[    8.024164] sdhci-pci 0000:1a:04.3: SDHCI controller found [104c:803c] (rev 0)
[    8.024186] sdhci-pci 0000:1a:04.3: PCI->APIC IRQ transform: INT C -> IRQ 20
[    8.024301] Registered led device: mmc0::
[    8.024367] mmc0: SDHCI controller on PCI [0000:1a:04.3] using DMA
[    8.092141] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[    8.093156] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:13.5/usb1/1-8/1-8:1.0/input/input2
[    8.093156] usbcore: registered new interface driver uvcvideo
[    8.093156] USB Video Class driver (v0.1.0)
[    8.140603] yenta_cardbus 0000:1a:04.0: CardBus bridge found [1179:ff00]
[    8.140629] yenta_cardbus 0000:1a:04.0: Enabling burst memory read transactions
[    8.140637] yenta_cardbus 0000:1a:04.0: Using CSCINT to route CSC interrupts to PCI
[    8.140640] yenta_cardbus 0000:1a:04.0: Routing CardBus interrupts to PCI
[    8.140647] yenta_cardbus 0000:1a:04.0: TI: mfunc 0x10a01b22, devctl 0x64
[    8.390917] yenta_cardbus 0000:1a:04.0: ISA IRQ mask 0x00d0, PCI irq 20
[    8.390923] yenta_cardbus 0000:1a:04.0: Socket status: 30000006
[    8.390928] pci_bus 0000:1a: Raising subordinate bus# of parent bus (#1a) from #1b to #1e
[    8.390938] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
[    8.390942] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge Memory window: 0xf8300000 - 0xf83fffff
[    8.390946] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[    8.615442] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input3
[    8.640790] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input4
[    8.829709] __ratelimit: 3 callbacks suppressed
[    8.829714] type=1505 audit(1257195458.140:12): operation="profile_replace" pid=756 name=/usr/share/gdm/guest-session/Xsession
[    8.831694] type=1505 audit(1257195458.150:13): operation="profile_replace" pid=757 name=/sbin/dhclient3
[    8.832029] type=1505 audit(1257195458.150:14): operation="profile_replace" pid=757 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.832217] type=1505 audit(1257195458.150:15): operation="profile_replace" pid=757 name=/usr/lib/connman/scripts/dhclient-script
[    8.834266] type=1505 audit(1257195458.150:16): operation="profile_replace" pid=758 name=/usr/bin/evince
[    8.842482] type=1505 audit(1257195458.160:17): operation="profile_replace" pid=758 name=/usr/bin/evince-previewer
[    8.845684] type=1505 audit(1257195458.160:18): operation="profile_replace" pid=758 name=/usr/bin/evince-thumbnailer
[    8.865761] type=1505 audit(1257195458.180:19): operation="profile_replace" pid=760 name=/usr/lib/cups/backend/cups-pdf
[    8.866189] type=1505 audit(1257195458.180:20): operation="profile_replace" pid=760 name=/usr/sbin/cupsd
[    8.868659] type=1505 audit(1257195458.180:21): operation="profile_replace" pid=761 name=/usr/sbin/tcpdump
[    9.456176] ath5k 0000:14:00.0: PCI->APIC IRQ transform: INT A -> IRQ 19
[    9.456187] ath5k 0000:14:00.0: setting latency timer to 64
[    9.456231] ath5k 0000:14:00.0: registered as 'phy0'
[    9.546389] ath: EEPROM regdomain: 0x64
[    9.546392] ath: EEPROM indicates we should expect a direct regpair map
[    9.546396] ath: Country alpha2 being used: 00
[    9.546398] ath: Regpair used: 0x64
[    9.904587] phy0: Selected rate control algorithm 'minstrel'
[    9.904587] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   10.130784] cfg80211: World regulatory domain updated:
[   10.130790]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.130794]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.130797]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.130800]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.130803]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.130806]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.544414] HDA Intel 0000:00:14.2: PCI->APIC IRQ transform: INT A -> IRQ 16
[   12.216055] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   12.216174] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[   13.994218] ppdev: user-space parallel port driver
[   19.760282] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.095590] [drm] Setting GART location based on new memory map
[   30.095590] [drm] Loading RS690/RS740 Microcode
[   30.095590] [drm] Num pipes: 1
[   30.095590] [drm] writeback test succeeded in 1 usecs
[   30.900235] irq 18: nobody cared (try booting with the "irqpoll" option)
[   30.900243] Pid: 0, comm: swapper Not tainted 2.6.31-12-generic #41lp386468apw1
[   30.900246] Call Trace:
[   30.900248]  <IRQ>  [<ffffffff810b0336>] __report_bad_irq+0x26/0xa0
[   30.900264]  [<ffffffff810b053c>] note_interrupt+0x18c/0x1d0
[   30.900268]  [<ffffffff810b0bb5>] handle_fasteoi_irq+0xd5/0x100
[   30.900273]  [<ffffffff8101499d>] handle_irq+0x1d/0x30
[   30.900276]  [<ffffffff81014077>] do_IRQ+0x67/0xe0
[   30.900281]  [<ffffffff810129d3>] ret_from_intr+0x0/0x11
[   30.900283]  <EOI>  [<ffffffff810316f6>] ? native_safe_halt+0x6/0x10
[   30.900293]  [<ffffffff81019ffc>] ? default_idle+0x4c/0xe0
[   30.900297]  [<ffffffff8101a0ee>] ? c1e_idle+0x5e/0x120
[   30.900301]  [<ffffffff81010e12>] ? cpu_idle+0xb2/0x100
[   30.900307]  [<ffffffff8151df33>] ? start_secondary+0xa9/0xab
[   30.900309] handlers:
[   30.900311] [<ffffffff81397610>] (usb_hcd_irq+0x0/0x80)
[   30.900316] [<ffffffff81397610>] (usb_hcd_irq+0x0/0x80)
[   30.900320] Disabling IRQ #18

---

### Post by zkneebone on 2009-11-03
When screen says "Loading Grub 1.5" hit ESC key and select it from the list.  I'm going to try it from my USB Drive and let you know. I have a Toshiba Satellite M305 with the same issues.

---

### Post by zkneebone on 2009-11-03
> **zkneebone said:**
> When screen says "Loading Grub 1.5" hit ESC key and select it from the list.  I'm going to try it from my USB Drive and let you know. I have a Toshiba Satellite M305 with the same issues.

Wifi is up and running now under the 9.10.31-12 kernel i386 version.

---

### Post by zkneebone on 2009-11-03
> **zkneebone said:**
> Wifi is up and running now under the 9.10.31-12 kernel i386 version.
ifconfig shows eth0 is up and running, too.

---

### Post by kaito_kid on 2009-11-04
> **KayakJim said:**
> Encountering the same problems with 9.10 fresh on a Toshiba Satellite P505-S8950 with Atheros Ethernet and Intel 5100 wireless.

At startup I have a screen roll of about 9 seconds of "MAC in deep sleep" messages before the Ubuntu splash page appears. Once logged in I have no Ethernet or Wireless.

exactly the same problem (but with satellite p300-220) with the same wireless card (intel 5100). :D
someone has an idea on how to resolve this problem? ^^

thx ;P

---

### Post by stevene on 2009-11-04
Sorry for what is probably a stupid question, but what kernel version do you mean? Karmic ships with 2.6.31.14 and an apt-get update/upgrade doesn't indicate a new kernel version available.

---

### Post by KayakJim on 2009-11-04
> **kaito_kid said:**
> exactly the same problem (but with satellite p300-220) with the same wireless card (intel 5100). :D
someone has an idea on how to resolve this problem? ^^

thx ;P

So far the only 2 options that I have seen suggested is to either use 9.04 instead of 9.10 or install a previous kernel. Please note that I may have missed other suggestions but those are the two that have been verified to work.

---

### Post by bobcollard on 2009-11-04
For those of you using Dells, There is a solution.  See this link and my signature.

[http://en.community.dell.com/wikis/linux/ubuntu-9-10-dell-factory-recovery-iso.aspx](http://en.community.dell.com/wikis/linux/ubuntu-9-10-dell-factory-recovery-iso.aspx)

---

### Post by bluisana on 2009-11-04
Running on the previous Kernel didn't work for me.

---

### Post by zkneebone on 2009-11-04
> **stevene said:**
> Sorry for what is probably a stupid question, but what kernel version do you mean? Karmic ships with 2.6.31.14 and an apt-get update/upgrade doesn't indicate a new kernel version available.

To fix the problem I did what dougallen mentioned in his post on page one.
I downloaded the following three files to a USB drive from a different computer.
1) [http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12_2.6.31-12.41lp386468apw1_all.deb](http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12_2.6.31-12.41lp386468apw1_all.deb) (9.3M)
2) [http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb](http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb) (669K)
3) [http://people.canonical.com/~apw/lp386468-karmic/linux-image-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb](http://people.canonical.com/~apw/lp386468-karmic/linux-image-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb) (28M)
And then I connected that USB drive to my Toshiba Satellite with karmic running.
I installed the three .deb files one at a time (by double-clicking) in the order 1-2-3. Then I restarted Ubuntu.
Right after the Toshiba screen, the "Loading Grub 1.5" Screen popped up. I hit ESC and selected ubuntu-2.6.31-12-generic from the list of kernels. I logged in and my Wifi and Ethernet were detected and working.
Then, so I don't have to hit ESC every time I boot performed the following edit:
In a konsole I typed 
gksudo gedit /boot/grub/menu.lst
and entered my root password. I found the line containing the 2.6.31-12 kernel and moved it to the very first line. Now it is the default kernel. My network cards work every time now.

---

### Post by zkneebone on 2009-11-04
For those of you with an Atheros Wifi card there is something else to try on this thread.
[http://ubuntuforums.org/showthread.php?t=1305812](http://ubuntuforums.org/showthread.php?t=1305812)

---

### Post by kaito_kid on 2009-11-04
> **zkneebone said:**
> To fix the problem I did what dougallen mentioned in his post on page one.
I downloaded the following three files to a USB drive from a different computer.
1) [http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12_2.6.31-12.41lp386468apw1_all.deb](http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12_2.6.31-12.41lp386468apw1_all.deb) (9.3M)
2) [http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb](http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb) (669K)
3) [http://people.canonical.com/~apw/lp386468-karmic/linux-image-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb](http://people.canonical.com/~apw/lp386468-karmic/linux-image-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb) (28M)
And then I connected that USB drive to my Toshiba Satellite with karmic running.
I installed the three .deb files one at a time (by double-clicking) in the order 1-2-3. Then I restarted Ubuntu.
Right after the Toshiba screen, the "Loading Grub 1.5" Screen popped up. I hit ESC and selected ubuntu-2.6.31-12-generic from the list of kernels. I logged in and my Wifi and Ethernet were detected and working.
now it's working with my toshiba ^^
thx ;)
:KS

---

### Post by microcell on 2009-11-04
> **zkneebone said:**
> To fix the problem I did what dougallen mentioned in his post on page one.
I downloaded the following three files to a USB drive from a different computer.
1) [http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12_2.6.31-12.41lp386468apw1_all.deb]("http://people.canonical.com/%7Eapw/lp386468-karmic/linux-headers-2.6.31-12_2.6.31-12.41lp386468apw1_all.deb") (9.3M)
2) [http://people.canonical.com/~apw/lp386468-karmic/linux-headers-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb]("http://people.canonical.com/%7Eapw/lp386468-karmic/linux-headers-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb") (669K)
3) [http://people.canonical.com/~apw/lp386468-karmic/linux-image-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb]("http://people.canonical.com/%7Eapw/lp386468-karmic/linux-image-2.6.31-12-generic_2.6.31-12.41lp386468apw1_i386.deb") (28M)
And then I connected that USB drive to my Toshiba Satellite with karmic running.
I installed the three .deb files one at a time (by double-clicking) in the order 1-2-3. Then I restarted Ubuntu.
Right after the Toshiba screen, the "Loading Grub 1.5" Screen popped up. I hit ESC and selected ubuntu-2.6.31-12-generic from the list of kernels. I logged in and my Wifi and Ethernet were detected and working.
Then, so I don't have to hit ESC every time I boot performed the following edit:
In a konsole I typed 
gksudo gedit /boot/grub/menu.lst
and entered my root password. I found the line containing the 2.6.31-12 kernel and moved it to the very first line. Now it is the default kernel. My network cards work every time now.

works for me on Toshiba satellite P305 too. Thank you, mate :-)

---

### Post by linux00T on 2009-11-05
I had the same problem with the wired connection after upgrading from 9.04 to 9.10.
BUT, it was solved when I use wicd.

Hope it helps.

---

### Post by madsmaddad on 2009-11-06
Ok, I have tried Dougallens suggestion from post #9, installed those three debs, and rebooted, selecting the .12 version, Didin't work, so I deleted my wireless configuration, rebooted and rebuilt wireless connection, It still doesn't work. I am using 3Com USB wireless stick with ZD1211 chip. 

Dmesg gives: 

   22.748045] intel8x0: clocking to 48000
   23.627566] usb 1-1: firmware: requesting zd1211/zd1211_ub
   23.775704] usb 1-1: firmware version 0x4330 and device bootcode version 0x4721 differ 
   23.775713] usb 1-1: firmware: requesting zd1211/zd1211_ur 
   23.933507] usb 1-1: firmware: requesting zd1211/zd1211_uphr 
   24.013729] zd1211rw 1-1:1.0: firmware version 4605
   24.053717] zd1211rw 1-1:1.0: zd1211 chip 6891:a727 v4721 high 00-14-7c RF2959_RF pa0 g----   
   24.056857] cfg80211: Calling CRDA for country: US  
   24.060566] cfg80211: Regulatory domain changed to country: US   
   24.060573]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
   24.060579]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)   
   24.060584]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)   
   24.060589]  (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
   24.060594]  (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
   24.060599]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
   24.088124] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
   28.285947] agpgart-sis 0000:00:00.0: AGP 3.5 bridge 
   28.285971] agpgart-sis 0000:00:00.0: bridge is in legacy mode, falling back to 2.x  
   28.285980] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x mode 
   28.286036] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode 
   35.640808] CPU0 attaching NULL sched-domain. 
   35.640821] CPU1 attaching NULL sched-domain.  

Slight concern over setting in US but I think channel 11 is same in UK. 

I will try the ACPI = off suggestion, but otherwise any other suggestions?

---

### Post by Pheros on 2009-11-10
I'm having the same wireless problem on my HP Pavilion, Intel 5100AGN card.  I tried dougallen's suggestion but to no avail.  I looked into the Linux Wireless website but it says it doesn't have drivers for the recent kernels as they are all intree.  

Any help would be appreciated.

---

### Post by Pheros on 2009-11-10
I found a work-around that was effective for my system.

Go to:
[http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

And download

[compat-wireless-2.6.32-rc6.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.32/compat-wireless-2.6.32-rc6.tar.bz2")

follow the instructions on the webpage about building, installing, and unloading, then reboot, and wifi should work!

Joe

---

### Post by KayakJim on 2009-11-10
I installed 9.04 Jaunty and my wireless is working perfectly. 

I will stay with that until the wireless drivers are able to be compiled for 9.10's newer kernel and then upgrade.

---

### Post by Pheros on 2009-11-10
Maybe not...wireless worked at Work, where the network is not encrypted (secured by other means, of course), but back at home still having the same problem as before.  It seems like it might have something to do with the Network Connections controller/applet program...possibly that it doesn't handle the security procedures correctly?

Anyway, back into the fray...

---

### Post by Pheros on 2009-11-11
Playing around a bit more, I found that when my wireless router was on WPA2 Personal security Karmic wouldn't connect.  However, if you alter your router to WPA Personal instead, it connects fine.

This seems to be an adequate work around if you have control over the local wireless router...

otherwise...

---

### Post by Tintinlinux on 2009-12-07
I have a Toshiba P300 and I got the same problem as you concerning WIFI and Lan network.
I have modified the grub.cfg file and added: "pci=use_crs"
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash pci=use_crs
After reboot WIFI and Lan are OK.
I hope this will help you

---

### Post by syntonic on 2009-12-10
> **Tintinlinux said:**
> I have a Toshiba P300 and I got the same problem as you concerning WIFI and Lan network.
I have modified the grub.cfg file and added: "pci=use_crs"
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash pci=use_crs
After reboot WIFI and Lan are OK.
I hope this will help you

Hi Tintinlinux,

That is by far the easiest and best solution to this problem so far. Works perfectly for me and no need to use non-standard kernels (but you do have to remember to edit grub.cfg whenever an apt update adds a new kernel.

Suggest all others with this prob use this method.

Cheers,
Paul

---

### Post by syntonic on 2009-12-13
Further to this, my business partner has the exact same laptop as me. He just installed from the same CD and his networking and wireless work perfectly out of the box... Go figure!!

---

### Post by eldarskiy on 2009-12-29
> **Tintinlinux said:**
> I have a Toshiba P300 and I got the same problem as you concerning WIFI and Lan network.
I have modified the grub.cfg file and added: "pci=use_crs"
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash pci=use_crs
After reboot WIFI and Lan are OK.
I hope this will help you

Super,thanx for you!

---

### Post by hoffboy on 2010-01-01
> **syntonic said:**
> Hi Tintinlinux,

That is by far the easiest and best solution to this problem so far. Works perfectly for me and no need to use non-standard kernels (but you do have to remember to edit grub.cfg whenever an apt update adds a new kernel.

Suggest all others with this prob use this method.

Cheers,
Paul

I don't have permissions to edit grub.cfg. Total newb here. Anyone able to help. Tried to add myself to root group but apparently that didn't work. Zero networks available...both wired and wireless are not working at all. Sigh...shouldn't have upgraded.

-Matt

---

### Post by simonthesorcerer on 2010-01-10
> **Tintinlinux said:**
> I have a Toshiba P300 and I got the same problem as you concerning WIFI and Lan network.
I have modified the grub.cfg file and added: "pci=use_crs"
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash pci=use_crs
After reboot WIFI and Lan are OK.
I hope this will help you

Thank you so much Tintinlinux your solution worked for me just fine with my Toshiba Sat Pro U400 and intel wifi link 5100

---

### Post by cantInstallUbu on 2010-02-03
> **hoffboy said:**
> I don't have permissions to edit grub.cfg. Total newb here. Anyone able to help. Tried to add myself to root group but apparently that didn't work. Zero networks available...both wired and wireless are not working at all. Sigh...shouldn't have upgraded.

-Matt

Just do ```
chmod 0644 grub.cfg
``` then edit the file, and then chmod it back to 0444 when you're done editing.

---

### Post by kaito_kid on 2010-03-04
> **Tintinlinux said:**
> I have a Toshiba P300 and I got the same problem as you concerning WIFI and Lan network.
I have modified the grub.cfg file and added: "pci=use_crs"
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash pci=use_crs
After reboot WIFI and Lan are OK.
I hope this will help you

thx ^_^
but to avoid edit grub.cfg every time, just edit "/etc/grub.d/10_linux"
and add "pci=use_crs" to "linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2"
=> it will be : "linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2 pci=use_crs"
:KS

(don't forget, after editing "10_linux" to run "sudo update-grub" =)

---

