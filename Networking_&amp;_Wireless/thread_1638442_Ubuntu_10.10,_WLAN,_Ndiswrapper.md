---
title: "Ubuntu 10.10, WLAN, Ndiswrapper"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by gr34t3st on 2010-12-05
Hey,

I've been using Ubuntu 10.10 32bit for about a week now. I'm running it on a Sony Vaio CW (VPCCW290x). I've been working out the kinks and this is the last major hardware problem. 

[QUOTE=Driver Details]
Atheros® AR928X Wireless Network Adapter Driver
[Sony Support Driver Download Page]("http://esupport.sony.com/US/perl/swu-download.pl?mdl=VPCCW290X&upd_id=4820&os_id=7")
[/QUOTE]

As the title says, I'm having problems with my WLAN connections. Speeds are limited dramatically. I'm getting download speeds of about 700-800b/s. Through Google and the forums, I learned about ndiswrapper which requires Windows XP WLAN drivers. I went to Sony's support website and located the driver. As expected, the driver is an .exe install, NOT the convenient .inf file. 

After more research, I've learned to use cabextract and 7zip to extract the .inf file. Cabextract gives me an error, while 7zip on WINE gives me a few files: .rsrc_1, CERTIFICATE, .data, .rdata, .text, and a .rsrc folder. The .inf wasn't in that folder either. I installed the driver through WINE to find the extract .inf file in the Windows C:/ drive but had no success.

Finally, I found a website called Atheros.cz which had the .inf available for download. I downloaded the file and pointed ndiswrapper to it. Ndiswrapper seems to install it alright. I opened ndiswrapper again and received a pop-up telling me that ndiswrapper was "unable to see if hardware is present." Once I click Ok, it has my driver under the currently installed list with the message "Hardware Present: Yes" After all of this, my internet speeds are still atrocious on wireless internet. I'm beginning to give up on this project.. I'm assuming I have the right driver but I'm just missing something. I haven't blacklisted Ubuntu's driver or anything else so maybe that would be where the problem lies. Unfortunately, I'm not sure how to do that. Please let me know if there is anything more I can do...

Thanks!

---

### Post by northd_tech on 2010-12-05
Hi,

You are certain that is an Atheros AR928x wireless interface?  Can you post the results of these terminal commands (Applications > Accessories > Terminal):

```
lspci
sudo lshw -C network
lsmod
lsbusb
ifconfig
iwconfig
ndiswrapper -l
```

The reason I ask is that this thread claims that Ubuntu 10.10 Meerkat works "out of the box" for that Atheros interface:

[http://ubuntuforums.org/showthread.php?t=1332317](http://ubuntuforums.org/showthread.php?t=1332317)

---

### Post by gr34t3st on 2010-12-05
> **northd_tech said:**
> 
```
lspci
sudo lshw -C network
lsmod
lsbusb
ifconfig
iwconfig
ndiswrapper -l
```


lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

sudo lshw -C network
```
PCI (sysfs)
```

lsmod
```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:dd:08:c9:c4:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathw driverversion=1.56+,06/04/2010,7.7.0.523 latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:16 memory:e7a00000-e7a0ffff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:24:be:c3:44:a7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.113 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

Module                  Size  Used by
aes_i586                7280  495 
aes_generic            26875  1 aes_i586
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
kvm_intel              42019  0 
kvm                   256341  1 kvm_intel
snd_hda_codec_nvhdmi    13615  4 
ndiswrapper           184207  0 
snd_hda_codec_realtek   217971  1 
nvidia               9344006  42 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
sony_laptop            29088  0 
btusb                  10969  2 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               55847  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
joydev                  8735  0 
psmouse                59033  0 
videodev               43098  1 uvcvideo
lp                      7342  0 
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
intel_ips              11101  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
parport                31492  3 parport_pc,ppdev,lp
uvesafb                22649  1 
usbhid                 36882  0 
hid                    67742  1 usbhid
firewire_ohci          21106  0 
ahci                   19013  0 
sky2                   45127  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
libahci                21667  3 ahci
video                  18712  0 
intel_agp              26424  0 
output                  1883  1 video
agpgart                32011  2 nvidia,intel_agp

```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:24:be:c3:44:a7  
          inet addr:192.168.0.113  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:beff:fec3:44a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39460583 (39.4 MB)  TX bytes:2287268 (2.2 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 78:dd:08:c9:c4:30  
          inet6 addr: fe80::7add:8ff:fec9:c430/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:246778 (246.7 KB)  TX bytes:145241 (145.2 KB)
          Interrupt:16 Memory:e7a00000-e7a10000 

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

ndiswrapper -l
```

WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
WARNING: /etc/modprobe.d/bad_list line 1: ignoring bad line starting with 'alia'
netathw : driver installed
	device (168C:002B) present (alternate driver: ath9k)

```

Hope this helps..

---

### Post by northd_tech on 2010-12-05
> **gr34t3st said:**
> **lspci**
02:00.0 Network controller: [COLOR=Red]Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)[/COLOR]
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8057 PCI-E Gigabit Ethernet Controller (rev 10)

**sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: [COLOR=Red]AR9285[/COLOR] Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:dd:08:c9:c4:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR=Red]**driver=ndiswrapper+netathw **driverversion=1.56+,06/04/2010,7.7.0.523[/COLOR] latency=0 link=no multicast=yes [COLOR=Red]wireless=IEEE 802.11g[/COLOR]
       resources: irq:16 memory:e7a00000-e7a0ffff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:24:be:c3:44:a7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.113 latency=0  link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

