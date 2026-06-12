---
title: "Upgrade to 10.10 broke my DVR"
date: 2010-10-11
forum: Mythbuntu
---

### Post by gilson585 on 2010-10-11
Idk what happened. Basicly it worked before the upgrade and now it doesn't. Most everything looks fine except when I go to view livetv. It loads the analog encoders video fine, no audio, though previous recordings have audio. OK switch to digital tuner, locks up mythfrontend most of the time with a black screen, killall mythfrontend.real back to where I started. I have no way of backing up all the recordings on this machine so a fresh install is out of the question. I'm sure it's sumthing simple, it alwasy is in the end. Also get odd messages in the terminal when dpkg runs which didn't happen before and I'm sure is related.
```
gilson585@Daves-MediaPC:~$ sudo dpkg-reconfigure mythbuntu-repos       
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Configuring mythbuntu-repos
```
Oh and another note, before the upgrade began installing stuff it tossed a message about libc6 and the screensaver saying it needed to be restarted or something which it walked itself through in the following steps prior to installing packages.

If it's any help this is what I get if I launch the frontend from the CMD line and try to watch livetv.

```
gilson585@Daves-MediaPC:~$ mythfrontend
2010-10-11 17:02:22.495 mythfrontend version: branches/release-0-23-fixes [26732] www.mythtv.org
2010-10-11 17:02:22.496 Using runtime prefix = /usr
2010-10-11 17:02:22.496 Using configuration directory = /home/gilson585/.mythtv
2010-10-11 17:02:23.252 Empty LocalHostName.
2010-10-11 17:02:23.252 Using localhost value of Daves-MediaPC
2010-10-11 17:02:23.271 New DB connection, total: 1
2010-10-11 17:02:23.276 Connected to database 'mythconverg' at host: localhost
2010-10-11 17:02:23.277 Closing DB connection named 'DBManager0'
2010-10-11 17:02:23.297 ScreenSaverX11Private: XScreenSaver support enabled
2010-10-11 17:02:23.299 DPMS is disabled.
2010-10-11 17:02:23.301 Primary screen: 0.
2010-10-11 17:02:23.302 Connected to database 'mythconverg' at host: localhost
2010-10-11 17:02:23.304 Using screen 0, 1024x768 at 0,0
2010-10-11 17:02:23.328 Desktop video mode: 1024x768 60.006 Hz
2010-10-11 17:02:23.333 MythUI Image Cache size set to 20971520 bytes
2010-10-11 17:02:23.344 Enabled verbose msgs:  important general
2010-10-11 17:02:23.347 Primary screen: 0.
2010-10-11 17:02:23.348 Using screen 0, 1024x768 at 0,0
2010-10-11 17:02:23.349 Using theme base resolution of 1280x720
2010-10-11 17:02:23.355 LIRC: Successfully initialized '/dev/lircd' using '/home/gilson585/.mythtv/lircrc' config
2010-10-11 17:02:23.355 JoystickMenuThread Error: Joystick disabled - Failed to read /home/gilson585/.mythtv/joystickmenurc
2010-10-11 17:02:23.394 Using Frameless Window
2010-10-11 17:02:23.394 Using Full Screen Window
2010-10-11 17:02:23.513 Using the OpenGL painter
2010-10-11 17:02:23.624 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/Mythbuntu/base.xml'
2010-10-11 17:02:23.628 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default-wide/base.xml'
2010-10-11 17:02:23.634 XMLParseBase: Loaded base theme from '/usr/share/mythtv/themes/default/base.xml'
2010-10-11 17:02:23.634 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-10-11 17:02:23.638 Current MythTV Schema Version (DBSchemaVer): 1254
2010-10-11 17:02:23.896 Registering Internal as a media playback plugin.
2010-10-11 17:02:23.906 Cannot load language en_us for module mytharchive
2010-10-11 17:02:23.932 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2010-10-11 17:02:23.951 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.951 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.952 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.952 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.952 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.953 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.953 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.953 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.953 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.954 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.954 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.954 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.955 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.955 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.955 MediaMonitorUnix::AddDevice() - empty device path.
2010-10-11 17:02:23.955 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2010-10-11 17:02:23.958 Cannot load language en_us for module mythmusic
2010-10-11 17:02:23.963 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2010-10-11 17:02:23.976 Cannot load language en_us for module mythvideo
2010-10-11 17:02:23.977 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2010-10-11 17:02:24.018 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//mainmenu.xml
2010-10-11 17:02:24.019 Found mainmenu.xml for theme 'Mythbuntu'
2010-10-11 17:02:24.248 Using NV NPOT texture extension
2010-10-11 17:02:24.307 MythContext: Connecting to backend server: 192.168.1.4:6543 (try 1 of 1)
2010-10-11 17:02:24.307 Using protocol version 23056
2010-10-11 17:02:34.028 TV: Attempting to change from None to WatchingLiveTV
2010-10-11 17:02:34.028 MythContext: Connecting to backend server: 192.168.1.4:6543 (try 1 of 1)
2010-10-11 17:02:34.029 Using protocol version 23056
2010-10-11 17:02:34.124 Spawning LiveTV Recorder -- begin
2010-10-11 17:02:34.627 Spawning LiveTV Recorder -- end
2010-10-11 17:02:34.630 ProgramInfo(): Updated pathname '':'' -> '3030_20101011170234.nuv'
2010-10-11 17:02:34.635 We have a playbackURL(/var/lib/mythtv/livetv/3030_20101011170234.nuv) & cardtype(V4L)
2010-10-11 17:02:34.636 We have a RingBuffer
[ac3 @ 0x29a64f0]No channel layout specified. The encoder will guess the layout, but it might be incorrect.
2010-10-11 17:02:34.802 Opening audio device 'spdif'. ch 2(2) sr 44100 (reenc 0)
2010-10-11 17:02:34.802 Opening ALSA audio device 'spdif'.
[ac3 @ 0x467a0a0]No channel layout specified. The encoder will guess the layout, but it might be incorrect.
2010-10-11 17:02:34.900 Opening audio device 'spdif'. ch 2(2) sr 44100 (reenc 0)
2010-10-11 17:02:34.900 Opening ALSA audio device 'spdif'.
[ac3 @ 0x467a060]No channel layout specified. The encoder will guess the layout, but it might be incorrect.
2010-10-11 17:02:35.117 Opening audio device 'spdif'. ch 2(2) sr 44100 (reenc 0)
2010-10-11 17:02:35.118 Opening ALSA audio device 'spdif'.
2010-10-11 17:02:35.261 ProgramInfo(): Updated pathname '':'' -> '3030_20101011170234.nuv'
2010-10-11 17:02:35.307 VDPAU: Created 2 output surfaces.
2010-10-11 17:02:35.307 VDPAU: Version 1
2010-10-11 17:02:35.307 VDPAU: Information NVIDIA VDPAU Driver Shared Library  260.19.06  Mon Sep 13 04:58:44 PDT 2010
2010-10-11 17:02:35.308 VDPAU: Created VDPAU render device 1024x768
2010-10-11 17:02:35.315 ProgramInfo(): Updated pathname '':'' -> '3030_20101011170234.nuv'
2010-10-11 17:02:35.337 OSD Theme Dimensions W: 1280 H: 720
2010-10-11 17:02:35.370 ProgramInfo(): Updated pathname '':'' -> '3030_20101011170234.nuv'
2010-10-11 17:02:35.371 New DB connection, total: 2
2010-10-11 17:02:35.371 Connected to database 'mythconverg' at host: localhost
2010-10-11 17:02:35.408 TV: Changing from None to WatchingLiveTV
2010-10-11 17:02:35.408 TV: State is LiveTV & mctx == ctx
2010-10-11 17:02:35.409 TV: UpdateOSDInput done
2010-10-11 17:02:35.409 TV: UpdateLCD done
2010-10-11 17:02:35.409 TV: ITVRestart done
2010-10-11 17:02:35.410 Realtime priority would require SUID as root.
2010-10-11 17:02:35.438 OpenGLVideoSync()
2010-10-11 17:02:35.470 Video timing method: SGI OpenGL
2010-10-11 17:02:35.501 VDPAU: Added 2 output surfaces (total 4, max 4)
2010-10-11 17:02:42.628 ~OpenGLVideoSync() -- closing opengl vsync
2010-10-11 17:02:43.118 MythContext: Connecting to backend server: 192.168.1.4:6543 (try 1 of 1)
2010-10-11 17:02:43.119 Using protocol version 23056
2010-10-11 17:02:43.464 ProgramInfo(): Updated pathname '':'' -> '6081_20101011170243.mpg'
2010-10-11 17:02:43.489 NVP(0): Disabling Audio, params(-1,2,44100)
2010-10-11 17:02:43.540 ProgramInfo(): Updated pathname '':'' -> '6081_20101011170243.mpg'
2010-10-11 17:02:43.541 VDPAU: Created 2 output surfaces.
2010-10-11 17:02:43.542 VDPAU: Created VDPAU render device 1024x768
2010-10-11 17:02:43.558 OSD Theme Dimensions W: 1280 H: 720
2010-10-11 17:02:43.592 ProgramInfo(): Updated pathname '':'' -> '6081_20101011170243.mpg'
2010-10-11 17:02:43.613 ProgramInfo(): Updated pathname '':'' -> '6081_20101011170243.mpg'
2010-10-11 17:02:43.614 LiveTVChain(live-Daves-MediaPC-2010-10-11T17:02:33): SwitchTo() not switching to current
2010-10-11 17:02:43.614 Realtime priority would require SUID as root.
2010-10-11 17:02:43.645 OpenGLVideoSync()
2010-10-11 17:02:43.696 Video timing method: SGI OpenGL
2010-10-11 17:02:43.772 VDPAU: Added 2 output surfaces (total 4, max 4)
Terminated
```

