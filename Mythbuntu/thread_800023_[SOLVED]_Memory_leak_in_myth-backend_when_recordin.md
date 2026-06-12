---
title: "[SOLVED] Memory leak in myth-backend when recording from DVB-C"
date: 2008-05-19
forum: Mythbuntu
---

### Post by ian dobson on 2008-05-19
Hi all,

Loks as if I've found a major memory leak in mythtv-backend when recording from dvb-c. System specs:-

```
2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation Unknown device 2833 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
05:00.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
05:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```

Syslog DVB:
```
May 19 19:44:11 alpha2 kernel: [   46.949331] DVB: registering new adapter (Satelco EasyWatch DVB-C MK3)
May 19 19:44:11 alpha2 kernel: [   47.556001] DVB: registering frontend 0 (Philips TDA10023 DVB-C)...
r
```

Syslog IVTV
```
May 19 19:44:11 alpha2 kernel: [   45.476809] ivtv:  Start initialization, version 1.1.0
May 19 19:44:11 alpha2 kernel: [   45.476901] ivtv0: Initializing card #0
May 19 19:44:11 alpha2 kernel: [   45.476903] ivtv0: Autodetected Hauppauge card (cx23416 based)
May 19 19:44:11 alpha2 kernel: [   46.048084] ivtv0: Autodetected Hauppauge WinTV PVR-150
May 19 19:44:11 alpha2 kernel: [   46.048085] ivtv0: Reopen i2c bus for IR-blaster support
May 19 19:44:11 alpha2 kernel: [   46.466749] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
May 19 19:44:11 alpha2 kernel: [   46.716697] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
May 19 19:44:11 alpha2 kernel: [   46.932822] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
May 19 19:44:11 alpha2 kernel: [   46.949229] ivtv0: Registered device video1 for encoder MPG (9216 kB)
May 19 19:44:11 alpha2 kernel: [   46.949244] ivtv0: Registered device video32 for encoder YUV (2048 kB)
May 19 19:44:11 alpha2 kernel: [   46.949262] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
May 19 19:44:11 alpha2 kernel: [   46.949277] ivtv0: Registered device video24 for encoder PCM (320 kB)
May 19 19:44:11 alpha2 kernel: [   46.949279] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
May 19 19:44:11 alpha2 kernel: [   46.949291] ivtv:  End initialization
May 19 19:44:44 alpha2 kernel: [   85.441566] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
May 19 19:44:44 alpha2 kernel: [   85.639227] ivtv0: Encoder revision: 0x02060039
```

```
SATELCO EasyWatch PCI DVB-C HDTV
Hauppage PVR-150.

mythbackend version: 0.21.20080304-1 www.mythtv.org
```

