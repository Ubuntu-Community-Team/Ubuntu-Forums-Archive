---
title: "RFH: Do you get 0-byte recordings? (Even infrequently) Please post info about it here"
date: 2011-02-14
forum: Mythbuntu
---

### Post by tgm4883 on 2011-02-14
There have been a number of people saying they are getting 0-byte recordings. Fortunately the issue appears uncommon, and happens infrequently on user systems. Unfortunately, since it is so infrequent it is difficult to gather information to resolve the issue. This thread is an attempt to try and gather as much information as we can in the hopes that if MythTV can provide a fix for it they will.

The issue appears to happen across all Distros and MythTV versions. Post in this thread if you see this issue regardless of what Distro and/or MythTV version you are using.

I myself have only seen it personally on an HD-PVR, but others have reported it on DVB cards of all kinds. 

If this happens to you, please post here with the following information:

[B]Distro and release (eg. Ubuntu 10.10, Fedora 13): 
Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
Tuners you see the issue on:
Other tuners on your system:
Firmware version version (eg. 'dmesg | grep hdpvr'):
Kernel Version (uname -a):
Snippet of dmesg around the time the issue is happening:
Any other info you think is relevant:[/B]

---

### Post by tgm4883 on 2011-02-14
**Distro and release (eg. Ubuntu 10.10, Fedora 13):  **
Mythbuntu 10.04

**Full version of all MythTV packages (eg. dpkg -l mythtv-backend): **
ii  mythtv-backend                       2:0.24.0+fixes.20110213.3d55e51-0ubu A personal video recorder application (server)
ii  mythtv-backend-master                2:0.24.0+fixes.20110213.3d55e51-0ubu Metapackage to setup and configure a "Master Backend" profile of MythTV.

**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):**
mythtv-updates repository (mythbuntu-repos)

**Tuners you see the issue on:**
HD-PVR

**Other tuners on your system:** 
pcHDTV 5500

**Firmware version version (eg. 'dmesg | grep hdpvr'):**
[    7.955363] hdpvr 1-3:1.0: untested firmware version 0x15, the driver might not work
[    8.283460] hdpvr 1-3:1.0: device now attached to /dev/video0
[    8.283494] usbcore: registered new interface driver hdpvr

**Kernel Version (uname -a): **
Linux ares 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux

**Snippet of dmesg around the time the issue is happening: **
N/A, issue is not happening at this moment.

**Any other info you think is relevant: **
In my case, the blue "halo" on the HD-PVR remains on and I get a 0-byte recording. The blue halo remains on and 0-byte recordings happen for all following recordings on that tuner until I power cycle the HD-PVR and restart the backend service.

---

### Post by ck102 on 2011-02-15
**Distro and release (eg. Ubuntu 10.10, Fedora 13): **
Ubuntu 10.10

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
ii  mythtv-backend 2:0.24.0+fixes A personal video recorder application (serve
ii  mythtv-backend 2:0.24.0+fixes Metapackage to setup and configure a "Master

[B]Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
[/B]
mythtv-updates repository (mythbuntu-repos)

**Tuners you see the issue on:**
HD-PVR

**Other tuners on your system:**
PVR-150

**Firmware version version (eg. 'dmesg | grep hdpvr'):**
[    6.364704] hdpvr 1-4:1.0: untested firmware version 0x15, the driver might not work
[    6.683368] hdpvr 1-4:1.0: device now attached to video0
[    6.683481] usbcore: registered new interface driver hdpvr
[   48.516849] hdpvr 1-4:1.0: device video0 disconnected
[   54.637145] hdpvr 1-4:1.0: untested firmware version 0x15, the driver might not work
[   54.950956] hdpvr 1-4:1.0: device now attached to video0

**Kernel Version (uname -a):**
Linux mytv 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
Not available - issue is not currently happening.  

**Any other info you think is relevant:**
When my HD-PVR becomes unusable, it corrupts the first recording about 10 minutes in and the blue halo remains off.  It then gives me 0 byte recordings until the HDPVR is power cycled.  I do not have to restart the backend.  I had the problem on 10.04 as well.  When I was using 10.04, I tried the installing the V4L/DVB from source. I wanted to test the changes that Alan Young had made (hoping it would fix the issue) This resulted in the blue halo remaining on when it corrupted.  I power cycle the HD-PVR once a week to prevent loosing recordings.

---

### Post by melevittfl on 2011-02-16
**Distro and release (eg. Ubuntu 10.10, Fedora 13): **
Mythbuntu 10.04


**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
ii  mythtv-backend               2:0.24.0+fixes.20110215.72b7 A personal video recorder application (server)
ii  mythtv-backend-master        2:0.24.0+fixes.20110215.72b7 Metapackage to setup and configure a "Master Backend" profile of MythTV.


**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):**
Mythbuntu repos

Tuners you see the issue on:
myth@mythtv:~$ dmesg | grep dvb
[    5.238720] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[    5.238725] usb 1-4: firmware: requesting dvb-usb-dib0700-1.20.fw
[    6.538725] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[    7.248025] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[    7.248093] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    7.308750] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    7.308753] cx88/2: registering cx8802 driver, type: dvb access: shared
[    7.678871] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[    7.679029] usbcore: registered new interface driver dvb_usb_dib0700


**Other tuners on your system**:

**Firmware version version (eg. 'dmesg | grep hdpvr'):**
dvb-usb-dib0700-1.20.fw'

**Kernel Version (uname -a):**
Linux mythtv 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
Don't have anything in dmesg logs from when it happens


**Any other info you think is relevant:**
I  changed the tuning timeout in mythtv-setup a few days ago. It hasn't happened since, although it only ever happened every few months or so. 

It has only happened since upgrading to MythTv .24 via the Mythbuntu autobuilds.

---

### Post by rakmount on 2011-02-18
[SIZE=2]**Distro and release (eg. Ubuntu 10.10, Fedora 13): **[/SIZE] 
 [SIZE=2]Mythbuntu 10.10[/SIZE]
 [SIZE=2][B]
Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):[/B][/SIZE]
 [SIZE=2]ii  mythtv-backend                  2:0.24.0+fixes.20110206.1a69c92 A personal video recorder application (server) [/SIZE]
 [SIZE=2]ii  mythtv-backend-master           2:0.24.0+fixes.20110206.1a69c92 Metapackage to setup and configure a "Master Backend" profile of MythTV. [/SIZE]
 [SIZE=2][B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):[/B][/SIZE]
 [SIZE=2]mythtv-updates repository (mythbuntu-repos)[/SIZE]
 [SIZE=2][B]
Tuners you see the issue on:[/B][/SIZE]
 [SIZE=2]HD-PVR[/SIZE]
 [SIZE=2](using SPDIF input)[/SIZE]
 [SIZE=2][B]
Other tuners on your system:
[/B]none[/SIZE]
 
[SIZE=2]**Firmware version version (eg. 'dmesg | grep hdpvr'):**[/SIZE]
 [SIZE=2][    3.130840] hdpvr 1-6:1.0: untested firmware version 0x15, the driver might not work [/SIZE]
 [SIZE=2][    3.466100] hdpvr 1-6:1.0: device now attached to video0 [/SIZE]
 [SIZE=2][    3.466171] usbcore: registered new interface driver hdpvr [/SIZE]
 [SIZE=2][B]
Kernel Version (uname -a):[/B][/SIZE]
 [SIZE=2]Linux McMyth 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux[/SIZE]

 [SIZE=2][B]Snippet of dmesg around the time the issue is happening:
[/B][COLOR=Indigo]from syslog dated last occurence -[/COLOR][/SIZE]
 [SIZE=2]Feb 10 20:59:51 McMyth lircd-0.8.7-pre3[1039]: accepted new client on /var/run/lirc/lircd [/SIZE]
 [SIZE=2]Feb 10 20:59:51 McMyth lircd-0.8.7-pre3[1039]: removed client [/SIZE]
 [SIZE=2]Feb 10 20:59:52 McMyth lircd-0.8.7-pre3[1039]: accepted new client on /var/run/lirc/lircd [/SIZE]
 [SIZE=2]Feb 10 20:59:52 McMyth lircd-0.8.7-pre3[1039]: removed client [/SIZE]
 [SIZE=2]Feb 10 20:59:52 McMyth lircd-0.8.7-pre3[1039]: accepted new client on /var/run/lirc/lircd [/SIZE]
 [SIZE=2]Feb 10 20:59:52 McMyth lircd-0.8.7-pre3[1039]: removed client[/SIZE]
 [SIZE=2]Feb 10 21:01:14 McMyth lircd-0.8.7-pre3[1751]: MCU top is now: 50953 (a change of: 30) [/SIZE]
 [SIZE=2]Feb 10 21:01:14 McMyth lircd-0.8.7-pre3[1751]: USB received: 63, expectingBytes: 60. Hex data (headers: 134 60 0):#011 [/SIZE]
 [SIZE=2]Feb 10 21:01:26 McMyth lircd-0.8.7-pre3[1751]: MCU top is now: 51247 (a change of: 5[/SIZE]
 [SIZE=2]Feb 10 21:01:26 McMyth lircd-0.8.7-pre3[1751]: USB received: 63, expectingBytes: 61. Hex data (headers: 140 61 0):#011 [/SIZE]
 [SIZE=2]Feb 10 21:01:28 McMyth lircd-0.8.7-pre3[1751]: MCU top is now: 53297 (a change of: 5[/SIZE]
 [SIZE=2]Feb 10 21:01:28 McMyth lircd-0.8.7-pre3[1751]: USB received: 63, expectingBytes: 61. Hex data (headers: 184 61 0):#011 
[/SIZE]
[COLOR=Indigo]saw problem at this point and stopped recording[/COLOR]

 [SIZE=2]Feb 10 21:01:41 McMyth lircd-0.8.7-pre3[1039]: accepted new client on /var/run/lirc/lircd [/SIZE]
 [SIZE=2]Feb 10 21:01:49 McMyth lircd-0.8.7-pre3[1751]: MCU top is now: 54613 (a change of: 42) [/SIZE]
 [SIZE=2]Feb 10 21:01:49 McMyth lircd-0.8.7-pre3[1751]: USB received: 63, expectingBytes: 60. Hex data (headers: 213 60 0):#011 [/SIZE]

[SIZE=2]**Snippet of  MythWelcome log around the time the issue is happening:**[/SIZE]
 [SIZE=2]2011-02-10 20:58:51.113 MythWelcome received a SCHEDULE_CHANGE event [/SIZE]
 [SIZE=2]2011-02-10 20:59:52.431 MythWelcome received a recording list change event [/SIZE]
 [SIZE=2]2011-02-10 20:59:52.431 MythWelcome received a recording list change event [/SIZE]
 [SIZE=2]2011-02-10 20:59:52.431             [deferred to pending handler] [/SIZE]
 [SIZE=2]2011-02-10 20:59:52.431 MythWelcome received a SCHEDULE_CHANGE event [/SIZE]
[COLOR=Indigo]saw problem at this point and stopped recording[/COLOR][SIZE=2]
2011-02-10 21:01:39.116 Locking input devices [/SIZE]
 [SIZE=2]2011-02-10 21:01:40.011 mythfrontend version: fixes/0.24 [v0.24-151-g1a69c92] 
[/SIZE]
 [SIZE=2]**Any other info you think is relevant:**[/SIZE]
 [SIZE=2]This has happened on more than one occasion, always when recording Grays Anatomy or Private Practice on a HD channel. Recording same from non-HD works. Recording other programs on same HD channel works. 
[/SIZE]
[SIZE=2]I believe it may be sound related – listings (Schedules Direct) show these 2 programs in particular as stereo. Actual satellite provided listing shows them as 5.1 Dolby (I don't have precise details available at the moment) while all other successfully recorded shows from same station list merely as stereo.[/SIZE]

[SIZE=2]After the problem occurs and another show records (hit or miss), it will have no sound. Only fix is a reboot of myth box and a power-cycle of HD-PVR.
[/SIZE]

---

### Post by mookie60 on 2011-02-26
Distro and release (eg. Ubuntu 10.10, Fedora 13):
mythbuntu 9.04

Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):

mythtv-backend     0.21.0+fixes21768
mythtv-backend-mas 0.21.0+fixes21768

Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
mythbuntu repos (i think)

Tuners you see the issue on:
hauppauge 1600, pchdtv 5500

Other tuners on your system:
see above

Firmware version version (eg. 'dmesg | grep hdpvr'):
sorry, don't know what to replace hdpvr with

Kernel Version (uname -a):
what ever was the last issued for 9.04

Snippet of dmesg around the time the issue is happening:
sorry, no longer have the issue, so can't provide the info

Any other info you think is relevant:
It's been several months since this problem occurred.   When it was happening, it varied from once per week, to 2-3 times per night (on either tuner).

Both my digital tuners take a long time to lock in a channel, so I thought it might be related.  So I extended the signal timeout, it's currently at 5500.  This seemed to improve things but I think I maxed out the adjustment.  

***After setting "quick tune" (for both tuners) to "Always", the problem has never reoccurred.***

I wish I could provide more complete info, but as it's been at least 4-5 months since the problem occurred, I just don't remember the issues fully.

---

### Post by ian dobson on 2011-02-27
Hi,

I sometimes see 0 byte recordings. When I see one every recording after it is 0 byte until I reboot the box.

More info here [http://ubuntuforums.org/showthread.php?t=1676491](http://ubuntuforums.org/showthread.php?t=1676491)

Kernel
Linux alpha2 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

2 DVB-C tuner cards 
```
07:00.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: KNC One Device 0022
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (3750ns min, 9500ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fb101000 (32-bit, non-prefetchable) [size=512]
        Kernel driver in use: budget_av
        Kernel modules: budget-av

07:01.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: KNC One Device 002c
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (3750ns min, 9500ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at fb100000 (32-bit, non-prefetchable) [size=512]
        Kernel driver in use: budget_av
        Kernel modules: budget-av
```

MythTV version
```
ii  libmyth-0.23-0                             0.23.1+fixes26732-0ubuntu0+mythbuntu2             Common library code for MythTV and add-on modules (runtime)
ii  libmythtv-perl                             0.23.1+fixes26732-0ubuntu0+mythbuntu2             A PERL library to access some MythTV features
ii  mythbuntu-repos                            8.5-0ubuntu0+mythbuntu~auto20101013003830         Mythbuntu repos installer
ii  mythtv-backend                             0.23.1+fixes26732-0ubuntu0+mythbuntu2             A personal video recorder application (server)
ii  mythtv-common                              0.23.1+fixes26732-0ubuntu0+mythbuntu2             A personal video recorder application (common data)
ii  mythtv-database                            0.23.1+fixes26732-0ubuntu0+mythbuntu2             A personal video recorder application (database)
ii  mythtv-transcode-utils                     0.23.1+fixes26732-0ubuntu0+mythbuntu2             Utilities used for transcoding MythTV tasks
ii  mythweb                                    0.23.1+fixes26732-0ubuntu0+mythbuntu2             Web interface add-on module for MythTV
```

syslog messages when the tuners die
```
Feb 22 01:19:25 alpha2 kernel: [116475.798614] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 22 01:19:25 alpha2 kernel: [116475.798626] Pid: 30780, comm: FahCore_a3.exe Tainted: P            2.6.35-25-generic #44-Ubuntu
Feb 22 01:19:25 alpha2 kernel: [116475.798628] Call Trace:
Feb 22 01:19:25 alpha2 kernel: [116475.798630]  <IRQ>  [<ffffffff810cbc1b>] __report_bad_irq+0x2b/0xa0
Feb 22 01:19:25 alpha2 kernel: [116475.798638]  [<ffffffff810cbe1c>] note_interrupt+0x18c/0x1d0
Feb 22 01:19:25 alpha2 kernel: [116475.798642]  [<ffffffff8102cd89>] ? ack_apic_level+0x79/0x1b0
Feb 22 01:19:25 alpha2 kernel: [116475.798645]  [<ffffffff810cc61d>] handle_fasteoi_irq+0xdd/0x110
Feb 22 01:19:25 alpha2 kernel: [116475.798648]  [<ffffffff8100cb12>] handle_irq+0x22/0x30
Feb 22 01:19:25 alpha2 kernel: [116475.798651]  [<ffffffff815921ec>] do_IRQ+0x6c/0xf0
Feb 22 01:19:25 alpha2 kernel: [116475.798655]  [<ffffffff8158add3>] ret_from_intr+0x0/0x11
Feb 22 01:19:25 alpha2 kernel: [116475.798656]  <EOI>
Feb 22 01:19:25 alpha2 kernel: [116475.798658] handlers:
Feb 22 01:19:25 alpha2 kernel: [116475.798662] [<ffffffffa0a96380>] (interrupt_hw+0x0/0x2b0 [saa7146])
Feb 22 01:19:25 alpha2 kernel: [116475.798681] [<ffffffffa005d890>] (sil24_interrupt+0x0/0x1ac [sata_sil24])
Feb 22 01:19:25 alpha2 kernel: [116475.798695] Disabling IRQ #18
Feb 22 01:19:26 alpha2 kernel: [116476.085905] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.128119] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.168091] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.218061] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.238064] DVB: TDA10023(0): tda10023_readreg: readreg error (reg == 0x11, ret == -5)
```

Running on a Asus p8p67 with a 2600CPU/16Gb ram and 8Tb RAID5 array. 

Note the system was running on a quad core2 for almost 2years with out any major problems. The nobody cared errors started after upgrading the motherboard. The error can take upto a week for it to appear. I'm now testing with the irqpoll kernel parameter......

Regards
Ian Dobson

---

### Post by JRoque250 on 2011-03-01
This issue has been driving me nuts.
[B]
Distro and release (eg. Ubuntu 10.10, Fedora 13): 
[/B]Ubuntu 10.04

[B] Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
[/B]2:0.24.0+fixes.2011
[B]
Where you get your mythtv packages from (standard repos, avenard repos, 
mythbuntu repos, compile from source, etc):
[/B]ppa mythbuntu 0.24[B]

Tuners you see the issue on:
[/B]HDHR[B]

Other tuners on your system:
[/B]Comcast DTA
Comcast STB HD
WinTV PVR-150 (One analog tuning, one tunes to DTA output on ch 3)[SIZE=2][B]Firmware version version (eg. 'dmesg | grep hdpvr'):
[/B]HDHR firmware: 20100828

[/SIZE][B] Kernel Version (uname -a):
[/B]2.6.32-25[B]

Snippet of dmesg around the time the issue is happening:
[/B]TBD...[B]

Any other info you think is relevant:
[/B]It started, perhaps only coincidentally, after the 0.24 upgrade. I've run the server for >2 years without a problem. It seems to only happen on one channel (local Fox HD) and only when scheduling a recording. Live TV, on the same tuner and channel, works fine. In fact, I've watched the scheduled recording and when it remains at 0 byte after a couple of seconds, I launch a client, tune to the second HDRH tuner and hit record - and that works. 

I changed tuning on that channel to the exact frequency detected by HDHomeRun Config during scanning but that didn't help. I run Mythtv on the base OS (ubuntu) that hosts several VirtualBox guests so rebooting is not as easy for me.JR

---

### Post by ianc on 2011-03-04
It's OK for me at the moment, but I've thrown away a lot of functionality whilst trying to get it that way.

**Distro and release (eg. Ubuntu 10.10, Fedora 13): **
Ubuntu 10.04

**Full version of all MythTV packages (eg. dpkg -l mythtv-backend): **
mythtv-backend                            0.23.0+fixes25423-0ubuntu0+mythbuntu2

**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):**
mythtv-updates repository (mythbuntu-repos)

**Tuners you see the issue on:**
Nova-T 500 PCI
[B]
Other tuners on your system: [/B]
None now: previously also had a Freecom DVB-T USB but I removed this as part of my attempts to get a stable system
[B]
Firmware version version (eg. 'dmesg | grep hdpvr'):[/B]
$ dmesg | grep dvb 
[  109.256752] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware 
[  109.256762] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw 
[  109.436870] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw' 
[  110.342864] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state. 
[  110.342978] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
[  111.899249] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer. 
[  112.473029] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected. 
[  112.473220] usbcore: registered new interface driver dvb_usb_dib0700 

**Kernel Version (uname -a): **
Linux server 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux

**Snippet of dmesg around the time the issue is happening: **
N/A, issue is not happening at this moment (fingers firmly crossed...).

**Any other info you think is relevant:**
Had this issue a lot (almost daily) at one time. Since then I have removed the USB tuner I was also using, applied all the “usual” tweaks for this card (LNA on, disable RC polling, usbcore autosuspend, quick tuning always), stopped active EIT scanning, stopped transcoding, stopped commflagging, extended timeouts, ...etc. 

The two things I did that seemed to make the most difference were to disable Active EIT scanning & to set Quick Tuning to “Always”.

I still have a few issues in the log files, but I'm not convinced that these are Mythtv's fault and anyway they're not currently having any noticable detrimental effect.

So: my system has now been stable for several weeks, but it'd be nice to be able to turn some things back on.

---

### Post by jusmop on 2011-03-05
Distro and release (eg. Ubuntu 10.10, Fedora 13):
Ubuntu 10.10 Desktop AMD64

Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
2:0.24.0+fixes.20110302.0d3d

Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
Mythbuntu.

Tuners you see the issue on:
DViCO FusionHDTV DVB-T Lite
DViCO FusionHDTV DVB-T Plus

Other tuners on your system:
Just the 2 above.

Firmware version version (eg. 'dmesg | grep hdpvr'):
Don't really understand all the dmesg guff, so here's the lines that I think are relevant to the setup of the DVB cards:

[   11.202549] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   11.203401] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   11.203407]   alloc irq_desc for 17 on node 0
[   11.203409]   alloc kstat_irqs on node 0
[   11.203422] cx8800 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   11.204895] cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected], frontend(s): 1
[   11.204898] cx88[0]: TV tuner type 4, Radio tuner type -1
[   11.311478] bttv: driver version 0.9.18 loaded
[   11.311482] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   11.354306] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
[   11.402294] cx88[0]/0: found at 0000:01:09.0, rev: 5, irq: 17, latency: 32, mmio: 0xfa000000
[   11.402401] cx88[0]/0: registered device video1 [v4l2]
[   11.402436] cx88[0]/0: registered device vbi0
[   11.402715] bttv: Bt8xx card found (0).
[   11.403077] bttv 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   11.403086] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 16, latency: 32, mmio: 0xfdeff000
[   11.403134] bttv0: detected: DViCO FusionHDTV DVB-T Lite [card=128], PCI subsystem ID is 18ac:db10
[   11.403137] bttv0: using: DViCO FusionHDTV DVB-T Lite [card=128,autodetected]
[   11.403169] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   11.403630] bttv0: tuner absent
[   11.403887] bttv0: add subdevice "dvb0"
[   11.411412] cx88[0]/2: cx2388x 8802 Driver Manager
[   11.411432] cx88-mpeg driver manager 0000:01:09.2: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   11.411440] cx88[0]/2: found at 0000:01:09.2, rev: 5, irq: 17, latency: 32, mmio: 0xf9000000
[   11.558456] bt878: AUDIO driver version 0.0.0 loaded
[   11.558601] bt878: Bt878 AUDIO function found (0).
[   11.558617] bt878 0000:01:08.1: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   11.558620] bt878_probe: card id=[0xdb1018ac],[ DViCO FusionHDTV DVB-T Lite ] has DVB functions.
[   11.558627] bt878(0): Bt878 (rev 17) at 01:08.1, irq: 16, latency: 32, memory: 0xfdefe000
[   11.800473] DVB: registering new adapter (bttv0)
[   12.110563] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
[   13.188142] cx88/2: cx2388x dvb driver version 0.0.8 loaded
[   13.188146] cx88/2: registering cx8802 driver, type: dvb access: shared
[   13.188149] cx88[0]/2: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21]
[   13.188152] cx88[0]/2: cx2388x based DVB/ATSC card
[   13.188154] cx8802_alloc_frontends() allocating 1 frontend(s)
[   13.810339] DVB: registering new adapter (cx88[0])
[   13.810345] DVB: registering adapter 1 frontend 0 (Zarlink ZL10353 DVB-T)...