---

### Post by gilson585 on 2010-10-11
Ok now when I try removing the tuners in backend-setup and re add them I get as far as scanning for channels on the digital tuner and it locks up. What is going on here? pls help me

---

### Post by gilson585 on 2010-10-11
Ok this is BS I did a fresh install and it's still not working what is going on here.

---

### Post by David Grigor on 2010-10-12
What tuner are you using ? 

I'm having a problem with the HVR-1250 Tuner. It works great in 10.04 with myth .23.1.  Fresh install of 10.10 the tuner also hangs in scan when it gets to the first channel to lock.  Revert back to 10.04 and it works fine. Also tried to install mythv .24 trunk and same issue. 

I reverted back to 10.04 and restored my database for now until something comes up on the forums. I may try to install 10.10 intp a seperate partition so I can troubleshoot.

---

### Post by gilson585 on 2010-10-12
Yes I have 2 HVR-1250's and a WinTV Go. I have had the same experience as you plus my WinTV Go card has video but no audio. I've tried debugging myth for the devs but I don't get any useful Information due to the hang and no crash. Me thinks it has todo with the kernel but I could be wrong.

---

### Post by gilson585 on 2010-10-12
Ok I found some info in syslog
```
Oct 12 10:51:03 Daves-DVR kernel: [  100.685426] BUG: unable to handle kernel paging request at 0000010100000028
Oct 12 10:51:03 Daves-DVR kernel: [  100.685438] IP: [<ffffffffa0069563>] videobuf_dma_unmap+0x43/0xb0 [videobuf_dma_sg]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685456] PGD 0 
Oct 12 10:51:03 Daves-DVR kernel: [  100.685462] Oops: 0000 [#1] SMP 
Oct 12 10:51:03 Daves-DVR kernel: [  100.685469] last sysfs file: /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
Oct 12 10:51:03 Daves-DVR kernel: [  100.685476] CPU 1 
Oct 12 10:51:03 Daves-DVR kernel: [  100.685479] Modules linked in: mceusb ir_lirc_codec lirc_dev snd_hda_codec_realtek mt2131 s5h1409 tuner_simple tuner_types tuner tvaudio tda7432 msp3400 nvidia(P) snd_hda_intel ir_sony_decoder snd_bt87x snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ir_jvc_decoder snd_timer snd_seq_device ir_rc6_decoder cx23885 cx2341x ir_rc5_decoder bttv videobuf_dvb ir_nec_decoder v4l2_common videodev v4l1_compat v4l2_compat_ioctl32 snd asus_atk0110 i2c_algo_bit videobuf_dma_sg ir_common ir_core edac_core dvb_core videobuf_core btcx_risc soundcore psmouse k10temp lp edac_mce_amd tveeprom snd_page_alloc serio_raw parport i2c_piix4 usb_storage usbhid hid r8169 mii ahci libahci pata_atiixp
Oct 12 10:51:03 Daves-DVR kernel: [  100.685574] 
Oct 12 10:51:03 Daves-DVR kernel: [  100.685583] Pid: 2127, comm: cx23885[0] dvb Tainted: P            2.6.35-22-generic #34-Ubuntu M4A78 PLUS/System Product Name
Oct 12 10:51:03 Daves-DVR kernel: [  100.685590] RIP: 0010:[<ffffffffa0069563>]  [<ffffffffa0069563>] videobuf_dma_unmap+0x43/0xb0 [videobuf_dma_sg]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685605] RSP: 0018:ffff880128687dc0  EFLAGS: 00010246
Oct 12 10:51:03 Daves-DVR kernel: [  100.685611] RAX: 0000010100000000 RBX: ffff88012ae23ef8 RCX: 0000000000000002
Oct 12 10:51:03 Daves-DVR kernel: [  100.685616] RDX: 0000000000000006 RSI: ffffc900110f5000 RDI: ffff880129c080a0
Oct 12 10:51:03 Daves-DVR kernel: [  100.685622] RBP: ffff880128687dd0 R08: 0000000000000000 R09: 00000000ffffffff
Oct 12 10:51:03 Daves-DVR kernel: [  100.685627] R10: 00000000ffffffff R11: 0000000000000001 R12: ffff880115ba5828
Oct 12 10:51:03 Daves-DVR kernel: [  100.685633] R13: ffff88012ae23ef8 R14: ffff880115ba5828 R15: ffff88012b1e2dc0
Oct 12 10:51:03 Daves-DVR kernel: [  100.685639] FS:  00007f0b8ea8b840(0000) GS:ffff880001e40000(0000) knlGS:0000000000000000
Oct 12 10:51:03 Daves-DVR kernel: [  100.685646] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 12 10:51:03 Daves-DVR kernel: [  100.685651] CR2: 0000010100000028 CR3: 000000011374c000 CR4: 00000000000006e0
Oct 12 10:51:03 Daves-DVR kernel: [  100.685657] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 12 10:51:03 Daves-DVR kernel: [  100.685663] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 12 10:51:03 Daves-DVR kernel: [  100.685670] Process cx23885[0] dvb (pid: 2127, threadinfo ffff880128686000, task ffff88012b1e2dc0)
Oct 12 10:51:03 Daves-DVR kernel: [  100.685675] Stack:
Oct 12 10:51:03 Daves-DVR kernel: [  100.685678]  ffff88012ae23ef8 ffff88012ae23e00 ffff880128687e00 ffffffffa0c9412a
Oct 12 10:51:03 Daves-DVR kernel: [  100.685687] <0> ffff880128687df0 ffff880115ba5828 ffff880115ba5828 ffff880115ba5928
Oct 12 10:51:03 Daves-DVR kernel: [  100.685696] <0> ffff880128687e10 ffffffffa0c95d5e ffff880128687e40 ffffffffa0108457
Oct 12 10:51:03 Daves-DVR kernel: [  100.685706] Call Trace:
Oct 12 10:51:03 Daves-DVR kernel: [  100.685727]  [<ffffffffa0c9412a>] cx23885_free_buffer+0x5a/0xa0 [cx23885]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685745]  [<ffffffffa0c95d5e>] dvb_buf_release+0xe/0x10 [cx23885]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685759]  [<ffffffffa0108457>] videobuf_queue_cancel+0xf7/0x120 [videobuf_core]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685772]  [<ffffffffa01084e7>] __videobuf_read_stop+0x17/0x70 [videobuf_core]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685784]  [<ffffffffa010855e>] videobuf_read_stop+0x1e/0x30 [videobuf_core]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685794]  [<ffffffffa00fd8c8>] videobuf_dvb_thread+0x168/0x1e0 [videobuf_dvb]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685805]  [<ffffffffa00fd760>] ? videobuf_dvb_thread+0x0/0x1e0 [videobuf_dvb]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685815]  [<ffffffff8107f0b6>] kthread+0x96/0xa0
Oct 12 10:51:03 Daves-DVR kernel: [  100.685825]  [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
Oct 12 10:51:03 Daves-DVR kernel: [  100.685833]  [<ffffffff8107f020>] ? kthread+0x0/0xa0
Oct 12 10:51:03 Daves-DVR kernel: [  100.685840]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x0/0x10
Oct 12 10:51:03 Daves-DVR kernel: [  100.685844] Code: 19 75 6e 8b 53 28 85 d2 74 4b 48 8b 7f 28 8b 4b 30 48 8b 73 20 48 85 ff 74 4e 48 8b 87 e8 01 00 00 48 85 c0 74 42 83 f9 02 77 5d <48> 8b 40 28 48 85 c0 74 0a 45 31 c0 90 ff d0 48 8b 73 20 48 89 
Oct 12 10:51:03 Daves-DVR kernel: [  100.685911] RIP  [<ffffffffa0069563>] videobuf_dma_unmap+0x43/0xb0 [videobuf_dma_sg]
Oct 12 10:51:03 Daves-DVR kernel: [  100.685923]  RSP <ffff880128687dc0>
Oct 12 10:51:03 Daves-DVR kernel: [  100.685926] CR2: 0000010100000028
Oct 12 10:51:03 Daves-DVR kernel: [  100.685932] ---[ end trace 5a49d3fff27e282f ]---
```
Anything else I can do to help figure this out?

