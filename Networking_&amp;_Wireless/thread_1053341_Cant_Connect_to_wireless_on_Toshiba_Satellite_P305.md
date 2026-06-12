---
title: "Cant Connect to wireless on Toshiba Satellite P305D atheros card"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Mister Mister on 2009-01-28
so, I decided to switch to ubuntu because I needed to clear out my hard-drive anyway and I was sick of vista.  However, now that I've installed ubuntu 8.10, I can't get any kind of wireless connection, which is bad as my college has almost no easily available wired connection points.  I'm new to ubuntu, and the laptop was a gift, so I'm sorry if this is all gratingly pointless but this is all the info I could get by following the HOWTO guide on asking for wireless help.

The laptop is, as far as I can tell, a toshiba satellite P305D, bought around july-august of 2008.  I'm running ubuntu ibex.  

edit:  sorry to not have been specific before, but the problem is that there's not any indication that the laptop has a card installed, even though I know it does.  not even an option to connect to wireless.

lspci:  ```
stefan@stefan-laptop:~$ lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge

00:01.0 PCI bridge: Toshiba America Info Systems Device 9602

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control

01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)

09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)

09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)

09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

stefan@stefan-laptop:~$ 

```

ifconfig: 
```
stefan@stefan-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:68:80:f2:c9  

          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::21e:68ff:fe80:f2c9/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:110207 errors:0 dropped:0 overruns:0 frame:0

          TX packets:69688 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:153821392 (153.8 MB)  TX bytes:5957360 (5.9 MB)

          Interrupt:18 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig: 
```
stefan@stefan-laptop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



pan0      no wireless extensions.



```

lfmod:
```
stefan@stefan-laptop:~$ lsmod

Module                  Size  Used by

ipv6                  263972  10 

af_packet              25728  2 

binfmt_misc            16904  1 

sco                    18308  2 

bridge                 56980  0 

stp                    10628  1 bridge

bnep                   20480  2 

rfcomm                 44432  0 

l2cap                  30464  6 bnep,rfcomm

bluetooth              61924  6 sco,bnep,rfcomm,l2cap

ppdev                  15620  0 

powernow_k8            22148  0 

cpufreq_ondemand       14988  2 

cpufreq_powersave       9856  0 

cpufreq_conservative    14600  0 

cpufreq_stats          13188  0 

freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats

cpufreq_userspace      11396  0 

container              11520  0 

pci_slot               12552  0 

sbs                    19464  0 

sbshc                  13440  1 sbs

iptable_filter         10752  0 

ip_tables              19600  1 iptable_filter

x_tables               22916  1 ip_tables

sbp2                   29324  0 

parport_pc             39204  0 

lp                     17156  0 

parport                42604  3 ppdev,parport_pc,lp

joydev                 18368  0 

snd_hda_intel         381488  4 

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss

snd_seq_dummy          10884  0 

snd_seq_oss            38528  0 

snd_seq_midi           14336  0 

snd_rawmidi            29824  1 snd_seq_midi

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29960  2 snd_pcm,snd_seq

snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

serio_raw              13444  0 

uvcvideo               62728  0 

sdhci_pci              15360  0 

psmouse                45200  0 

evdev                  17696  12 

sdhci                  23940  1 sdhci_pci

compat_ioctl32          9344  1 uvcvideo

pcspkr                 10624  0 

snd                    63268  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

mmc_core               58268  1 sdhci

soundcore              15328  1 snd

i2c_piix4              16144  0 

videodev               41344  1 uvcvideo

i2c_core               31892  1 i2c_piix4

snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

v4l1_compat            22404  2 uvcvideo,videodev

lmpcm_usb              12800  0 

video                  25104  0 

output                 11008  1 video

fglrx                1813960  31 

ath_pci                99096  0 

wlan                  211952  1 ath_pci

ath_hal               198864  1 ath_pci

agpgart                42184  1 fglrx

wmi                    14504  0 

ac                     12292  0 

battery                18436  0 

button                 14224  0 

shpchp                 37908  0 

pci_hotplug            35236  1 shpchp

ext3                  133384  1 

jbd                    55444  1 ext3

mbcache                16004  1 ext3

sr_mod                 22212  0 

cdrom                  43168  1 sr_mod

ata_generic            12932  0 

usbhid                 35840  0 

hid                    50560  1 usbhid

sd_mod                 42264  3 

crc_t10dif              9984  1 sd_mod

sg                     39732  0 

pata_atiixp            12800  0 

ohci1394               37936  0 

ahci                   37132  2 

ieee1394               96324  2 sbp2,ohci1394

pata_acpi              12160  0 

ohci_hcd               31888  0 

ehci_hcd               43276  0 

libata                177312  4 ata_generic,pata_atiixp,ahci,pata_acpi

scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata

dock                   16656  1 libata

usbcore               148848  6 uvcvideo,lmpcm_usb,usbhid,ohci_hcd,ehci_hcd

sky2                   53380  0 

thermal                23708  0 

processor              42156  2 powernow_k8,thermal

fan                    12548  0 

fbcon                  47648  0 

tileblit               10880  1 fbcon

font                   16512  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit

fuse                   60828  3 

```

network configuration:
```
stefan@stefan-laptop:~$ sudo lshw -C network

[sudo] password for stefan: 

  *-network UNCLAIMED     

       description: Ethernet controller

       product: AR242x 802.11abg Wireless PCI Express Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       version: 01

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix cap_list

       configuration: latency=0

  *-network

       description: Ethernet interface

       product: 88E8040 PCI-E Fast Ethernet Controller

       vendor: Marvell Technology Group Ltd.

       physical id: 0

       bus info: pci@0000:04:00.0

       logical name: eth0

       version: 12

       serial: 00:1e:68:80:f2:c9

       size: 100MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.110 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 22:f5:67:7d:4b:b7

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

stefan@stefan-laptop:~$ 



```


EDIT:  I managed to find the solution in a thread kevdog posted in.  If anyone reads this and has the same problem, the solution is as follows:

> Ohhh the dreaded 242x or 5007 chipset -- not really.

You have no driver currently associated with the card. I'm assuming you can connect right now using an ethernet connection.

I'd enable the linux-backport package.

So if you were running intrepid this would be the linux-backports-modules-intrepid package.

So here is the quick way to do everything:

gksu gedit /etc/apt/sources.list

Remove # sign in front of the lines that state:
#deb http//us.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse
#deb-src http//us.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse


Save the file.

Then run the following at the command line:
sudo aptitude update
sudo aptitude install linux-backports-modules-intrepid

This should then install the ath5k driver for you (which is the actual name of the driver you are going to use).

sudo modprobe ath5k

Check if the driver is loaded with
lshw -C network

Let me know what you find!

---

### Post by pogo07 on 2009-01-28
I had the same problem with my Toshiba A300.  I solved it by connecting via hardwire to the Internet and doing an update [System] [Administration] [Update Manager].  This allows Ubuntu to update your drivers.  You will then get the request to enable restricted drivers - Do this for the WiFi driver, restart and viola the system works.  I've had to do this for two other computerss so it seems to be a bug in the system.
Good Luck

---