Kernel Version (uname -a):
Linux pooper 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Snippet of dmesg around the time the issue is happening:
dmesg does not have any output after booting - at least for me...

Any other info you think is relevant:
I've been running MythTV for years (always fixes and always upgrading both MythTV and Ubuntu, whenever a new release of either comes out) and have not noticed this problem before. Two weeks ago it happened 11 times in 4 days. Some recordings during that time were fine. After upgrading 0.24-fixes and other Ubuntu updates 3 days ago (like I always do whenever the system tells me updates are available), and doing the required reboot (the update included a new kernel) I have not seen this issue since.

Also, a friend recently updated MythTV from 0.23-fixes to 0.24-fixes 2 weeks ago but did *not* update his OS (Ubuntu 10.04) and immediately saw the issue (again, last week).


Cheers,
Justin.

---

### Post by mlord on 2011-03-06
I recently set up a Mythtv system for a buddy, using an HDPVR to capture from a Rogers cable box (HDMI) via an HD-Fury (HDMI-to-component).

In initial testing, nothing would record reliably / repeatedly.

So we opened up the (fanless) HDPVR, measured chip temperatures, and decided it was poorly designed and in need of extra cooling.

We glued heatsinks onto the two primary chips, and plugged a 40x40x10mm fan into the "fan power" socket on the mainboard.  My buddy drilled holes for airflow on two sides, and glued the fan to the case over one set of the holes.

Thus far, it has been a reliable set-up after the refit.

-ml

---

### Post by Dan_R on 2011-03-16
[B]Distro and release (eg. Ubuntu 10.10, Fedora 13): 
[/B]Mythbuntu 10.10[B]

Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
[/B]mythtv-backend       2:0.24.0+fixes.20110[B]

Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
[/B]mythtv-updates repository (mythbuntu-repos)

[B] Tuners you see the issue on:
[/B]HD-PVR[B]

Other tuners on your system:
Firmware version version (eg. 'dmesg | grep hdpvr'):
[/B][   11.755147] hdpvr 1-2:1.0: untested firmware version 0x12, the driver might not work
[   12.049269] hdpvr 1-2:1.0: device now attached to video0
[   12.049293] usbcore: registered new interface driver hdpvr[B]

Kernel Version (uname -a):
[/B]Linux HTPC 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux[B]

Snippet of dmesg around the time the issue is happening:
Any other info you think is relevant:
[/B]Recording failed and without any input from me, it was able to record another show 4 hours later no problem on a different channel, and record the next day on the same channel.

Here is the failed recording on channel BBC America from yesterday, it changes channels using 6200ch. This happens about once every two months but is not consistent on any channel or program. I only record maybe one or two programs a day. My system also uses mythwelcome for shutdown and ACPI Wakeup. 

There are times that I do have to powercycle the HD-PVR for this same error, but this time I did not. The times I do have to powercycle and reboot the computer, until I do that, all recordings are 0-byte files.

mythbackend.log

```
2011-03-15 17:59:32.530 Started recording: "Top Gear": channel 2114 on cardid 1, sourceid 2
Warning: Unit Spec ID different.
Warning: Unit Software Version different.
2011-03-15 17:59:37.234 Updating status for "Top Gear" on cardid 1 (Tuning => Recording)
2011-03-15 17:59:37.362 TVRec(1): rec->GetPathname(): '/var/lib/mythtv/recordings/2114_20110315180000.mpg'
2011-03-15 17:59:37.805 MPEGRec(/dev/video0) Error: StartEncoding failed
                        eno: Resource temporarily unavailable (11)
2011-03-15 17:59:37.872 MPEGRec(/dev/video0) Error: Failed to start recording
2011-03-15 17:59:38.552 TVRec(1): Changing from RecordingOnly to None
2011-03-15 17:59:38.594 Updating status for "Top Gear" on cardid 1 (Recording => Recorder Failed)
2011-03-15 17:59:38.687 Reschedule requested for id 0.
2011-03-15 17:59:38.804 MainServer::ANN Playback
2011-03-15 17:59:38.844 adding: HTPC as a client (events: 0)
2011-03-15 17:59:38.886 MainServer::ANN Monitor
2011-03-15 17:59:38.891 Scheduled 83 items in 0.2 = 0.05 match + 0.15 place
2011-03-15 17:59:38.928 adding: HTPC as a client (events: 1)
2011-03-15 17:59:39.027 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 2114 --starttime 20110315180000  > $
2011-03-15 17:59:40.962 I'm idle now... shutdown will occur in 1200 seconds.

```

---

### Post by badger_fruit on 2011-03-18
**Distro and release (eg. Ubuntu 10.10, Fedora 13): **
Mythbuntu 10.4

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
ii  mythtv-backend     0.23.0++fixes25362 A personal video recorder application (server)
ii  mythtv-backend-mas 0.23.0++fixes25362 Metapackage to setup and configure a "Master Backend

[B]Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
[/B]Std repos included with Mythbuntu

**Tuners you see the issue on:**
NOVA T_**D**_500

**Other tuners on your system:**
NOVA T500

**Firmware version version (eg. 'dmesg | grep hdpvr'):**
[   10.855181] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   10.855188] cx88/2: registering cx8802 driver, type: dvb access: shared

**Kernel Version (uname -a):**
Linux bgrsvr-v 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
Not available - issue is not currently happening.  

I have observed I lose a lot of recordings when the dual-card NOVA T**_D_** 500 is installed. I could not figure out why, but I removed the card and I have a sinlge NOVA T 500 in now - every single recording works.  Could it be the TD500 I wonder?  Could it be the specification of the computer after all, it's only a P4 3GHZ with 1GB of RAM, not the most exciting specification by a long shot!  I was about to make a new thread asking for a definate answer:  If I install a 2nd card, do I need to scan for channels on it, or will the ones picked up by the existing card "just work" on the new card ... ?

---

### Post by NautiusMaximus on 2011-03-19
Yes, this has happened to me as well. Here's the info:

Distro and release (eg. Ubuntu 10.10, Fedora 13):

Ubuntu 10.04

Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):

```
dpkg -l mythtv-backend*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythtv-backend 0.23.1+fixes26 A personal video recorder application (serve
ii  mythtv-backend 0.23.1+fixes26 Metapackage to setup and configure a "Master

``` 


Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):

Not entirely sure I understand this, but I guess the answer is whatever the default option is in Mythbuntu. I've enabled autobuilds in the MythTV control centre.

Tuners you see the issue on:

Hauppauge WinTV NOVA T 500

Other tuners on your system:

None

Firmware version version (eg. 'dmesg | grep hdpvr'):

Sorry, that command does nothing on my system. Happy to try again if someone can suggest some alternative syntax (I'm really not a Linux expert

Kernel Version (uname -a):

Linux htpc 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64 GNU/Linux

Snippet of dmesg around the time the issue is happening:

Sorry, I don't know what dmesg is. Happy to post it if someone can explain to a Linux n00b how to find it

Any other info you think is relevant:

It's happened a couple of times, separated by a few weeks, most recently this week. Both times it stopped recording all programs, but was cured by a reboot. Here's the mythtv backend log around the time one of the recordings started:

```
2011-03-16 20:57:16.123 AutoExpire: CalcParams(): Max required Free Space: 100.0 GB w/freq: 15 min
2011-03-16 20:57:30.341 TVRec(4): ASK_RECORDING 4 29 0 0
2011-03-16 20:58:01.922 TVRec(4): Changing from None to RecordingOnly
2011-03-16 20:58:01.923 ProgramInfo(): Updated pathname '':'' -> '1031_20110316205800.mpg'
2011-03-16 20:58:01.934 TVRec(4): HW Tuner: 4->4
2011-03-16 20:58:02.103 AutoExpire: CalcParams(): Max required Free Space: 102.0 GB w/freq: 14 min
2011-03-16 20:58:02.111 Started recording: Dark Blue "K-Town": channel 1031 on cardid 4, sourceid 1
2011-03-16 21:01:23.220 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/disk2/mythtv/videos:
2011-03-16 21:01:23.261 UPnpMedia: BuildMediaMap Done. Found 87 objects
2011-03-16 21:12:16.215 AutoExpire: CalcParams(): Max required Free Space: 102.0 GB w/freq: 14 min

```

and here's the same log around the time the same recording finished:
```

2011-03-16 21:59:30.601 TVRec(4): ASK_RECORDING 4 29 0 0
2011-03-16 22:00:02.903 TVRec(4): Changing from RecordingOnly to None
2011-03-16 22:00:02.999 ProgramInfo(): Updated pathname '':'' -> '1031_20110316205800.mpg'
2011-03-16 22:00:03.010 Finished recording Dark Blue "K-Town": channel 1031
2011-03-16 22:00:03.027 TVRec(4): Changing from None to RecordingOnly
2011-03-16 22:00:03.032 TVRec(4): HW Tuner: 4->4
2011-03-16 22:00:03.108 AutoExpire: CalcParams(): Max required Free Space: 102.0 GB w/freq: 14 min
2011-03-16 22:00:03.120 Started recording: Sons of Anarchy "Fa Guan": channel 1031 on cardid 4, sourceid 1
2011-03-16 22:00:03.144 ProgramInfo(): Updated pathname '':'' -> '1031_20110316205800.mpg'
2011-03-16 22:00:03.155 ProgramInfo(): Updated pathname '':'' -> '1031_20110316220000.mpg'

```

and here's a bit in the middle which appears to be riddled with error messages (no idea if it's relevant):

```
2011-03-16 21:37:46.895 adding: htpc as a client (events: 2)
2011-03-16 21:37:46.968 MainServer::ANN Monitor
2011-03-16 21:37:46.973 adding: htpc as a client (events: 2)
2011-03-16 21:37:47.059 ProgramInfo(1031_20110316205800.mpg), Error: GetPlaybackURL: '1031_20110316205800.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.063 ProgramInfo(1028_20110315235800.mpg), Error: GetPlaybackURL: '1028_20110315235800.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.075 ProgramInfo(1031_20110315150800.mpg), Error: GetPlaybackURL: '1031_20110315150800.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.086 ProgramInfo(1002_20110314203000.mpg), Error: GetPlaybackURL: '1002_20110314203000.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.097 ProgramInfo(1003_20110314195800.mpg), Error: GetPlaybackURL: '1003_20110314195800.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.108 ProgramInfo(1001_20110313222300.mpg), Error: GetPlaybackURL: '1001_20110313222300.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.119 ProgramInfo(1002_20110313205800.mpg), Error: GetPlaybackURL: '1002_20110313205800.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.146 ProgramInfo(1010_20100624000500.mpg), Error: GetPlaybackURL: '1010_20100624000500.mpg' should be local, but it can not be found.
2011-03-16 21:37:47.936 MainServer::ANN Monitor
2011-03-16 21:37:47.940 adding: htpc as a client (events: 2)
2011-03-16 21:38:14.602 MainServer::ANN Monitor
2011-03-16 21:38:14.617 adding: htpc as a client (events: 2)
2011-03-16 21:38:14.677 MainServer::ANN Monitor
2011-03-16 21:38:14.762 adding: htpc as a client (events: 2)
2011-03-16 21:38:14.855 ProgramInfo(1031_20110316205800.mpg), Error: GetPlaybackURL: '1031_20110316205800.mpg' should be local, but it can not be found.
2011-03-16 21:38:14.863 ProgramInfo(1028_20110315235800.mpg), Error: GetPlaybackURL: '1028_20110315235800.mpg' should be local, but it can not be found.
2011-03-16 21:38:14.874 ProgramInfo(1031_20110315150800.mpg), Error: GetPlaybackURL: '1031_20110315150800.mpg' should be local, but it can not be found.
2011-03-16 21:38:14.885 ProgramInfo(1002_20110314203000.mpg), Error: GetPlaybackURL: '1002_20110314203000.mpg' should be local, but it can not be found.
2011-03-16 21:38:14.897 ProgramInfo(1003_20110314195800.mpg), Error: GetPlaybackURL: '1003_20110314195800.mpg' should be local, but it can not be found.
2011-03-16 21:38:14.908 ProgramInfo(1001_20110313222300.mpg), Error: GetPlaybackURL: '1001_20110313222300.mpg' should be local, but it can not be found.
2011-03-16 21:38:14.919 ProgramInfo(1002_20110313205800.mpg), Error: GetPlaybackURL: '1002_20110313205800.mpg' should be local, but it can not be found.
2011-03-16 21:38:14.945 ProgramInfo(1010_20100624000500.mpg), Error: GetPlaybackURL: '1010_20100624000500.mpg' should be local, but it can not be found.
2011-03-16 21:38:15.866 MainServer::ANN Monitor
2011-03-16 21:38:15.884 adding: htpc as a client (events: 2)

```

Good luck in figuring out what the problem is!

---

### Post by Zennon on 2011-03-31
[B]Distro and release (eg. Ubuntu 10.10, Fedora 13): 
[/B]Ubuntu 10.10 Maverick Meerkat
[B]
Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
[/B]mythtv-backend 2:0.24.0+fixes

[B]Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
[/B]Avenard repos
[B]
Tuners you see the issue on:
[/B]DigitalNow TinyTwin DVB-T Receiver
[B]
Other tuners on your system:
[/B]None
[B]
Firmware version version (eg. 'dmesg | grep hdpvr'):
[/B][   22.683937] af9013: firmware version:4.95.0
[   22.984929] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   22.988445] af9013: firmware version:4.95.0
[   23.147882] usbcore: registered new interface driver dvb_usb_af9015
[B]
Kernel Version (uname -a):
[/B]Linux XBMCLive 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686 GNU/Linux
[B]
Snippet of dmesg around the time the issue is happening:
[/B][ 4799.687555] af9013: I2C read failed reg:d330
[ 4844.773478] af9015: command failed:2
[ 4844.773497] af9013: I2C read failed reg:d330
[ 4854.648916] af9015: command failed:2
[ 4854.648938] af9013: I2C read failed reg:d330
[ 4861.248886] af9015: command failed:2
[ 4861.248905] af9013: I2C read failed reg:d330
[ 5027.434997] af9015: command failed:2
[ 5027.435018] af9013: I2C read failed reg:d2e6
[B]
Any other info you think is relevant:
[/B]Have been running XBMC/MythTV on my ASRock Ion system for 18 months now, starting with Ubuntu 9.04 (XBMCLive) and always immediately applying latest updates. Have infrequently experienced issue of 0-byte recordings before - recompiling the DVB-drivers upon kernel upgrades seemed to have resolved it over time. However, the 0-byte recordings issue has now come back in my latest setup and has been persistently annoying over the last 3 weeks. Only solution seems to be to power off system & unplug DVB card for about 10 minutes and then reboot. This is my only major annoyance with an otherwise wonderful XBMC/MythTV setup and it would be great to see this bug resolved. Thanks to whoever is looking into this.