---

### Post by gilson585 on 2010-10-12
If this affects you please visit this bug report and mark "this affects me"
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659348](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659348)

---

### Post by David Grigor on 2010-10-12
I'll reinstall 10.10 side by side with my 10.04 installation and see if I get the similiar log output.

---

### Post by gilson585 on 2010-10-12
Thanks I'd like to put some heat on this bug so it gets assigned and fixed.

---

### Post by marksoccer on 2010-10-12
This bug also affects me.  I tried to say that on the bug, but I didn't see any link called "this affects me", so I subscribed instead.  I can confirm that I had no problems in 10.04 with my HVR-1250 tuner running mythtv 0.23.1.  I did a fresh install of 10.10 and everytime I try to scan channels in mythtv, the scan freezes and the tuner is locked.  I cannot even attempt to scan again until I restart (I assume there is a way to reset the tuner... but I don't know how).  I also tried scanning with w_scan, and the scan looked fine until I got messages stating that there was a VCT and PAT timeout.  At that point, I could no longer stop the process with ctrl-C or ctrl-Z.

---

### Post by gilson585 on 2010-10-12
You must be logged into launchpad and click the green link above the large bold title that says it affects you.

---

### Post by marksoccer on 2010-10-12
Ah, I got it.  I think there is a bug in chrome when I hit that button, it brought me further down the page.