lsmod
```

Module                  Size  Used by
xt_tcpudp               4992  4
iptable_nat             9604  1
nf_nat                 23980  1 iptable_nat
nf_conntrack_ipv4      21904  2 iptable_nat
nf_conntrack           79216  3 iptable_nat,nf_nat,nf_conntrack_ipv4
acpi_cpufreq           10832  4
cpufreq_userspace       6180  0
cpufreq_ondemand       11152  0
cpufreq_powersave       3200  0
cpufreq_stats           8416  0
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    10632  0
iptable_filter          4608  1
ip_tables              24104  2 iptable_nat,iptable_filter
x_tables               23560  3 xt_tcpudp,iptable_nat,ip_tables
coretemp                9856  0
msr                     6152  0
w83627ehf              27272  0
hwmon_vid               5120  1 w83627ehf
i2c_i801               12188  0
lp                     14916  0
tda10023                8324  1
snd_usb_audio         100384  0
snd_pcm_oss            47648  0
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         13200  1 snd_pcm
snd_usb_lib            21120  1 snd_usb_audio
wm8775                  8204  0
snd_hwdep              12552  1 snd_usb_audio
ipv6                  311720  32
snd_seq_dummy           5764  0
cx25840                30096  0
snd_seq_oss            38912  0
snd_seq_midi           10688  0
snd_rawmidi            29856  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tuner                  49056  0
tea5767                 7812  1 tuner
tda8290                13828  1 tuner
tuner_simple           10632  1 tuner
mt20xx                 14600  1 tuner
tea5761                 6916  1 tuner
snd_timer              27912  2 snd_pcm,snd_seq
serio_raw               9092  0
budget_av              23808  22
saa7146_vv             56064  1 budget_av
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ivtv                  152512  0
pwc                    92224  1
i2c_algo_bit            8452  1 ivtv
snd                    70856  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_usb_lib,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        17028  1 saa7146_vv
cx2341x                14596  1 ivtv
psmouse                46236  0
videobuf_core          22020  2 saa7146_vv,videobuf_dma_sg
budget_core            14468  1 budget_av
dvb_core               94380  2 budget_av,budget_core
tveeprom               20624  1 ivtv
compat_ioctl32         11136  1 pwc
videodev               30720  4 saa7146_vv,ivtv,pwc
saa7146                22152  3 budget_av,saa7146_vv,budget_core
atl1                   40460  0
soundcore              10400  1 snd
iTCO_wdt               15312  0
v4l2_common            21888  8 wm8775,cx25840,tuner,saa7146_vv,ivtv,cx2341x,compat_ioctl32,videodev
v4l1_compat            15492  3 saa7146_vv,ivtv,videodev
ttpci_eeprom            3968  1 budget_core
mii                     7552  1 atl1
iTCO_vendor_support     5764  1 iTCO_wdt
i2c_core               28544  16 i2c_i801,tda10023,wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,budget_av,ivtv,i2c_algo_bit,budget_core,tveeprom,ttpci_eeprom
button                 10912  0
parport_pc             41128  1
parport                44300  2 lp,parport_pc
evdev                  14976  0
shpchp                 38172  0
pci_hotplug            34608  1 shpchp
pcspkr                  4992  0
ext3                  149264  2
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sr_mod                 20132  0
cdrom                  41512  1 sr_mod
pata_acpi               9856  0
ata_generic             9988  0
sg                     41880  0
sd_mod                 33280  11
ehci_hcd               41996  0
floppy                 69096  0
uhci_hcd               29856  0
pata_jmicron            8448  2
usbcore               169904  6 snd_usb_audio,snd_usb_lib,pwc,ehci_hcd,uhci_hcd
ahci                   33028  4
libata                176304  4 pata_acpi,ata_generic,pata_jmicron,ahci
scsi_mod              178488  4 sr_mod,sg,sd_mod,libata
raid10                 26368  0
raid456               131360  1
async_xor               6144  1 raid456
async_memcpy            4608  1 raid456
async_tx               10484  3 raid456,async_xor,async_memcpy
xor                     7184  2 raid456,async_xor
raid1                  26880  0
raid0                   9472  0
multipath              11008  0
linear                  7424  0
md_mod                 88476  7 raid10,raid456,raid1,raid0,multipath,linear
thermal                19744  0
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0
fbcon                  46336  0
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  1
```
DVB-C card setup for 2 simultanious recordings. Before I start recording from the DVB mythtv-backend uses about 1% memory (I have 3Gb in the box). After recording for about 30minutes mythtv-backend uses 4.1%. If I record from the PVR-150 I don't see this happening.

I have already tried deleting all cards/video sources but that didn't help. The memory is only freed when I stop the backend and restart it again. 