---

### Post by ian dobson on 2011-04-01
> **ian dobson said:**
> Hi,

I sometimes see 0 byte recordings. When I see one every recording after it is 0 byte until I reboot the box.

More info here [http://ubuntuforums.org/showthread.php?t=1676491](http://ubuntuforums.org/showthread.php?t=1676491)

Kernel
Linux alpha2 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

2 DVB-C tuner cards 
```
07:00.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: KNC One Device 0022
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (3750ns min, 9500ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at fb101000 (32-bit, non-prefetchable) [size=512]
        Kernel driver in use: budget_av
        Kernel modules: budget-av

07:01.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: KNC One Device 002c
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (3750ns min, 9500ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at fb100000 (32-bit, non-prefetchable) [size=512]
        Kernel driver in use: budget_av
        Kernel modules: budget-av
```

MythTV version
```
ii  libmyth-0.23-0                             0.23.1+fixes26732-0ubuntu0+mythbuntu2             Common library code for MythTV and add-on modules (runtime)
ii  libmythtv-perl                             0.23.1+fixes26732-0ubuntu0+mythbuntu2             A PERL library to access some MythTV features
ii  mythbuntu-repos                            8.5-0ubuntu0+mythbuntu~auto20101013003830         Mythbuntu repos installer
ii  mythtv-backend                             0.23.1+fixes26732-0ubuntu0+mythbuntu2             A personal video recorder application (server)
ii  mythtv-common                              0.23.1+fixes26732-0ubuntu0+mythbuntu2             A personal video recorder application (common data)
ii  mythtv-database                            0.23.1+fixes26732-0ubuntu0+mythbuntu2             A personal video recorder application (database)
ii  mythtv-transcode-utils                     0.23.1+fixes26732-0ubuntu0+mythbuntu2             Utilities used for transcoding MythTV tasks
ii  mythweb                                    0.23.1+fixes26732-0ubuntu0+mythbuntu2             Web interface add-on module for MythTV
```

syslog messages when the tuners die
```
Feb 22 01:19:25 alpha2 kernel: [116475.798614] irq 18: nobody cared (try booting with the "irqpoll" option)
Feb 22 01:19:25 alpha2 kernel: [116475.798626] Pid: 30780, comm: FahCore_a3.exe Tainted: P            2.6.35-25-generic #44-Ubuntu
Feb 22 01:19:25 alpha2 kernel: [116475.798628] Call Trace:
Feb 22 01:19:25 alpha2 kernel: [116475.798630]  <IRQ>  [<ffffffff810cbc1b>] __report_bad_irq+0x2b/0xa0
Feb 22 01:19:25 alpha2 kernel: [116475.798638]  [<ffffffff810cbe1c>] note_interrupt+0x18c/0x1d0
Feb 22 01:19:25 alpha2 kernel: [116475.798642]  [<ffffffff8102cd89>] ? ack_apic_level+0x79/0x1b0
Feb 22 01:19:25 alpha2 kernel: [116475.798645]  [<ffffffff810cc61d>] handle_fasteoi_irq+0xdd/0x110
Feb 22 01:19:25 alpha2 kernel: [116475.798648]  [<ffffffff8100cb12>] handle_irq+0x22/0x30
Feb 22 01:19:25 alpha2 kernel: [116475.798651]  [<ffffffff815921ec>] do_IRQ+0x6c/0xf0
Feb 22 01:19:25 alpha2 kernel: [116475.798655]  [<ffffffff8158add3>] ret_from_intr+0x0/0x11
Feb 22 01:19:25 alpha2 kernel: [116475.798656]  <EOI>
Feb 22 01:19:25 alpha2 kernel: [116475.798658] handlers:
Feb 22 01:19:25 alpha2 kernel: [116475.798662] [<ffffffffa0a96380>] (interrupt_hw+0x0/0x2b0 [saa7146])
Feb 22 01:19:25 alpha2 kernel: [116475.798681] [<ffffffffa005d890>] (sil24_interrupt+0x0/0x1ac [sata_sil24])
Feb 22 01:19:25 alpha2 kernel: [116475.798695] Disabling IRQ #18
Feb 22 01:19:26 alpha2 kernel: [116476.085905] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.128119] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.168091] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.218061] saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
Feb 22 01:19:26 alpha2 kernel: [116476.238064] DVB: TDA10023(0): tda10023_readreg: readreg error (reg == 0x11, ret == -5)
```

Running on a Asus p8p67 with a 2600CPU/16Gb ram and 8Tb RAID5 array. 

Note the system was running on a quad core2 for almost 2years with out any major problems. The nobody cared errors started after upgrading the motherboard. The error can take upto a week for it to appear. I'm now testing with the irqpoll kernel parameter......

Regards
Ian Dobson

irqpoll fixed it for me. It looks as if the PCI-e to PCI bridge sometimes has timing problems.

Regards
Ian DObson

---

### Post by Dan_R on 2011-04-10
Just a follow-up to my post (#12) with 0-byte recordings on my HD-PVR. A few days after I made the post I changed the tuner timeout on the capture card setup from 3000ms (old setting from 0.23?) to 7000ms and I have had no problems. I have since increased my recordings now that it seems stable.

---

### Post by el_Paraguayo on 2011-04-23
I get this a lot (but I can be very specific about what causes it in my instance)
 
**Distro and release (eg. Ubuntu 10.10, Fedora 13): Mythbuntu 10.10**
**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*): 0.23.1+fixes26**
 
**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc): standard repos (I assume, not changed any setting)**
 
**Tuners you see the issue on: Nova-T PCI (dvb-t)**
 
**Other tuners on your system: none**
 
**Firmware version version (eg. 'dmesg | grep hdpvr'): uses cx88 module**
 
**Kernel Version (uname -a): Linux HTPC 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux**
 
**Snippet of dmesg around the time the issue is happening:**
 
**Any other info you think is relevant:**
 
Ok, what triggers it for me is suspend/resume. Scheduled recordings give me zero byte recordings after resume.
 
I've got "/etc/init.d/myth-backend restart" in a resume script but that's not fixing it.
 
 
EDIT: OK, I have fixed it for my system now.
 
I've got a script in /etc/pm/sleep.d which stops myth-backend when suspending (note my spelling mistake in the post above, should have been "myth*tv*-backend").
After the backend is stopped I remove the cx88_dvb module.
 
When resuming the maching I do it the other way round, I insert the module and then restart the backend.
 
I'm not taking any credit for this - solution came from [here]("http://ubuntuforums.org/showpost.php?p=9561124&postcount=15") - although I had to stop backend before I could remove module, and I used the init.d stop route rather than the "stop mythtv-backend".
 
Bingo, no more 0B recordings for me (touch wood).

---