---

### Post by bbruenfl on 2010-10-14
I have the same problem as above.  HVR-1250 broken by upgrade to 10.10 (amd64).  

My current build is pretty new, so it wasn't a huge thrash for me to do a clean install of 10.04 to get functionality but if anyone has a good set of instructions for downgrading to 10.04, could you post a link in this thread?  It might save some folks some gray hairs.

If more logs are needed I'm happy to oblige.

---

### Post by gilson585 on 2010-10-15
I wish I did have some sort of straight forward directions for going back to 10.04. I myself had a hell of a time trying to do so. 

I Made a backup of mythconverge sql database (put in safe place like thumbdrive)

Then I started with booting to 10.04 live cd w/o installing

Then moved everything I wanted to keep out of /var/lib/mythtv to a new folder I named /mythtv-0, then deleted all other directories and files on drive

Reboot, install 10.04 (DO NOT FORMAT DRIVE), reboot, install other packages and plugins I wanted.

Move stuff back into /var/lib/mythtv and apply proper permissions.
```
cd /var/lib
sudo chmod 775 mythtv -R
sudo chown mythtv:mythtv mythtv -R
```
Restore mythconverge sql database, this was prolly the hardest and most frustrating part as the process is poorly documented. I'm truly sorry if you can't make it work this is the best I've got.

