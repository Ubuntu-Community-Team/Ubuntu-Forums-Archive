---
title: "Trouble with ATi TV Wonder tuner"
date: 2008-05-23
forum: Multimedia Software
---

### Post by linuxpenguin on 2008-05-23
I'm setting up a PC with MythTV using Mythbuntu.  Everything's set up fine, except I can't get the TV tuner card to work!  It's an ATi TV Wonder Pro that I bought a while back.  Anyone got any ideas?  I'm in the US, and it's being hooked up to a regular analog cable connection.

For good measure here's my "lspci" and "lsmod" of this machine:
```
myth@myth-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:0a.0 Network controller: RaLink RT2600 802.11 MIMO

```

```
myth@myth-desktop:~$ lsmod
Module                  Size  Used by
cx88_vp3054_i2c         3968  0 
cx8802                 19588  0 
videobuf_dvb            7812  0 
dvb_core               81404  1 videobuf_dvb
af_packet              23812  4 
ipv6                  267780  23 
speedstep_lib           6532  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8712  0 
container               5632  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
snd_intel8x0           35356  2 
snd_ac97_codec        101028  1 snd_intel8x0
arc4                    2944  2 
ac97_bus                3072  1 snd_ac97_codec
ecb                     4480  2 
blkcipher               8324  1 ecb
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
rt61pci                25472  0 
rt2x00pci              11264  1 rt61pci
rt2x00lib              22528  2 rt61pci,rt2x00pci
rfkill                  8592  1 rt2x00lib
cx8800                 35848  0 
cx88xx                 66088  2 cx8802,cx8800
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
ir_common              36100  1 cx88xx
mac80211              165652  3 rt61pci,rt2x00pci,rt2x00lib
i2c_algo_bit            7300  2 cx88_vp3054_i2c,cx88xx
tveeprom               16656  1 cx88xx
snd_seq_oss            35584  0 
cfg80211               15112  1 mac80211
videodev               29440  2 cx8800,cx88xx
v4l1_compat            15492  1 videodev
compat_ioctl32          2304  1 cx8800
v4l2_common            18304  4 tuner,cx8800,cx88xx,videodev
videobuf_dma_sg        14980  4 cx8802,videobuf_dvb,cx8800,cx88xx
videobuf_core          18820  5 cx8802,videobuf_dvb,cx8800,cx88xx,videobuf_dma_sg
nvidia               4718832  22 
serio_raw               7940  0 
btcx_risc               5896  3 cx8802,cx8800,cx88xx
eeprom_93cx6            3200  1 rt61pci
snd_seq_midi            9376  0 
i2c_core               24832  11 cx88_vp3054_i2c,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,cx88xx,i2c_algo_bit,tveeprom,nvidia
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                  9232  0 
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              25492  1 
agpgart                34760  2 nvidia,intel_agp
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
parport_pc             36260  1 
parport                37832  2 lp,parport_pc
evdev                  13056  3 
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
ata_generic             8324  0 
ata_piix               19588  2 
floppy                 59588  0 
pata_acpi               8320  0 
libata                159344  3 ata_generic,ata_piix,pata_acpi
scsi_mod              151436  4 sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 

```

(The "Conexant CX23880/1/2/3 PCI Video and Audio Decoder" is my tuner card.)  I had this card working at one point in time on a different PC but that was a while ago, and I don't remember what I did.  This would be a great media PC if I could just get the tuner to work - wifi and Video Out were a breeze to set up.