### Post by Zennon on 2011-05-08
> Just a follow-up to my post (#12) with 0-byte recordings on my HD-PVR. A  few days after I made the post I changed the tuner timeout on the  capture card setup from 3000ms (old setting from 0.23?) to 7000ms and I  have had no problems. I have since increased my recordings now that it  seems stable.I can confirm that changing the tuner timeout from 3000ms to 7000ms solved the issue for me as well. I haven't experienced empty recordings for about three weeks now.

---

### Post by joshpond on 2011-06-02
Distro and release (eg. Ubuntu 10.10, Fedora 13): 
Mythbuntu 11.04

Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
 mythtv-backend 2:0.24.0+fixes

Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
Haven't changed anything so standard

Tuners you see the issue on:
HDHomeRun DVB-T

Other tuners on your system:
None

Firmware version version (eg. 'dmesg | grep hdpvr'):
Latest for HDHomeRun, can't remember off the top of my head.

Kernel Version (uname -a):
Linux core 2.6.38-8-generic

Snippet of dmesg around the time the issue is happening:
Random and haven't caught one yet.

Any other info you think is relevant:

---

### Post by Digicrat on 2011-06-07
**Distro and release (eg. Ubuntu 10.10, Fedora 13): **
Mythbuntu 10.10

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythtv-backend 2:0.24.0+fixes A personal video recorder application (serve
ii  mythtv-backend 2:0.24.0+fixes Metapackage to setup and configure a "Master


**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):**
standard

**Kernel Version (uname -a):**
Linux mythtv 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

**Tuners you see the issue on:**
I have 2 HDHomeRun Network-based Tuners - one configured for QAM, the other for ATSC.  I've periodically seen 0-byte recordings on both.  

I believe the issue is related to signal quality.  My (unconfirmed) theory is that if there is weak or no signal in the first few seconds of a recording, the attempt fails and we get a 0-byte recording.  

For example, in poor weather (when ATSC reception suffers), I tend to get 0-byte recordings with greater frequency.

The best confirmation of this may have been from the last time I got a 0-byte recording - turned out that the tuner card had actually been accidentally unplugged.  The mythbackend apparently didn't detect this and attempted to record on the unavailable tuner anyway.  This theory should be easy to test, though I haven't gotten around to doing so yet to confirm this wasn't just a coincidence.  



In either case, I think these issues do illustrate a potential bug (lack of feature?) in the backend - If a tuner is not available, or if a recordings reception fails (size/length is 0, or significantly less than expected) the system should not flag the episode as recorded, and further delete the recording if the size is below some threshold.  Ideally (or does it do this already?), if multiple tuners are available, it should treat a lack of signal-lock as a busy tuner allowing it to try any other free tuners which may or may not have better reception.

---

### Post by ck102 on 2011-06-10
> **ck102 said:**
> **Distro and release (eg. Ubuntu 10.10, Fedora 13): **
Ubuntu 10.10

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
ii  mythtv-backend 2:0.24.0+fixes A personal video recorder application (serve
ii  mythtv-backend 2:0.24.0+fixes Metapackage to setup and configure a "Master

[B]Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
[/B]
mythtv-updates repository (mythbuntu-repos)

**Tuners you see the issue on:**
HD-PVR

**Other tuners on your system:**
PVR-150

**Firmware version version (eg. 'dmesg | grep hdpvr'):**
[    6.364704] hdpvr 1-4:1.0: untested firmware version 0x15, the driver might not work
[    6.683368] hdpvr 1-4:1.0: device now attached to video0
[    6.683481] usbcore: registered new interface driver hdpvr
[   48.516849] hdpvr 1-4:1.0: device video0 disconnected
[   54.637145] hdpvr 1-4:1.0: untested firmware version 0x15, the driver might not work
[   54.950956] hdpvr 1-4:1.0: device now attached to video0

**Kernel Version (uname -a):**
Linux mytv 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
Not available - issue is not currently happening.  

**Any other info you think is relevant:**
When my HD-PVR becomes unusable, it corrupts the first recording about 10 minutes in and the blue halo remains off.  It then gives me 0 byte recordings until the HDPVR is power cycled.  I do not have to restart the backend.  I had the problem on 10.04 as well.  When I was using 10.04, I tried the installing the V4L/DVB from source. I wanted to test the changes that Alan Young had made (hoping it would fix the issue) This resulted in the blue halo remaining on when it corrupted.  I power cycle the HD-PVR once a week to prevent loosing recordings.

About the time I posted this, I was experiencing the failed recordings about once a week.  I changed the following to grub:

```
GRUB_CMDLINE_LINUX="acpi=off noapic"
```

Since making this change, I have not experienced any 0 byte recordings.  If I undo this change, the failed recordings are back within the week.

---

### Post by brianafischer on 2011-06-10
**Distro and release (eg. Ubuntu 10.10, Fedora 13):**
$ lsb_release -a
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid
```


**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
$ dpkg -l mythtv-backend*
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
ii  mythtv-backend       2:0.24.1+fixes.20110 A personal video recorder application (server)
ii  mythtv-backend-maste 2:0.24.1+fixes.20110 Metapackage to setup and configure a "Master Backend" pr
```


**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):**
mythbuntu repos


**Tuners you see the issue on:**
```
Model: "Techsan Electronics B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card"
Device: pci 0x2103 "B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card"
```


**Other tuners on your system:**
[LIST]
HD-PVR
HDHomeRun
[/LIST]


**Firmware version version (eg. 'dmesg | grep hdpvr'):**
$dmesg | grep -i dvb
```
[   25.261693] DVB: registering new adapter (FlexCop Digital TV device)
[   25.511208] DVB: registering adapter 1 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   25.891150] DVB: registering new adapter (cx18)
[   25.956338] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   25.956389] cx18-0: DVB Frontend registered
[   25.956391] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
```
```
$ dmesg | grep -i hdpvr
[   25.242828] hdpvr 1-5:1.0: untested firmware version 0x12, the driver might not work
[   25.546293] hdpvr 1-5:1.0: device now attached to /dev/video0
[   25.546308] usbcore: registered new interface driver hdpvr
```


**Kernel Version (uname -a):**
$ uname -a
```
Linux phenomhd 2.6.32-32-generic-pae #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 i686 GNU/Linux
```


**Snippet of dmesg around the time the issue is happening:**
Unfortunately I do not have this...

Any other info you think is relevant:
Think it is related to SD recordings.  Always happens when changing from SD to HD.  This bug is filed under [http://code.mythtv.org/trac/ticket/9177#comment:26](http://code.mythtv.org/trac/ticket/9177#comment:26)

---

### Post by ktmom on 2011-06-30
**Distro and release (eg. Ubuntu 10.10, Fedora 13):**
$ lsb_release -a
```
[No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid

```

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
$ dpkg -l mythtv-backend*
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version                          Description
+++-================================-================================-================================================================================
ii  mythtv-backend                   2:0.24.1+fixes.20110624.572b95a- A personal video recorder application (server)
ii  mythtv-backend-master            2:0.24.1+fixes.20110624.572b95a- Metapackage to setup and configure a "Master Backend" profile of MythTV.

```

**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):**
$ cat /etc/apt/sources.list
```

#deb cdrom:[Mythbuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

**Tuners you see the issue on:**
Hauppauge WinTV-HVR2250
$ dmesg | grep saa
```

[   18.107035] saa7164 driver loaded
[   18.107335] saa7164 0000:02:00.0: PCI INT A -> Link[LNK4] -> GSI 9 (level, low) -> IRQ 9
[   18.107668] CORE saa7164[0]: subsystem: 0070:8891, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   18.107674] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 9, latency: 0, mmio: 0xce000000
[   18.107680] saa7164 0000:02:00.0: setting latency timer to 64
[   18.107684] IRQ 9/saa7164[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   18.388085] saa7164_downloadfirmware() no first image
[   18.388285] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   18.388290] saa7164 0000:02:00.0: firmware: requesting v4l-saa7164-1.0.3.fw
[   18.712804] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   18.712808] saa7164_downloadfirmware() firmware loaded.
[   18.712819] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   18.712825] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   18.712827] saa7164_downloadfirmware() BSLSize = 0x0
[   18.712829] saa7164_downloadfirmware() Reserved = 0x0
[   18.712831] saa7164_downloadfirmware() Version = 0x51cc1
[   26.885575] saa7164_downloadimage() Image downloaded, booting...
[   26.988072] saa7164_downloadimage() Image booted successfully.
[   29.174407] saa7164_downloadimage() Image downloaded, booting...
[   30.836341] saa7164_downloadimage() Image booted successfully.
[   30.894020] saa7164[0]: Hauppauge eeprom: model=88061
[   31.854208] DVB: registering new adapter (saa7164)
[   34.931356] DVB: registering new adapter (saa7164)
```

**Other tuners on your system:**
      HDHomeRun

**Firmware version version (eg. 'dmesg | grep hdpvr'):**
$ dmesg | grep -i dvb
```
[   30.894010] tveeprom 4-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   31.854208] DVB: registering new adapter (saa7164)
[   31.854216] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   34.931356] DVB: registering new adapter (saa7164)
[   34.931361] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...

```

**Kernel Version (uname -a):**
$ uname -a
```
Linux mythbox 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
```

**Snippet of dmesg around the time the issue is happening:**
not available - using mythwelcome but attached sys log around the failure.

**Any other info you think is relevant:**
Had the problem under 9.10 with the HVR2250 tuner.  I think I turned off apic in grub and increased the tuner timeouts and forgot all about this.  Recently upgraded to 10.04 and mythtv .24-fixes and now having the problem intermittently again.

Have tried GRUB_CMDLINE_LINUX="nolapic" and increased the tuning timeouts on all tuners.

The tuner most recently stopped recording 47 minutes into two shows and then didn't record anything after until the next reboot.  There were slews (technical term) of these errors in the syslog:
```
Event timed out
saa7164_api_i2c_read() error, ret(1) = 0x32
s5h1411_readreg: readreg error (ret == -5)
Event timed out
saa7164_api_i2c_write() error, ret(1) = 0xc
s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
```

I've attached text files of the sys.log (sunday the boot and around the failure - monday the boot after the failure where everything was ok again) and the mythbackend.log around the time of the failure. Card failure time stamp at about; 2011-06-26 21:48:18.855

$ lspci
```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
05:07.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
06:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```

---

### Post by ian dobson on 2011-07-06
Hi,

OK I've had a look at my 0byte problems with the iptv recorder and have found something interesting:-

I see this when the recording works
```

2011-07-05 20:08:29.878 TVRec(5): ASK_RECORDING 5 29 0 0
2011-07-05 20:09:01.335 TVRec(5): Changing from None to RecordingOnly
2011-07-05 20:09:01.360 TVRec(5): HW Tuner: 5->5
Looking for data for Channel 90008 on 1
Opening /data/bin/itgate1.vlm for Channel 90008
Starting vlc1 -I telnet --telnet-port 4211 --vlm-conf /data/bin/itgate1.vlm  -v
Tuning to http://192.168.0.60/cgi-bin/zapTo?path=1:0:1:2721:2bd:7:0:0:0:0:
Countdown 4
Countdown 3
Countdown 2
Countdown 1
Connecting to vlc
sending password
starting playback
sending control 90008 play
quitting
2011-07-05 20:09:12.190 AutoExpire: CalcParams(): Max required Free Space: 252.0 GB w/freq: 7 min
2011-07-05 20:09:12.191 Started recording: "Numb3rs - Die Logik des Verbrechens": channel 93009 on cardid 5, sourceid 3
2011-07-05 20:09:12.192 scheduler: Started recording: "Numb3rs - Die Logik des Verbrechens": channel 93009 on cardid 5, sourceid 3
2011-07-05 20:09:12.377 ProgramInfo(93009_20110705200900.mpg), Error: GetPlaybackURL: '93009_20110705200900.mpg' should be local, but it can not be found.
2011-07-05 20:09:14.290 Updating status for "Numb3rs - Die Logik des Verbrechens" on cardid 5 (Tuning => Recording)
2011-07-05 20:09:14.347 TVRec(5): EIT scanning disabled for all sources on this card.
2011-07-05 20:09:14.359 TVRec(5): rec->GetPathname(): '/data/mythtv/recordings/93009_20110705200900.mpg'
2011-07-05 20:10:01.205 Reschedule requested for id -1.

```

And when it doesn't work:-
```

2011-07-06 12:43:29.807 TVRec(5): ASK_RECORDING 5 29 0 0
2011-07-06 12:44:01.675 TVRec(5): Changing from None to RecordingOnly
2011-07-06 12:44:02.095 TVRec(5): HW Tuner: 5->5
2011-07-06 12:44:02.166 TVRec(5): rec->GetPathname(): '/data/mythtv/recordings/93009_20110706124400.mpg'
2011-07-06 12:44:02.181 AutoExpire: CalcParams(): Max required Free Space: 252.0 GB w/freq: 14 min
2011-07-06 12:44:02.191 Started recording: "Numb3rs - Die Logik des Verbrechens": channel 93009 on cardid 5, sourceid 3
2011-07-06 12:44:02.217 scheduler: Started recording: "Numb3rs - Die Logik des Verbrechens": channel 93009 on cardid 5, sourceid 3
Looking for data for Channel 90008 on 1
Opening /data/bin/itgate1.vlm for Channel 90008
Starting vlc1 -I telnet --telnet-port 4211 --vlm-conf /data/bin/itgate1.vlm  -v
Tuning to http://192.168.0.60/cgi-bin/zapTo?path=1:0:1:2721:2bd:7:0:0:0:0:
Countdown 4
Countdown 3
Countdown 2
Countdown 1
Connecting to vlc
sending password
starting playback
sending control 90008 play
quitting
2011-07-06 12:45:01.980 MainServer::ANN Monitor
2011-07-06 12:45:02.009 MainServer::ANN Monitor
2011-07-06 12:45:02.260 adding: alpha2 as a client (events: 0)
2011-07-06 12:45:02.262 adding: alpha2 as a client (events: 0)
2011-07-06 12:45:08.190 EITScanner (1): Now looking for EIT data on multiplex of channel 153
2011-07-06 12:45:08.220 EITCache: Pruning all entries that ended before UTC 2011-07-05T12:50:28
2011-07-06 12:45:08.253 EITCache: Deleting old cache entries from the database
2011-07-06 12:45:10.298 EITScanner (1): Started passive scan.
2011-07-06 12:45:10.646 MainServer::ANN Monitor

```
Note the message Started recording and rec->GetPathname comming before the tuning script is called. 

and here's a dump of the vlc output. Note the stream seems to be getting to mythtv, but mythtv just doesn't save it to disk (The first connect refused message appears when mythtv should stop the recording).

```

07-07-2011 02:31:01 ,\*ÉßVLC media player 1.1.9 The Luggage (revision exported)
07-07-2011 02:31:01 Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
07-07-2011 02:31:01 Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
07-07-2011 02:31:01 [0x941190] inhibit interface error: Failed to connect to the D-Bus session daemon: //bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
07-07-2011 02:31:01 
07-07-2011 02:31:01 [0x941190] main interface error: no suitable interface module
07-07-2011 02:31:01 [0x943250] main interface error: no suitable interface module
07-07-2011 02:31:01 [0x83d120] main libvlc error: interface "globalhotkeys,none" initialization failed
07-07-2011 02:31:01 [0x943600] [telnet] lua interface: Listening on host "localhost:4212".
07-07-2011 02:31:11 [0x965f80] [Media: 90008] main stream out warning: missing value for option mux
07-07-2011 02:31:11 Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
07-07-2011 02:31:12 libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 0) for PID 0
07-07-2011 02:31:12 libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 0) for PID 222
07-07-2011 02:31:12 [0x96c500] [Media: 90008] ts demux warning: first packet for pid=223 cc=0xd
07-07-2011 02:31:12 [0x96c500] [Media: 90008] ts demux warning: first packet for pid=224 cc=0xb
07-07-2011 02:33:29 libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 12) for PID 222
07-07-2011 02:41:29 libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 3) for PID 222
07-07-2011 02:45:29 libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 0) for PID 222
07-07-2011 02:53:29 libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 7) for PID 222
07-07-2011 02:57:29 libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 3) for PID 222
07-07-2011 03:09:29 libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 6) for PID 222
07-07-2011 03:21:29 libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 9) for PID 222
07-07-2011 03:33:29 libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 12) for PID 222
07-07-2011 03:36:40 [0x968960] [Media: 90008] access_output_udp access out warning: send error: Connection refused
07-07-2011 03:37:29 last line repeated 4074 times
07-07-2011 03:37:29 libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 9) for PID 222
07-07-2011 03:37:29 [0x968960] [Media: 90008] access_output_udp access out warning: send error: Connection refused
07-07-2011 03:45:01 last line repeated 41677 times

```


So it looks like a mythtv timing problem.

Running 2:0.24.1+fixes.20110706.b491236-0ubuntu0mythbuntu3 on 64bit 11.04.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-07-07
Hi All,

A simple question: Is this thread going anywhere/is a dev actually looking at this? I don't expect a solution, I'd just like to know if anything's going on in the background.

Regards
Ian Dobson

---

### Post by tgm4883 on 2011-07-07
> **ian dobson said:**
> Hi All,

A simple question: Is this thread going anywhere/is a dev actually looking at this? I don't expect a solution, I'd just like to know if anything's going on in the background.

Regards
Ian Dobson

Yep, there are developers looking at the info. Whether it proves fruitful or not remains to be seen though.

---

### Post by ian dobson on 2011-07-07
> **tgm4883 said:**
> Yep, there are developers looking at the info. Whether it proves fruitful or not remains to be seen though.

OK Thanks, that all I wanted to know. I'll continue my search for the cause of 0byte recordings with IPTV tuners.

Regards
Ian Dobson

---

### Post by ian dobson on 2011-07-12
Hi,

It's just happened again, and as I said in the last post the MythTV backend displays the following message before the channel change script starts when the recording doesn't work:-

scheduler: Started recording: "": channel XXX on cardid YYY, sourceid ZZZ

```
Recording worked
2011-07-12 10:33:30.172 TVRec(5): ASK_RECORDING 5 29 0 0
2011-07-12 10:34:01.766 TVRec(5): Changing from None to RecordingOnly
2011-07-12 10:34:01.851 TVRec(5): HW Tuner: 5->5
* Looking for data for Channel 90015 on 1
* Opening /data/bin/itgate1.vlm for Channel 90015
* Need to use CAM for channel 90015
* Tuning to http://192.168.0.62/cgi-bin/zapTo?path=1:0:1:c73d:26e:1:0:0:0:0:
* Starting vlc1 -I telnet --telnet-port 4211 --vlm-conf /data/bin/itgate1.vlm  -v
* Tuning to http://192.168.0.60/cgi-bin/zapTo?path=1:0:1:c73d:26e:1:0:0:0:0:
* Countdown 4
* Countdown 3
* Countdown 2
* Countdown 1
* Connecting to vlc
* sending password
* starting playback
* sending control 90015 play
* quitting
2011-07-12 10:34:16.556 AutoExpire: CalcParams(): Max required Free Space: 252.0 GB w/freq: 7 min
2011-07-12 10:34:16.593 Started recording: "Dr. G - Beruf: Gerichtsmedizinerin":"Medizinische Mysterien unter der Lupe": channel 93021 on cardid 5, sourceid 3
2011-07-12 10:34:16.594 scheduler: Started recording: "Dr. G - Beruf: Gerichtsmedizinerin":"Medizinische Mysterien unter der Lupe": channel 93021 on cardid 5, so$
2011-07-12 10:34:18.532 Updating status for "Dr. G - Beruf: Gerichtsmedizinerin":"Medizinische Mysterien unter der Lupe" on cardid 5 (Tuning => Recording)
2011-07-12 10:34:18.539 TVRec(5): EIT scanning disabled for all sources on this card.
2011-07-12 10:34:18.699 TVRec(5): rec->GetPathname(): '/data/mythtv/recordings/93021_20110712103400.mpg'
2011-07-12 10:35:01.842 MainServer::ANN Monitor



Recording didn't work
2011-07-12 10:36:30.069 TVRec(6): ASK_RECORDING 6 29 0 0
2011-07-12 10:37:01.547 TVRec(6): Changing from None to RecordingOnly
2011-07-12 10:37:01.614 TVRec(6): HW Tuner: 6->6
2011-07-12 10:37:01.717 TVRec(6): rec->GetPathname(): '/data/mythtv/recordings/93000_20110712103700.mpg'
2011-07-12 10:37:01.733 AutoExpire: CalcParams(): Max required Free Space: 252.0 GB w/freq: 4 min
2011-07-12 10:37:01.747 Started recording: "Einsatz in New York": channel 93000 on cardid 6, sourceid 3
2011-07-12 10:37:01.764 scheduler: Started recording: "Einsatz in New York": channel 93000 on cardid 6, sourceid 3
* Looking for data for Channel 90000 on 2
* Opening /data/bin/itgate2.vlm for Channel 90000
* Starting vlc2 -I telnet --telnet-port 4212 --vlm-conf /data/bin/itgate2.vlm  -v
* Tuning to http://192.168.0.61/cgi-bin/zapTo?path=1:0:1:2730:2bd:7:0:0:0:0:
* Countdown 4
* Countdown 3
* Countdown 2
* Countdown 1
* Connecting to vlc
* sending password
* starting playback
* sending control 90000 play
* quitting
2011-07-12 10:37:28.541 EITScanner (3): Added 249 EIT Events
2011-07-12 10:37:28.579 EITScanner: Rate limiting reschedules..
2011-07-12 10:38:54.715 AutoExpire: CalcParams(): Max required Free Space: 252.0 GB w/freq: 4 min
2011-07-12 10:40:01.305 MainServer::ANN Monitor
```

Note the data is grabbed from the settopbox/feed into VLC in both cases and vlc passes it onto MythTV but when the recording doesn't work it looks as if the backend just looses track of what should go where.

Regards
Ian Dobson

---

### Post by ktmom on 2011-07-21
I'm getting failures pretty regularly under 10.04.2 mythtv .24-fixes AMD 64-bit running 32-bit.  In addition to my previous post, I am getting recordings which stop at some point into them.  Today it was 8-ish minutes in.  Then nothing recorded after until I rebooted the system.

I'm frustrated since I had exactly the same problem when I first installed the 2250 under 9.10.  I have been racking my brain to remember all of the things I attempted (no I can't find my notes) and it seems that I think I played with increasing the latency for the card.

A lspci -v shows:
```
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. Device 8891
	Flags: bus master, fast devsel, [COLOR="Red"]**latency 0**[/COLOR], IRQ 9
	Memory at ce000000 (64-bit, non-prefetchable) [size=4M]
	Memory at ce400000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164

```

Does that *latency 0* seem right?  The trouble is, I can't remember how I went about telling the system to increase the latency.  Should I bother chasing this?

mythbackend around the failure:
```
2011-07-21 19:07:39.655 DevRdB(/dev/dvb/adapter1/frontend0) Error: Poll giving up
2011-07-21 19:07:39.660 DVBSH(/dev/dvb/adapter1/frontend0) Error: Device error detected
2011-07-21 19:07:39.675 DevRdB(/dev/dvb/adapter0/frontend0) Error: Poll giving up
2011-07-21 19:07:39.679 DVBSH(/dev/dvb/adapter0/frontend0) Error: Device error detected
2011-07-21 19:08:09.700 DVBRec(5:/dev/dvb/adapter1/frontend0) Error: Stream handler died unexpectedly.
2011-07-21 19:08:09.700 DVBRec(4:/dev/dvb/adapter0/frontend0) Error: Stream handler died unexpectedly.
2011-07-21 19:08:09.724 TVRec(5): Changing from RecordingOnly to None
2011-07-21 19:08:09.726 Updating status for TMZ on cardid 5 (Recording => Recorder Failed)
2011-07-21 19:08:09.729 Reschedule requested for id 0.
2011-07-21 19:08:09.756 MainServer, Error: PREVIEW_SUCCESS but no receivers.
2011-07-21 19:08:10.291 TVRec(4): Changing from RecordingOnly to None
2011-07-21 19:08:10.325 Updating status for "Dr. Phil":"Accused of the Unthinkable" on cardid 4 (Recording => Recorder Failed)
2011-07-21 19:08:10.467 MainServer, Error: PREVIEW_SUCCESS but no receivers.
2011-07-21 19:08:11.047 Reschedule interrupted, will retry
2011-07-21 19:08:11.047 Reschedule requested for id 0.
2011-07-21 19:08:11.048 Reschedule requested for id 0.
```


and of course the syslog is full of these:

```
Jul 21 19:07:24 mythbox kernel: [108745.957028] Event timed out
Jul 21 19:07:24 mythbox kernel: [108745.957042] saa7164_api_i2c_read() error, ret(2) = 0x32
Jul 21 19:07:24 mythbox kernel: [108745.957049] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:25 mythbox kernel: [108747.076028] Event timed out
Jul 21 19:07:25 mythbox kernel: [108747.076041] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:07:25 mythbox kernel: [108747.076050] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:34 mythbox kernel: [108755.957030] Event timed out
Jul 21 19:07:34 mythbox kernel: [108755.957042] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:07:34 mythbox kernel: [108755.957050] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:35 mythbox kernel: [108757.076030] Event timed out
Jul 21 19:07:35 mythbox kernel: [108757.076043] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:07:35 mythbox kernel: [108757.076052] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:44 mythbox kernel: [108765.957026] Event timed out
Jul 21 19:07:44 mythbox kernel: [108765.957039] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:44 mythbox kernel: [108765.957048] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:07:45 mythbox kernel: [108767.076028] Event timed out
Jul 21 19:07:45 mythbox kernel: [108767.076041] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:45 mythbox kernel: [108767.076050] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:07:49 mythbox kernel: [108770.948026] Event timed out
Jul 21 19:07:49 mythbox kernel: [108770.948039] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:49 mythbox kernel: [108770.948045] saa7164_dvb_pause_tsport() pause transition failed, ret = 0x32
Jul 21 19:07:49 mythbox kernel: [108770.968022] Event timed out
Jul 21 19:07:49 mythbox kernel: [108770.968027] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:49 mythbox kernel: [108770.968032] saa7164_dvb_pause_tsport() pause transition failed, ret = 0x32
Jul 21 19:07:54 mythbox kernel: [108775.956037] Event timed out
Jul 21 19:07:54 mythbox kernel: [108775.956050] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:54 mythbox kernel: [108775.956059] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:07:55 mythbox kernel: [108777.076029] Event timed out
Jul 21 19:07:55 mythbox kernel: [108777.076041] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:55 mythbox kernel: [108777.076050] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:07:59 mythbox kernel: [108780.948050] Event timed out
Jul 21 19:07:59 mythbox kernel: [108780.948064] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:59 mythbox kernel: [108780.948070] saa7164_dvb_acquire_tsport() acquire transition failed, ret = 0x32
Jul 21 19:07:59 mythbox kernel: [108780.968052] Event timed out
Jul 21 19:07:59 mythbox kernel: [108780.968058] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:59 mythbox kernel: [108780.968063] saa7164_dvb_acquire_tsport() acquire transition failed, ret = 0x32
Jul 21 19:08:04 mythbox kernel: [108785.957029] Event timed out
Jul 21 19:08:04 mythbox kernel: [108785.957042] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:04 mythbox kernel: [108785.957051] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:08:05 mythbox kernel: [108787.076028] Event timed out
Jul 21 19:08:05 mythbox kernel: [108787.076041] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:05 mythbox kernel: [108787.076050] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:08:09 mythbox kernel: [108790.948028] Event timed out
Jul 21 19:08:09 mythbox kernel: [108790.948041] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:08:09 mythbox kernel: [108790.948047] saa7164_dvb_stop_tsport() stop transition failed, ret = 0x32
Jul 21 19:08:09 mythbox kernel: [108790.968026] Event timed out
Jul 21 19:08:09 mythbox kernel: [108790.968035] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:08:09 mythbox kernel: [108790.968041] saa7164_dvb_stop_tsport() stop transition failed, ret = 0x32
Jul 21 19:08:14 mythbox kernel: [108795.957069] Event timed out
Jul 21 19:08:14 mythbox kernel: [108795.957078] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:14 mythbox kernel: [108795.957083] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:08:14 mythbox kernel: [108795.957087] tda18271_init: error -5 on line 826
Jul 21 19:08:14 mythbox kernel: [108795.957089] tda18271_tune: error -5 on line 904
Jul 21 19:08:14 mythbox kernel: [108795.957092] tda18271_set_params: error -5 on line 985
Jul 21 19:08:15 mythbox kernel: [108797.076042] Event timed out
Jul 21 19:08:15 mythbox kernel: [108797.076055] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:15 mythbox kernel: [108797.076065] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:08:15 mythbox kernel: [108797.076072] tda18271_init: error -5 on line 826
Jul 21 19:08:15 mythbox kernel: [108797.076078] tda18271_tune: error -5 on line 904
Jul 21 19:08:15 mythbox kernel: [108797.076083] tda18271_set_params: error -5 on line 985
Jul 21 19:08:24 mythbox kernel: [108805.957055] Event timed out
Jul 21 19:08:24 mythbox kernel: [108805.957066] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:24 mythbox kernel: [108805.957075] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Jul 21 19:08:25 mythbox kernel: [108807.076039] Event timed out
Jul 21 19:08:25 mythbox kernel: [108807.076052] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:25 mythbox kernel: [108807.076062] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Jul 21 19:08:34 mythbox kernel: [108815.957026] Event timed out
Jul 21 19:08:34 mythbox kernel: [108815.957036] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:34 mythbox kernel: [108815.957044] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:08:35 mythbox kernel: [108817.076058] Event timed out
Jul 21 19:08:35 mythbox kernel: [108817.076071] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:35 mythbox kernel: [108817.076080] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:08:44 mythbox kernel: [108825.956041] Event timed out
Jul 21 19:08:44 mythbox kernel: [108825.956053] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:44 mythbox kernel: [108825.956061] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:08:45 mythbox kernel: [108827.076038] Event timed out
Jul 21 19:08:45 mythbox kernel: [108827.076051] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:45 mythbox kernel: [108827.076060] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:08:55 mythbox kernel: [108836.956039] Event timed out
Jul 21 19:08:55 mythbox kernel: [108836.956051] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:08:55 mythbox kernel: [108836.956059] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:08:56 mythbox kernel: [108838.076033] Event timed out
Jul 21 19:08:56 mythbox kernel: [108838.076045] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:08:56 mythbox kernel: [108838.076053] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:09:01 mythbox CRON[4043]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jul 21 19:09:05 mythbox kernel: [108846.957028] Event timed out
Jul 21 19:09:05 mythbox kernel: [108846.957041] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:09:05 mythbox kernel: [108846.957048] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:09:06 mythbox kernel: [108848.076029] Event timed out
Jul 21 19:09:06 mythbox kernel: [108848.076043] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:09:06 mythbox kernel: [108848.076051] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:09:15 mythbox kernel: [108856.957028] Event timed out
Jul 21 19:09:15 mythbox kernel: [108856.957040] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:15 mythbox kernel: [108856.957049] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:09:16 mythbox kernel: [108858.076057] Event timed out
Jul 21 19:09:16 mythbox kernel: [108858.076070] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:16 mythbox kernel: [108858.076079] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:09:25 mythbox kernel: [108866.956033] Event timed out
Jul 21 19:09:25 mythbox kernel: [108866.956045] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:25 mythbox kernel: [108866.956053] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:09:26 mythbox kernel: [108868.076034] Event timed out
Jul 21 19:09:26 mythbox kernel: [108868.076047] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:26 mythbox kernel: [108868.076056] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:09:35 mythbox kernel: [108876.957027] Event timed out
Jul 21 19:09:35 mythbox kernel: [108876.957040] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:35 mythbox kernel: [108876.957049] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:09:36 mythbox kernel: [108878.076038] Event timed out
Jul 21 19:09:36 mythbox kernel: [108878.076051] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:36 mythbox kernel: [108878.076061] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:09:45 mythbox kernel: [108886.956032] Event timed out
Jul 21 19:09:45 mythbox kernel: [108886.956044] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:45 mythbox kernel: [108886.956053] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:09:45 mythbox kernel: [108886.956061] tda18271_init: error -5 on line 826
Jul 21 19:09:45 mythbox kernel: [108886.956067] tda18271_tune: error -5 on line 904
Jul 21 19:09:45 mythbox kernel: [108886.956072] tda18271_set_params: error -5 on line 985
Jul 21 19:09:46 mythbox kernel: [108888.076046] Event timed out
Jul 21 19:09:46 mythbox kernel: [108888.076059] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:46 mythbox kernel: [108888.076069] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:09:46 mythbox kernel: [108888.076076] tda18271_init: error -5 on line 826
Jul 21 19:09:46 mythbox kernel: [108888.076081] tda18271_tune: error -5 on line 904
Jul 21 19:09:46 mythbox kernel: [108888.076087] tda18271_set_params: error -5 on line 985
Jul 21 19:09:55 mythbox kernel: [108896.957026] Event timed out
Jul 21 19:09:55 mythbox kernel: [108896.957038] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:55 mythbox kernel: [108896.957047] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Jul 21 19:09:56 mythbox kernel: [108898.076037] Event timed out
Jul 21 19:09:56 mythbox kernel: [108898.076050] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:56 mythbox kernel: [108898.076060] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
```

---

### Post by ian dobson on 2011-07-22
> **ktmom said:**
> I'm getting failures pretty regularly under 10.04.2 mythtv .24-fixes AMD 64-bit running 32-bit.  In addition to my previous post, I am getting recordings which stop at some point into them.  Today it was 8-ish minutes in.  Then nothing recorded after until I rebooted the system.

I'm frustrated since I had exactly the same problem when I first installed the 2250 under 9.10.  I have been racking my brain to remember all of the things I attempted (no I can't find my notes) and it seems that I think I played with increasing the latency for the card.

