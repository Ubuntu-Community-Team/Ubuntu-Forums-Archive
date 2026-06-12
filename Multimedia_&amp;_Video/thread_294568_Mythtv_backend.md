---
title: "Mythtv backend"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by pacificdrums on 2006-11-06
When I try to start mythtv backend with this command
```
 sudo /etc/init.d/mythtv-backend start
```
I get the error
```
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

```
I also tried to start it with ```
mythbackend
```
and got
```
2006-11-06 17:24:12.705 Using runtime prefix = /usr
2006-11-06 17:24:12.789 New DB connection, total: 1
2006-11-06 17:24:12.798 Connected to database 'mythconverg' at host: localhost
2006-11-06 17:24:12.806 Current Schema Version: 1160
Starting up as the master server.
2006-11-06 17:24:12.869 New DB connection, total: 2
2006-11-06 17:24:12.870 Connected to database 'mythconverg' at host: localhost
2006-11-06 17:24:12.874 EITHelper: localtime offset -8:00:00 
2006-11-06 17:24:12.884 New DB connection, total: 3
2006-11-06 17:24:12.885 Connected to database 'mythconverg' at host: localhost
2006-11-06 17:24:12.965 New DB scheduler connection
2006-11-06 17:24:12.966 Connected to database 'mythconverg' at host: localhost
2006-11-06 17:24:12.973 Main::Starting HttpServer
QServerSocket: failed to bind or listen to the socket
2006-11-06 17:24:12.979 Main::HttpServer Create Error
2006-11-06 17:24:12.980 Main::Registering HttpStatus Extension
2006-11-06 17:24:12.990 mythbackend version: 0.20.20060828-3 www.mythtv.org
2006-11-06 17:24:13.043 Enabled verbose msgs:  important general
2006-11-06 17:24:13.043 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2006-11-06 17:24:13.045 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
QServerSocket: failed to bind or listen to the socket
2006-11-06 17:24:13.049 Failed to bind port 6543. Exiting.
```

I cannot figure out why I am getting this.](*,)  Any help would be greatly apritiated!

---

### Post by halfhalo on 2006-11-06
have you set up mythbackend byrunning mythtv-setup?

---

### Post by pacificdrums on 2006-11-06
> **halfhalo said:**
> have you set up mythbackend byrunning mythtv-setup?

Yes, sorry I could have been more specific. I have run setup and the backend is on the same computer as the frontend.The ip is set to 127.0.0.1, I just left those settings default. If you need any more info let me know. Thx

---

### Post by cheuschober on 2006-11-07
pacificdrums, I'm running into the exact same problem.

Anyone know what we might be missing?

---

### Post by superm1 on 2006-11-07
Guys,

This error message is normal when launching mythtv-backend from the init script (QT management error).  You should have the process actually running.  If you are getting an error about not being able to bind to the port in the logs however, that is because you have the backend running.  You will need to issue a 

```
sudo /etc/init.d/mythtv-backend restart
```

in this case.  If for some reason it still doesn't die, manually kill the process.

---

### Post by pacificdrums on 2006-11-07
> **superm1 said:**
> Guys,

This error message is normal when launching mythtv-backend from the init script (QT management error).  You should have the process actually running.  If you are getting an error about not being able to bind to the port in the logs however, that is because you have the backend running.  You will need to issue a 

```
sudo /etc/init.d/mythtv-backend restart
```

in this case.  If for some reason it still doesn't die, manually kill the process.

Yea I tried that too and iv tried restarting the computer then running the start command.
This is what I get with the restart command
```
shaun@shaun-linux:~$ sudo /etc/init.d/mythtv-backend restart
Password:
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
shaun@shaun-linux:~$ 


```
just this morning I got the backend to run in daemon mode with this
```
mythbackend -d
```
Now I can run the frontend and and I can watch tv and it all seems to work. :-k

---

### Post by superm1 on 2006-11-07
The init scripts *should* work though.  When you tried with the init script, did it at least log t o/var/log/mythtv/mythbackend.log why it didn't start?

---

### Post by pacificdrums on 2006-11-07
> **superm1 said:**
> The init scripts *should* work though.  When you tried with the init script, did it at least log t o/var/log/mythtv/mythbackend.log why it didn't start?

Here is the log

