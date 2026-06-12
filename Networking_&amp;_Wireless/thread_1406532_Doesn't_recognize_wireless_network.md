---
title: "Doesn't recognize wireless network"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by tcinlo on 2010-02-14
I am exploring Ubuntu 8.10 on my Asus netbook without yet installing it.  While using Ubuntu I cannot get it to recognize any wireless networks.
 
Is this because I am only exploring  Ubuntu and it has not yet been installed?  The networks are recognized when using the XP operating system.
 
Will Ubuntu recognize the wireless networks once it is installed as the operating system?

---

### Post by coffeecat on 2010-02-14
> **tcinlo said:**
> Will Ubuntu recognize the wireless networks once it is installed as the operating system?

It depends upon the specific wireless chipset you have in your netbook. Most chipsets are supported out of the box, the drivers and firmware being included with a default installation, and will work in a live session. For some (such as Broadcom) there are licensing issues, and you have to install the firmware once you have made a hard-disc install before wireless will work. And for a small difficult minority, you have to resort to something like ndiswrapper and use the Windows driver.

However, I notice you say you are using version 8.10. Is that right?. 8.10 (Intrepid) will reach end of life (become unsupported) in April and, being nearly 18-months old, it won't support newer chipsets. Furthermore, support for Atheros wireless chipsets (which are common in netbooks) was problematic in 8.10. There are still issues with some Atheros chipsets, but the situation is better in later releases.

So, a couple of questions. Which model Asus are you using? Do you have a reason for not trying the latest version of Ubuntu (9.10)? Open a terminal while in an Ubuntu session, and post the output of:

```
lspci | grep Wireless
```If that doesn't work, try:

```
lspci | grep 802.11
```That should give us the wireless chipset.

---

### Post by tcinlo on 2010-02-14
I have an Asus netbook with Ubuntu 8.10. The wireless won't connect. I'm a total rookie. As near as I can figure my LAN is Atheros Communications Inc. Ar 242x 802.11abg Wireless PCI Express Adapter (rev 01).
 
Ubuntu doesn't seem to recognize it or have a driver for it. Do I need to load a driver? Where would I find that?

---

### Post by northd_tech on 2010-02-14
Can you run the following commands in a terminal and post the results here:

```
lspci

lsusb

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig
```

---

### Post by tcinlo on 2010-02-14
[EMAIL="tim@tim-laptop:~$"]tim@tim-laptop:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
[EMAIL="tim@tim-laptop:~$"]tim@tim-laptop:~$[/EMAIL] lsusb
Bus 005 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 005 Device 003: ID 0951:1606 Kingston Technology 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 15d9:0a41  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[EMAIL="tim@tim-laptop:~$"]tim@tim-laptop:~$[/EMAIL] lsmod
Module                  Size  Used by
ipv6                  263972  8 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  0 
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace      11396  0 
sbs                    19464  0 
container              11520  0 
wmi                    14504  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
uvcvideo               62728  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
evdev                  17696  11 
psmouse                45200  0 
serio_raw              13444  0 
video                  25104  0 
output                 11008  1 video
battery                18436  0 
ac                     12292  0 
pcspkr                 10624  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
ath_pci                99096  0 
wlan                  211952  1 ath_pci
ath_hal               198864  1 ath_pci
atl2                   34072  0 
snd_seq_dummy          10884  0 
eeepc_laptop           16528  0 
button                 14224  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              33724  1 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  3 drm,intel_agp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
libusual               27156  1 usb_storage
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  2 
pata_acpi              12160  0 
ahci                   37132  0 
ata_generic            12932  0 
libata                177312  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              155212  4 usb_storage,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  7 uvcvideo,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
[EMAIL="tim@tim-laptop:~$"]tim@tim-laptop:~$[/EMAIL] uname -a
Linux tim-laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
[EMAIL="tim@tim-laptop:~$"]tim@tim-laptop:~$[/EMAIL] sudo lshw -C network
[sudo] password for tim: 
Sorry, try again.
[sudo] password for tim: 
Sorry, try again.
[sudo] password for tim: 
Sorry, try again.
sudo: 3 incorrect password attempts
[EMAIL="tim@tim-laptop:~$"]tim@tim-laptop:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:88:42:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