A lspci -v shows:
```
02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. Device 8891
	Flags: bus master, fast devsel, [COLOR="Red"]**latency 0**[/COLOR], IRQ 9
	Memory at ce000000 (64-bit, non-prefetchable) [size=4M]
	Memory at ce400000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164

```

Does that *latency 0* seem right?  The trouble is, I can't remember how I went about telling the system to increase the latency.  Should I bother chasing this?

mythbackend around the failure:
```
2011-07-21 19:07:39.655 DevRdB(/dev/dvb/adapter1/frontend0) Error: Poll giving up
2011-07-21 19:07:39.660 DVBSH(/dev/dvb/adapter1/frontend0) Error: Device error detected
2011-07-21 19:07:39.675 DevRdB(/dev/dvb/adapter0/frontend0) Error: Poll giving up
2011-07-21 19:07:39.679 DVBSH(/dev/dvb/adapter0/frontend0) Error: Device error detected
2011-07-21 19:08:09.700 DVBRec(5:/dev/dvb/adapter1/frontend0) Error: Stream handler died unexpectedly.
2011-07-21 19:08:09.700 DVBRec(4:/dev/dvb/adapter0/frontend0) Error: Stream handler died unexpectedly.
2011-07-21 19:08:09.724 TVRec(5): Changing from RecordingOnly to None
2011-07-21 19:08:09.726 Updating status for TMZ on cardid 5 (Recording => Recorder Failed)
2011-07-21 19:08:09.729 Reschedule requested for id 0.
2011-07-21 19:08:09.756 MainServer, Error: PREVIEW_SUCCESS but no receivers.
2011-07-21 19:08:10.291 TVRec(4): Changing from RecordingOnly to None
2011-07-21 19:08:10.325 Updating status for "Dr. Phil":"Accused of the Unthinkable" on cardid 4 (Recording => Recorder Failed)
2011-07-21 19:08:10.467 MainServer, Error: PREVIEW_SUCCESS but no receivers.
2011-07-21 19:08:11.047 Reschedule interrupted, will retry
2011-07-21 19:08:11.047 Reschedule requested for id 0.
2011-07-21 19:08:11.048 Reschedule requested for id 0.
```


and of course the syslog is full of these:

```
Jul 21 19:07:24 mythbox kernel: [108745.957028] Event timed out
Jul 21 19:07:24 mythbox kernel: [108745.957042] saa7164_api_i2c_read() error, ret(2) = 0x32
Jul 21 19:07:24 mythbox kernel: [108745.957049] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:25 mythbox kernel: [108747.076028] Event timed out
Jul 21 19:07:25 mythbox kernel: [108747.076041] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:07:25 mythbox kernel: [108747.076050] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:34 mythbox kernel: [108755.957030] Event timed out
Jul 21 19:07:34 mythbox kernel: [108755.957042] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:07:34 mythbox kernel: [108755.957050] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:35 mythbox kernel: [108757.076030] Event timed out
Jul 21 19:07:35 mythbox kernel: [108757.076043] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:07:35 mythbox kernel: [108757.076052] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:07:44 mythbox kernel: [108765.957026] Event timed out
Jul 21 19:07:44 mythbox kernel: [108765.957039] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:44 mythbox kernel: [108765.957048] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:07:45 mythbox kernel: [108767.076028] Event timed out
Jul 21 19:07:45 mythbox kernel: [108767.076041] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:45 mythbox kernel: [108767.076050] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:07:49 mythbox kernel: [108770.948026] Event timed out
Jul 21 19:07:49 mythbox kernel: [108770.948039] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:49 mythbox kernel: [108770.948045] saa7164_dvb_pause_tsport() pause transition failed, ret = 0x32
Jul 21 19:07:49 mythbox kernel: [108770.968022] Event timed out
Jul 21 19:07:49 mythbox kernel: [108770.968027] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:49 mythbox kernel: [108770.968032] saa7164_dvb_pause_tsport() pause transition failed, ret = 0x32
Jul 21 19:07:54 mythbox kernel: [108775.956037] Event timed out
Jul 21 19:07:54 mythbox kernel: [108775.956050] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:54 mythbox kernel: [108775.956059] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:07:55 mythbox kernel: [108777.076029] Event timed out
Jul 21 19:07:55 mythbox kernel: [108777.076041] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:07:55 mythbox kernel: [108777.076050] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:07:59 mythbox kernel: [108780.948050] Event timed out
Jul 21 19:07:59 mythbox kernel: [108780.948064] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:59 mythbox kernel: [108780.948070] saa7164_dvb_acquire_tsport() acquire transition failed, ret = 0x32
Jul 21 19:07:59 mythbox kernel: [108780.968052] Event timed out
Jul 21 19:07:59 mythbox kernel: [108780.968058] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:07:59 mythbox kernel: [108780.968063] saa7164_dvb_acquire_tsport() acquire transition failed, ret = 0x32
Jul 21 19:08:04 mythbox kernel: [108785.957029] Event timed out
Jul 21 19:08:04 mythbox kernel: [108785.957042] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:04 mythbox kernel: [108785.957051] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:08:05 mythbox kernel: [108787.076028] Event timed out
Jul 21 19:08:05 mythbox kernel: [108787.076041] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:05 mythbox kernel: [108787.076050] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:08:09 mythbox kernel: [108790.948028] Event timed out
Jul 21 19:08:09 mythbox kernel: [108790.948041] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:08:09 mythbox kernel: [108790.948047] saa7164_dvb_stop_tsport() stop transition failed, ret = 0x32
Jul 21 19:08:09 mythbox kernel: [108790.968026] Event timed out
Jul 21 19:08:09 mythbox kernel: [108790.968035] saa7164_api_transition_port() error, ret = 0x32
Jul 21 19:08:09 mythbox kernel: [108790.968041] saa7164_dvb_stop_tsport() stop transition failed, ret = 0x32
Jul 21 19:08:14 mythbox kernel: [108795.957069] Event timed out
Jul 21 19:08:14 mythbox kernel: [108795.957078] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:14 mythbox kernel: [108795.957083] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:08:14 mythbox kernel: [108795.957087] tda18271_init: error -5 on line 826
Jul 21 19:08:14 mythbox kernel: [108795.957089] tda18271_tune: error -5 on line 904
Jul 21 19:08:14 mythbox kernel: [108795.957092] tda18271_set_params: error -5 on line 985
Jul 21 19:08:15 mythbox kernel: [108797.076042] Event timed out
Jul 21 19:08:15 mythbox kernel: [108797.076055] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:15 mythbox kernel: [108797.076065] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:08:15 mythbox kernel: [108797.076072] tda18271_init: error -5 on line 826
Jul 21 19:08:15 mythbox kernel: [108797.076078] tda18271_tune: error -5 on line 904
Jul 21 19:08:15 mythbox kernel: [108797.076083] tda18271_set_params: error -5 on line 985
Jul 21 19:08:24 mythbox kernel: [108805.957055] Event timed out
Jul 21 19:08:24 mythbox kernel: [108805.957066] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:24 mythbox kernel: [108805.957075] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Jul 21 19:08:25 mythbox kernel: [108807.076039] Event timed out
Jul 21 19:08:25 mythbox kernel: [108807.076052] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:25 mythbox kernel: [108807.076062] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Jul 21 19:08:34 mythbox kernel: [108815.957026] Event timed out
Jul 21 19:08:34 mythbox kernel: [108815.957036] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:34 mythbox kernel: [108815.957044] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:08:35 mythbox kernel: [108817.076058] Event timed out
Jul 21 19:08:35 mythbox kernel: [108817.076071] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:35 mythbox kernel: [108817.076080] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:08:44 mythbox kernel: [108825.956041] Event timed out
Jul 21 19:08:44 mythbox kernel: [108825.956053] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:44 mythbox kernel: [108825.956061] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:08:45 mythbox kernel: [108827.076038] Event timed out
Jul 21 19:08:45 mythbox kernel: [108827.076051] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:08:45 mythbox kernel: [108827.076060] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:08:55 mythbox kernel: [108836.956039] Event timed out
Jul 21 19:08:55 mythbox kernel: [108836.956051] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:08:55 mythbox kernel: [108836.956059] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:08:56 mythbox kernel: [108838.076033] Event timed out
Jul 21 19:08:56 mythbox kernel: [108838.076045] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:08:56 mythbox kernel: [108838.076053] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:09:01 mythbox CRON[4043]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jul 21 19:09:05 mythbox kernel: [108846.957028] Event timed out
Jul 21 19:09:05 mythbox kernel: [108846.957041] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:09:05 mythbox kernel: [108846.957048] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:09:06 mythbox kernel: [108848.076029] Event timed out
Jul 21 19:09:06 mythbox kernel: [108848.076043] saa7164_api_i2c_read() error, ret(1) = 0x32
Jul 21 19:09:06 mythbox kernel: [108848.076051] s5h1411_readreg: readreg error (ret == -5)
Jul 21 19:09:15 mythbox kernel: [108856.957028] Event timed out
Jul 21 19:09:15 mythbox kernel: [108856.957040] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:15 mythbox kernel: [108856.957049] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:09:16 mythbox kernel: [108858.076057] Event timed out
Jul 21 19:09:16 mythbox kernel: [108858.076070] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:16 mythbox kernel: [108858.076079] s5h1411_writereg: writereg error 0x19 0xf7 0x0000, ret == -5)
Jul 21 19:09:25 mythbox kernel: [108866.956033] Event timed out
Jul 21 19:09:25 mythbox kernel: [108866.956045] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:25 mythbox kernel: [108866.956053] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:09:26 mythbox kernel: [108868.076034] Event timed out
Jul 21 19:09:26 mythbox kernel: [108868.076047] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:26 mythbox kernel: [108868.076056] s5h1411_writereg: writereg error 0x19 0xf7 0x0001, ret == -5)
Jul 21 19:09:35 mythbox kernel: [108876.957027] Event timed out
Jul 21 19:09:35 mythbox kernel: [108876.957040] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:35 mythbox kernel: [108876.957049] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:09:36 mythbox kernel: [108878.076038] Event timed out
Jul 21 19:09:36 mythbox kernel: [108878.076051] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:36 mythbox kernel: [108878.076061] s5h1411_writereg: writereg error 0x19 0xf5 0x0001, ret == -5)
Jul 21 19:09:45 mythbox kernel: [108886.956032] Event timed out
Jul 21 19:09:45 mythbox kernel: [108886.956044] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:45 mythbox kernel: [108886.956053] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:09:45 mythbox kernel: [108886.956061] tda18271_init: error -5 on line 826
Jul 21 19:09:45 mythbox kernel: [108886.956067] tda18271_tune: error -5 on line 904
Jul 21 19:09:45 mythbox kernel: [108886.956072] tda18271_set_params: error -5 on line 985
Jul 21 19:09:46 mythbox kernel: [108888.076046] Event timed out
Jul 21 19:09:46 mythbox kernel: [108888.076059] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:46 mythbox kernel: [108888.076069] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Jul 21 19:09:46 mythbox kernel: [108888.076076] tda18271_init: error -5 on line 826
Jul 21 19:09:46 mythbox kernel: [108888.076081] tda18271_tune: error -5 on line 904
Jul 21 19:09:46 mythbox kernel: [108888.076087] tda18271_set_params: error -5 on line 985
Jul 21 19:09:55 mythbox kernel: [108896.957026] Event timed out
Jul 21 19:09:55 mythbox kernel: [108896.957038] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:55 mythbox kernel: [108896.957047] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
Jul 21 19:09:56 mythbox kernel: [108898.076037] Event timed out
Jul 21 19:09:56 mythbox kernel: [108898.076050] saa7164_api_i2c_write() error, ret(1) = 0x32
Jul 21 19:09:56 mythbox kernel: [108898.076060] s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == -5)
```

Hi,
Maybe try booting with irqpoll as a kernel commandline. I was also seeing i2c errors with my saa7164 tuners until I enabled irqpoll. I've now been running about 3 months and haven't seen a single error since then.

Regards
Ian Dobson

---

### Post by jpoet on 2011-07-23
Ian,

I noticed in your example, that when it failed the EIT scanner was running, and when it succeeded EIT scanning was disabled.  Is that consistent?  Is the EIT scanner running on all of your failures?

I am in America, so I don't typically use EIT.  I did temporarily enable EIT and made some test recordings to see if I could reproduce the problem, but so far have not been able to.

This kind of problem is always easier to fix, when it can be reproduced, and this kind of problem is always hard to reproduce!


John

---

### Post by ian dobson on 2011-07-24
> **jpoet said:**
> Ian,

I noticed in your example, that when it failed the EIT scanner was running, and when it succeeded EIT scanning was disabled.  Is that consistent?  Is the EIT scanner running on all of your failures?

I am in America, so I don't typically use EIT.  I did temporarily enable EIT and made some test recordings to see if I could reproduce the problem, but so far have not been able to.

This kind of problem is always easier to fix, when it can be reproduced, and this kind of problem is always hard to reproduce!


John

No, I just cut out some of the messages that were not relevant. I only have EIT enabled for my 2 PCI dvb-c tuners and not the network tuners.

I'm 100% sure it's a bug in the recording code for network tuners. When the recording works I see messages about "start recording" after my tuner script has run, and before when it doesn't. In both cases the backend accepts the stream as I don't see any connection errors from the process that feeds the stream into mythtv.

Regards
Ian Dobson

---

### Post by jpoet on 2011-07-24
> **ian dobson said:**
> No, I just cut out some of the messages that were not relevant. I only have EIT enabled for my 2 PCI dvb-c tuners and not the network tuners.

I'm 100% sure it's a bug in the recording code for network tuners. When the recording works I see messages about "start recording" after my tuner script has run, and before when it doesn't. In both cases the backend accepts the stream as I don't see any connection errors from the process that feeds the stream into mythtv.

Regards
Ian Dobson

I assume this is with 0.24?  Is there any chance you could try the development version of Myth?  A lot of changes have been made in this area, in the development version of Myth, and the problem ***may*** have already been fixed.

If you are not currently running the development version,  I do realize that it is tricky to test, since it has a different database schema.  Going back to 0.24 would require restoring a backup of the database.


John

---

### Post by ian dobson on 2011-07-24
Hi,

Running 24.1-fixes. I've been seeing this problem since upgrading to 24. One in about 8 recodings doesn't work.

Going to 25 is not really an option for me. I have a large video collection and don't really want to screw anything up. Maybe I could build a test box/attach a network recording an see if it works, but thats a longer job than I have time for, at the moment.

Regards
Ian Dobson

---

### Post by GeorgeBigfoot on 2011-07-30
**Distro and release (eg. Ubuntu 10.10, Fedora 13):**
MythBuntu 11.04

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
2:0.24.0+fixes.20110416.9
[B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):[/B]
Generally only update on major OS/Myth release  -ie download ISO and install from that

**Tuners you see the issue on:**
I have 2 Leadtek DTV2000DS - dual HD card (ie 4 tuners in total) [http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=56&bid=2&sid=54496](http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=56&bid=2&sid=54496)

