---
title: "ipw2200 problems in Lucid"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by allendevans on 2012-03-12
Hey!
 
I'm having the same problems with Lucid 10.04 on my Aspire 1690, with  ipw2200.  I've tried the suggestions on this page without success.  I  believe the problem is the ipw2200 module, and the highlighted lines  below.  So far, I've not been able to rfkill from on to off.

Please assist if you have the time ...

Items to think about ...

```
XXX@XXX:~$ dmesg | tail -40
[   14.826762] ipw2200 0000:06:03.0: firmware: requesting ipw2200-bss.fw
[   14.961129] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.961138] i915 0000:00:02.0: setting latency timer to 64
[   14.984584] [drm] set up 7M of stolen space
[   15.176676] type=1505 audit(1331481720.855:5):  operation="profile_load" pid=677 name="/usr/share/gdm/guest-session/Xsession"
[   15.183541] type=1505 audit(1331481720.859:6):  operation="profile_replace" pid=679 name="/sbin/dhclient3"
[   15.199711] type=1505 audit(1331481720.875:7):  operation="profile_replace" pid=679 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.200197] type=1505 audit(1331481720.879:8):  operation="profile_replace" pid=679 name="/usr/lib/connman/scripts/dhclient-script"
[   15.208176] type=1505 audit(1331481720.887:9):  operation="profile_load" pid=683 name="/usr/bin/evince"
[   15.248174] type=1505 audit(1331481720.927:10):  operation="profile_load" pid=683 name="/usr/bin/evince-previewer"
[   15.318110] ipw2200: Radio Frequency Kill Switch is On:
[   15.318112] Kill switch must be turned off for wireless networking to work.
[   15.328082] type=1505 audit(1331481721.007:11):  operation="profile_load" pid=683 name="/usr/bin/evince-thumbnailer"
[   15.393582] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   15.412754] [drm] initialized overlay support
[   15.664153] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.665860] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.684124] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.684730] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.685519] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.688375] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   15.700498] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   15.763619] tg3 0000:06:08.0: firmware: requesting tigon/tg3_tso5.bin
[   16.121860] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.496378] fb0: inteldrmfb frame buffer device
[   16.496383] registered panic notifier
[   16.496394] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.496453] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.496479] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   16.502744] vga16fb: initializing
[   16.502749] vga16fb: mapped to 0xc00a0000
[   16.502754] vga16fb: not registering due to another framebuffer present
[   16.630251] Console: switching to colour frame buffer device 160x50
[   16.820035] intel8x0_measure_ac97_clock: measured 54214 usecs (2612 samples)
[   16.820041] intel8x0: clocking to 48000
[   17.638802] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   17.638807] tg3: eth0: Flow control is on for TX and on for RX.
[   17.639047] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.844969] ttyS1: LSR safety check engaged!
[   27.852020] eth0: no IPv6 routers present 
 
```
```
XXX@XXX:~$ sudo lshw -C Network
[sudo] password for XXX: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:84:8a:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:17 memory:b0118000-b0118fff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:a9:0f:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5788-v3.01 ip=192.168.1.103 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:b0100000-b010ffff 
 
```
```
XXX@XXX:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
06:01.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:01.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
06:08.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03) 
 
```
```
XXX@XXX:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results 
 
```
```
XXX@XXX:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ] 
 
```
```
XXX@XXX:~$ uname -mr
2.6.32-21-generic i686 
     Code:
     XXX@XXX:~$ lsb_release -d
Description:    Ubuntu 10.04 LTS 
 
```
```
XXX@XXX:~$ lsmod | grep ipw2200
ipw2200               135216  0 
libipw                 39896  1 ipw2200
lib80211                5046  2 ipw2200,libipw 
 
```
```
XXX@XXX:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback 
 
```
```
XXX@XXX:~$ dmesg | tail
[   16.820035] intel8x0_measure_ac97_clock: measured 54214 usecs (2612 samples)
[   16.820041] intel8x0: clocking to 48000
[   17.638802] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   17.638807] tg3: eth0: Flow control is on for TX and on for RX.
[   17.639047] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.844969] ttyS1: LSR safety check engaged!
[   27.852020] eth0: no IPv6 routers present
[ 1195.850797] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1195.850801] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1195.850805] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details. 
 
```
```
XXX@XXX:~$ cat /etc/rc.local
# added following four lines 11 Mar 2012 - ade
# per [http://ubuntuforums.org/showthread.php?t=1154721](http://ubuntuforums.org/showthread.php?t=1154721)
ifdown eth1
rmmod ipw2200
modprobe ipw2200
ifup eth1

# following line is rc.local's default line - ade 
exit 0 

```Ok.  That replicates pretty much everything from the thread  above.  I'll be sitting by my keyboard waiting for the responses to flow  in.  :smile:  


Thanks ... Allen.

---

### Post by allendevans on 2012-03-12
Sorry, the bolding didn't stick.  The following two lines should have been bolded.

[   15.318112] Kill switch must be turned off for wireless networking to work.
[   15.328082] type=1505 audit(1331481721.007:11):  operation="profile_load" pid=683 name="/usr/bin/evince-thumbnailer"


Thanks ... Allen

---

### Post by chili555 on 2012-03-12
What does this tell us?```
rfkill list all
lsmod | grep acer
```Thanks.> So far, I've not been able to rfkill from on to off.How so? With a switch or key combination or...?

