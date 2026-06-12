---
title: "XFCE Hardy wireless problem"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by guido32 on 2010-05-16
I have a Dell Latitude C400 laptop running Xubuntu Hardy.  I am a newbie and am trying to install a PCMCIA wireless card.  The card is a TRENDnet model # TEW-421PC/A.  I am using XFCE.  My friend palsyboy has been helping me perform the install and will post more information on the matter.

---

### Post by palsyboy on 2010-05-16
I'd be happy to resolve this for guido32 in person, but I'm a few hundred miles away from him.  The other problem is that I've never used Xfce, so I don't know the GUI tools available.

After searching online, we tried installing wcid, but the package wasn't found.  We installed wifi-radar, and it worked, but as it sees no SSIDs, it's safe to assume that the card isn't working.  According to [this document]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), the card had a pretty good chance of working.  Does anyone have any insight?

---

### Post by NUboon2Age on 2010-05-16
Please provide the info found at  [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681")

I've used Xubuntu and managed to fix a gnarly Broadcom problem in Xubuntu Jaunty Jackalope, but have limited Linux knowledge but will pitch in as I can...  And others may have much more help to provide.

---

### Post by NUboon2Age on 2010-05-16
(after providing basic info)... in XFCE I think under System or Accessories there is some form of the GUI third party driver manager 'Jockey' provided listed as "Hardware Drivers".  If that were available, and its just a matter of missing drivers its possible that might fix it right up.

---

### Post by guido32 on 2010-05-18
sorry for the delay.  here is what info i get for each of the categories:

1)already listed

2)   

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

3)  

eth0      Link encap:Ethernet  HWaddr 00:0b:db:09:e6:51  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe09:e651/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5746027 (5.4 MB)  TX bytes:183172 (178.8 KB)
          Interrupt:11 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.3 KB)  TX bytes:1400 (1.3 KB)

4)

Module                  Size  Used by
ipv6                  268036  8 
i915                   32640  2 
drm                    82452  3 i915
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_ich           6288  0 
speedstep_lib           6532  1 speedstep_ich
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 speedstep_ich,cpufreq_stats,cpufreq_ondemand
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
parport_pc             36260  1 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
pcmcia                 40876  0 
dcdbas                  9504  0 
serio_raw               7940  0 
evdev                  13056  7 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
snd_intel8x0           35356  1 
snd_ac97_codec        101028  1 snd_intel8x0
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
ac97_bus                3072  1 snd_ac97_codec
psmouse                40336  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78724  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
video                  19856  0 
output                  4736  1 video
button                  9232  0 
battery                14212  0 
ac                      6916  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
snd                    56996  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25492  1 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
agpgart                34760  3 drm,intel_agp
usbhid                 32128  0 
hid                    38784  1 usbhid
ext3                  136968  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
ata_generic             8324  0 
pata_acpi               8320  0 
floppy                 59588  0 
ata_piix               19588  2 
libata                159728  3 ata_generic,pata_acpi,ata_piix
3c59x                  46376  0 
mii                     6400  1 3c59x
scsi_mod              151692  3 sg,sd_mod,libata
uhci_hcd               27024  0 
usbcore               146412  3 usbhid,uhci_hcd
thermal                16796  0 
processor              36616  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3584  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

5) 

This is really long.  Is there a specific code I am looking for?  Here is some code that I think pertains to the PCMCIA card:

[   48.015933] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   48.015950] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   48.016798] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   48.017092] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   48.017416] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   73.136333] NET: Registered protocol family 10
[   73.137543] lo: Disabled Privacy Extensions
[   79.534619] eth0: no IPv6 routers present

That's all I can give you tonight.  I will respond to furthur replies tomorrow.

---