**Other tuners on your system:**
None, only those above. I was on 9.10 but upgraded to 11.04 about a month ago. When I installed 11.04, I had 1 DTV2000DS and 1 Leadtek DTV1000S([http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=56&bid=2&sid=28602](http://www.umart.com.au/pro/products_listnew.phtml?id=10&id2=56&bid=2&sid=28602)), which I've since replaced about a week ago to be a DTV2000DS. Seems to be happening more since that replacement. 
[B]
Firmware version version (eg. 'dmesg | grep hdpvr'):[/B]
(dmesg | grep hdpvr - didn't give any results so I've just copied out the relevent seciton)

```
[   10.213306] dvb-usb: found a 'Leadtek WinFast DTV2000DS' in warm state.
[   10.214206] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.214591] DVB: registering new adapter (Leadtek WinFast DTV2000DS)
[   10.250841] af9013: firmware version:4.65.0.0
[   10.254189] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   10.262011] tda18271 0-00c0: creating new instance
[   10.264815] TDA18271HD/C2 detected @ 0-00c0
[   10.357049] r8169 0000:03:00.0: eth0: link down
[   10.357055] r8169 0000:03:00.0: eth0: link down
[   10.357451] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.603611] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.604020] DVB: registering new adapter (Leadtek WinFast DTV2000DS)
[   10.820888] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   10.824263] af9013: firmware version:4.65.0.0
[   10.835641] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   10.835861] tda18271 1-00c0: creating new instance
[   10.838012] af9015: command failed:2
[   10.839514] tda18271_read_regs: [1-00c0|M] ERROR: i2c_transfer returned: -1
[   10.839517] Unknown device (0) detected @ 1-00c0, device not supported.
[   10.839521] tda18271_attach: [1-00c0|M] error -22 on line 1270
[   10.839524] tda18271 1-00c0: destroying instance
[   10.839629] Registered IR keymap rc-empty
[   10.839725] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/usb2/2-1/rc/rc0/input5
[   10.839773] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:00.2/usb2/2-1/rc/rc0
[   10.839775] dvb-usb: schedule remote query interval to 500 msecs.
[   10.839778] dvb-usb: Leadtek WinFast DTV2000DS successfully initialized and connected.
[   11.023370] dvb-usb: found a 'Leadtek WinFast DTV2000DS' in warm state.
[   11.023431] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.023777] DVB: registering new adapter (Leadtek WinFast DTV2000DS)
[   11.027744] af9013: firmware version:4.65.0.0
[   11.030996] DVB: registering adapter 2 frontend 0 (Afatech AF9013 DVB-T)...
[   11.031167] tda18271 2-00c0: creating new instance
[   11.034120] TDA18271HD/C2 detected @ 2-00c0
[   11.259858] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   11.363289] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.363698] DVB: registering new adapter (Leadtek WinFast DTV2000DS)
[   11.580821] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   11.584318] af9013: firmware version:4.65.0.0
[   11.595697] DVB: registering adapter 3 frontend 0 (Afatech AF9013 DVB-T)...
[   11.595918] tda18271 3-00c0: creating new instance
[   11.597696] af9015: command failed:2
[   11.599321] tda18271_read_regs: [3-00c0|M] ERROR: i2c_transfer returned: -1
[   11.599324] Unknown device (0) detected @ 3-00c0, device not supported.
[   11.599328] tda18271_attach: [3-00c0|M] error -22 on line 1270
[   11.599331] tda18271 3-00c0: destroying instance
[   11.599436] Registered IR keymap rc-empty
[   11.599530] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:01.2/usb3/3-1/rc/rc1/input6
[   11.599585] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:04:01.2/usb3/3-1/rc/rc1
[   11.599587] dvb-usb: schedule remote query interval to 500 msecs.
[   11.599591] dvb-usb: Leadtek WinFast DTV2000DS successfully initialized and connected.
[   11.607483] usbcore: registered new interface driver dvb_usb_af9015
```







**Kernel Version (uname -a):**
Linux MythBox2 2.6.38-8-generic
[B]
Snippet of dmesg around the time the issue is happening:[/B]
Can't find anything specific in dmesg, I'll watch more carefully...

**Any other info you think is relevant:**
This issue wasn't happening on my old 9.10 system. I installed 11.04 from ISO and then pushed a backup of the myth database back in. I can't see any obvious links to this only happening on one tuner or any one channel. This weekend myth was scheduled to record 5 programs and 2 came back with O Byte recordings. 



Normal recording in Backend
```
2011-07-30 22:00:02.694 Started recording: "The Jackal": channel 1010 on cardid 6, sourceid 1
2011-07-30 22:00:03.706 Updating status for "The Jackal" on cardid 6 (Tuning => Recording)
2011-07-30 22:00:03.751 TVRec(6): rec->GetPathname(): '/mythFiles/recordings/1010_20110730220000.mpg'
-
-
-
-
2011-07-31 00:45:00.732 TVRec(6): Changing from RecordingOnly to None
2011-07-31 00:45:00.787 Updating status for "The Jackal" on cardid 6 (Recording => Recorded)
2011-07-31 00:45:00.788 Finished recording The Jackal: channel 1010
2011-07-31 00:45:00.838 Reschedule requested for id 0.
2011-07-31 00:45:01.168 Scheduled 61 items in 0.3 = 0.14 match + 0.17 place
2011-07-31 00:45:01.172 Finished recording The Jackal: channel 1010
-
-
-
-
2011-07-31 00:45:57.158 JobQueue: Commercial Detection Starting for "The Jackal" recorded from channel 1010 at 2011-07-30T22:00:00
```

Something I just noticed (while grabbing the backend logs above) - while it was recording, lots of errros being written to the log (stopped when recording finished), no idea if related or not, i'll go looking after this post...:
```
2011-07-31 00:42:04.598 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (936 errors)
2011-07-31 00:42:14.603 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (937 errors)
2011-07-31 00:42:24.607 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (936 errors)
2011-07-31 00:42:34.640 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (936 errors)
2011-07-31 00:42:44.645 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (933 errors)
2011-07-31 00:42:54.649 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (936 errors)
2011-07-31 00:43:04.671 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (932 errors)
2011-07-31 00:43:14.676 MythSocket(7f647400c090:38): writeStringList: Error, No data written on writeBlock (936 errors)
```





This is a recording that Failed (O bytes)```

2011-07-29 19:30:02.741 Started recording: "Better Homes and Gardens": channel 1007 on cardid 8, sourceid 1
2011-07-29 19:42:35.851 MainServer::ANN Monitor
2011-07-29 19:42:35.926 adding: MythBox2 as a client (events: 0)
2011-07-29 19:42:35.976 MainServer::ANN Monitor
2011-07-29 19:42:36.026 adding: MythBox2 as a client (events: 1)
2011-07-29 19:42:39.144 ProgramInfo(1007_20110729193000.mpg), Error: GetPlaybackURL: '1007_20110729193000.mpg' should be local, but it can not be found.
2011-07-29 19:42:39.284 ProgramInfo(1007_20110729193000.mpg), Error: GetPlaybackURL: '1007_20110729193000.mpg' should be local, but it can not be found.
2011-07-29 19:42:39.460 ProgramInfo(1007_20110729193000.mpg), Error: GetPlaybackURL: '1007_20110729193000.mpg' should be local, but it can not be found.
2011-07-29 19:42:39.997 ProgramInfo(1007_20110729193000.mpg), Error: GetPlaybackURL: '1007_20110729193000.mpg' should be local, but it can not be found.
2011-07-29 19:42:42.359 ProgramInfo(1007_20110729193000.mpg), Error: GetPlaybackURL: '1007_20110729193000.mpg' should be local, but it can not be found.
2011-07-29 19:42:49.460 ProgramInfo(1007_20110729193000.mpg), Error: GetPlaybackURL: '1007_20110729193000.mpg' should be local, but it can not be found.
```

This shows the end of the recording (which failed) and the start of the next recording (which succeeded)
```
2011-07-29 20:29:29.506 TVRec(6): ASK_RECORDING 6 29 0 0
2011-07-29 20:30:02.079 TVRec(6): Changing from None to RecordingOnly
2011-07-29 20:30:02.133 TVRec(6): HW Tuner: 6->6
2011-07-29 20:30:02.351 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
2011-07-29 20:30:02.425 Started recording: "The Lost Valentine": channel 1007 on cardid 6, sourceid 1
2011-07-29 20:30:02.570 ProgramInfo(1007_20110729193000.mpg), Error: GetPlaybackURL: '1007_20110729193000.mpg' should be local, but it can not be found.
2011-07-29 20:30:02.618 ProgramInfo(1007_20110729203000.mpg), Error: GetPlaybackURL: '1007_20110729203000.mpg' should be local, but it can not be found.
2011-07-29 20:30:02.766 ProgramInfo(1007_20110729203000.mpg), Error: GetPlaybackURL: '1007_20110729203000.mpg' should be local, but it can not be found.
2011-07-29 20:30:03.346 Updating status for "The Lost Valentine" on cardid 6 (Tuning => Recording)
2011-07-29 20:30:03.400 New DB connection, total: 4
2011-07-29 20:30:03.451 TVRec(6): rec->GetPathname(): '/mythFiles/recordings/1007_20110729203000.mpg'
2011-07-29 20:30:03.451 Connected to database 'mythconverg' at host: localhost
2011-07-29 20:40:00.220 TVRec(8): Changing from RecordingOnly to None
2011-07-29 20:40:00.297 Updating status for "Better Homes and Gardens" on cardid 8 (Tuning => Recorder Failed)
2011-07-29 20:40:00.347 Reschedule requested for id 0.
2011-07-29 20:40:00.701 Scheduled 64 items in 0.3 = 0.08 match + 0.24 place
2011-07-29 20:40:00.980 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1007 --starttime 20110729193000  > /dev/null'
```
And the second recording finishing with success:
```
2011-07-29 22:45:00.878 TVRec(6): Changing from RecordingOnly to None
2011-07-29 22:45:00.919 Updating status for "The Lost Valentine" on cardid 6 (Recording => Recorded)
2011-07-29 22:45:00.920 Finished recording The Lost Valentine: channel 1007
2011-07-29 22:45:00.974 Reschedule requested for id 0.
2011-07-29 22:45:01.290 Scheduled 62 items in 0.3 = 0.15 match + 0.15 place
2011-07-29 22:45:01.384 MainServer, Error: PREVIEW_SUCCESS but no receivers.
2011-07-29 22:45:01.396 Finished recording The Lost Valentine: channel 1007
2011-07-29 22:45:50.607 JobQueue: Commercial Detection Starting for "The Lost Valentine" recorded from channel 1007 at 2011-07-29T20:30:00
```
Reading some of the other posts in this page has given me some stuff to try/test, I'll go and try fiddling with the. Specifically tuner timeout and the EIT options.

If you need more info from me, please msg/reply and I'll get it. 

Good luck to whoever's trying to figure this out and thanks for your effort.

---

### Post by tgm4883 on 2011-08-11
Uploaded a log file from a recent occurrence of this issue. HDPVR. This has three recordings on it. The first 2 are fine, but the third one (starting at 6:00 PM) is where the issue happened. I have none of that recording.

---

### Post by GeorgeBigfoot on 2011-09-04
Well, I've managed to fix my problem but I don't think it will help the general problem sorry... 

In my last post I noted that I was going to try fiddling with some options "specifically tuner timeout and the EIT options". I did try various combinations/edits to these options (as noted in other posts in this thread but without any success). Was getting really annoying losing 1/2 of my recordings!!! I started more digging around and took a look at the linuxtv page for my tuner (ie [http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS]("http://linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS") ). At that bottom there are notes under "Making it work in Ubuntu" (in particular "Losing 1 tuner") that show how to get this working on ubuntu 11.04, however note that the default install with the 5.1 firmware requires a fix (as noted). Basically, following these instructions and turning off power management on the USB bus fixed my problem. Both tuners will now record on the one card.

As a side effect, it does seem to take longer to get a lock sometimes but I can live with that, the system is at least reliable!

Good luck to others with this problem :)

---

### Post by RecklessMW on 2011-09-08
I use to have this problem quite frequently (after upgrading to 0.24, currently running 0.24-fixes), but I have managed to solve it by a reconfiguration of my system.

Originally I had a MBE with 4xHDD and 2xDVB-T Tuners, a SBE/FE with 2xHDD, 2xDVB-T PCI Tuners (Both Mythbuntu 10.04 32 Bit) and a NAS Machine with 4x HDD (Ubuntu 10.04 64Bit), plus 2xFE Machines Netbooting.  The MBE + SBE would write to local hard drives + drives on the NAS Machine.

When system was recording 2+ Shows, and most likely commercial flagging, I would start to get 0-byte recordings.  I tried many things to solve the problem, moved the DB from the MBE to the NAS Machine, tried NFSv4, RemoteFS, Storage Groups, Bridged Network Cards in MBE and NAS, all to no avail.

Whilst I was grappling with getting the BE and FE's to shutdown when Idle, I removed all the storage from the BE's and moved them to the NAS (as the mythtv-backend process would die when one of the BE's was told by the MBE to sleep), so now my BE's have no storage, and write everything to the NAS.  It was at this point that the 0 Byte recordings stopped occurring.

My setup now looks like this:

NAS Server - MySQL Server, 7x HDD, MBE - Dummy Tuner
SBE1/FE - Network Boots, 2x PCI DVB-T Tuners, No HDD
SBE2  - Network Boots, 2x PCI DVT-T Tuners, No HDD
2x FE - Network Booting

SBE1/FE machine is my main TV, so is quite often recording and watching videos / recorded TV.  All machines are P4 3.0Ghz machines, with 2Gb RAM, Gigabit LAN

Since making this move, my MythTV System is rock solid, and saves a bit of power as well.  (Green Friendly :) )

---

### Post by PatrickD-52761 on 2011-09-17
I started getting these on a regular basis last Wednesday.  It happens on one or the other card (or both), and only when I try to schedule a recording. The Live TV works, and I can record from Live TV without any issues.  I've done complete reinstalls of Mythbuntu 11.04 and upgraded v4l using the linuxtv.org git version.

Here are the answers to the requested questions: (I'll edit this more in around 20 minutes or so, as I scheduled two recordings to reproduce this issue).

[B]Distro and release (eg. Ubuntu 10.10, Fedora 13): 
     [/B]Mythbuntu 11.04

[B] Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
      [/B]```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythtv-backend 2:0.24.0+fixes A personal video recorder application (serve
ii  mythtv-backend 2:0.24.0+fixes Metapackage to setup and configure a "Master

```[B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
     [/B]When the issue first started, I was getting the packages through the mythtv repository (addin in the Mythtv Control Centre application). Now, I'm getting them through ubuntu, and still having the issues.  As mentioned, I upgraded v4linux using the git repository at linuxtv.org, due to no sound on one tuner.
[B]  
Tuners you see the issue on:
[/B]      Hauppauge HVR-1600 (cx18) (2 tuners)
[B]
Other tuners on your system: 
     [/B]N/A although I'm going to try adding a Pinnacle PCTV80e USB to it as soon as I fix patching issues.

[B] Firmware version version (eg. 'dmesg | grep hdpvr'):
     [/B]```

[   28.397080] cx18-1: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   28.646530] cx18-1: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)

```[B] 

Kernel Version (uname -a):
     [/B]Linux dcky-mythbuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux

[B]
Snippet of dmesg around the time the issue is happening:
[/B]```

[ 1970.821153] usb 2-1.2: new low speed USB device using uhci_hcd and address 5
[ 1970.968842] input: USB Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input9
[ 1970.969268] generic-usb 0003:0461:4D0F.0006: input,hidraw4: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:10.0-1.2/input0
[ 1979.172477] i2c i2c-3: sendbytes: NAK bailout.
[ 1979.172548] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1985.939824] i2c i2c-3: sendbytes: NAK bailout.
[ 1985.939895] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1985.953118] i2c i2c-3: sendbytes: NAK bailout.
[ 1985.985208] i2c i2c-3: sendbytes: NAK bailout.
[ 1985.985289] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1985.997822] i2c i2c-3: sendbytes: NAK bailout.
[ 1986.031426] i2c i2c-3: sendbytes: NAK bailout.
[ 1986.031502] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1986.051147] i2c i2c-3: sendbytes: NAK bailout.
[ 1986.069192] i2c i2c-3: sendbytes: NAK bailout.
[ 1986.069285] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1986.081750] i2c i2c-3: sendbytes: NAK bailout.
[ 1988.401310] i2c i2c-3: sendbytes: NAK bailout.
[ 1988.401381] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1988.415003] i2c i2c-3: sendbytes: NAK bailout.
[ 1989.191020] i2c i2c-3: sendbytes: NAK bailout.
[ 1989.191099] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1995.443174] i2c i2c-3: sendbytes: NAK bailout.
[ 1995.443246] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1995.456390] i2c i2c-3: sendbytes: NAK bailout.
[ 1998.910743] i2c i2c-3: sendbytes: NAK bailout.
[ 1998.910814] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1998.930033] i2c i2c-3: sendbytes: NAK bailout.
[ 1998.966504] i2c i2c-3: sendbytes: NAK bailout.
[ 1998.966583] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 1998.988154] i2c i2c-3: sendbytes: NAK bailout.
[ 1999.204539] i2c i2c-3: sendbytes: NAK bailout.
[ 1999.204612] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2004.745615] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[ 2009.220540] i2c i2c-3: sendbytes: NAK bailout.
[ 2009.220612] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2019.236518] i2c i2c-3: sendbytes: NAK bailout.
[ 2019.236590] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2029.253324] i2c i2c-3: sendbytes: NAK bailout.
[ 2029.253396] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2039.268487] i2c i2c-3: sendbytes: NAK bailout.
[ 2039.268559] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2049.286738] i2c i2c-3: sendbytes: NAK bailout.
[ 2049.286820] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2059.304634] i2c i2c-3: sendbytes: NAK bailout.
[ 2059.304714] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2069.316486] i2c i2c-3: sendbytes: NAK bailout.
[ 2069.316557] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2079.332514] i2c i2c-3: sendbytes: NAK bailout.
[ 2079.332586] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2089.348507] i2c i2c-3: sendbytes: NAK bailout.
[ 2089.348579] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2099.364476] i2c i2c-3: sendbytes: NAK bailout.
[ 2099.364547] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2109.380476] i2c i2c-3: sendbytes: NAK bailout.
[ 2109.380548] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2119.396476] i2c i2c-3: sendbytes: NAK bailout.
[ 2119.396547] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2129.412499] i2c i2c-3: sendbytes: NAK bailout.
[ 2129.412570] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2139.428476] i2c i2c-3: sendbytes: NAK bailout.
[ 2139.428547] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2149.444541] i2c i2c-3: sendbytes: NAK bailout.
[ 2149.444612] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2159.466047] i2c i2c-3: sendbytes: NAK bailout.
[ 2159.466128] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2169.476492] i2c i2c-3: sendbytes: NAK bailout.
[ 2169.476563] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2179.492785] i2c i2c-3: sendbytes: NAK bailout.
[ 2179.492856] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2189.508498] i2c i2c-3: sendbytes: NAK bailout.
[ 2189.508569] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2199.524487] i2c i2c-3: sendbytes: NAK bailout.
[ 2199.524559] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2209.540561] i2c i2c-3: sendbytes: NAK bailout.
[ 2209.540633] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2219.556486] i2c i2c-3: sendbytes: NAK bailout.
[ 2219.556558] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2229.573187] i2c i2c-3: sendbytes: NAK bailout.
[ 2229.573261] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2239.588487] i2c i2c-3: sendbytes: NAK bailout.
[ 2239.588558] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2249.604485] i2c i2c-3: sendbytes: NAK bailout.
[ 2249.604557] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2259.620541] i2c i2c-3: sendbytes: NAK bailout.
[ 2259.620613] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2269.636475] i2c i2c-3: sendbytes: NAK bailout.
[ 2269.636547] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2279.652519] i2c i2c-3: sendbytes: NAK bailout.
[ 2279.652592] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2289.668829] i2c i2c-3: sendbytes: NAK bailout.
[ 2289.668899] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2299.684488] i2c i2c-3: sendbytes: NAK bailout.
[ 2299.684559] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2309.700487] i2c i2c-3: sendbytes: NAK bailout.
[ 2309.700559] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2312.227853] i2c i2c-3: sendbytes: NAK bailout.
[ 2312.227925] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2312.241018] i2c i2c-3: sendbytes: NAK bailout.
[ 2312.253206] i2c i2c-3: sendbytes: NAK bailout.
[ 2312.253277] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2312.267440] i2c i2c-3: sendbytes: NAK bailout.
[ 2319.716496] i2c i2c-3: sendbytes: NAK bailout.
[ 2319.716568] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2329.732498] i2c i2c-3: sendbytes: NAK bailout.
[ 2329.732570] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2339.748561] i2c i2c-3: sendbytes: NAK bailout.
[ 2339.748634] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2349.764502] i2c i2c-3: sendbytes: NAK bailout.
[ 2349.764574] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2359.783786] i2c i2c-3: sendbytes: NAK bailout.
[ 2359.783861] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[ 2369.796793] i2c i2c-3: sendbytes: NAK bailout.
[ 2369.796865] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID


```[B]
Any other info you think is relevant:[/B]

I've posted about this on mythtvtalk, and tried removing the tuners/input sources, then running mysql and truncating the tables for cardinput and capturecard. Then I readded the capture cards and input sources.  This didn't resolve the issue at all.  [Here]("http://www.mythtvtalk.com/recording-using-hauppage-hvr-1600-hit-miss-what-do-15044/") is my thread on mythtvtalk about the problem.

I noticed that my mouse and keyboard showed up in the dmesg output, along with a probe of an external usb drive (which holds one of my storage locations). The line for the USB Drive is

```

[ 2004.745615] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)

```

Which makes me wonder if it's something to do with it not being able to access that storage location.

*****UPDATE***** I may have fixed the issue. I removed my External USB drive from the storage locations, and tried a test recording with both tuners. They are recording as I type.  I'm trying another one (scheduled two shows at the same time on "use any available input"), and if they record, I'll call this issue solved (for me at least).  


Have a great day:)
Patrick.

---

### Post by johnlatz on 2011-10-09
**Distro and release (eg. Ubuntu 10.10, Fedora 13):**
MythBuntu 11.04

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
2:0.24.0+fixes.20110425.56c
[B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):[/B]
mythbuntu repos

**Tuners you see the issue on:**
Hauppauge HVR-2250: digital recording only, analog recordings are always good

**Other tuners on your system:**
I also have an HVR-1600 on which the mechanical input for the digital side is physically broken, so it is only an analog card - and I never have trouble with analog recordings
[B]
Firmware version version (eg. 'dmesg | grep *firmware*'):[/B]
   [ 19.100075] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   19.694337] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   19.834650] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   20.708889] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   20.728876] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)