GL to all

---

### Post by David Grigor on 2010-10-15
No Magic here either. 

I keep all my recordings on a separate partition from / and swap. Made sure I save a few important files like asound.conf, resolve.conf, fstab, network/interfaces backed up the database as described on [http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading) > clean install keeping old database.

Reinstalled 10.04 ( use the advanced and chose my old / and swap locations, making sure I don't touch the partition with my recordings and saved files ), put back the important config files, restored the db and was back up and running again pretty quickly. Then later went back and installed the additional programs I like to use, mkvmerge, gnome system monitor, k9copy, and handbrake. 

Next major upgrade, I'm going to install into a seperate partition and run both OS versions until I know all hardware works then lastly restore my db into the new version.

---

### Post by bbruenfl on 2010-10-15
> Next major upgrade, I'm going to install into a seperate partition and  run both OS versions until I know all hardware works then lastly restore  my db into the new version.

I seem to remember making the same pledge the last time I installed a major update.  Maybe I'll remember next time.

---

### Post by Veerappan on 2010-10-16
Hi all,

I ran into the same issue on upgrading to 10.10 (HVR-1250 not working, Mythfrontend hangs on starting to watch live TV).

I tried a few things, but after poking around with the v4l-dvb mercurial source tree, fixing the compile there, and then attempting to get things to work and failing, I just decided to try a newer kernel from the ubuntu mainline PPA:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/)

