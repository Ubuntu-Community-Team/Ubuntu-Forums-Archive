---
title: "Wireless does not work with Realtek 8192E wirelesss card (Samsung N120 netbook)"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by yume00 on 2009-06-19
I'm running Ubuntu Network Remix 9.04 as a USB Live Image, but I couldn't get wireless to work. Could anyone please help? Thanks.

1 ) Machine Brand and Model (PC/Laptop):
Samsung N120

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)


$ lsusb

Bus 001 Device 005: ID 0ac8:c335 Z-Star Microelectronics Corp. 
Bus 001 Device 003: ID 1516:8628 CompUSA 128M Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

3 ) check interface:
Code:

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:77:fb:9a:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ iwconfig


(hint) if the Wireless interface name is wlan0 you can also use
Code:

$ iwconfig wlan0

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


4 ) Check for modules:
Code:

$ lsmod

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
i915                   65540  3 
drm                    96296  4 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
btusb                  19608  2 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
psmouse                61972  0 
serio_raw              13316  0 
pcspkr                 10496  0 
snd 62628 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_de vice
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
video                  25360  0 
intel_agp              34108  1 
output                 11008  1 video
soundcore              15200  1 snd
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
squashfs               46344  1 
aufs                  165924  1 
exportfs               12544  1 aufs
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usbhid                 42336  0 
usb_storage            82880  1 
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


5 ) Kernel boot messages
Code:

$ dmesg

.....

[   60.872809] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   60.872819] Bluetooth: BNEP filters: protocol multicast
[   60.918990] Bridge firewalling registered
[   62.440698] lp: driver loaded but no devices found
[   62.459802] ppdev: user-space parallel port driver
[   63.733986] [drm] Initialized drm 1.1.0 20060810
[   63.757339] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   63.757352] pci 0000:00:02.0: setting latency timer to 64
[   63.757710] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   63.770167] [drm:i915_setparam] *ERROR* unknown parameter 4
[   63.770240] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   64.970973] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   66.033879] sky2 eth0: enabling interface
[   66.034432] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.147372] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   76.379009] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  210.600697] Monitor-Mwait will be used to enter C-2 state
[  210.619539] Marking TSC unstable due to TSC halts in idle


6 ) Network configuration
Code:

$ sudo lshw -C network

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:fb:9a:d2
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:64:4a:6a:a8:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


7 ) Scan for networks:
Code:

$ iwlist scan

ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


8 ) Ubuntu Version:
Code:

$ lsb_release -d

ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 9.04

9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

$ uname -mr

ubuntu@ubuntu:~$ -uname -mr
bash: -uname: command not found


10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart

ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

I went into Windows system manager and check, the wireless card is Realtek 8192E 802.11n wireless card.

---

### Post by smallrock on 2009-06-26
Hi. I got wifi working on Samsung n120 with Ubuntu 9.04 Jaunty UNR by using Ndiswrapper. Just install Ndiswrapper with Synaptic, download Windows XP driver for Samsung n120 wifi card Realtek 8192 (you can find it on samsung webpage) and unpack it, and then just find unpacked net819xp.inf file with ndiswrapper and it should work (off course you need to set up your wifi functions like ssid, password etc.) Ndiswrapper may say that it couldn't find the device, but it works.
Good luck.

---

### Post by strombom on 2009-06-27
I have another problem with the same hardware.

It can connect to wifi networks with no encryption. However, when I try to connect to an encrypted network it just keeps asking for the key, which I have confirmed is the correct one on another computer.

---

### Post by MJV_fi on 2009-07-11
> **smallrock said:**
> I got wifi working on Samsung n120 with Ubuntu 9.04 Jaunty UNR by using Ndiswrapper.

Thank you for this.

After struggling with the issue for a while I tried this, and for me it's also working. (Also, my router uses WPA2 security and was found and connected to without problems - with the correct password, of course.)

---

### Post by northd_tech on 2009-12-04
From my experience, the Realtek 8192E needs different sourcecode than the 8192SE (and make sure whether you need the 32-bit or 64-bit versions, too).

See chili555's post #2 here for the 8192SE method (and I'm still searching for a working method for the 8192E).  