**Kernel Version (uname -a):**
Linux Mythbox 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
[B]
Snippet of dmesg around the time the issue is happening:[/B]
Not from dmseg (nothing there around the time of the issue), this is from mythbackend.log
```
2011-10-09 08:29:00.374 Reschedule requested for id 0.
2011-10-09 08:29:05.283 Scheduled 397 items in 4.9 = 0.07 match + 4.82 place
2011-10-09 08:29:05.467 scheduler: Scheduled items: Scheduled 397 items in 4.9 = 0.07 match + 4.82 place
2011-10-09 08:29:29.825 TVRec(3): ASK_RECORDING 3 29 0 0
2011-10-09 08:29:30.178 TVRec(12): ASK_RECORDING 12 29 0 0
2011-10-09 08:29:30.414 TVRec(11): ASK_RECORDING 11 29 0 0
2011-10-09 08:30:03.003 TVRec(11): Changing from None to RecordingOnly
2011-10-09 08:30:03.078 TVRec(11): HW Tuner: 11->11
2011-10-09 08:30:03.618 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 7 min
2011-10-09 08:30:03.687 Started recording: "Peep and the Big Wide  World/Pocoyo":"Current Events; Quack Loses His Hat; Pocoyo -- Pocoyo's  Balloon": channel 65639 on cardid 11, sourceid 2
2011-10-09 08:30:03.739 scheduler: Started recording: "Peep and the Big  Wide World/Pocoyo":"Current Events; Quack Loses His Hat; Pocoyo --  Pocoyo's Balloon": channel 65639 on cardid 11, sourceid 2
2011-10-09 08:30:04.439 ProgramInfo(65639_20111009083000.mpg), Error:  GetPlaybackURL: '65639_20111009083000.mpg' should be local, but it can  not be found.
2011-10-09 08:30:04.622 ProgramInfo(65639_20111009083000.mpg), Error:  GetPlaybackURL: '65639_20111009083000.mpg' should be local, but it can  not be found.
2011-10-09 08:30:04.859 ProgramInfo(65639_20111009083000.mpg), Error:  GetPlaybackURL: '65639_20111009083000.mpg' should be local, but it can  not be found.

```[B]

Any other info you think is relevant:[/B]
**ONLY HAPPENS** with one of the two digital recorders on the card:
Encoder 4 [ DVB : /dev/dvb/adapter1/frontend0 ] is local on Mythbox and is not recording.
    Encoder 5 [ DVB : /dev/dvb/adapter1/frontend0 ] is local on Mythbox and is not recording.
    Encoder 11 [ DVB : /dev/dvb/adapter2/frontend0 ] is local on Mythbox and is not recording.
    Encoder 12 [ DVB : /dev/dvb/adapter2/frontend0 ] is local on Mythbox and is not recording.
Digital-1 (Encoder 4 & 5) never ever suffers a recording issue.  Digital-2 (Encoder 11 & 12) does sporadically.  I have tried deleting and reinstalling all my cards from mythbackend - didn't help.  I have successfully recorded two channels on the same card when the two shows were on the same carrier frequency, but still I've tried forcing only one encoder per card - didn't help.    Suspected it might be an issue with throughput to disk (if I were recording too many shows for the buses), doesn't seem to be correlated to how many recordings are concurrent.  

My other suspicion is that my signal quality may be poor - I have a separate cable coax going to the TV, and certain digital channels that should be there are unable to be scanned by the TV; on other frequencies, I get signal dropouts on the TV (the screen will go blank for a significant fraction of one second, the TV will report "No signal", then the video will come back), but then the recordings on those frequencies are pristine.   I've tried upping the timeout for Myth to lock channel to no avail.  But then again - why would Digital-2 have problems when Digital-1 never does?

My family uses Myth exclusively as a timeshift device - we do not watch live TV through the Myth system.  Every recording is scheduled through the Mythweb interface, and it does *seem* that certain frequencies are more susceptible to the issue than others, but that may just be a result of how much PBS we record relative to any other channel.

---