---

### Post by allendevans on 2012-03-14
Hello.  Thanks for your interest.  Sorry for my slow response.  

Here is the code you requested.

```
XXX@XXX:~$ rfkill list all
XXX@XXX:~$ lsmod | grep acer
XXX@XXX:~$ 

```I tried reinstalling and recompiling a new kernel using "make  allyesconfig" and "make allmodconfig" to see if that would address the  problem.  Currently using the standard Ubuntu 10.04 LTS kernel with the  sole modification of selecting "Pentium M" (MPENTIUMM) as the CPU.

Why does this matter?  So far, no change.  Tonight I'll kick off a "make allyesconfig" compile and see if that works.


Thanks ... Allen.

---

### Post by flash63 on 2012-03-14
> **allendevans said:**
> Hey!
I'm having the same problems with Lucid 10.04 on my Aspire 1690 ...


Hello,
in this case you need Acer-Hotkey to enable WLAN.

Translation to install via DKMS
[http://translate.google.de/translate?hl=de&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FAcer_Hotkeys%2FDKMS](http://translate.google.de/translate?hl=de&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FAcer_Hotkeys%2FDKMS)

Additional informations here [http://translate.google.de/translate?sl=auto&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F2670605%2F&act=url](http://translate.google.de/translate?sl=auto&tl=en&js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fforum.ubuntuusers.de%2Fpost%2F2670605%2F&act=url)

For the startup options and to enable the LED see [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

---

### Post by chili555 on 2012-03-14
> **allendevans said:**
> Hello.  Thanks for your interest.  Sorry for my slow response.  

Here is the code you requested.

```
XXX@XXX:~$ rfkill list all
XXX@XXX:~$ lsmod | grep acer
XXX@XXX:~$ 

```I tried reinstalling and recompiling a new kernel using "make  allyesconfig" and "make allmodconfig" to see if that would address the  problem.  Currently using the standard Ubuntu 10.04 LTS kernel with the  sole modification of selecting "Pentium M" (MPENTIUMM) as the CPU.

Why does this matter?  So far, no change.  Tonight I'll kick off a "make allyesconfig" compile and see if that works.


Thanks ... Allen.You said:> So far, I've not been able to rfkill from on to off. And then I said:> How so? With a switch or key combination or...? So, how so?

Is rfkill installed?```
rfkill --version
```If not, can you hook up the ethernet and install it?```
sudo apt-get install rfkill
```Then see what it reports again:```
rfkill list all

```

---

### Post by allendevans on 2012-03-14
Hello.  Thanks for your reply, Chili555.

Sorry for any confusion.  I don't believe I'm getting the same responses from rfkill, as before I reinstalled Lucid and upgraded to the newest kernel.  Here are the answers to your questions.

```
XXX@XXX:/usr/src/linux-source-2.6.32$ rfkill --version
rfkill 0.4

```I ran this command twice.  The first time gave the output provided above.  To ensure I have the latest version, I ran "sudo apt-get install rfkill".  Afterwards, I received the same results, version "0.4".

```
XXX@XXX:/usr/src/linux-source-2.6.32$ rfkill list all
XXX@XXX:/usr/src/linux-source-2.6.32$ 

```Answering your question about the rfkill switch ...

You said:     Quote:
                                                 So far, I've not been able to rfkill from on to off.                                 
And then I said:     Quote:
                                                 How so? With a switch or key combination or...?     
                 
I implied, poorly, that on my Acer Aspire 1690, the Fn-F3 swtich wasn't switching the wireless card on/off.  Based on my experience, Fn-F3 is a standard (?) wireless on/off switch for Acer laptops.  Because it's an internal wireless card, I don't believe I can physically access the wireless card to check for a physical on/off switch.  FYI, under Lucid, my Acer Aspire 1690's Fn-F3 combination displays a "Power Information" dialog.

I believe I need a patch of some sort to direct the Fn-F3 switch to address the wireless card.  A post to that end was received over night, but I haven't attempted to implement it yet.

Thanks for you support.

Allen.

---

### Post by allendevans on 2012-03-14
flash63 ...

Sha-zam!  I believed it was a Fn-F3 button (or similar) mismatch.  I queried for ipw2200 (thinking that to be the root cause) and Acer, but didn't run across this fix.

I'm reading the pages now and will post a response later letting you know if this solved my problem.

Vielen Dank! ... Allen.

---

### Post by chili555 on 2012-03-14
> Based on my experience, Fn-F3 is a standard (?) wireless on/off switch for Acer laptops.But not in this case. Here is a link to the manual: [http://support.acer-euro.com/documents/manuals/notebook/manual_aspire1690.html](http://support.acer-euro.com/documents/manuals/notebook/manual_aspire1690.html)

Pages 3 and 4 indicate that the button is indicated as 6 in the attached image. Now can you enable wireless?

---

### Post by allendevans on 2012-03-15
Chilli555 ... my, you are thorough.

You fixed the problem!  This laptop has been in a closet for about three years, I forgot the bluetooth and wireless are controlled by that set of buttons ... and fixated on the Fn-F3 button.  I feel silly.   

Glad for it too ... compiling the "acerhk-source" module is giving me fits.

Many thanks to you and flash63.

---