[http://ubuntuforums.org/showpost.php?p=8335065&postcount=2](http://ubuntuforums.org/showpost.php?p=8335065&postcount=2)

The Realtek 8187__ appear to sometimes be able to use the 8192__ modules from what I've been reading.

---

### Post by OlyDLG on 2009-12-08
> **smallrock said:**
> Hi. I got wifi working on Samsung n120 with Ubuntu 9.04 Jaunty UNR by using Ndiswrapper. Just install Ndiswrapper with Synaptic, download Windows XP driver for Samsung n120 wifi card Realtek 8192 (you can find it on samsung webpage) and unpack it, and then just find unpacked net819xp.inf file with ndiswrapper and it should work (off course you need to set up your wifi functions like ssid, password etc.) Ndiswrapper may say that it couldn't find the device, but it works.
Good luck.

Hi!  I followed these instructions, everything appeared to work fine, but Ubuntu isn't finding the wireless card, even after logging out and back in.  Is there a way force Ubuntu to look for the card?  Or something else that needs to be done that isn't in the instructions above?  Thanks!

---

### Post by Romualdou on 2009-12-20
Hi,
 
same issue, I started another thread for my Samsung R522 with Realtek 8192E. Did you install 32 or 64bit verstion of ubuntu ?

---

### Post by northd_tech on 2010-02-06
> **Romualdou said:**
> Hi,
 
same issue, I started another thread for my Samsung R522 with Realtek 8192E. Did you install 32 or 64bit verstion of ubuntu ?

It sounds like Realtek might finally have a working fix for this Romauldou (but you need to email them for the newest driver)- see these threads:

[http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E](http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E)

[http://ubuntuforums.org/showthread.php?p=8782922#post8782922](http://ubuntuforums.org/showthread.php?p=8782922#post8782922)

---

### Post by kjnelan on 2010-05-31
(Okay, I know it's bad form to resurrect old threads, but this page does come up at the top in searches so I thought I'd post this anyway.)

If you have tried all of the above and are still having difficulty with your Realtek 8192 as I was, then read the following:

I had one bugger of a time getting the realtek 8192SE to work on my Toshiba Satellite. The fix actually was not on my computer, but on the router. The moment I changed the router from both “WPA2 AND WPA” to just WPA everything worked like a charm. I'm not a programmer and can not even begin to understand why things suddenly just worked after that change, but it did.

I've tried several live CD's, all of which now work with my wireless 8192SE after making just that one change.

Good luck all.

---

### Post by dekinstoke on 2010-10-03
Here's a fix for the 8192e. It doesnt work right till the firmware is updated:

[http://www.kickenhardware.net/forum/showthread.php?t=19337](http://www.kickenhardware.net/forum/showthread.php?t=19337)

---

### Post by nyash on 2010-10-10
Can someone confirm that he has succesfully managed to run his wifi realtek 8192E card on Ubuntu 10.10 X64?

If so, how have you done it?

---

### Post by moaoci on 2010-10-11
My realtek rtl8192e is working very well, but it is the version provided by realtek technical support at [EMAIL="wlanfae@realtek.com"]wlanfae@realtek.com[/EMAIL].  Don't hesitate to email them to get your (absolutely free, by the way) driver for Linux/Ubuntu. Don't try to find it in their download section, it is not there and I have no idea why (they got the rtl8192se but not the rtl8192e). They will provide instructions. It is not a fix, it is a Linux driver provided by realtek. 

The driver will have to be recompiled after each linux kernel upgrade, until Linux provides us with a good driver.  

Some Ubuntu versions include the compiled staging  RTL8192E and this one is not working (not for for me anyway).  The staging driver has to be deleted because it takes precedence over the realtek supplied driver.  Open a terminal, sudo nautilus, and then go to filesystem/lib/modules/(your current kernel number)/kernel/driver/staging.  Find the RTL8192E directory and delete it (or rename it if you hesitate...).  Restart the computer and the realtek supplied driver will go on.

Enjoy your new freedom...

---

### Post by nyash on 2010-10-11
I can't get it to work.

I mailed realtek and got rtl8192e_linux_2.6.0014.0401.2010.tar.gz

I followed their instructions, that is:

going to] /lib/modules/2.6.3xxxxxx/
$ find -name "r8192e_pci.ko"

 deleting the file the above command reported

and then installed the driver the usual
sudo su, make, make  install way.

then i tried ./wlan0up, but this commands reports that a file named "r8192e_pci.ko" exists.
in the instructions they said to use ifconfig wlanx up as an alternative, so i did by typing

ifconfig wlan5 up   (wlan5 was my wifi interface)

After rebooting I have no wifi access.

I have been doing this succesfully on the earlier ubuntu version 10.04, but here, the same proccess on 10.10 x64 doesnt work. Anyone got past such issues?

---

### Post by moaoci on 2010-10-11
All problems I had with realtek drivers were corrected by realtek support.  Since I am only on Ubuntu 10.4 , I suggest you write back realtek user support explaining the problem. 

lshw -C network  should give you the driver version that the system sees...  version=14.0401.2010 in your case.  If it says staging, look for the staging rtl8192e repertory in all the kernel version and delete them.

Don't hesitate to ask realtek for support, I had the rtl8192e and the rtl8192se drivers corrected this way in early 2010. One problem was the firmware that was not included in the package, the other was the related to the battery management that shut off the driver when not on AC.

Please let us know when the driver is up and running in Ubuntu 10.10.

---

### Post by moaoci on 2010-10-11
For your information... This guy reported a problem with the 14.0401.2010 driver... 

[http://art.ubuntuforums.org/showpost.php?p=9943819&postcount=22](http://art.ubuntuforums.org/showpost.php?p=9943819&postcount=22)

---

### Post by nyash on 2010-10-11
> **moaoci said:**
> For your information... This guy reported a problem with the 14.0401.2010 driver... 

[http://art.ubuntuforums.org/showpost.php?p=9943819&postcount=22](http://art.ubuntuforums.org/showpost.php?p=9943819&postcount=22)

Thanks, I have actually tried that out, but without removing the staging drivers (Didn't know I had to until today). Will give it a shot again.

edit: bleh, installation fails just as before ;/

---