### Post by jimmybondo on 2011-10-10
Distro and release (eg. Ubuntu 10.10, Fedora 13): 
```
Ubuntu 11.04
```
Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):
```
mythtv-backend 2:0.24.1+fixes.20110911.8f865a6-0ubuntu0mythbu
mythtv-backend-master                        2:0.24.1+fixes.20110911.8f865a6-0ubuntu0mythbu
```

Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):
> mythbuntu nightly repos
Tuners you see the issue on:
> HDPVR
Other tuners on your system:
> None
Firmware version version (eg. 'dmesg | grep hdpvr'):
> Command did not yield any results, haven't upgraded firmware. I bought the tuner 1.5 years ago.
Kernel Version (uname -a):
```
Linux ginny 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
Snippet of dmesg around the time the issue is happening:
I don't have the start of the issue as my dmesg has filled with repetitions of this:
```
[1215436.890146] lirc_zilog: unable to read from the IR chip after 3 resets, giving up
[1215438.149248] lirc_zilog: i2c_master_send failed with -110
[1215438.149252] lirc_zilog: polling the IR receiver chip failed, trying reset
```
Any other info you think is relevant:

I wrote a script to restart everything and preserve uptime (for bragging rights):

```
sudo /etc/init.d/mythtv-backend stop
sudo rmmod hdpvr
sudo modprobe hdpvr
sudo rmmod lirc_zilog
sudo modprobe lirc_zilog
sudo /etc/init.d/mythtv-backend start
```

This requires a hdpvr power cycle, then reloads both the hdpvr driver, then the lirc_zilog IR blaster driver.

---

### Post by ian dobson on 2011-10-10
> **jimmybondo said:**
> Distro and release (eg. Ubuntu 10.10, Fedora 13): 
```
[1215436.890146] lirc_zilog: unable to read from the IR chip after 3 resets, giving up
[1215438.149248] lirc_zilog: i2c_master_send failed with -110
[1215438.149252] lirc_zilog: polling the IR receiver chip failed, trying reset
```
Any other info you think is relevant:



Maybe try booting with the irqpoll option. I was having i2c errors from my dvb cards until I enabled it.

Regards
Ian Dobson

---

### Post by ktmom on 2011-11-14
As it turns out, all of my problems seem to stem from my hardware and collisions.  I've had much better success for the last 6 weeks or so, in-spite of OTA atmospheric interference (always guaranteed to trigger the problem).

I don't fully understand, but what I know for sure is by adding an additional hard drive into my storage groups, and distributing recordings that coincide to different drives, my 0-byte recordings have been almost eliminated.  The only ones I still get are when a family member adds a recording and doesn't ensure it's on a different storage group.  The good news is, even if I get a 0-byte recording on one drive, the recordings on the other drive stay intact.

So, now I need to figure out where the gate is and if it's fixable (short of limiting my recordings :) ).  Either the HDD I'm using is to slow or the bus feeding it is.  I am probably going to start with upgrading the motherboard and then see what happens.

---

### Post by sbrattonuk on 2011-11-23
Distro and release: Mythbuntu 11.10  
Where you get your mythtv packages from: mythbuntu repos
 Tuners you see the issue on:  USB Dual Kworld U399.
 Firmware version version:  as included with Mythbuntu 11.10
 Kernel Version: as with Mythbuntu 11.10 (3.0.3 ?)

 Any other info you think is relevant:

Backend logs show that the recording has started but no log of it finishing.
First setup was working fine, but now every recording is 0 byte

Sorry for lack of version info & logs etc, I'm not currently connected to BackEnd.

Need to check storage location and access, I changed this early on to a 2nd HDD. 
Steven

---

### Post by jimmybondo on 2011-11-29
> **ian dobson said:**
> Maybe try booting with the irqpoll option. I was having i2c errors from my dvb cards until I enabled it.

Regards
Ian Dobson

I just got around to trying this and it helped for about a week. Here is what I did:

```
sudo vi /etc/default/grub
<add irqpoll to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll">
sudo update-grub
reboot
```

However, now I am getting the same errors in dmesg:
```
[630147.775683] lirc_zilog: i2c_master_send failed with -110
[630147.775686] lirc_zilog: polling the IR receiver chip failed, trying reset
[630148.874773] lirc_zilog: i2c_master_send failed with -110
[630148.874775] lirc_zilog: polling the IR receiver chip failed, trying reset
[630149.973998] lirc_zilog: i2c_master_send failed with -110
[630149.974000] lirc_zilog: polling the IR receiver chip failed, trying reset
[630151.073215] lirc_zilog: i2c_master_send failed with -110
[630151.073217] lirc_zilog: unable to read from the IR chip after 3 resets, giving up
```

Any ideas? I seem to get recordings that are only a few bytes long, then all subsequent recordings are 0-bytes.

Thanks,
Jim

---

### Post by ian dobson on 2011-11-29
> **jimmybondo said:**
> I just got around to trying this and it helped for about a week. Here is what I did:

```
sudo vi /etc/default/grub
<add irqpoll to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll">
sudo update-grub
reboot
```

However, now I am getting the same errors in dmesg:
```
[630147.775683] lirc_zilog: i2c_master_send failed with -110
[630147.775686] lirc_zilog: polling the IR receiver chip failed, trying reset
[630148.874773] lirc_zilog: i2c_master_send failed with -110
[630148.874775] lirc_zilog: polling the IR receiver chip failed, trying reset
[630149.973998] lirc_zilog: i2c_master_send failed with -110
[630149.974000] lirc_zilog: polling the IR receiver chip failed, trying reset
[630151.073215] lirc_zilog: i2c_master_send failed with -110
[630151.073217] lirc_zilog: unable to read from the IR chip after 3 resets, giving up
```

Any ideas? I seem to get recordings that are only a few bytes long, then all subsequent recordings are 0-bytes.

Thanks,
Jim

Hi, 
Do you see any other error messages in the log files, somthing along the lines of:
 interrupt X, but nobody cared (try irqpoll)

If you saw a nobody cared error, and If your running 11.10 then the irqpoll should fix the i2c errors, but due to a small bug in kernels > 2.6.39 irqpoll doesn't work. There's a patch upstream that should make it into the 11.10 kernel sometime soon.

The patch is actually really small (a 1 liner) so if you want to compile your own kernel, let me know and I'll dig out the information and post it here.

Regards
Ian Dobson

---

### Post by jimmybondo on 2011-11-30
> **ian dobson said:**
> Hi, 
Do you see any other error messages in the log files, somthing along the lines of:
 interrupt X, but nobody cared (try irqpoll)


I am actually on 11.04:

```
user@ginny:~$ uname -a
Linux ginny 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
user@ginny:~$ cat /etc/issue
Ubuntu 11.04 \n \l
```

So this should of worked, any more ideas or are any more logs helpful?
JIm

---

### Post by ian dobson on 2011-11-30
> **jimmybondo said:**
> I am actually on 11.04:

```
user@ginny:~$ uname -a
Linux ginny 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
user@ginny:~$ cat /etc/issue
Ubuntu 11.04 \n \l
```

So this should of worked, any more ideas or are any more logs helpful?
JIm

Is irqpoll actually enabled? What do you see when you do
 dmesg | grep command

The irqpoll bug hit kernel > 2.6.39 so you should be safe from it.

Regards
Ian Dobson

---

### Post by jimmybondo on 2011-11-30
> **ian dobson said:**
> Is irqpoll actually enabled? What do you see when you do
 dmesg | grep command

Looks like it is:

```
@ginny:~$ dmesg | grep command
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=14269af7-9967-47ba-a9e7-604442117bb7 ro splash vga=799 quiet splash irqpoll vt.handoff=7
```

Jim

---

### Post by ian dobson on 2011-11-30
> **jimmybondo said:**
> Looks like it is:

```
@ginny:~$ dmesg | grep command
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=14269af7-9967-47ba-a9e7-604442117bb7 ro splash vga=799 quiet splash irqpoll vt.handoff=7
```

Jim

Hi,

Then sorry I'm not sure what your problem is.

Regards
Ian Dobson

---

### Post by stefanst on 2011-12-25
**Distro and release (eg. Ubuntu 10.10, Fedora 13):**
Mythbuntu 11.10

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
 2:0.24.0+fixes.20110908.1de0431-0ubun
[B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):[/B]
Mythbuntu

**Tuners you see the issue on:**
HD PVR

**Other tuners on your system:**
None

**Firmware version version (eg. 'dmesg | grep hdpvr')**
```
[   25.071685] hdpvr 1-2:1.0: firmware version 0xf dated Mar 11 2009 06:03:02
[   25.071688] hdpvr 1-2:1.0: untested firmware, the driver might not work.
[   25.256293] hdpvr 1-2:1.0: device now attached to video0
```

**Kernel Version (uname -a):**
 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
Couldn't find anything remarkable, but here it goes:
```
[ 2342.471796] show_signal_msg: 6 callbacks suppressed
[ 2342.471801] mythpreviewgen[2145]: segfault at b3138130 ip 0538e43a sp b2449d00 error 6 in libmythavcodec.so.52.86.1[4fec000+513000]
```


**Any other info you think is relevant:**
About 50% or so of my recordings end up as 0 byte. When I get ONE 0byte recording, I have to restart the HD-PVR, otherwise all subsequent recordings are 0byte too. 
Sometimes the 0byte recordings don't happen for a week, at other times it happens constantly.  
This started happening shortly after a distro-upgrade. I believe it was when upgrading Myth 0.23 to 0.24, but I am NOT absolutely certain.
Even though I am currently running 11.10, it also happened with 11.4. I did two clean installs, issue was not fixed. I am currently considering dumping all recordings and going back to 0.23.

---

### Post by taptap1 on 2012-01-03
Hi All,

A simple question: Is this thread going anywhere/is a dev actually  looking at this? I don't expect a solution, I'd just like to know if  anything's going on in the background.

Regards
Ian Dobson




 [**vacances au vietnam**](http://www.passionvietnamtravel.com)| [**tour au vietnam**](http://www.passionvietnamtravel.com)| [**circuit au vietnam**](http://www.passionvietnamtravel.com)| [**circuit vietnam**](http://www.passionvietnamtravel.com)| [**voyage au vietnam**](http://www.passionvietnamtravel.com)| [**voyage vietnam**](http://www.passionvietnamtravel.com)| [**do go noi that**](http://dogo.thuongmaikinhbac.com) | [**lap dat camera**](http://lapdatcamera.thuongmaikinhbac.com) | [**vacances au vietnam**](http://fr.passionvietnamtravel.com) |  [**voyage au vietnam**](http://fr.passionvietnamtravel.com) |[**mua ban**](http://raovat.thuongmaikinhbac.com/) -  [**rao vat mien phi**](http://raovat.thuongmaikinhbac.com/)
[Thông tin th&#432;&#417;ng m&#7841;i]("http://thuongmaikinhbac.com")

---

### Post by ktmom on 2012-01-04
I just want to say that all of my problems are resolved by actually making use of the storage directories from within Mythtv.  I still have my older/slower SATA drives in use, but by allowing the system to determine load balancing, I am able to record on 4 channels simultaneously and without regard to one of the station's signals getting atmospheric interference (OTA).  Since actually setting my system up the way the designers seemed to have envisioned it, I have gone from ~40-50% of my recordings being lost, to no 0-byte recordings at all.  And the system is transcoding up to 2 shows at a time while recording.

In my case, I mark this down to operator error :redface:

---

### Post by ubnewbie2 on 2012-01-07
**Distro and release (eg. Ubuntu 10.10, Fedora 13):** mythbuntu 11.10

**Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):** downloaded live CD
Tuners you see the issue on: unknown, but all tuners are DVB

**Any other info you think is relevant:**  Noticed I was getting failure to lock on live TV, so I doubled the default timeout.  I think it needs to be a bit longer still, because maybe this caused the 0 byte recording.

**Edit: ** noticed this was happening on one channel only so far - all in one digital transport stream, that is.  Doubled my signal and tuning timeouts in the card config for all cards.  First couple of tests worked, so will monitor and see what happens.

---

### Post by dborn on 2012-01-08
**Distro and release (eg. Ubuntu 10.10, Fedora 13):**
 Mythbuntu 10.04 LTS

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
 mythtv-backend 0.23.1+fixes26 A personal video recorder application (serve
mythtv-backend 0.23.1+fixes26 Metapackage to setup and configure a "Master
[B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):[/B]
Mythbuntu

**Tuners you see the issue on:**
HD PVR

**Other tuners on your system:**
HVR-2250 (using analog for SD cable) Happened before adding this tuner.

**Firmware version version (eg. 'dmesg | grep hdpvr')**
 	Code:
 	[   11.601821] hdpvr 1-7:1.0: untested firmware version 0x15, the driver might not work
[   11.928897] hdpvr 1-7:1.0: device now attached to video0
[   11.928916] usbcore: registered new interface driver hdpvr


**Kernel Version (uname -a):**
 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:32:42 UTC 2011 x86_64 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
System has been rebooted since the last time, so nothing to give you.
[B]

Any other info you think is relevant:[/B]
I am using Gavin Hurlbut's "hdpvr killer device" to automatically power cycle the hd-pvr when it locks up. It doesn't happen very frequently but once in a while. The last few times it happened are on 2011-12-12, 2011-12-19 and 2011-12-23 and none since.
I've seen this happen for a long time, always on 0.23 and through several different kernel upgrades.
The blue halo will stay on from the last successful recording and will then fail on the next start of recording. Once it locked in switching to Live TV and rebooting the computer alone (couldn't get out of Live TV mode) fixed the problem, without having to power cycle the HD-PVR.

HD-PVR is Rev D2, power supply fried recently so I replaced it with another 5V, 2A switching PS with no difference in locking behaviour.
HD-PVR is connected to USB2 port on it's own bus

**lsusb:**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 002: ID 0bc7:0008 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1241:f766 Belkin 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 2040:4901 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by PatrickD-52761 on 2012-01-09
> **dborn said:**
> **Distro and release (eg. Ubuntu 10.10, Fedora 13):**
 Mythbuntu 10.04 LTS

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
 mythtv-backend 0.23.1+fixes26 A personal video recorder application (serve
mythtv-backend 0.23.1+fixes26 Metapackage to setup and configure a "Master
[B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):[/B]
Mythbuntu

**Tuners you see the issue on:**
HD PVR

**Other tuners on your system:**
HVR-2250 (using analog for SD cable) Happened before adding this tuner.

**Firmware version version (eg. 'dmesg | grep hdpvr')**
 	Code:
 	[   11.601821] hdpvr 1-7:1.0: untested firmware version 0x15, the driver might not work
[   11.928897] hdpvr 1-7:1.0: device now attached to video0
[   11.928916] usbcore: registered new interface driver hdpvr


**Kernel Version (uname -a):**
 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:32:42 UTC 2011 x86_64 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
System has been rebooted since the last time, so nothing to give you.
[B]

Any other info you think is relevant:[/B]
I am using Gavin Hurlbut's "hdpvr killer device" to automatically power cycle the hd-pvr when it locks up. It doesn't happen very frequently but once in a while. The last few times it happened are on 2011-12-12, 2011-12-19 and 2011-12-23 and none since.
I've seen this happen for a long time, always on 0.23 and through several different kernel upgrades.
The blue halo will stay on from the last successful recording and will then fail on the next start of recording. Once it locked in switching to Live TV and rebooting the computer alone (couldn't get out of Live TV mode) fixed the problem, without having to power cycle the HD-PVR.

HD-PVR is Rev D2, power supply fried recently so I replaced it with another 5V, 2A switching PS with no difference in locking behaviour.
HD-PVR is connected to USB2 port on it's own bus

**lsusb:**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 002: ID 0bc7:0008 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1241:f766 Belkin 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 2040:4901 Hauppauge 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm not sure if this will help you or not, but you might want to check over at [http://www.linuxtv.org](http://www.linuxtv.org) (the people who are creating the drivers for your TV Tuner).  Taylor Ralph (might be Ralph Taylor also) submitted a patch for the HD-PVR that's supposed to help it work with firmware versions > 15. I realize that your version is 15, but his patch may have fixed some of your issues.

Plus, you can post the issue there on their mailing list, and possibly get help with it.

Have a great day:)
Patrick.

---

### Post by ubnewbie2 on 2012-01-20
Hmmm, thought things were going well, but I just got three 0-byte recordings in one night !!!  One of them I really wanted :(

Are any fixes coming through trying to address this issue??

---

### Post by ubnewbie2 on 2012-01-22
Edit:   I seem to have this solved now.  Guess I am one the lucky ones, but the fix for me was to add  vmalloc=192M  to the GRUB_CMDLINE_LINUX_DEFAULT  line in Grub's config.

=======================================================

0 byte recordings is getting so bad I can't rely on mythtv to record shows.  I am missing 2 or 3 every night lately.


Distro and release (eg. Ubuntu 10.10, Fedora 13): Mythbuntu 11.10

Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):  mythtv-backend 2:0.24.1+fixes

Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc): mythbuntu 

Tuners you see the issue on: WinFast DTV1000-T cx2388x based DVB/ATSC card (2 of these) and ASUS My Cinema U3100 Mini DVBT Tuner

Other tuners on your system: no others

Firmware version version (eg. 'dmesg | grep hdpvr'): n/a
Kernel Version (uname -a):Linux mythbuntu4 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:45:26 UTC 2012 i686 athlon i386 GNU/Linux


Snippet of dmesg around the time the issue is happening:


Any other info you think is relevant:
mythbackend log

> 2012-01-22 21:14:29.579 TVRec(3): ASK_RECORDING 3 29 0 0
2012-01-22 21:15:02.965 TVRec(3): Changing from None to RecordingOnly
2012-01-22 21:15:03.026 TVRec(3): HW Tuner: 3->3
2012-01-22 21:15:03.460 AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 4 min
2012-01-22 21:15:03.666 Started recording: "Jurassic Park III": channel 1073 on cardid 3, sourceid 1
[B]2012-01-22 21:15:03.853 DVBSH(/dev/dvb/adapter1/frontend0) Warning: Opening DVR device /dev/dvb/adapter1/dvr0 failed : Cannot allocate memory
2012-01-22 21:15:04.009 DVBSH(/dev/dvb/adapter1/frontend0): [/B]**Failed to open DVR device /dev/dvb/adapter1/dvr0 : Cannot allocate memory**
2012-01-22 21:15:04.112 ProgramInfo(1073_20120122211500.mpg), Error: GetPlaybackURL: '1073_20120122211500.mpg' should be local, but it can not be found.
2012-01-22 21:15:04.202 ProgramInfo(1090_20120122183000.mpg), Error: GetPlaybackURL: '1090_20120122183000.mpg' should be local, but it can not be found.
2012-01-22 21:15:13.207 AutoExpire: CalcParams(): Max required Free Space: 7.0 GB w/freq: 4 min

---

### Post by Whitebeam on 2012-02-12
**Distro and release (eg. Ubuntu 10.10, Fedora 13):**
 Mythbuntu 11.10

**Full version of the MythTV Backend package (eg. dpkg -l mythtv-backend*):**
 mythtv-backend 2:0.24.2+fixes
[B]
Where you get your mythtv packages from (standard repos, avenard repos, mythbuntu repos, compile from source, etc):[/B]
Mythbuntu repos

**Tuners you see the issue on:**
2 x Hauppauge Nova-T DVB-T USB Stiicks

**Other tuners on your system:**
None.

**Firmware version version (eg. 'dmesg | grep hdpvr')**
 	Not certain what you want here - dmesg | grep dvb didn't suggest a firmware version

**Kernel Version (uname -a):**
 3.0.0.15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux

**Snippet of dmesg around the time the issue is happening:**
System has been rebooted since the last time, so nothing to give you.
[B]

Any other info you think is relevant:[/B]
Zero length recordings on 80% of attempts until I disabled EIT scanning, now seems to work 100% using XMLTV.

Tuning delays of 350ms and 425ms in the tuning options for the cards.

Max of 2 recordings per tuner

**lsusb:**
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 005 Device 002: ID 2040:7060 Hauppauge Nova-T Stick 2
  Bus 005 Device 003: ID 2040:7060 Hauppauge Nova-T Stick 2
   
Peter

---

### Post by shadowlordKT on 2012-03-01
I was experiencing daily 0-byte recordings to the point where my HD-PVR was essentially unreliable/useless.  It would require a reboot of the MythTV machine to get it working again.

Then I read a thread about inadequate ventilation of the HD-PVR and bought a mini wire-rack shelf from the local dollar store.  After placing the HD-PVR on top of it (now with 2-3 inches clearance below it), the difference was night and day, and I'm running nearly 3 months without a single 0-byte recording.

I haven't changed any other settings/software, kernels or distros during this time.

---

### Post by tgm4883 on 2012-03-02
> **shadowlordKT said:**
> I was experiencing daily 0-byte recordings to the point where my HD-PVR was essentially unreliable/useless.  It would require a reboot of the MythTV machine to get it working again.

Then I read a thread about inadequate ventilation of the HD-PVR and bought a mini wire-rack shelf from the local dollar store.  After placing the HD-PVR on top of it (now with 2-3 inches clearance below it), the difference was night and day, and I'm running nearly 3 months without a single 0-byte recording.

I haven't changed any other settings/software, kernels or distros during this time.

That is kinda what I was feeling about this issue. I tend to think it's highly dependent on hareware revision and environment.

---

### Post by pyite on 2012-04-07
I never had this happen until the latest Ubuntu Precise update (kernel is 3.2.0-22-generic #35-Ubuntu SMP Tue Apr 3) and now it happens every time.

No problems on my 11.10 machine.  Actually even if I use an older kernel, it still happens with Precise.  @%&@%&@%&

Anyone else seeing this?

---

### Post by jamoody on 2012-09-22
I've recently upgraded from MythTV 0.24 to 0.25-2 and I now get intermittent recording failures which prevent all future recordings until reboot. I've deleted all tuners and re-added them after the upgrade with no change.  Several dozen MultiRec recordings will happen just fine, and then a recording gets "stuck" on a tuner and all future recordings on any tuner seem to not get dispatched. Several hours after the recording should have ended the "stuck" recording is still shown as green in Previous Recordings list along with status O, implying it is still recording, but no file is created; missed recordings don't show in the Previous Recordings list at all. After reboot the missed recordings show as red with status M in the Previous Recordings list.  So far all failures have occurred only on HD-5500 (2 different systems) and only when MultiRec>=2. HDHomeRun with default MultiRec=2 so far has not shown the problem. Also HD-5500 with MultiRec=1 (no MuntiRec) has not shown the problem.  I can't see anything in the mythbackend.log to give any insite into the failure.

---

### Post by The Toastcutter on 2012-11-03
> **pyite said:**
> I never had this happen until the latest Ubuntu Precise update (kernel is 3.2.0-22-generic #35-Ubuntu SMP Tue Apr 3) and now it happens every time.

No problems on my 11.10 machine.  Actually even if I use an older kernel, it still happens with Precise.  @%&@%&@%&

Anyone else seeing this?

Bit of a late reply here, but I've recently gone done a two-step update.

First from 11.10/0.24 to 11.10/0.25, which worked fine, then after a week or two updated to 12.04/0.25.

Since the 12.04 update I get maybe one in ten recordings work, the other 9 out of ten are zero byte.

I have two tuners, a Sony PlayTV and an Asus 3100 Mini, both which use  the dib0700 chipset, and get the same results when using either. I've deleted them and re-added them, tried increasing the tuning timeout and the tuning delay, all without any joy.

I've got clonezilla backups of both versions and have switched back and forth between the two, and its fully repeatable.


I just tried a mainline kernel, 3.3.0-994.201203080434, and the problem still occurs with that.

Planning on trying 12.10 and 0.26, separately and together.

Edit: 0.26 hasn't fixed it (it doesn't look like a MythTV problem)

Edit: running with the previous precise kernel (linux-image-3.2.0-31-generic-pae ) seems to have fixed it. Either the current version is broken, or something went wrong during my 11.10->12.04 upgrade. I guess I'll find out when 3.2.0-33 comes along.

---

### Post by Rocco64 on 2012-11-19
Zero-byte recordings have been a particular problem for me since upgrading my system to Mythbuntu 12.04 + MythTV 0.25 (currently kernel 3.2.0-33), and do not appear to have been helped much by moving forward to MythTV 0.26.

My tuner is a USB HVR-950Q. It is attached to a terrestrial ATSC antenna with good reception, which is the only signal/input source.

I also experience "Error opening jump program file buffer" when changing channels in LiveTV mode and frequent "Partial Lock" behaviour when tuning the channels.  This was new to me with 12.04+0.25.  Previously I was running 11.10 and MythTV 0.24 and never saw this; it happens all the time now. I have not seen any discussion relating these behaviours... but I find it odd that they should manifest at the same time. My gut tells me the Partial Lock on channel tuning bears some relation to the failed recordings.

The zero-byte recordings were intermittent (say once per week) with 11.10+0.24 but now they have become closer to once per day. The behaviour is inconsistent but, as noted elsewhere, the problem seems less likely to manifest itself after the system (or backend) is stopped and started.  It is also inconsistent in that a 7-7:30pm recording may go successfully, but the 8-9pm recording fails.  Also, if the 8-9pm recording fails, then the 9-10pm recording on the same night will usually fail.

I have a combined frontend/backend machine.  It shuts down when idle and wakes itself for the next recording.  The backend logs show nothing out of the ordinary when starting the recording, but thereafter you can see where the commflag process can't use the file.  System status indicates the recording is in process for the whole time of the scheduled program

I have tried most, if not all, of the suggestions in this forum:
- Moved the USB tuner to a less warm area by way of an extension cable
- Deleted and re-added the capture card, channels, etc.
- Upgraded to 0.26 (2:0.26.0+fixes.20121114.... from Mythbuntu repository)
- Disabled EIT collection
- Changed tuner timeouts

It seems like the only way to improve the likelihood of sucess is to regularly stop and start the backend or reboot the whole machine.

---

### Post by The Toastcutter on 2012-11-19
My tuner problems seem to have been introduced with the 3.2.0-32 kernel, and are still happening with 3.2.0-33. I get near-perfect recording with 3.2.0-31.

Rocco64 - have you tried this with the 3.2.0-31 kernel?

---

### Post by Rocco64 on 2012-11-20
I have not... I'll see if it's still installed.

---

### Post by Rocco64 on 2012-11-25
Update: 3.2.0-31 reinstalled and set as the default today. Not enough scheduled recordings have passed to give a verdict; will follow-up in a couple of days.

---

### Post by Rocco64 on 2012-11-28
Five days on and no failures in a dozen recordings; this qualifies as a success!

---

### Post by The Toastcutter on 2012-11-28
> **Rocco64 said:**
> Five days on and no failures in a dozen recordings; this qualifies as a success!
That's good - I'm not the only one then :)

I'm going to try bisecting this and see if I can't narrow it down to an actual commit.

This might take a little while - need to wait until no-one's watching tv.

---

### Post by The Toastcutter on 2012-12-06
I've narrowed it down to this commit:

 [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commit;h=1cef533d4e688acbf048b5b32e6f3ca9a265ed4e](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commit;h=1cef533d4e688acbf048b5b32e6f3ca9a265ed4e)

Everything before this commit works. Everything after this commit fails.
Reverting this commit on the current head works.

Rocco64 - are you interested in testing this to see if you get the same results?

---

### Post by superm1 on 2012-12-07
> **The Toastcutter said:**
> I've narrowed it down to this commit:

 [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commit;h=1cef533d4e688acbf048b5b32e6f3ca9a265ed4e](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=commit;h=1cef533d4e688acbf048b5b32e6f3ca9a265ed4e)

Everything before this commit works. Everything after this commit fails.
Reverting this commit on the current head works.

Rocco64 - are you interested in testing this to see if you get the same results?

Can you please file a kernel bug with as many details as possible?

[http://bugs.launchpad.net/ubuntu/+source/linux](http://bugs.launchpad.net/ubuntu/+source/linux)

---

### Post by The Toastcutter on 2012-12-07
> **superm1 said:**
> Can you please file a kernel bug with as many details as possible?

Shall do. 

I have another tuner with the same chipset, but a different vendor. I want to check these bisect kernels against this tuner as well, just to make sure it's not just some local hardware glitch.

(Earlier testing gave identical results on both tuners, but I'd like to be sure)

---

### Post by The Toastcutter on 2012-12-10
> **The Toastcutter said:**
> Shall do. 

I have another tuner with the same chipset, but a different vendor. I want to check these bisect kernels against this tuner as well, just to make sure it's not just some local hardware glitch.

(Earlier testing gave identical results on both tuners, but I'd like to be sure)

It does happen exactly the same with either tuner.

Bug submitted: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1088733](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1088733)

---

### Post by Rocco64 on 2013-02-01
Hi - I dropped out of this conversation after having success with the -31 kernel.  Two months on and things are still better than with the -33 kernel, but zero-byte recordings happen about once a week, then it's necessary to restart the machine and things more-or-less reset.

I appreciate your work, ToastCutter, on raising the defect and following up. My Myth box is the main PVR for the house, so it is difficult to perform experiments.

---

### Post by siren09 on 2013-08-15
One year down the track (nearly), are you still seeing these issues, Jamoody?  I have been experiencing them on a regular basis for the last 12 months - things were fine before that.  Did you ever get a set up which worked?  If so, can you post the magic formula - this is still driving me nuts!

Edit: I see this arrived at the end of the posting, so I'll make the question a bit more generic.  I am still having significant issues, platform is:

Ubuntu 13.04
mythtv-backend    2:0.26.0+fixes - sources from fixes
tuners: 2x Hauppauge Nova-TD Stick (52009) (but note I also have the same issues with af9015 based sticks)
firmware: 1.2
Kernel: Linux toby 3.8.0-23-generic #34-Ubuntu

Typical dmesg which cause the tuner to fail are:
dib0700: rc submit urb failed; and
DiB0070 I2C write failed

Once failed, the machine requires a reboot and unplug/replug of the tuners to resolve.  I do have a script which resets the usb using hub_ctrl, and this appears to resolve on a reboot NO unplug/replug, though I don't think the recovery is as robust as with the fuller resolution.  However, when I am away from home, this is the best I can manage.

I get zero byte recordings, often after a failed recording with a 376 bytes file size (always seems to be that size).

Can someone tell me what debug flags to turn on in order to log more information to the group.  I would dearly love to see this resolved.

Cheers.

---

### Post by jim_collins2 on 2013-10-10
I have this issue and to be honest have not read all the previous threads.  My problem seems to be the fact that that particular channel (for me it is CBS) does not have a strong enough signal to tune in.  I cannot watch it through the myth system, but if I use the signal that goes directly to my TV I can watch this channel but I cannot watch ABC.  Both signals strength are in the 80's.  Not sure why one would work through myth and one through the TV and be opposite, but that could contribute to the problem if it isn't the sole reason for the problem.  I am trying a signal booster this week to see if that eliminates the problem.  This did happen when upgrading to the latest version of mythbuntu about a month ago.  Would love to hear if anyone else has this or a similar issue.  I was able to tune all channels before the upgrade.

---

### Post by ktmom on 2013-10-12
> **jim_collins2 said:**
> I have this issue and to be honest have not read all the previous threads.  My problem seems to be the fact that that particular channel (for me it is CBS) does not have a strong enough signal to tune in. 

I went through something similar, also with CBS and ABC.  I'm a ways from their transmitters. I have a homerun and a 2250 tuners. I was running mythbuntu 9.04 w/ mythtv 0.24-fixes for several years.  When I upgraded to 12.04 w/ 0.27-fixes it took me a bit to get it stable again.  What I did that I *think* fixed it;

increase the value under: mythbackend setup -> capture card setup -> signal timeout (mine is 1000)
increase the value under: mythbackend setup -> capture card setup -> tuning timeout (mine is 12000)

There is also a setting in:  mythbackend setup -> capture card setup -> recording options -> DVB tuning delay (mine is at 3000 for the homerun tuner)

I also unticked anything allowing EIT scans on the 2250 and set the backend idle before for EIT to 7200 secs:  mythbackend setup -> general -> EIT scanner options (pg 4).

---

### Post by jim_collins2 on 2013-10-14
I'll definitely try to increase the timeout times and see if that helps.  I actually let the program "Scan" for channels and it somehow found an additional CBS that it uses as channel 1.  The only issue with that one is that there is no program information - always says unknown.  I'll post when I increase the times!!!  Thanks for the tip.

---

