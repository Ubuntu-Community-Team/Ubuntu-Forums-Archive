---
title: "[SOLVED] New mythbutu install issue"
date: 2008-05-20
forum: Mythbuntu
---

### Post by nrune on 2008-05-20
Well mythbuntu has installed beautifully and runs well I have a major problem however. 

amd 64 
eVGA 6200LE 256MB PCI-E Nvidia e-GeForce with TV/out
Asus A8R-MX/S
1 ddr2 ram
hauppauge pvr150

I have the video to go to svideo out and works really well until I click watch live tv. Then I get a black screen, and no key pressed will bring any kind of menu or response to the screen.  When I unplug the svideo cable from the 6200le nvidia card nothing changes on the screen. I plugged in a monitor to the vga port and it did not have any signal so I am not sure where the problem is. 

Dmesg is rather disturbing with a **segfault**.

```
[   36.847206] Linux video capture interface: v2.00
[   37.037473] nvidia: module license 'NVIDIA' taints kernel.
[   37.395885] ivtv:  Start initialization, version 1.1.0
[   37.395993] ivtv0: Initializing card #0
[   37.395996] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   37.416114] ACPI: PCI Interrupt 0000:02:11.0[A] -> GSI 18 (level, low) -> IRQ 18
[   37.463809] lirc_dev: IR Remote Control driver registered, at major 61 
[   37.516309] tveeprom 0-0050: Hauppauge model 26552, rev F0A3, serial# 8919043
[   37.516313] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   37.516315] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   37.516317] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   37.516319] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   37.516321] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   37.516324] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   37.592643] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   37.592661] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   37.592663] tuner 0-0043: type set to tda9887
[   37.595634] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   37.610677] 
[   37.610680] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[   37.610682] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   37.623223] input: Generic X-Box pad as /devices/pci0000:00/0000:00:1c.1/usb2/2-2/2-2:1.0/input/input6
[   37.633474] usbcore: registered new interface driver xpad
[   37.633480] /build/buildd/linux-2.6.24/drivers/input/joystick/xpad.c: X-Box pad driver:v0.0.6
[   37.657394] lirc_atiusb[3]: inbound endpoint not found
[   37.657412] usbcore: registered new interface driver lirc_atiusb
[   37.679686] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   37.693733] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   37.701513] tuner-simple 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   37.701516] tuner 0-0061: type set to Philips NTSC MK3 (F
[   37.701840] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   37.701853] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   37.701866] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   37.701878] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   37.701894] ivtv0: Registered device radio0 for encoder radio
[   37.701897] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   37.701909] ivtv:  End initialization
[   37.702642] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   37.702649] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   37.702807] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   37.704126] ACPI: PCI Interrupt 0000:00:1d.0[C] -> GSI 22 (level, low) -> IRQ 22
[   39.236037] lp0: using parport0 (interrupt-driven).
[   39.505527] Adding 3012148k swap on /dev/hda5.  Priority:-1 extents:1 across:3012148k
[   40.212194] EXT3 FS on hda1, internal journal
[   41.779041] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.206111] No dock devices found.
[   44.662879] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[   44.662913] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   44.662915] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   44.662916] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   44.662918] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   46.558045] NET: Registered protocol family 10
[   46.558539] lo: Disabled Privacy Extensions
[   53.937103] Marking TSC unstable due to cpufreq changes
[   53.941010] Time: acpi_pm clocksource has been installed.
[   54.104490] Clocksource tsc unstable (delta = -201134949 ns)
[   54.721620] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   54.811145] ivtv0: Encoder revision: 0x02060039
[   57.518190] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   58.855213] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.482803] uli526x: eth0 NIC Link is Down
[   60.803931] lirc_serial: auto-detected active high receiver
[   60.803935] lirc_dev: lirc_register_plugin: sample_rate: 0
[   66.728796] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
[   66.729538] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   68.936412] NET: Registered protocol family 17
[   76.456445] eth0: no IPv6 routers present
[  202.483629] mythfrontend.re[6522]: segfault at 9eeba0 rip 9eeba0 rsp 43ba6d88 error 15
[  341.211396] mythtv-setup.re[6878]: segfault at 128 rip 7f3a728336fa rsp 432ef470 error 4
[  756.398138] mythfrontend.re[7459]: segfault at 9fccb0 rip 9fccb0 rsp 43e3dd88 error 15
[  842.462728] mythfrontend.re[7752]: segfault at 9e5780 rip 9e5780 rsp 446e5d88 error 15
```
 
Help?

Additional info:
Glxgears and glxinfo looks great direct render etc.  Don't think the problem is with the  6200le I feel like the video is going elsewhere besides svideo, but I am not sure where or how.  Any ideas?

Mike

---