```
2006-11-07 10:29:40.763 Using runtime prefix = /usr
2006-11-07 10:29:40.853 New DB connection, total: 1
2006-11-07 10:29:40.863 Connected to database 'mythconverg' at host: localhost
2006-11-07 10:29:40.871 Current Schema Version: 1160
Starting up as the master server.
2006-11-07 10:29:40.884 New DB connection, total: 2
2006-11-07 10:29:40.886 Connected to database 'mythconverg' at host: localhost
2006-11-07 10:29:40.890 EITHelper: localtime offset -8:00:00 
2006-11-07 10:29:40.901 New DB connection, total: 3
2006-11-07 10:29:40.903 Connected to database 'mythconverg' at host: localhost
2006-11-07 10:29:40.954 New DB scheduler connection
2006-11-07 10:29:40.955 Connected to database 'mythconverg' at host: localhost
2006-11-07 10:29:40.963 Main::Starting HttpServer
2006-11-07 10:29:40.970 Main::Registering HttpStatus Extension
2006-11-07 10:29:40.981 mythbackend version: 0.20.20060828-3 www.mythtv.org
2006-11-07 10:29:40.990 Enabled verbose msgs:  important general
2006-11-07 10:29:40.991 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2006-11-07 10:29:40.993 AutoExpire: Required Free Space: 2.1 GB w/freq: 10 min
2006-11-07 10:29:42.967 Reschedule requested for id -1.
2006-11-07 10:29:43.084 Scheduled 0 items in 0.1 = 0.10 match + 0.02 place
2006-11-07 10:29:43.089 Seem to be woken up by USER

```
I do not see anything but maybe you will. Like I said it works when I run it in daemon mode. :confused:

---

### Post by superm1 on 2006-11-07
That log looks pristine to me.... perhaps is there an older /var/log/mythtv/mythbackend.0.log or something to that nature in the folder too?  The init script will rename these and create new ones as they grow.

---

### Post by pacificdrums on 2006-11-07
> **superm1 said:**
> That log looks pristine to me.... perhaps is there an older /var/log/mythtv/mythbackend.0.log or something to that nature in the folder too?  The init script will rename these and create new ones as they grow.

No thats the only one. The only error I get is the one in the command line

```
shaun@shaun-linux:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackend.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
shaun@shaun-linux:~$ 

```

---

### Post by lonce on 2006-11-08
are you logged in as the Myth user.  When you install mythtv it creates a myth user.  check out my site in my sig, the support site.  Go to the how to's and there is a step by step about putting myth on edgy.  Works every time.

---

### Post by superm1 on 2006-11-08
> **pacificdrums said:**
> No thats the only one. The only error I get is the one in the command line

```
shaun@shaun-linux:~$ sudo /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackend.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
shaun@shaun-linux:~$ 

```
Your absolutely sure that the backend isn't running after this?  Ignoring that error, the backend should still at least spawn....

---

### Post by pacificdrums on 2006-11-08
OK, yes I think the backend is running because I have to stop it before I can try to start it again. And thanks lonce I will try that.

---

### Post by superm1 on 2006-11-08
pacificdrums,

Sorry that we haven't come to the conclusion of whats going on here.  If you determine what the cause/solution is, please post back and I'll add it to the HOWTO on the edgy wiki/fix the package.

---

### Post by pacificdrums on 2006-11-10
When I log in as the mythtv user it seems to work fine. I just followed lonce's guide to get the mythtv user working correctly. 

Many thanks to everyone who helped!!! I really like Ubuntu and without these forums I would probably not be able to use it. :D

---

### Post by lonce on 2006-11-10
I aim to please.

We have forums over at our site where we answer linux and mythtv specific questions.  Check em out.  The support link in my sig.

---

### Post by superm1 on 2006-11-10
> **pacificdrums said:**
> When I log in as the mythtv user it seems to work fine. I just followed lonce's guide to get the mythtv user working correctly. 

Many thanks to everyone who helped!!! I really like Ubuntu and without these forums I would probably not be able to use it. :D
Could you clarify what exactly you did here that resolved the issue for you?  A majority of people that have used the official guide haven't had any troubles, but a few have come across very similar problems.

---

### Post by bla2000 on 2006-11-11
I've been following your guide and I get the same error but I also have problems watching live tv.  It shows a blank screen and quits.   I can see that there is a password set in the mythconverg database for mythtv but how to I logon as mythtv user?  Where is the password specified? 

Do I need to set my own password? 

sudo passwd mythtv