**lsmod**
Module                  Size  Used by
[COLOR=Red]ndiswrapper           184207  0 [/COLOR]

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:24:be:c3:44:a7  
          inet addr:192.168.0.113  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:beff:fec3:44a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39460583 (39.4 MB)  TX bytes:2287268 (2.2 MB)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr 78:dd:08:c9:c4:30  
          inet6 addr: fe80::7add:8ff:fec9:c430/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
         **[COLOR=Red] RX bytes:246778 (246.7 KB)  TX bytes:145241 (145.2 KB)[/COLOR]**
          Interrupt:16 Memory:e7a00000-e7a10000 
[B]
iwconfig[/B]
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries:0  Invalid misc: 0   Missed beacon: 0
[B]
ndiswrapper -l[/B]
WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
WARNING: /etc/modprobe.d/bad_list line 1: ignoring bad line starting with 'alia'
[COLOR=Red][B]netathw : driver installed
    device (168C:002B) present (alternate driver: ath9k)[/B][/COLOR]


According to post #127 on another thread, your Atheros AR9285 wireless is just supposed to work "out of the box" with ubuntu 10.04 Beta (and I would expect the newer ver. 10.10 as well).
http://ubuntuforums.org/showpost.php?p=9146138&postcount=127

Let's try getting rid of that ndiswrapper module and trying the Linux "native" Atheros wireless module instead:

[CODE]sudo rmmod ndiswrapper
sudo modprobe ath9k
ifconfig
iwconfig
```If you get any error messages, could you post those here also?

---

### Post by gr34t3st on 2010-12-05
Update: I edited my /etc/modprobe.d/bad_list and deleted the line that contained my driver. Now, when I open ndiswrapper, I don't receive the pop up that tells me my hardware is not detected. It also says hardware is detected under my driver. Unfortunately, my speeds are still really, really low.

---

### Post by northd_tech on 2010-12-05
What does **lsmod** tell you now, after modifying the /etc/modprobe.d file?

---

### Post by gr34t3st on 2010-12-05
> **northd_tech said:**
> What does **lsmod** tell you now, after modifying the /etc/modprobe.d file?

lsmod
```
Module                  Size  Used by
arc4                    1165  2 
ath9k                  88756  0 
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
aes_i586                7280  307 
aes_generic            26875  1 aes_i586
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
rfcomm                 33811  4 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
kvm_intel              42019  0 
kvm                   256341  1 kvm_intel
snd_hda_codec_nvhdmi    13615  4 
nvidia               9344006  42 
snd_hda_codec_realtek   217971  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
sony_laptop            29088  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8735  0 
uvcvideo               55847  0 
btusb                  10969  2 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw               4022  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
lp                      7342  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
intel_ips              11101  0 
parport                31492  3 parport_pc,ppdev,lp
uvesafb                22649  0 
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19013  0 
firewire_ohci          21106  0 
sky2                   45127  0 
sdhci_pci               6339  0 
firewire_core          46643  1 firewire_ohci
intel_agp              26424  0 
libahci                21667  3 ahci
crc_itu_t               1383  1 firewire_core
sdhci                  15890  1 sdhci_pci
led_class               2633  2 ath9k,sdhci
agpgart                32011  2 nvidia,intel_agp
video                  18712  0 
output                  1883  1 video

```

My internet speeds seem faster.. I tried downloading a file and it stayed around 10 kbps and then dropped back to below 1kbps. I typed in the commands you told me to as well to get that result.

EDIT: My speeds are still really low. It seems like my download speeds jumped to 10 kbps and now they're back where they were.

---

### Post by northd_tech on 2010-12-05
> **gr34t3st said:**
> lsmod
[CODE]Module                  Size  Used by
ath9k                  88756  0 
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211

That looks to be the collection of Atheros modules.  I did a search for "slow connection Atheros AR928x" and found a few threads that talked about installing kernel backports to fix slow connections (but most of this was at least 2 versions of Ubuntu old, so the fix methods aren't correct for your 10.10 Meerkat install).

The instructions for Maverick Meerkat backports is here:
https://help.ubuntu.com/community/UbuntuBackports

I've gotta run for a while, but this is what came up in my search for slow connections on that Atheros WiFi family (but some of it was quite old):
http://ubuntuforums.org/showthread.php?t=1597069

http://ubuntuforums.org/showthread.php?t=894177

http://ubuntuforums.org/showthread.php?t=1247572

http://ubuntuforums.org/showthread.php?t=1482950

---

### Post by walt.smith1960 on 2010-12-05
Do you have a means to create a live CD or USB of 10.04? I have that WiFi chip in an ASUS netbook and it has supported the Atheros 9xxx PCIe WiFi natively since 9.04, I think.  I've read where some have had wireless issues with 10.10.  Just a thought......

---

### Post by Pronker on 2011-03-17
I'm having similar problems... although my system actually freezes entirely!

It's similar to this guy's problem:
[http://ubuntuforums.org/archive/index.php/t-1063435.html](http://ubuntuforums.org/archive/index.php/t-1063435.html)

I've tried installing backports but it didn't help... 

:( I'm desparate!

---

