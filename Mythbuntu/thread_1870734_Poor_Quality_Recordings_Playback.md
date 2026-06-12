---
title: "Poor Quality Recordings Playback"
date: 2011-10-27
forum: Mythbuntu
---

### Post by MickSulley on 2011-10-27
Hi,

I have a fresh install of Ubuntu 11.10 with MythTV and other Myth bits added.  I have recorded TV and the playback quality is very poor, seems to be low resolution and a slight stutter of the picture, also the sound is out of sync.  If I exit MythTV Frontend, go to the recordings folder and double click the recording it plays fine. 

What could cause this? Is there some setup that I may have got wrong?

Thanks
Mick

---

### Post by nickrout on 2011-10-27
I think we need a bit more information :)

What recording hardware (ie tuner)?

mediainfo output on an affected recording?

Playback settings in mythfrontend?

---

### Post by keepitsimpleengr on 2011-10-27
Mythtv can be a touchy about things, and what your system is and how it is set up is essential to doing any adjustments/tuning.

Consider running "Hardinfo" from Ubuntu Software Center and sharing that information.

[http://help.ubuntu.com/community/HardInfo]("http://help.ubuntu.com/community/HardInfo") :guitar:

---

### Post by MickSulley on 2011-10-28
I had never heard of 'hardinfo' before, a really good tool!

Here is the output.

```
Computer
Summary
Computer
Processor	4x Intel(R) Core(TM) i3 CPU 540 @ 3.07GHz
Memory	7994MB (812MB used)
Operating System	Ubuntu 11.10
User Name	myth (Myth)
Date/Time	Fri 28 Oct 2011 09:41:39 BST
Display
Resolution	1360x768 pixels
OpenGL Renderer	Unknown
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA Intel
Input Devices
Power Button	
Power Button	
AT Translated Set 2 keyboard	
HDA Intel HDMI/DP,pcm	3=
HDA Intel HDMI/DP,pcm	3=
ImExPS/2 Generic Explorer Mouse	
IR-receiver inside an USB DVB receiver	
Printers
No printers found	
SCSI Disks
ATA WDC WD20EADS-00R	
HL-DT-ST DVDRAM GH22NS50	
Operating System
Version
Kernel	Linux 3.0.0-12-generic (x86_64)
Compiled	#20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011
C Library	Unknown
Default C Compiler	GNU C Compiler version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
Distribution	Ubuntu 11.10
Current Session
Computer Name	umyth
User Name	myth (Myth)
Home Directory	/home/myth
Desktop Environment	GNOME 2.32.1
Misc
Uptime	3 minutes
Load Average	0.74, 0.52, 0.23
Kernel Modules
Loaded Modules
rfcomm	Bluetooth RFCOMM ver 1.11
bnep	Bluetooth BNEP ver 1.3
bluetooth	Bluetooth Core ver 2.16
tda18271	NXP TDA18271HD analog / digital tuner driver
binfmt_misc	
af9013	Afatech AF9013 DVB-T demodulator driver
snd_hda_codec_hdmi	HDMI HD-audio codec
snd_hda_codec_realtek	Realtek HD-audio codec
psmouse	PS/2 mouse driver
dvb_usb_af9015	Driver for Afatech AF9015 DVB-T
dvb_usb	A library module containing commonly used USB and DVB function USB DVB devices
ppdev	
serio_raw	Raw serio driver
snd_hda_intel	Intel HDA driver
snd_hda_codec	HDA codec core
snd_hwdep	Hardware dependent layer
snd_pcm	Midlevel PCM code for ALSA.
snd_seq_midi	Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	Midlevel RawMidi code for ALSA.
snd_seq_midi_event	MIDI byte <-> sequencer event coder
snd_seq	Advanced Linux Sound Architecture sequencer.
snd_timer	ALSA timer interface
snd_seq_device	ALSA sequencer device management
snd	Advanced Linux Sound Architecture driver for soundcards.
ir_lirc_codec	LIRC IR handler bridge
lirc_dev	LIRC base driver module
ir_sony_decoder	Sony IR protocol decoder
ir_jvc_decoder	JVC IR protocol decoder
soundcore	Core sound module
ir_rc6_decoder	RC6 IR protocol decoder
snd_page_alloc	Memory allocator for ALSA system.
ir_rc5_decoder	RC5(x) IR protocol decoder
ir_nec_decoder	NEC IR protocol decoder
cx23885	v4l2 driver module for cx23885 based TV cards
rc_core	
altera_stapl	altera FPGA kernel module
cx2341x	cx23415/6/8 driver
videobuf_dma_sg	helper module to manage video4linux dma sg buffers
videobuf_dvb	
videobuf_core	helper module to manage video4linux buffers
v4l2_common	misc helper functions for v4l2 device drivers
videodev	Device registrar for Video4Linux drivers v2
v4l2_compat_ioctl32	
altera_ci	altera FPGA CI module
dvb_core	DVB Core Driver
btcx_risc	some code shared by bttv and cx88xx drivers
tveeprom	i2c Hauppauge eeprom decoder driver
parport_pc	PC-style parallel port driver
i915	Intel Graphics
drm_kms_helper	DRM KMS helper
drm	DRM shared core routines
mei	Intel(R) Management Engine Interface
i2c_algo_bit	I2C-Bus bit-banging algorithm
video	ACPI Video Driver
lm75	LM75 driver
it87	IT8705F/IT871xF/IT872xF hardware monitoring driver
hwmon_vid	hwmon-vid driver
coretemp	Intel Core temperature monitor
lp	
parport	
pata_jmicron	SCSI low-level driver for Jmicron PATA ports
e1000e	Intel(R) PRO/1000 Network Driver
Boots
Boots
Fri Oct 28 09:38	33..0.0-12-generic|-
Thu Oct 27 23:31	33..0.0-12-generic|-
Thu Oct 27 23:03	33..0.0-12-generic|-
Wed Oct 26 23:33	33..0.0-12-generic|-
Wed Oct 26 23:05	33..0.0-12-generic|-
Wed Oct 26 19:59	33..0.0-12-generic|-
Wed Oct 26 14:22	33..0.0-12-generic|-
Wed Oct 26 09:14	33..0.0-12-generic|-
Tue Oct 25 22:46	33..0.0-12-generic|-
Tue Oct 25 21:59	33..0.0-12-generic|-
Tue Oct 25 21:16	33..0.0-12-generic|-
Tue Oct 25 20:55	33..0.0-12-generic|-
Tue Oct 25 20:12	22..6.38-11-generi|-
Tue Oct 25 20:07	33..0.0-12-generic|-
Tue Oct 25 19:46	33..0.0-12-generic|-
Tue Oct 25 19:30	33..0.0-12-generic|-
Tue Oct 25 19:15	33..0.0-12-generic|-
Tue Oct 25 09:58	33..0.0-12-generic|-
Tue Oct 25 09:47	33..0.0-12-generic|-
Mon Oct 24 23:36	22..6.38-11-generi|-
Sun Oct 23 00:00	22..6.38-11-generi|-
Sat Oct 22 21:47	22..6.38-11-generi|-
Sat Oct 22 17:02	22..6.38-11-generi|-
Sat Oct 22 14:37	22..6.38-11-generi|-
Sat Oct 22 14:28	22..6.38-11-generi|-
Sat Oct 22 10:11	22..6.38-11-generi|-
Fri Oct 21 23:29	22..6.38-11-generi|-
Fri Oct 21 00:01	22..6.38-11-generi|-
Thu Oct 20 23:43	22..6.38-11-generi|-
Thu Oct 20 23:25	22..6.38-11-generi|-
Thu Oct 20 22:37	22..6.38-11-generi|-
Mon Oct 17 12:07	22..6.38-11-generi|-
Sun Oct 16 22:25	22..6.38-11-generi|-
Sun Oct 16 09:48	22..6.38-11-generi|-
Sun Oct 16 01:05	22..6.38-11-generi|-
Fri Oct 14 21:28	22..6.38-11-generi|-
Fri Oct 14 21:25	22..6.38-11-generi|-
Fri Oct 14 21:19	22..6.38-11-generi|-
Fri Oct 14 21:13	22..6.38-11-generi|-
Fri Oct 14 21:11	22..6.38-11-generi|-
Fri Oct 14 21:10	22..6.38-11-generi|-
Fri Oct 14 20:59	22..6.38-11-generi|-
Fri Oct 14 20:54	22..6.38-11-generi|-
Fri Oct 14 20:48	22..6.38-11-generi|-
Fri Oct 14 17:33	22..6.38-11-generi|-
Fri Oct 14 17:02	22..6.38-11-generi|-
Fri Oct 14 16:21	22..6.38-11-generi|-
Wed Oct 12 22:41	22..6.38-11-generi|-
Wed Oct 12 20:25	22..6.38-11-generi|-
Wed Oct 12 19:29	22..6.38-11-generi|-
Wed Oct 12 19:10	22..6.38-11-generi|-
Languages
Available Languages
en_AG	English language locale for Antigua and Barbuda
en_AG.utf8	English language locale for Antigua and Barbuda
en_AU.utf8	English locale for Australia
en_BW.utf8	English locale for Botswana
en_CA.utf8	English locale for Canada
en_DK.utf8	English locale for Denmark
en_GB.utf8	English locale for Britain
en_HK.utf8	English locale for Hong Kong
en_IE.utf8	English locale for Ireland
en_IN	English language locale for India
en_IN.utf8	English language locale for India
en_NG	English locale for Nigeria
en_NG.utf8	English locale for Nigeria
en_NZ.utf8	English locale for New Zealand
en_PH.utf8	English language locale for Philippines
en_SG.utf8	English language locale for Singapore
en_US.utf8	English locale for the USA
en_ZA.utf8	English locale for South Africa
en_ZM	English locale for Zambia
en_ZM.utf8	English locale for Zambia
en_ZW.utf8	English locale for Zimbabwe
zh_CN.utf8	Chinese locale for Peoples Republic of China
zh_SG.utf8	Chinese language locale for Singapore
Filesystems
Mounted File Systems
/dev/sda4	/	95.44 % (11.0 GiB of 240.6 GiB)
udev	/dev	0.00 % (3.8 GiB of 3.8 GiB)
tmpfs	/run	0.05 % (1.5 GiB of 1.5 GiB)
none	/run/lock	0.00 % (5.0 MiB of 5.0 MiB)
none	/run/shm	0.00 % (3.8 GiB of 3.8 GiB)
Display
Display
Resolution	1360x768 pixels
Vendor	The X.Org Foundation
Version	1.10.4
Monitors
Monitor 0	1360x768 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DOUBLE-BUFFER	
DPMS	
DRI2	
GLX	
Generic Event Extension	
GestureExtension	
MIT-SCREEN-SAVER	
MIT-SHM	
RANDR	
RECORD	
RENDER	
SECURITY	
SGI-GLX	
SHAPE	
SYNC	
X-Resource	
XC-MISC	
XFIXES	
XFree86-DGA	
XFree86-VidModeExtension	
XINERAMA	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
XVideo-MotionCompensation	
OpenGL
Vendor	Unknown
Renderer	Unknown
Version	Unknown
Direct Rendering	No
Environment Variables
Environment Variables
USER	myth
LANGUAGE	en_GB:en
COMPIZ_CONFIG_PROFILE	ubuntu
HOME	/home/myth
DESKTOP_SESSION	ubuntu
XDG_SESSION_COOKIE	ba68bc5b4a20538c93e20b4a00000007-1319791111.684674-1430207675
GTK_MODULES	canberra-gtk-module:canberra-gtk-module
XDG_SEAT_PATH	/org/freedesktop/DisplayManager/Seat0
LC_CTYPE	en_GB.UTF-8
UBUNTU_MENUPROXY	libappmenu.so
MANDATORY_PATH	/usr/share/gconf/ubuntu.mandatory.path
DEFAULTS_PATH	/usr/share/gconf/ubuntu.default.path
USERNAME	myth
LC_COLLATE	en_GB.UTF-8
PATH	/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
XDG_SESSION_PATH	/org/freedesktop/DisplayManager/Session0
DISPLAY	:0
LANG	en_GB.UTF-8
XAUTHORITY	/home/myth/.Xauthority
LC_MESSAGES	en_GB.UTF-8
SHELL	/bin/bash
GDMSESSION	ubuntu
PWD	/home/myth
XDG_CONFIG_DIRS	/etc/xdg/xdg-ubuntu:/etc/xdg
XDG_DATA_DIRS	/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/
SSH_AUTH_SOCK	/tmp/keyring-9Cpm89/ssh
SSH_AGENT_PID	1519
DBUS_SESSION_BUS_ADDRESS	unix:abstract=/tmp/dbus-Afja8pihnC,guid=259afc7bdc7fbdc314ce5b4c0000001e
GNOME_DESKTOP_SESSION_ID	this-is-deprecated
SESSION_MANAGER	local/umyth:@/tmp/.ICE-unix/1480,unix/umyth:/tmp/.ICE-unix/1480
XDG_CURRENT_DESKTOP	Unity
GNOME_KEYRING_CONTROL	/tmp/keyring-9Cpm89
GPG_AGENT_INFO	/tmp/keyring-9Cpm89/gpg:0:1
IBUS_ENABLE_SYNC_MODE	1
GIO_LAUNCHED_DESKTOP_FILE	/usr/share/applications/hardinfo.desktop
GIO_LAUNCHED_DESKTOP_FILE_PID	2635
Users
Users
root	root
daemon	daemon
bin	bin
sys	sys
sync	sync
games	games
man	man
lp	lp
mail	mail
news	news
uucp	uucp
proxy	proxy
www-data	www-data
backup	backup
list	Mailing List Manager
irc	ircd
gnats	Gnats Bug-Reporting System (admin)
nobody	nobody
libuuid	
syslog	
messagebus	
avahi-autoipd	Avahi autoip daemon
avahi	Avahi mDNS daemon
usbmux	usbmux daemon
gdm	Gnome Display Manager
speech-dispatcher	Speech Dispatcher
kernoops	Kernel Oops Tracking Daemon
pulse	PulseAudio daemon
rtkit	RealtimeKit
hplip	HPLIP system user
saned	
mysql	MySQL Server
ntp	
mythtv	
mick2	mick2
myth	Myth
sshd	
lightdm	Light Display Manager
colord	colord colour management daemon
guest-Ol06VE	Guest
Devices
Processor
Processors
Intel(R) Core(TM) i3 CPU 540 @ 3.07GHz	3066.60MHz
Intel(R) Core(TM) i3 CPU 540 @ 3.07GHz	3066.60MHz
Intel(R) Core(TM) i3 CPU 540 @ 3.07GHz	3066.60MHz
Intel(R) Core(TM) i3 CPU 540 @ 3.07GHz	3066.60MHz
Memory
Memory
Total Memory	7994340 kB
Free Memory	6425900 kB
Buffers	70816 kB
Cached	756232 kB
Cached Swap	0 kB
Active	727120 kB
Inactive	611848 kB
Active(anon)	512724 kB
Inactive(anon)	178768 kB
Active(file)	214396 kB
Inactive(file)	433080 kB
Unevictable	0 kB
Mlocked	0 kB
Virtual Memory	16374648 kB
Free Virtual Memory	16374648 kB
Dirty	104 kB
Writeback	0 kB
AnonPages	511512 kB
Mapped	171656 kB
Shmem	179664 kB
Slab	60744 kB
SReclaimable	39360 kB
SUnreclaim	21384 kB
KernelStack	3016 kB
PageTables	23060 kB
NFS_Unstable	0 kB
Bounce	0 kB
WritebackTmp	0 kB
CommitLimit	20371816 kB
Committed_AS	2521840 kB
VmallocTotal	34359738367 kB
VmallocUsed	399248 kB
VmallocChunk	34359335716 kB
HardwareCorrupted	0 kB
AnonHugePages	0 kB
HugePages_Total	0
HugePages_Free	0
HugePages_Rsvd	0
HugePages_Surp	0
Hugepagesize	2048 kB
DirectMap4k	59072 kB
DirectMap2M	8194048 kB
PCI Devices
PCI Devices
Host bridge	Intel Corporation Core Processor DRAM Controller (rev 18)
PCI bridge	Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) (prog-if 00 [Normal decode])
VGA compatible controller	Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
Communication controller	Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
IDE interface	Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06) (prog-if 85 [Master SecO PriO])
Serial controller	Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06) (prog-if 02 [16550])
Ethernet controller	Intel Corporation 82578DM Gigabit Network Connection (rev 06)
USB Controller	Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
Audio device	Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
PCI bridge	Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
PCI bridge	Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) (prog-if 00 [Normal decode])
USB Controller	Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
PCI bridge	Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
ISA bridge	Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
IDE interface	Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
SMBus	Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
IDE interface	Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
Multimedia video controller	Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
IDE interface	JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
USB Controller	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
USB Controller	VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
Host bridge	Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
Host bridge	Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
Host bridge	Intel Corporation Core Processor QPI Link 0 (rev 05)
Host bridge	Intel Corporation Core Processor QPI Physical 0 (rev 05)
Host bridge	Intel Corporation Core Processor Reserved (rev 05)
Host bridge	Intel Corporation Core Processor Reserved (rev 05)
USB Devices
Printers
Printers
No printers found	
Battery
No batteries
No batteries found on this system	
Sensors
Cooling Fans
fan1	1350RPM
fan2	0RPM
Temperatures
temp1	25.00°C
temp2	25.00°C
temp3	21.00°C
Voltage Values
in0	0.912V
in1	1.568V
in2	3.360V
in3	2.896V
in4	0.192V
in5	3.104V
in6	0.016V
in7	2.976V
in8	3.104V
Input Devices
Input Devices
Power Button	
Power Button	
AT Translated Set 2 keyboard	
HDA Intel HDMI/DP,pcm	3=
HDA Intel HDMI/DP,pcm	3=
ImExPS/2 Generic Explorer Mouse	
IR-receiver inside an USB DVB receiver	
Storage
SCSI Disks
ATA WDC WD20EADS-00R	
HL-DT-ST DVDRAM GH22NS50	
DMI
BIOS
Date	07/23/2010
Vendor	Award Software International, Inc. (www.award-bios.com)
Version	F3
Board
Name	Q57M-S2H
Vendor	Gigabyte Technology Co., Ltd. (www.gigabyte.com.tw)
Resources
I/O Ports
0000-0cf7 	PCI Bus 0000:00
0000-001f 	dma1
0020-0021 	pic1
0040-0043 	timer0
0050-0053 	timer1
0060-0060 	keyboard
0064-0064 	keyboard
0070-0073 	rtc0
0080-008f 	dma page reg
00a0-00a1 	pic2
00c0-00df 	dma2
00f0-00ff 	fpu
0290-029f 	pnp 00:01
0290-0294 	pnp 00:01
0295-0296 	IT8705F/IT871xF/IT872xF hardware monitoring driver
0295-0296 	IT8705F/IT871xF/IT872xF hardware monitoring driver
02f8-02ff 	serial
0378-037a 	parport0
03f8-03ff 	serial
0400-04cf 	pnp 00:0c
0400-0403 	ACPI PM1a_EVT_BLK
0404-0405 	ACPI PM1a_CNT_BLK
0408-040b 	ACPI PM_TMR
0410-0415 	ACPI CPU throttle
0420-042f 	ACPI GPE0_BLK
0450-0450 	ACPI PM2_CNT_BLK
04d0-04d1 	pnp 00:01
04d2-04ff 	pnp 00:0c
0500-051f 	Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
0800-0805 	pnp 00:01
0880-088f 	pnp 00:01
0cf8-0cff 	PCI conf1
0d00-ffff 	PCI Bus 0000:00
1000-1fff 	PCI Bus 0000:02
c000-cfff 	PCI Bus 0000:03
cb00-cb0f 	JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
cb00-cb0f 	SCSI low-level driver for Jmicron PATA ports
cc00-cc03 	JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
cc00-cc03 	SCSI low-level driver for Jmicron PATA ports
cd00-cd07 	JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
cd00-cd07 	SCSI low-level driver for Jmicron PATA ports
ce00-ce03 	JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
ce00-ce03 	SCSI low-level driver for Jmicron PATA ports
cf00-cf07 	JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
cf00-cf07 	SCSI low-level driver for Jmicron PATA ports
d000-dfff 	PCI Bus 0000:04
df00-df1f 	VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
df00-df1f 	uhci_hcd
eb00-eb0f 	Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
eb00-eb0f 	ata_piix
ec00-ec0f 	Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
ec00-ec0f 	ata_piix
ed00-ed03 	Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
ed00-ed03 	ata_piix
ee00-ee07 	Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
ee00-ee07 	ata_piix
ef00-ef03 	Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
ef00-ef03 	ata_piix
f000-f007 	Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
f000-f007 	ata_piix
f200-f20f 	Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
f200-f20f 	ata_piix
f300-f30f 	Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
f300-f30f 	ata_piix
f400-f403 	Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
f400-f403 	ata_piix
f500-f507 	Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
f500-f507 	ata_piix
f600-f603 	Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
f600-f603 	ata_piix
f700-f707 	Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
f700-f707 	ata_piix
f800-f81f 	Intel Corporation 82578DM Gigabit Network Connection (rev 06)
f900-f907 	Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06) (prog-if 02 [16550])
f900-f907 	serial
fa00-fa0f 	Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06) (prog-if 85 [Master SecO PriO])
fa00-fa0f 	ata_generic
fb00-fb03 	Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06) (prog-if 85 [Master SecO PriO])
fb00-fb03 	ata_generic
fc00-fc07 	Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06) (prog-if 85 [Master SecO PriO])
fc00-fc07 	ata_generic
fd00-fd03 	Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06) (prog-if 85 [Master SecO PriO])
fd00-fd03 	ata_generic
fe00-fe07 	Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06) (prog-if 85 [Master SecO PriO])
fe00-fe07 	ata_generic
ff00-ff07 	Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
Memory
00000000-0000ffff 	reserved
00010000-0009f7ff 	System RAM
0009f800-0009ffff 	reserved
000a0000-000bffff 	PCI Bus 0000:00
000c0000-000dffff 	PCI Bus 0000:00
000c0000-000c7fff 	Video ROM
000ce400-000cffff 	pnp 00:0e
000e0000-000effff 	pnp 00:0e
000f0000-000fffff 	reserved
000f0000-000fffff 	System ROM
00100000-d7baffff 	System RAM
01000000-015f613e 	Kernel code
015f613f-01aba17f 	Kernel data
01bb9000-01d0bfff 	Kernel bss
d7bb0000-d7be2fff 	ACPI Non-volatile Storage
d7be3000-d7beffff 	ACPI Tables
d7bf0000-d7bfffff 	reserved
d7c00000-febfffff 	PCI Bus 0000:00
d7c00000-d7dfffff 	PCI Bus 0000:03
d7e00000-d7ffffff 	PCI Bus 0000:02
d8000000-d81fffff 	PCI Bus 0000:02
d8200000-d8200fff 	Intel Flush Page
e0000000-efffffff 	Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
f4000000-f7ffffff 	PCI MMCONFIG 0000 [bus 00-3f]
f4000000-f7ffffff 	reserved
f4000000-f7ffffff 	pnp 00:0d
fb400000-fb7fffff 	Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
fba00000-fbbfffff 	PCI Bus 0000:01
fba00000-fbbfffff 	Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
fba00000-fbbfffff 	cx23885[0]
fbd00000-fbdfffff 	PCI Bus 0000:03
fbe00000-fbefffff 	PCI Bus 0000:04
fbeff000-fbeff0ff 	VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
fbeff000-fbeff0ff 	ehci_hcd
fbfc0000-fbfdffff 	Intel Corporation 82578DM Gigabit Network Connection (rev 06)
fbfc0000-fbfdffff 	Intel(R) PRO/1000 Network Driver
fbff4000-fbff7fff 	Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
fbff4000-fbff7fff 	ICH HD audio
fbffa000-fbffa0ff 	Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
fbffb000-fbffb3ff 	Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
fbffb000-fbffb3ff 	ehci_hcd
fbffc000-fbffc3ff 	Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
fbffc000-fbffc3ff 	ehci_hcd
fbffd000-fbffdfff 	Intel Corporation 82578DM Gigabit Network Connection (rev 06)
fbffd000-fbffdfff 	Intel(R) PRO/1000 Network Driver
fbffe000-fbffefff 	Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06) (prog-if 02 [16550])
fbfff000-fbfff00f 	Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
fbfff000-fbfff00f 	Intel(R) Management Engine Interface
fec00000-ffffffff 	reserved
fec00000-fec003ff 	IOAPIC 0
fed00000-fed003ff 	HPET 0
fed10000-fed1dfff 	pnp 00:0e
fed40000-fed44fff 	PCI Bus 0000:00
fee00000-fee00fff 	Local APIC
fee00000-fee00fff 	pnp 00:0e
ffb00000-ffb7ffff 	pnp 00:0e
fff00000-ffffffff 	pnp 00:0e
100000000-1fbffffff 	System RAM
1fc000000-1ffffffff 	reserved
200000000-21fffffff 	System RAM
DMA
4	cascade
Network
Interfaces
Network Interfaces
lo	0.00MiB	0.00MiB	127.0.0.1
eth0	0.31MiB	0.06MiB	192.168.0.10
IP Connections
Connections
0.0.0.0:6543	LISTEN	0.0.0.0:*	tcp
0.0.0.0:6544	LISTEN	0.0.0.0:*	tcp
0.0.0.0:80	LISTEN	0.0.0.0:*	tcp
0.0.0.0:22	LISTEN	0.0.0.0:*	tcp
127.0.0.1:631	LISTEN	0.0.0.0:*	tcp
0.0.0.0:17500		0.0.0.0:*	udp
127.0.0.1:3306	LISTEN	0.0.0.0:*	tcp
192.168.0.10:47689	ESTABLISHED	199.47.216.147:80	tcp
192.168.0.10:53828	CLOSE_WAIT	199.47.216.172:443	tcp
192.168.0.10:56453	ESTABLISHED	199.47.216.174:443	tcp
:::22	LISTEN	:::*	tcp6
::1:631	LISTEN	:::*	tcp6
0.0.0.0:68		0.0.0.0:*	udp
192.168.0.10:123		0.0.0.0:*	udp
127.0.0.1:123		0.0.0.0:*	udp
0.0.0.0:123		0.0.0.0:*	udp
0.0.0.0:17500		0.0.0.0:*	udp
0.0.0.0:5353		0.0.0.0:*	udp
0.0.0.0:52130		0.0.0.0:*	udp
:::53269		:::*	udp6
::1:123		:::*	udp6
fe80::1e6f:65ff:fe3:123		:::*	udp6
:::123		:::*	udp6
:::5353		:::*	udp6
Routing Table
IP routing table
0.0.0.0 / 192.168.0.1	0.0.0.0	UG	eth0
169.254.0.0 / 0.0.0.0	255.255.0.0	U	eth0
192.168.0.0 / 0.0.0.0	255.255.255.0	U	eth0
ARP Table
ARP Table
192.168.0.1	00:22:6b:fb:8f:3e	eth0
DNS Servers
Name servers
62.24.202.5	
62.24.243.2	
Statistics
IP
459	Total packets received
2	With invalid addresses
0	Incoming packets discarded
0	Incoming packets discarded
457	Incoming packets delivered
348	Requests sent out
ICMP
0	ICMP messages failed
0	ICMP messages failed
0	ICMP messages failed
0	ICMP messages failed
TCP
10	Active connections openings
2	Resets sent
2	Resets sent
0	Bad segments received.
2	Resets sent
275	Segments received
201	Segments send out
0	Bad segments received.
0	Bad segments received.
2	Resets sent
UDP
173	Packets received
0	Packet receive errors
0	Packet receive errors
144	Packets sent
UDPLITE
TCPEXT
5	TCP sockets finished time wait in fast timer
7	Delayed acks sent
200	Packet headers predicted
32	Acknowledgments not containing data payload received
6	Predicted acknowledgments
IPEXT
Shared Directories
SAMBA
NFS
Benchmarks
CPU Blowfish
CPU Blowfish
This Machine	3067 MHz	10.719
Intel(R) Celeron(R) M processor 1.50GHz	(null)	26.1876862
PowerPC 740/750 (280.00MHz)	(null)	172.816713
CPU CryptoHash
CPU CryptoHash
This Machine	3067 MHz	124.242
CPU Fibonacci
CPU Fibonacci
This Machine	3067 MHz	6.512
Intel(R) Celeron(R) M processor 1.50GHz	(null)	8.1375674
PowerPC 740/750 (280.00MHz)	(null)	58.07682
CPU N-Queens
CPU N-Queens
This Machine	3067 MHz	14.336
FPU FFT
FPU FFT
This Machine	3067 MHz	3.420
FPU Raytracing
FPU Raytracing
This Machine	3067 MHz	9.092
Intel(R) Celeron(R) M processor 1.50GHz	(null)	40.8816714
PowerPC 740/750 (280.00MHz)	(null)	161.312647

```

---

### Post by keepitsimpleengr on 2011-10-29
Your hardware is fine.

You should try increasing the ring buffer to maximum.

You set an appropriate video playback profile:
[http://www.mythtv.org/wiki/Playback_profiles#High_Quality_default_settings]("http://www.mythtv.org/wiki/Playback_profiles#High_Quality_default_settings")

Are you using High Quality transcoder?



Are you using the HDMI output?

---

### Post by MickSulley on 2011-10-29
Thanks for your suggestions - 

Increased the ring buffer to maximum.  That has made a big difference, much better!

You set an appropriate video playback profile: - That was already set to High Quality

Are you using High Quality transcoder?  Now to show my ignorance - what does that mean?

Are you using the HDMI output? - Yes

Many thanks for your help
Mick

---

### Post by keepitsimpleengr on 2011-10-29
> **MickSulley said:**
> Are you using High Quality transcoder?  Now to show my ignorance - what does that mean?

Under *TV - Setting - Gerenal - General(Jobs)*

Default decoder > High Quality

Also *TV - Settings - Playback - General Playback( 1 / 8 )*

Try enabling real-time threads ~ but read the comment on this.

Make sure your monitor's resolution is set properly. This should happen automagically.

Have fun...:popcorn:

---

### Post by nickrout on 2011-10-29
> **keepitsimpleengr said:**
> Under *TV - Setting - Gerenal - General(Jobs)*

Default decoder > High QualitySurely this will only make a difference if you are transcoding - and in general, why would you?> 

Also *TV - Settings - Playback - General Playback( 1 / 8 )*

Try enabling real-time threads ~ but read the comment on this.

Make sure your monitor's resolution is set properly. This should happen automagically.

Have fun...:popcorn:

---