btw, I have 2 capture cards, a pvr 150 and 250.  I also had mythtv running for the past year based on kubuntu the hoary version.  I followed an old guide from [http://www.abarbaccia.com/](http://www.abarbaccia.com/).  

Thanks.

---

### Post by bla2000 on 2006-11-11
Here is a section of my mythbackend.log:

```

Starting up as the master server.
2006-11-10 23:53:26.504 New DB connection, total: 2
2006-11-10 23:53:26.505 Connected to database 'mythconverg' at host: localhost
2006-11-10 23:53:26.511 EITHelper: localtime offset -8:00:00
2006-11-10 23:53:26.618 New DB connection, total: 3
2006-11-10 23:53:26.619 Connected to database 'mythconverg' at host: localhost
2006-11-10 23:53:26.688 EITHelper: localtime offset -8:00:00
2006-11-10 23:53:26.943 New DB scheduler connection
2006-11-10 23:53:26.944 Connected to database 'mythconverg' at host: localhost
2006-11-10 23:53:27.161 Main::Starting HttpServer
2006-11-10 23:53:27.172 Main::Registering HttpStatus Extension
2006-11-10 23:53:27.291 mythbackend version: 0.20.20060828-3 www.mythtv.org
2006-11-10 23:53:27.301 Enabled verbose msgs:  important general
2006-11-10 23:53:27.303 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2006-11-10 23:53:27.391 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2006-11-10 23:53:29.106 Reschedule requested for id -1.
2006-11-10 23:53:30.821 Scheduled 199 items in 1.7 = 0.42 match + 1.30 place
2006-11-10 23:53:30.930 Recording starts soon, AUTO-Startup assumed
2006-11-10 23:53:53.062 MainServer::HandleAnnounce Monitor
2006-11-10 23:53:53.068 adding: ubuntu1 as a client (events: 0)
2006-11-10 23:53:53.069 MainServer::HandleAnnounce Monitor
2006-11-10 23:53:53.070 adding: ubuntu1 as a client (events: 1)
2006-11-10 23:53:53.083 MainServer::HandleAnnounce Playback
2006-11-10 23:53:53.083 adding: ubuntu1 as a client (events: 0)
2006-11-10 23:53:53.099 TVRec(1): Changing from None to WatchingLiveTV
2006-11-10 23:53:53.105 TVRec(1): HW Tuner: 1->1
2006-11-10 23:53:53.365 Unknown video codec
2006-11-10 23:53:53.371 Please go into the TV Settings, Recording Profiles and2006-11-10 23:55:10.336 setup the four 'Software Encoders' profiles.
2006-11-10 23:55:10.336 Assuming RTjpeg for now.
2006-11-10 23:55:10.337 NVR: Error, unknown audio codec
2006-11-10 23:55:10.368 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2006-11-10 23:55:50.383 TVRec(1): Changing from WatchingLiveTV to None
2006-11-10 23:55:50.472 Finished recording TV Guide: channel 1012
2006-11-10 23:57:36.120 Using runtime prefix = /usr
2006-11-10 23:57:36.418 New DB connection, total: 1
2006-11-10 23:57:36.434 Connected to database 'mythconverg' at host: localhost
2006-11-10 23:57:36.461 Current Schema Version: 1160
2006-11-10 23:53:53.372 setup the four 'Software Encoders' profiles.
2006-11-10 23:53:53.372 Assuming RTjpeg for now.
2006-11-10 23:53:53.373 NVR: Error, unknown audio codec
2006-11-10 23:53:53.413 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2006-11-10 23:54:33.428 TVRec(1): Changing from WatchingLiveTV to None
2006-11-10 23:54:33.480 Finished recording TV Guide: channel 1012
2006-11-10 23:54:47.076 Expiring TV Guide from Fri Nov 10 23:00:00 2006, 0 MBytes, forced expire (LiveTV recording)
2006-11-10 23:54:57.739 Reloading backend settings
2006-11-10 23:55:06.282 Reschedule requested for id 0.
2006-11-10 23:55:07.848 Scheduled 199 items in 1.6 = 0.00 match + 1.56 place
2006-11-10 23:55:10.137 MainServer::HandleAnnounce Playback
2006-11-10 23:55:10.140 adding: ubuntu1 as a client (events: 0)
2006-11-10 23:55:10.143 TVRec(1): Changing from None to WatchingLiveTV
2006-11-10 23:55:10.145 TVRec(1): HW Tuner: 1->1
2006-11-10 23:55:10.334 Unknown video codec
2006-11-10 23:55:10.335 Please go into the TV Settings, Recording Profiles and

```

---

### Post by bla2000 on 2006-11-11
dmesg info:

```

[17179588.072000] ivtv:  ==================== START INIT IVTV ====================
[17179588.072000] ivtv:  version 0.7.0 (tagged release) loading
[17179588.072000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REG PARM gcc-4.1
[17179588.072000] ivtv:  In case of problems please include the debug info between
[17179588.072000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179588.072000] ivtv:  any module options, when mailing the ivtv-users mailing list.
[17179588.072000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179588.072000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179588.072000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179588.120000] tveeprom 0-0050: Hauppauge model 26032, rev C199, serial# 8004 186
[17179588.120000] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[17179588.120000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179588.120000] tveeprom 0-0050: audio processor is CX25841 (idx 35)
[17179588.120000] tveeprom 0-0050: decoder processor is CX25841 (idx 28)
[17179588.120000] tveeprom 0-0050: has no radio, has IR remote
[17179588.264000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179588.520000] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[17179588.744000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.824000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.044000] irda_init()
[17179589.044000] NET: Registered protocol family 23
[17179592.456000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17179592.616000] input: PC Speaker as /class/input/input1
[17179592.896000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179592.920000] parport: PnPBIOS parport detected.
[17179592.920000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179592.960000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179593.092000] Floppy drive(s): fd0 is 1.44M
[17179593.112000] FDC 0 is a post-1991 82077
[17179593.636000] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input2
[17179593.672000] ts: Compaq touchscreen protocol output
[17179593.712000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179593.932000] ivtv0: Encoder revision: 0x02050032
[17179593.932000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179593.932000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179593.932000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179593.932000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179593.932000] tuner 0-0061: type set to 50 (TCL 2002N)
[17179594.052000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17179594.052000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.052000] agpgart: Detected VIA KM400/KM400A chipset
[17179594.060000] agpgart: AGP aperture is 64M @ 0xd8000000
[17179594.068000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179594.068000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 193
[17179594.068000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179594.068000] eth0: VIA Rhine II at 0x1e800, 00:11:2f:f3:c8:4e, IRQ 193.
[17179594.068000] eth0: MII PHY found at address 1, status 0x786d advertising 05 e1 Link 45e1.
[17179594.072000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179594.072000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179594.072000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 9
[17179594.072000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179594.188000] nvidia: module license 'NVIDIA' taints kernel.
[17179594.252000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179594.588000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.592000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.600000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.608000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.636000] ivtv:  ======================  NEXT CARD  ======================
[17179594.636000] ivtv1: Autodetected Hauppauge WinTV PVR-250 card (cx23416 based)
[17179594.636000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179594.636000] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[17179594.692000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[17179594.956000] tveeprom 2-0050: Hauppauge model 32062, rev C182, serial# 2908907
[17179594.956000] tveeprom 2-0050: tuner model is LG TAPC H791F (idx 82, type 39)
[17179594.956000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[17179594.956000] tveeprom 2-0050: audio processor is MSP3445 (idx 12)
[17179594.956000] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[17179594.956000] tveeprom 2-0050: has no radio, has IR remote
[17179595.096000] saa7115 2-0021: saa7115 found @ 0x42 (ivtv i2c driver #1)
[17179595.272000] msp3400 2-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #1)
[17179595.272000] msp3400 2-0040: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[17179595.344000] NET: Registered protocol family 17
[17179595.924000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179596.144000] ivtv1: Encoder revision: 0x02050032
[17179596.144000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179596.144000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179596.144000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179596.144000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179596.144000] tuner 2-0061: type set to 39 (LG NTSC (newer TAPC series))
[17179596.212000] ivtv1: Initialized Hauppauge WinTV PVR-250, card #1
[17179596.212000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 217 [17179596.212000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179596.520000] ivtv:  ====================  END INIT IVTV  ====================
[17179596.704000] NET: Registered protocol family 10
[17179596.704000] lo: Disabled Privacy Extensions
[17179596.704000] IPv6 over IPv4 tunneling driver
[17179596.744000] lp0: using parport0 (interrupt-driven).
[17179596.776000] lirc_dev: IR Remote Control driver registered, at major 61
[17179596.780000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179596.844000] bttv: driver version 0.9.16 loaded
[17179596.844000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179596.924000] cx2388x v4l2 driver version 0.0.5 loaded
[17179596.952000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179596.952000] lirc_dev: lirc_register_plugin: sample_rate: 10
[17179597.012000] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[17179597.012000] lirc_dev: lirc_register_plugin: sample_rate: 10
[17179597.116000] Adding 1534168k swap on /dev/disk/by-uuid/59e776ea-8158-4644-87ad-6f313e26199b.  Priority:-1 extents:1 across:1534168k
[17179597.192000] EXT3 FS on hda1, internal journal
[17179597.492000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179597.492000] SGI XFS Quota Management subsystem
[17179597.580000] XFS mounting filesystem hda7
[17179597.676000] Ending clean XFS mount for filesystem: hda7
[17179597.704000] XFS mounting filesystem hdb1
[17179597.796000] Ending clean XFS mount for filesystem: hdb1
[17179597.820000] kjournald starting.  Commit interval 5 seconds
[17179597.828000] EXT3 FS on hda6, internal journal
[17179597.828000] EXT3-fs: mounted filesystem with ordered data mode.
[17179603.920000] ACPI: Power Button (FF) [PWRF]
[17179603.920000] ACPI: Power Button (CM) [PWRB]
[17179603.920000] ACPI: Sleep Button (CM) [SLPB]
[17179604.084000] ibm_acpi: ec object not found
[17179604.124000] pcc_acpi: loading...
[17179606.688000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179606.688000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179606.688000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179607.636000] eth0: no IPv6 routers present
[17179610.872000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179610.872000] apm: overridden by ACPI.
[17179618.380000] Bluetooth: Core ver 2.8
[17179618.380000] NET: Registered protocol family 31
[17179618.380000] Bluetooth: HCI device and connection manager initialized
[17179618.380000] Bluetooth: HCI socket layer initialized
[17179618.532000] Bluetooth: L2CAP ver 2.8
[17179618.532000] Bluetooth: L2CAP socket layer initialized
[17179618.564000] Bluetooth: RFCOMM socket layer initialized
[17179618.564000] Bluetooth: RFCOMM TTY layer initialized
[17179618.564000] Bluetooth: RFCOMM ver 1.7

```

---

### Post by superm1 on 2006-11-11
> **bla2000 said:**
> I've been following your guide and I get the same error but I also have problems watching live tv.  It shows a blank screen and quits.   I can see that there is a password set in the mythconverg database for mythtv but how to I logon as mythtv user?  Where is the password specified? 

Do I need to set my own password? 

sudo passwd mythtv

btw, I have 2 capture cards, a pvr 150 and 250.  I also had mythtv running for the past year based on kubuntu the hoary version.  I followed an old guide from [http://www.abarbaccia.com/](http://www.abarbaccia.com/).  

Thanks.

bla2000,
It appears that there are troubles getting your card to tune stations.  Can you verify its functionality outside of mythtv?  Use tvtime or mplayer to test it.

---

### Post by bla2000 on 2006-11-11
I did:

```

ivtv-tune -c 11 /dev/video0
cat /dev/vidoe0 > /tmp/test1.mpg
```

This is the result:

[http://static.flickr.com/101/294818556_9925915f63_o.png]("http://static.flickr.com/101/294818556_9925915f63_o.png")

Do you know how I can fix the audio codec problem since it may also fix ivtv?  Thanks.

btw, at 1st I thought that my audio wasn't working when playing a cd but I had it muted so it seems to be fine otherwise.

---

### Post by bla2000 on 2006-11-11
I found this thread about enabling FFmpeg and that fixes the problem with mplayer.  I can view the clip that I recorded /dev/video0.

[http://ubuntuforums.org/showthread.php?p=1679043]("http://ubuntuforums.org/showthread.php?p=1679043")

---

### Post by bla2000 on 2006-11-11
I tested my 2nd vidoe device:

```

ivtv-tune -c 3 -d /dev/video1
/dev/video1: 61.250 MHz  (Signal Detected)
cat /dev/video1 > /tmp/test2.mpg

```

Audio and video work fine when I open in mplayer.

[http://static.flickr.com/117/294857332_eafa88ed9a_o.png]("http://static.flickr.com/117/294857332_eafa88ed9a_o.png")

In summary when open the .mpg file in mplayer:

/dev/video0 = pvr150 = works
/dev/video1 = pvr250 = works

---

### Post by bla2000 on 2006-11-11
My most recent mythvbackend.log file after starting the backend, logging in a mythtv user, and trying to watch tv or a recording:

```

Starting up as the master server.
2006-11-11 17:37:46.778 New DB connection, total: 2
2006-11-11 17:37:46.809 Connected to database 'mythconverg' at host: 192.168.1.11
2006-11-11 17:37:46.815 EITHelper: localtime offset -8:00:00 
2006-11-11 17:37:46.825 New DB connection, total: 3
2006-11-11 17:37:46.854 Connected to database 'mythconverg' at host: 192.168.1.11
2006-11-11 17:37:46.922 EITHelper: localtime offset -8:00:00 
2006-11-11 17:37:46.978 New DB scheduler connection
2006-11-11 17:37:47.010 Connected to database 'mythconverg' at host: 192.168.1.11
2006-11-11 17:37:47.014 Main::Starting HttpServer
2006-11-11 17:37:47.033 Main::Registering HttpStatus Extension
2006-11-11 17:37:47.064 mythbackend version: 0.20.20060828-3 www.mythtv.org
2006-11-11 17:37:47.075 Enabled verbose msgs:  important general
2006-11-11 17:37:47.107 AutoExpire: Found 2 recorders w/max rate of 144 MiB/min
2006-11-11 17:37:47.111 AutoExpire: Required Free Space: 3.1 GB w/freq: 10 min
2006-11-11 17:37:49.031 Reschedule requested for id -1.
2006-11-11 17:37:49.953 Scheduled 183 items in 0.9 = 0.48 match + 0.44 place
2006-11-11 17:37:49.961 Seem to be woken up by USER
2006-11-11 17:41:10.524 MainServer::HandleAnnounce Monitor
2006-11-11 17:41:10.584 adding: ubuntu1 as a client (events: 0)
2006-11-11 17:41:10.586 MainServer::HandleAnnounce Monitor
2006-11-11 17:41:10.586 adding: ubuntu1 as a client (events: 1)
2006-11-11 17:41:10.638 MainServer::HandleAnnounce Playback
2006-11-11 17:41:10.800 adding: ubuntu1 as a client (events: 0)
2006-11-11 17:41:10.916 TVRec(1): Changing from None to WatchingLiveTV
2006-11-11 17:41:10.922 TVRec(1): HW Tuner: 1->1
2006-11-11 17:41:11.389 Unknown video codec
2006-11-11 17:41:11.428 Please go into the TV Settings, Recording Profiles and
2006-11-11 17:41:11.429 setup the four 'Software Encoders' profiles.
2006-11-11 17:41:11.429 Assuming RTjpeg for now.
2006-11-11 17:41:11.430 NVR: Error, unknown audio codec
2006-11-11 17:41:11.472 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2006-11-11 17:41:51.558 TVRec(1): Changing from WatchingLiveTV to None
2006-11-11 17:41:51.587 Finished recording The New Canoe: channel 1010

```

Here's dmesg info:

```

[17179588.072000] ivtv:  ==================== START INIT IVTV ====================
[17179588.072000] ivtv:  version 0.7.0 (tagged release) loading
[17179588.072000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179588.072000] ivtv:  In case of problems please include the debug info between
[17179588.072000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179588.072000] ivtv:  any module options, when mailing the ivtv-users mailing list.
[17179588.072000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179588.072000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179588.072000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[17179588.120000] tveeprom 0-0050: Hauppauge model 26032, rev C199, serial# 8004186
[17179588.120000] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[17179588.120000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179588.120000] tveeprom 0-0050: audio processor is CX25841 (idx 35)
[17179588.120000] tveeprom 0-0050: decoder processor is CX25841 (idx 28)
[17179588.120000] tveeprom 0-0050: has no radio, has IR remote
[17179588.264000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179588.520000] cx25840 0-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[17179588.744000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.824000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.044000] irda_init()
[17179589.044000] NET: Registered protocol family 23
[17179592.456000] cx25840 0-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17179592.616000] input: PC Speaker as /class/input/input1
[17179592.896000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179592.920000] parport: PnPBIOS parport detected.
[17179592.920000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179592.960000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179593.092000] Floppy drive(s): fd0 is 1.44M
[17179593.112000] FDC 0 is a post-1991 82077
[17179593.636000] input: ImExPS/2 Logitech Wheel Mouse as /class/input/input2
[17179593.672000] ts: Compaq touchscreen protocol output
[17179593.712000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179593.932000] ivtv0: Encoder revision: 0x02050032
[17179593.932000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179593.932000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179593.932000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179593.932000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179593.932000] tuner 0-0061: type set to 50 (TCL 2002N)
[17179594.052000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[17179594.052000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.052000] agpgart: Detected VIA KM400/KM400A chipset
[17179594.060000] agpgart: AGP aperture is 64M @ 0xd8000000
[17179594.068000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[17179594.068000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 193
[17179594.068000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179594.068000] eth0: VIA Rhine II at 0x1e800, 00:11:2f:f3:c8:4e, IRQ 193.
[17179594.068000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179594.072000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179594.072000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179594.072000] PCI: Via IRQ fixup for 0000:00:11.5, from 10 to 9
[17179594.072000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179594.188000] nvidia: module license 'NVIDIA' taints kernel.
[17179594.252000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179594.588000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.592000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.600000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.608000] codec_read: codec 0 is not valid [0xfe0000]
[17179594.636000] ivtv:  ======================  NEXT CARD  ======================
[17179594.636000] ivtv1: Autodetected Hauppauge WinTV PVR-250 card (cx23416 based)
[17179594.636000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179594.636000] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[17179594.692000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[17179594.956000] tveeprom 2-0050: Hauppauge model 32062, rev C182, serial# 2908907
[17179594.956000] tveeprom 2-0050: tuner model is LG TAPC H791F (idx 82, type 39)
[17179594.956000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[17179594.956000] tveeprom 2-0050: audio processor is MSP3445 (idx 12)
[17179594.956000] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[17179594.956000] tveeprom 2-0050: has no radio, has IR remote
[17179595.096000] saa7115 2-0021: saa7115 found @ 0x42 (ivtv i2c driver #1)
[17179595.272000] msp3400 2-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #1)
[17179595.272000] msp3400 2-0040: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[17179595.344000] NET: Registered protocol family 17
[17179595.924000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179596.144000] ivtv1: Encoder revision: 0x02050032
[17179596.144000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179596.144000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179596.144000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179596.144000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179596.144000] tuner 2-0061: type set to 39 (LG NTSC (newer TAPC series))
[17179596.212000] ivtv1: Initialized Hauppauge WinTV PVR-250, card #1
[17179596.212000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[17179596.212000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179596.520000] ivtv:  ====================  END INIT IVTV  ====================
[17179596.704000] NET: Registered protocol family 10
[17179596.704000] lo: Disabled Privacy Extensions
[17179596.704000] IPv6 over IPv4 tunneling driver
[17179596.744000] lp0: using parport0 (interrupt-driven).
[17179596.776000] lirc_dev: IR Remote Control driver registered, at major 61 
[17179596.780000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179596.844000] bttv: driver version 0.9.16 loaded
[17179596.844000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179596.924000] cx2388x v4l2 driver version 0.0.5 loaded
[17179596.952000] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[17179596.952000] lirc_dev: lirc_register_plugin: sample_rate: 10
[17179597.012000] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[17179597.012000] lirc_dev: lirc_register_plugin: sample_rate: 10
[17179597.116000] Adding 1534168k swap on /dev/disk/by-uuid/59e776ea-8158-4644-87ad-6f313e26199b.  Priority:-1 extents:1 across:1534168k
[17179597.192000] EXT3 FS on hda1, internal journal
[17179597.492000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179597.492000] SGI XFS Quota Management subsystem
[17179597.580000] XFS mounting filesystem hda7
[17179597.676000] Ending clean XFS mount for filesystem: hda7
[17179597.704000] XFS mounting filesystem hdb1
[17179597.796000] Ending clean XFS mount for filesystem: hdb1
[17179597.820000] kjournald starting.  Commit interval 5 seconds
[17179597.828000] EXT3 FS on hda6, internal journal
[17179597.828000] EXT3-fs: mounted filesystem with ordered data mode.
[17179603.920000] ACPI: Power Button (FF) [PWRF]
[17179603.920000] ACPI: Power Button (CM) [PWRB]
[17179603.920000] ACPI: Sleep Button (CM) [SLPB]
[17179604.084000] ibm_acpi: ec object not found
[17179604.124000] pcc_acpi: loading...
[17179606.688000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179606.688000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179606.688000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17179607.636000] eth0: no IPv6 routers present
[17179610.872000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179610.872000] apm: overridden by ACPI.
[17179618.380000] Bluetooth: Core ver 2.8
[17179618.380000] NET: Registered protocol family 31
[17179618.380000] Bluetooth: HCI device and connection manager initialized
[17179618.380000] Bluetooth: HCI socket layer initialized
[17179618.532000] Bluetooth: L2CAP ver 2.8
[17179618.532000] Bluetooth: L2CAP socket layer initialized
[17179618.564000] Bluetooth: RFCOMM socket layer initialized
[17179618.564000] Bluetooth: RFCOMM TTY layer initialized
[17179618.564000] Bluetooth: RFCOMM ver 1.7
[17228131.040000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17228131.040000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17228131.040000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

---

### Post by bla2000 on 2006-11-12
I've fixed it. I figured out what I did wrong and it was all user error.  In mythtv-setup under hardware I mis-configure my capture cards.  I had the type set to "V4L" instead of "mpeg pvr-x-500". When my card info was auto-detected by the setup I thought that it filled in that 1st drop down correctly.

---

### Post by pacificdrums on 2006-11-12
> **superm1 said:**
> Could you clarify what exactly you did here that resolved the issue for you?  A majority of people that have used the official guide haven't had any troubles, but a few have come across very similar problems.

umm i'm not sure. Like I said, all I did was login as the mythtv user and it seems to work fine.

---

### Post by bla2000 on 2006-11-12
Everything is working now but do you know how to make it so if I logon with the mythtv user it automatically starts the frontend?  Also when I exit the frontend I'd like it to kick me straight out to the log on screen.  

I tried the automatic load of the frontend tip found here:

[http://parker1.co.uk/mythtv_tips.php]("http://parker1.co.uk/mythtv_tips.php")

but when I exit the frontend it leaves me at the gnome desktop instead of going back to the logon screen.  Thanks.

---

### Post by superm1 on 2006-11-12
> **bla2000 said:**
> Everything is working now but do you know how to make it so if I logon with the mythtv user it automatically starts the frontend?  Also when I exit the frontend I'd like it to kick me straight out to the log on screen.  

I tried the automatic load of the frontend tip found here:

[http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php)

but when I exit the frontend it leaves me at the gnome desktop instead of going back to the logon screen.  Thanks.
bla2000,
Glad you resolved the issue with mythtv-setup.

If you are trying to setup an automatic logon for the mythtv user, you  might want to consider just launching into a more light weight window manager for the mythtv user.  If you look at the wiki page for a frontend only box, you will see how to set up openbox and how to set it up so that just mythfrontend is started.  This leaves all of the cruft of gnome out of the picture during logon.

---

### Post by cheuschober on 2006-11-12
SuperM1, I'm running into the same failed authentication problems as the original author but without a backend. Also, strangely, I can't kill the backend.

I suspect my various passwords may have been mucked when I was trying to set up some samba shares.

Is there a course of action I should take?

Regards and thanks,
~Chad

---

### Post by bla2000 on 2006-11-12
> **superm1 said:**
> bla2000,
Glad you resolved the issue with mythtv-setup.

If you are trying to setup an automatic logon for the mythtv user, you  might want to consider just launching into a more light weight window manager for the mythtv user.  If you look at the wiki page for a frontend only box, you will see how to set up openbox and how to set it up so that just mythfrontend is started.  This leaves all of the cruft of gnome out of the picture during logon.

I've set 2 frontends that are also desktops so I'd like to keep the gnome desktop and login.

btw, have you seen this happen before?  On 1 of my frontends it doesn't recognized the commercial markings but on the other frontend and backend/frontend server the markings are recognized.  All 3 are connecting to the same mythconverg database.

---

### Post by superm1 on 2006-11-13
When you issue

```
sudo /etc/init.d/mythtv-backend restart
```

The authentication error is *normal*. The problem is if afterwords, the backend process isn't running.  If this is the case, then /var/log/mythtv/mythbackend.log should indicate why the process isn't running, eg can't bind port, can't write to directory etc.

If you were just messing with the passwords for the mythtv user account on the system, this won't affect the starting of the backend process.  Now on the other hand, if you were messing with mysql and changing things like that - you've got some bigger problems.  Look into installing phpmyadmin and resetting passwords with phpmyadmin.

---

### Post by superm1 on 2006-11-13
> **bla2000 said:**
> I've set 2 frontends that are also desktops so I'd like to keep the gnome desktop and login.

btw, have you seen this happen before?  On 1 of my frontends it doesn't recognized the commercial markings but on the other frontend and backend/frontend server the markings are recognized.  All 3 are connecting to the same mythconverg database.

Well this being the case, just click on system, choose preferences.  Choose Sessions.  You can add mythfrontend under the third tab, Startup Programs.  Log out and back in, and mythfrontend should start at login to the gnome session.

If one frontend isn't recognizing commercial markings, you probably dont have automatically skip commercials enabled.  I don't recall off hand where the setting for this is in the frontend.  If it flat out isn't *recognizing* the commercial markings though (eg press Z or Q and it doesn't jump), then this is a whole seperate problem that will require more debugging.

---

### Post by bla2000 on 2006-11-13
> **superm1 said:**
> If it flat out isn't *recognizing* the commercial markings though (eg press Z or Q and it doesn't jump), then this is a whole seperate problem that will require more debugging.

Z and Q didn't work.  I thought that it would be a tough thing to debug so I reformatted and installed ubuntu and then the mythtv-frontend.  Now commercial markings are recognized because Z and Q skip to the correct places.

Thanks for your help.

---

### Post by Kadin2048 on 2007-01-10
Hey everyone, 

At risk of bumping a really old thread, I am having the exact same issue as most of the other folks here.

It seems like the Authentication Error happens normally, and doesn't indicate a problem starting up the backend ... except that after I try to start the backend by running

$ sudo /etc/init.d/mythtv-backend restart

and it gives me the authentication-failed error, the back end doesn't seem to be running. At least, I don't think it's running, because if I try to "telnet localhost 6545" I get connection refused. According to what I've read, if the backend is functioning properly, I should be able to telnet to one of its ports.

On the other hand, tailing the /var/log/mythtv/mythtvbackend.log while doing this doesn't show any obvious errors. The last line is just "Seem to be woken up by USER". So if it's not running, no obvious signs of a problem there that I can see. (I would post the whole log but I'm typing from another computer.)

Is there any other way of telling whether the backend is running in good order? I just can't figure out if something is wrong, or if that error is just supposed to happen.

---

### Post by superm1 on 2007-01-10
> **Kadin2048 said:**
> Hey everyone, 

At risk of bumping a really old thread, I am having the exact same issue as most of the other folks here.

It seems like the Authentication Error happens normally, and doesn't indicate a problem starting up the backend ... except that after I try to start the backend by running

$ sudo /etc/init.d/mythtv-backend restart

and it gives me the authentication-failed error, the back end doesn't seem to be running. At least, I don't think it's running, because if I try to "telnet localhost 6545" I get connection refused. According to what I've read, if the backend is functioning properly, I should be able to telnet to one of its ports.

On the other hand, tailing the /var/log/mythtv/mythtvbackend.log while doing this doesn't show any obvious errors. The last line is just "Seem to be woken up by USER". So if it's not running, no obvious signs of a problem there that I can see. (I would post the whole log but I'm typing from another computer.)

Is there any other way of telling whether the backend is running in good order? I just can't figure out if something is wrong, or if that error is just supposed to happen.
Telnet should be working for the backend, but the ports are 6543 and 6544 by default.

A better way to check is this:
```
ps -p `cat /var/run/mythtv/mythbackend.pid`
```

If you get back a process number, its running.   If not, well its not.

---

### Post by Pollywoggy on 2007-01-12
> **pacificdrums said:**
> Yea I tried that too and iv tried restarting the computer then running the start command.
This is what I get with the restart command
```
shaun@shaun-linux:~$ sudo /etc/init.d/mythtv-backend restart
Password:
Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.
.
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.
shaun@shaun-linux:~$ 


```
just this morning I got the backend to run in daemon mode with this
```
mythbackend -d
```
Now I can run the frontend and and I can watch tv and it all seems to work. :-k

I am having the same problem, so there would seem to be something wrong with the startup script in Debian.  I will set this up on my laptop that runs Ubuntu as well.

---

### Post by superm1 on 2007-01-12
> **Pollywoggy said:**
> I am having the same problem, so there would seem to be something wrong with the startup script in Debian.  I will set this up on my laptop that runs Ubuntu as well.
The startup script works correctly when permissions are properly set (the backend is running afterwords).  What does your /var/log/mythtv/mythbackend.log show?

---

### Post by haggus on 2008-03-23
> **superm1 said:**
> Guys,

This error message is normal when launching mythtv-backend from the init script (QT management error).  You should have the process actually running.  If you are getting an error about not being able to bind to the port in the logs however, that is because you have the backend running.  You will need to issue a 

```
sudo /etc/init.d/mythtv-backend restart
```

in this case.  If for some reason it still doesn't die, manually kill the process.

Thank you I was racking my brains with this error and couldn't get anywhere my wife kids and dog would also like to thank you for sparing them the wrath of the enraged dad. :lolflag:

---