I have tried disabling upnp as per [https://bugs.launchpad.net:443/ubuntu/+source/mythtv/+bug/200761](https://bugs.launchpad.net:443/ubuntu/+source/mythtv/+bug/200761) but it doesn't make any differenceon my system.

Anyone got any ideas and sorry for the really long post?

Regards
Ian Dobson

---

### Post by ian dobson on 2008-05-19
anyone?

In the mean time I've written a small perl script that check how much memory myth-backend is using and if it's using too much and no encoder is active it stops/starts the backend.

Regards
Ian Dobson

---

### Post by laga on 2008-05-20
Have you tried disabling EIT?

---

### Post by ian dobson on 2008-05-20
> **laga said:**
> Have you tried disabling EIT?

No not yet. but that's not really a solution for me as I need the EPG from the DVB-C card, as the DVB channels aren't 100% the same as the analog ones.

I'll try it this evening and see if that makes any difference.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-05-20
Hi,

Just disabled EIT for the DVB-C card, recorded several hours of TV from the DVB-C card (Only 1 program, 2 programs at the same time and 2 programs from the DVB-C card and from the PVR-150 at the same time). In all my tests I've not seen a memory leak.

The memory usage for Mythtv-backend jumps from about 1% to 2% when recording but sinks back to about 1% when the reording is finished.

Although the leak is solved it doesn't really help me much, I still need the EPG for my digital input.

For extra info my cable provider sends DVB-C in QAM256 if that helps and the signal quality is very good.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-05-22
Hi all,

So what now? Although my hack work, it's not really a solution.

Should I open a bug report? Although the problem sounds abit like [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/200761](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/200761) disabling upnp doesn't help.

Is it worth opening a new bug report and attaching a valgrind log?

Regards
Ian Dobson

---

### Post by ian dobson on 2008-05-23
Hi All,

After running afew more tests I've found something interesting I think. The memory leak only happens when I record from some channels.

When I record from Pro7 I see the leak. I'll try other channels this weekend. Note I live in Switzerland and am on the GGA cable network.

Abit of googling produced this :-  [http://www.gossamer-threads.com/lists/mythtv/commits/326740](http://www.gossamer-threads.com/lists/mythtv/commits/326740)

Regards
Ian Dobson

---

### Post by ian dobson on 2008-05-24
Hi,

Just upgraded to the weekly builds and I am still seeing the memory leak.

The leak seems to happen on seveal channels, but it appears to be almost random. It seems to be a combination of recording and grabbing EIT at the same time, When "Active EIT" is enabled.

Regards
Ian Dobson

---

### Post by laga on 2008-05-24
A new bug report and a valgrind log would be great. Thanks! It'd be even better if you installed the debug symbols for the backend and libmyth by adding [http://ddebs.ubuntu.com/](http://ddebs.ubuntu.com/) to your sources.list as a repository and installing the corresponding packages. This page has a little bit more information: [https://wiki.ubuntu.com/DebuggingProgramCrash?highlight=(debug](https://wiki.ubuntu.com/DebuggingProgramCrash?highlight=(debug))

---

### Post by ian dobson on 2008-05-24
Hi,

Before I go ahead and install the debug symbols and use valgrind to create a dump log, I have a question. Will installing the debug symbols have a negative effect on my system after the tests are finished?

Exactly which hosts do I need to include in my sources file? When I use 
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy main universe
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates main universe
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed main universe
deb [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security main universe

apt-get wants to upgrade the following packages
The following packages will be upgraded:
  libmyth-0.21-0 libmyth-perl mythtv-backend mythtv-common mythtv-database mythtv-transcode-utils mythweb
 
When I try and install yelp-dbgsym
I get this:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  consolekit dbus esound-common gamin gnome-doc-utils gnome-mime-data libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libesd-alsa0 libgamin0 libgnome2-0 libgnome2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libhunspell-1.1-0 liblaunchpad-integration1 libnspr4-0d libnss3-1d
  librarian0 libxml2-utils python-libxml2 shared-mime-info xsltproc xulrunner-1.9 yelp
Suggested packages:
  libbonobo2-bin esound desktop-base gnome-icon-theme libgnomevfs2-bin python-libxml2-dbg
Recommended packages:
  libpam-ck-connector dbus-x11 esound-clients gnome-mount libgnomevfs2-extra launchpad-integration
The following NEW packages will be installed:
  consolekit dbus esound-common gamin gnome-doc-utils gnome-mime-data libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-glib1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libesd-alsa0 libgamin0 libgnome2-0 libgnome2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libhunspell-1.1-0 liblaunchpad-integration1 libnspr4-0d libnss3-1d
  librarian0 libxml2-utils python-libxml2 shared-mime-info xsltproc xulrunner-1.9 yelp yelp-dbgsym
0 upgraded, 35 newly installed, 0 to remove and 10 not upgraded.
Need to get 15.1MB of archives.
After this operation, 72.1MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

Regards
Ian Dobson

---

### Post by ian dobson on 2008-05-25
Hi,

Looking through the page you linked to, I should install:-
libgmyth0-dbgsym & mythtv-backend--dbgsym but an 
apt-cache search myth dbgsym
Only finds the debug symbols for libmyth0.

So should I create a log with only libmyth0 debugs or have I misunderstood something?

Regards
Ian Dobson

---

### Post by ian dobson on 2008-05-26
Hi,

I won't be able to do any testing for the next week or so, my paid job is taking over my time at the moment.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-06-02
Hi All,

Upgraded the ram in my Backend to 4Gb and ran afew tests.

Whenever I record anything from my DVB-C card mythbackend "eats" memory. I ran the tests using the following:-

```
valgrind --leak-check=full --error-limit=no --show-reachable=yes --log-file=logfile -v -- /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid --noupnp | tee backend.log
```

I've tried to attach the mythbackend & valgrind log files as well as a memory usage graph from munin, but the log files are too large :confused:

If anyone's interested you can download them from here [http://mail.planet-ian.com/myth.zip](http://mail.planet-ian.com/myth.zip)

If no one answers this/helps me out I'll open an error report.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-06-03
OK,

I've given up trying here. I'll try opening an error report.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-06-11
Hi,

Upgraded mythtv-backend to 0.21.0+fixes17453, 
kernel to 2.6.24-18-generic leak still happening.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-09-05
Hi,

Just upgraded to the latest weekly builds and the problem seems to be solved.

Regards
Ian Dobson

---