---

### Post by PhilGil on 2010-02-15
Is this a new Ubuntu install?  You might want to reconsider your version choice and try 9.10 instead - ASUS netbooks are very well-supported in Karmic.  

I have Karmic installed on a eee pc 1000h and haven't had any trouble with wireless (or much else, for that matter).

---

### Post by tcinlo on 2010-02-15
That's encouraging.  I tried all day to download 9.10 and put it on a disc and USB drive but couldn't get it to load.  I just bought a Ubuntu 9.10 disk off of ebay and will try to load that on the netbook.
 
I'm a total rookie...I assume 9.10 will load and wipe 8.10...yes?

---

### Post by PhilGil on 2010-02-15
> **tcinlo said:**
> That's encouraging.  I tried all day to download 9.10 and put it on a disc and USB drive but couldn't get it to load.  I just bought a Ubuntu 9.10 disk off of ebay and will try to load that on the netbook.
 I'm not sure why you're having problems getting 9.10 to load - you may need to post back here if you continue having trouble.
> **tcinlo said:**
> I'm a total rookie...I assume 9.10 will load and wipe 8.10...yes?The installer will ask if you'd like to use your entire drive for 9.10 or install it side-by-side with 8.10.

---

### Post by northd_tech on 2010-02-15
> **tcinlo said:**
> 
[COLOR=Blue]01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/COLOR]
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
  
lsmod
Module                  Size  Used by
[COLOR=Blue]**ath_pci**                99096  0 
wlan                  211952  1 **ath_pci**
ath_hal               198864  1 **ath_pci**[/COLOR]
atl2                   34072  0 

tim@tim-laptop:~$ uname -a
Linux tim-laptop 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

sudo lshw -C network

[sudo] password for tim: 
Sorry, try again.
sudo: 3 incorrect password attempts

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:88:42:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1

OK- you've got an Atheros [COLOR=Blue]AR242x [COLOR=Black]wireless interface, and it looks to me like there are some modules loaded (the blue [COLOR=Blue]ath_pci[/COLOR] stuff above).

I haven't worked with that interface before, but I seem to remember seeing some threads about that here at this forum- if you search for "atheros AR242x" you should probably find some related info here.

Also, you're running a 32-bit version of the [/COLOR][/COLOR]2.6.27-7-generic kernel (which is a little old).  It is possible that your network interface(s) will be better supported under a newer version (but I've had better luck with 9.04 than I have with 9.10 though).

I'm in no hurry to leave version 9.04.

edit:  There is a fix at post #4 here:
[http://ubuntuforums.org/showpost.php?p=8821272&postcount=4](http://ubuntuforums.org/showpost.php?p=8821272&postcount=4)

and post #3 on this longer thread here:
[http://ubuntuforums.org/showpost.php?p=8199350&postcount=3](http://ubuntuforums.org/showpost.php?p=8199350&postcount=3)

---

### Post by tcinlo on 2010-02-15
This has been very helpful...thanks.  Again, I'm a total rookie and one of the reasons I wanted to put linux on my netbook was to learn more...
 
...I followed the instructions and downloaded the linux headers and kernels.  Now it says to install them...I'm embarassed to say that I don't know how to do that.  I need  step by step instructions on how to do that.  I have the 3 files on a thumb drive.

---

### Post by northd_tech on 2010-02-15
If those are .deb files (Debian packages, which is what ubuntu uses), then you just plug the USB stick in, and click on the USB drive when it shows up on your desktop.

Then just navigate to the .deb files and double click them (or right click and "Open With" the Package installer).  If the order matters, you will probably get some error messages and warnings.

After you install all 3 of those files, I would run the Update Manager, and it should configure everything for you I believe.

There is a possibility that you might need some other stuff like wpa-supplicant, and wireless tools.  It is usually easiest if you can get a cabled ethernet connection to work, then run the Update Manager under System > Administration.  (It will want a password that is probably the same as your main login password).

---

### Post by frodon on 2010-02-16
Threads merged, please avoid duplicates.

---