EDIT: With a little playing I've got it so I can watch TV in TVtime, and MythTV is able to autodetect all my channels.  But I still can't watch TV in MythTV - choosing that option in the frontend brings me to a blank screen, then brings me to the same option screen again after a few seconds.  Running "mythtv-frontend" from a terminal emulator gives me this:
```
myth@myth-desktop:~$ mythfrontend
2008-05-23 15:14:59.922 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-23 15:15:00.484 XScreenSaver support enabled
2008-05-23 15:15:00.485 DPMS is active.
2008-05-23 15:15:00.486 Empty LocalHostName.
2008-05-23 15:15:00.487 Using localhost value of myth-desktop
2008-05-23 15:15:00.508 New DB connection, total: 1
2008-05-23 15:15:00.544 Connected to database 'mythconverg' at host: localhost
2008-05-23 15:15:00.547 Closing DB connection named 'DBManager0'
2008-05-23 15:15:00.549 Total desktop dim: 1024x768, over 2 screen[s].
2008-05-23 15:15:00.550 Screen 0 dim: 1024x768.
2008-05-23 15:15:00.550 Screen 1 dim: 1024x768.
2008-05-23 15:15:00.550 Primary screen 0.
2008-05-23 15:15:00.551 Connected to database 'mythconverg' at host: localhost
2008-05-23 15:15:00.554 Using screen 0, 1024x768 at 0,0
2008-05-23 15:15:00.604 New DB connection, total: 2
2008-05-23 15:15:00.605 Connected to database 'mythconverg' at host: localhost
2008-05-23 15:15:00.609 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-23 15:15:00.610 Enabled verbose msgs:  important general
2008-05-23 15:15:01.088 Unable to parse themeinfo.xml for glass-wide
2008-05-23 15:15:01.088 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-23 15:15:01.615 Unable to parse themeinfo.xml for glass-wide
2008-05-23 15:15:01.616 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-23 15:15:02.370 Total desktop dim: 1024x768, over 2 screen[s].
2008-05-23 15:15:02.371 Screen 0 dim: 1024x768.
2008-05-23 15:15:02.371 Screen 1 dim: 1024x768.
2008-05-23 15:15:02.371 Primary screen 0.
2008-05-23 15:15:02.372 Using screen 0, 1024x768 at 0,0
2008-05-23 15:15:02.376 Switching to square mode (Mythbuntu-8.04)
2008-05-23 15:15:02.492 Using the Qt painter
2008-05-23 15:15:02.493 JoystickMenuClient Error: Joystick disabled - Failed to read /home/myth/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2008-05-23 15:15:02.514 lirc_init failed for mythtv, see preceding messages
2008-05-23 15:15:04.804 Specified base font 'medium' does not exist for font clock
2008-05-23 15:15:04.805 Specified base font 'medium' does not exist for font small
2008-05-23 15:15:04.805 Specified base font 'medium' does not exist for font medium
2008-05-23 15:15:04.805 Specified base font 'medium' does not exist for font large
2008-05-23 15:15:04.808 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-23 15:15:04.982 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-23 15:15:05.140 Registering Internal as a media playback plugin.
2008-05-23 15:15:05.541 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-23 15:15:06.077 Failed to run 'cdrecord --scanbus'
2008-05-23 15:15:06.082 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-23 15:15:06.086 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-23 15:15:06.217 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
Failed to find network interface eth0
SIP listening on IP Address :5060 NAT address 
SIP: Cannot register; proxy, username or password not set
Destroying SipFsm object 
2008-05-23 15:15:11.654 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-23 15:15:11.656 Using protocol version 40
2008-05-23 15:15:11.881 TV: Attempting to change from None to WatchingLiveTV
2008-05-23 15:15:11.882 Using protocol version 40
2008-05-23 15:15:13.476 GetEntryAt(-1) failed.
2008-05-23 15:15:13.478 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-05-23 15:15:13.478 TV Error: LiveTV not successfully started
2008-05-23 15:15:13.523 TV Error: LiveTV not successfully started
2008-05-23 15:15:13.618 DPMS Deactivated 
2008-05-23 15:15:13.620 DPMS Reactivated.
2008-05-23 15:15:13.721 TV: Deleting TV Chain in destructor
2008-05-23 15:15:30.980 Received a remote 'Clear Cache' request
2008-05-23 15:16:16.767 Received a remote 'Clear Cache' request
2008-05-23 15:16:20.061 Deleting UPnP client...

```

---

### Post by linuxpenguin on 2008-05-24
Nevermind, I fixed it late last night.  I found a "howto" that gave me a little more insight how to set up the TV Wonder PRO with Ubuntu and MythTV:
[http://ubuntuforums.org/archive/index.php/t-220027.html](http://ubuntuforums.org/archive/index.php/t-220027.html)

---

