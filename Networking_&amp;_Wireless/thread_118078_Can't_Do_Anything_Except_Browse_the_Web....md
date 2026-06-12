---
title: "Can't Do Anything Except Browse the Web..."
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by NickFormerlyKnownAsPrince on 2006-01-16
This problem has me absolutely buggered, and I have no idea what to search for...

I can *finally* browse the web after disabling IPv6... but that's about it. I can download programs fine, but forget using apt-get/Synaptic (connections time out). I can't get on IRC... or anything else...

I'm using an IBM Thinkpad T43 with the Intel Wireless adapter (ipw2200 has been working for me thus far).

I doubt/don't know if these will help, but better to have it and not need it, right?

**lspci**
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460
0000:02:00.0 Ethernet controller: Broadcom Corporation: Unknown device 167d (rev 11)
0000:04:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0000:04:02.0 Network controller: Intel Corp.: Unknown device 4224 (rev 05)

**lsmod**
Module                  Size  Used by
ntfs                   92016  1
vfat                   12288  0
fat                    46492  1 vfat
isofs                  32824  0
nls_utf8                2176  1
udf                    75524  0
fglrx                 245412  7
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
ibm_acpi               17908  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
sg                     33696  0
sr_mod                 15652  0
cdrom                  33952  1 sr_mod
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
floppy                 52692  0
rtc                    11832  0
pcspkr                  3652  0
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
snd_intel8x0           30144  2
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  1
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  2 fglrx,intel_agp
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
dm_mod                 50364  4
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usb_storage            64704  2
tg3                    83716  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usb_storage,ehci_hcd,uhci_hcd
sd_mod                 17424  5
ide_generic             1664  0
ide_core              125268  2 usb_storage,ide_generic
ata_piix                9476  4
ahci                   11268  0
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  6 sg,sr_mod,usb_storage,sd_mod,ahci,libata
unix                   24624  369
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

**cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed

iface eth0 inet dhcp
        mtu 1492




auto eth1

**ifconfig eth1**
eth1      Link encap:Ethernet  HWaddr 00:13:CE:56:2E:8D
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4408934 (4.2 MiB)  TX bytes:647034 (631.8 KiB)
          Interrupt:21 Base address:0xe000 Memory:a8401000-a8401fff

**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

Also, I'm pretty sure this has to do with my router on some level. I mean, I've been able to do these things before on a WRT54G and a Netgear (can't remember the model number), but since I've been using this on a D-link DGL-4300 hooked up to a Netcomm NB5 modem... it's been nothing but trouble (it can't be a firewall... I've disabled it, put the router in the modem's DMZ and then put the laptop in the router's DMZ).

If anyone can help me on this at all, it'd be really appreciated.

*Edit* The plot grows thicker... I just noticed when I run apt-get from the terminal, the addresses always come up as 1.0.0.0, and when I tried telnetting into my shell account at otaku.freeshell.org, the address came up as 1.0.0.0. What does this mean? Is it some weird sort of DNS issue?

---

### Post by NickFormerlyKnownAsPrince on 2006-01-16
Fixed!

[https://wiki.ubuntu.com/StaticDnsWithDhcp](https://wiki.ubuntu.com/StaticDnsWithDhcp)

Just got the DNS server address from my ISP and made sure everything was in there (particularly the "auto eth1" bit for your main interface), and everything worked like a charm.

---