I installed the kernel from there (grab and install all 3 debs). After a reboot, I was able to start watching live TV.

Hope it helps.

--Aaron

---

### Post by bbruenfl on 2010-10-16
I had a little free time this morning and I worked out a path for reverting from 10.10 to 10.04.  I have to go to work but I wanted to throw out the broad strokes in case anybody ran into this over the weekend.

First, I would suggest installing mythbuntu autobuilds and set it to 0.23.1 PPA.  Then run an update and upgrade through apt-get or synaptic

Second, go to the Myth Control Center and create a backup using the built in feature.  Place it somewhere safe (i.e. thumbdrive).

Third, if you don't have your recordings, videos, etc on separate partitions mounted via fstab to the proper locations in /var/lib/mythtv/ now would be a good time to set it up.  Once you have that set up grab your fstab file and stick it on your thumbdrive.

Fourth, run a fresh install of 10.04 (Ubuntu or Mythbuntu) if you don't have one already.  I strongly suggest using a second hard drive or a side-by-side install.  If you used Ubuntu, you'll need to install Mythtv.  Install the autobuilds repository and set it up for 0.23.1 PPA.  Run an update and upgrade.

At this point, I ran through a basic setup to make sure all my hardware was working correctly but I suppose it isn't strictly necessary.

Fifth, use the directions for restoring your database under 
**[Clean Install of Mythbuntu, keeping old database]("http://www.mythbuntu.org/upgrading#")**


on [http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)

Might as well be safe and backup the database from your new os in case you run into trouble.

Grab the backup off of your thumbdrive and unpack the archive.  Buried in there you'll find a mysql file.  Put it in the /var/lib/mythtv/db_backups (?) and use it for the restore part of the instructions.

That should be it.  Start your local front end and off you go.  If you have remote frontends remember that the MySQL db password will be different.

I'll edit this when I have some time to make it a bit more clear but hopefully this will help.  

One caveat:  This will only work if the database version (might be 26732, I can't remember and I'm not near the system to check) is the same for both installations.

Cheers.

---

### Post by Hugolp on 2010-10-18
> **Veerappan said:**
> Hi all,

I ran into the same issue on upgrading to 10.10 (HVR-1250 not working, Mythfrontend hangs on starting to watch live TV).

I tried a few things, but after poking around with the v4l-dvb mercurial source tree, fixing the compile there, and then attempting to get things to work and failing, I just decided to try a newer kernel from the ubuntu mainline PPA:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/)

I installed the kernel from there (grab and install all 3 debs). After a reboot, I was able to start watching live TV.

Hope it helps.

--Aaron

I did this. Still the same problem.

EDIT: It is working. I can watch live tv now, but the problem is that the kernel crashes after a while, with some error relating the dvb card.

---

### Post by David Grigor on 2010-11-02
Just a quick update: I've been running the kernel update that Verrappan mentioned for a while now along with Mythtv .24 with no stability issues.  Tuner card has been just fine with both recording and livetv.   I did have issue when first applied that fix where video playback didn't like the default cpu+ setting but once I changed to vdpau, livetv was fine. 

It has been stable long enough now that I have completely removed by 10.04 binaries and only running 10.10. 

Good Luck to everyone with the tuner issue and thanks to Veerappan for posting his results.

---

### Post by Failbot on 2010-11-14
> **Veerappan said:**
> Hi all,

I ran into the same issue on upgrading to 10.10 (HVR-1250 not working, Mythfrontend hangs on starting to watch live TV).

I tried a few things, but after poking around with the v4l-dvb mercurial source tree, fixing the compile there, and then attempting to get things to work and failing, I just decided to try a newer kernel from the ubuntu mainline PPA:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc8-maverick/)

I installed the kernel from there (grab and install all 3 debs). After a reboot, I was able to start watching live TV.

Hope it helps.

--Aaron

Thanks! Initial tests seem good - I can tune to channels. Haven't tested long term stability, but this is definitely an improvement.
(Had Ubuntu 10.10 AMD_64, Leadtek DVR3200H)

---

### Post by gilson585 on 2010-11-16
Thx for all the feedback but I'm sticking with 10.04 till this is officially resolved.

---

### Post by David Grigor on 2010-11-16
Still no issues here either. Been about 3 weeks now with 10.10 & Myth .24. All the functionality that I use has worked perfectly.

---