### Post by nrune on 2008-05-21
Here is mythbackend.log
> Starting up as the master server.
2008-05-21 06:15:26.705 New DB connection, total: 3
2008-05-21 06:15:26.711 Connected to database 'mythconverg' at host: localhost
2008-05-21 06:15:27.123 Channel(/dev/video0) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2008-05-21 06:15:27.150 New DB scheduler connection
2008-05-21 06:15:27.162 Connected to database 'mythconverg' at host: localhost
2008-05-21 06:15:27.227 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-05-21 06:15:27.228 Main::Registering HttpStatus Extension
2008-05-21 06:15:27.228 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-05-21 06:15:27.229 Enabled verbose msgs:  important general
2008-05-21 06:15:27.273 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-21 06:15:30.201 Reschedule requested for id -1.
2008-05-21 06:15:31.204 Scheduled 0 items in 1.0 = 0.96 match + 0.04 place
2008-05-21 06:15:31.210 Seem to be woken up by USER
2008-05-21 06:16:47.175 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-21 06:16:47.182 Expiring 0 MBytes for 1100 @ Wed May 21 06:00:00 2008 => Pay-Per-View Previews
2008-05-21 06:16:47.183 Expiring 0 MBytes for 1100 @ Wed May 21 06:00:00 2008 => Pay-Per-View Previews
2008-05-21 06:17:16.367 MainServer::HandleAnnounce Monitor
2008-05-21 06:17:16.374 adding: mythtv as a client (events: 0)
2008-05-21 06:17:16.375 MainServer::HandleAnnounce Monitor
2008-05-21 06:17:16.376 adding: mythtv as a client (events: 1)
2008-05-21 06:17:16.392 MainServer::HandleAnnounce Playback
2008-05-21 06:17:16.398 adding: mythtv as a client (events: 0)
2008-05-21 06:17:16.406 TVRec(1): Changing from None to WatchingLiveTV
2008-05-21 06:17:16.416 TVRec(1): HW Tuner: 1->1
2008-05-21 06:17:16.868 Channel(/dev/video0) Warning: You have not set an external channel changing
			script for a composite or s-video input. Channel changing will do nothing.
2008-05-21 06:17:17.047 New DB connection, total: 4
2008-05-21 06:17:17.050 Connected to database 'mythconverg' at host: localhost
2008-05-21 06:17:18.452 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-05-21 06:17:18.455 NVR(/dev/video0) Error: Unknown audio codec
2008-05-21 06:17:18.495 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-05-21 06:17:18.509 NVR(/dev/video0): Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-05-21 06:17:58.502 TVRec(1): Changing from WatchingLiveTV to None
2008-05-21 06:17:58.512 Finished recording Pay-Per-View Previews: channel 1100
2008-05-21 06:17:58.527 MythSocket(8b93f0:-1): writeStringList: Error, socket went unconnected.

Here is mythfrontend.log
> Starting mythfrontend.real..
2008-05-21 06:15:46.743 New DB connection, total: 2
2008-05-21 06:15:46.744 Connected to database 'mythconverg' at host: localhost
2008-05-21 06:15:46.746 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-05-21 06:15:46.746 Enabled verbose msgs:  important general
2008-05-21 06:15:47.459 Unable to parse themeinfo.xml for glass-wide
2008-05-21 06:15:47.459 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-21 06:15:49.107 Unable to parse themeinfo.xml for glass-wide
2008-05-21 06:15:49.107 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-21 06:15:50.058 Primary screen 0.
2008-05-21 06:15:50.059 Using screen 0, 1600x1200 at 0,0
2008-05-21 06:15:50.061 Switching to square mode (ProjectGrayhem)
2008-05-21 06:15:50.170 Using the Qt painter
2008-05-21 06:15:50.171 lirc init success using configuration file: /home/nrune/.mythtv/lircrc
2008-05-21 06:15:50.172 JoystickMenuClient Error: Joystick disabled - Failed to read /home/nrune/.mythtv/joystickmenurc
2008-05-21 06:15:51.762 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768
2008-05-21 06:15:51.790 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/conflicts
2008-05-21 06:15:51.794 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/keyboard
2008-05-21 06:15:51.817 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/music
2008-05-21 06:15:51.848 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/priorities
2008-05-21 06:15:51.850 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/programfind
2008-05-21 06:15:51.850 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/programguide
2008-05-21 06:15:51.860 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/recordoptions
2008-05-21 06:15:51.869 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/shared
2008-05-21 06:15:51.880 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/status
2008-05-21 06:15:51.886 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/title
2008-05-21 06:15:51.896 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/tvplayback
2008-05-21 06:15:51.906 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/type
2008-05-21 06:15:51.907 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/video
2008-05-21 06:15:51.908 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/watermark
2008-05-21 06:15:51.987 Removing stale cache dir: /home/nrune/.mythtv/themecache/ProjectGrayhem.1024.768/weather
2008-05-21 06:17:10.454 Specified base font 'medium' does not exist for font clock
2008-05-21 06:17:10.455 Specified base font 'medium' does not exist for font small
2008-05-21 06:17:10.455 Specified base font 'medium' does not exist for font medium
2008-05-21 06:17:10.455 Specified base font 'medium' does not exist for font large
2008-05-21 06:17:10.456 Loading from: /usr/share/mythtv/themes/ProjectGrayhem/base.xml
2008-05-21 06:17:10.613 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-21 06:17:10.681 Registering Internal as a media playback plugin.
2008-05-21 06:17:10.890 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-21 06:17:11.469 Failed to run 'cdrecord --scanbus'
2008-05-21 06:17:11.477 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-21 06:17:11.491 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-21 06:17:11.525 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.138:5060 NAT address 192.168.1.138
SIP: Cannot register; proxy, username or password not set
2008-05-21 06:17:16.357 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-21 06:17:16.367 Using protocol version 40
2008-05-21 06:17:16.391 TV: Attempting to change from None to WatchingLiveTV
2008-05-21 06:17:16.391 Using protocol version 40
sh: rrrr: not found
2008-05-21 06:17:18.505 DPMS Deactivated 
2008-05-21 06:17:58.496 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-05-21 06:17:58.498 TV Error: LiveTV not successfully started
2008-05-21 06:17:58.550 TV: Deleting TV Chain in destructor
2008-05-21 06:17:58.552 DPMS Reactivated

---

### Post by superm1 on 2008-05-21
Sounds like you grabbed the wrong tuner type.  You should go back to mythtv-setup and pick the right one. MPEG-2 Encoders (PVR-XXX)

---

### Post by nrune on 2008-05-21
Duh, now working thanks!

Mike

---

