---
title: "HD-PVR still flaky"
date: 2013-05-25
forum: Mythbuntu
---

### Post by bleve on 2013-05-25
Well, I have most things working but now have seen what is a show stopper for me.  When recording a show or watching live TV it will stop recording with messages like the following every few seconds:

> May 25 20:09:01 mythtv01 mythbackend[1571]: E DeviceReadBuffer DeviceReadBuffer.cpp:513 (Poll) DevRdB(/dev/video0): Poll giving up 2
May 25 20:09:01 mythtv01 mythbackend[1571]: E RecThread mpegrecorder.cpp:1010 (run) MPEGRec(/dev/video0): Device error detected
May 25 20:09:04 mythtv01 mythbackend[1571]: W RecThread mpegrecorder.cpp:818 (SetV4L2DeviceOptions) MPEGRec(/dev/video0): Unable to set audio input.
May 25 20:09:06 mythtv01 mythbackend[1571]: W RecThread mpegrecorder.cpp:1315 (StartEncoding) MPEGRec(/dev/video0): StartEncoding failed#012#011#011#011eno: Resource temporarily unavailable (11)


I have yet to get a full program recorded as it usually gets into this state after 5 to 10 minutes.  After you see these messages start the BE shows that the program is still being recorded but the recording stops growing.  Any ideas?  I am on the latest HD-PVR firmware.  

Thanks

---

### Post by bleve on 2013-05-25
It just happened again, and I noticed that the HD-PVR has a red light on.  If I power down the HD-PVR and back on and reboot the BE I can record again.  Does not seem very stable.

---

### Post by one30nav on 2013-05-26
Do you have USB 2.0? Quick search of the forum shows similar errors and behavior when you try HD-PVR with USB 1.0.

---

### Post by yonkiman on 2013-05-27
It *might *be your HD-PVR's power supply.

My HD-PVR was getting less and less reliable with time until finally it wouldn't work at all.  What happened was the 5V supply was failing.  If you measured the 5V at the output of the wall wart (power adapter), it looked fine (5.2V).  But when I plugged it into my HD-PVR and measured the 5V supply rail inside the HD-PVR, it was around 3V.  

I hooked up a 5V 2A USB adapter and it's been working fine ever since.

Found out about it here:
[http://valkyriemt.wordpress.com/2011/04/09/a-defect-with-the-hd-pvr-will-eventually-fail-for-all/](http://valkyriemt.wordpress.com/2011/04/09/a-defect-with-the-hd-pvr-will-eventually-fail-for-all/)

-Fred

---

### Post by bleve on 2013-05-27
Have not checked power but it is USB 2.0:

> 11: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: cLrx.+fHLkLLMGCD
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0
  SysFS BusID: 1-2:1.0
  Hardware Class: unknown
  Model: "Hauppauge HD PVR"
  Hotplug: USB
  Vendor: usb 0x2040 "Hauppauge"
  Device: usb 0x4903 "Hauppauge HD PVR"
  Serial ID: "00A68446"
  Driver: "hdpvr"
  Driver Modules: "hdpvr"
  Speed: 480 Mbps
  Module Alias: "usb:v2040p4903d0000dc00dsc00dp00icFFisc02ip00"
  Driver Info #0:
    Driver Status: hdpvr is active
    Driver Activation Cmd: "modprobe hdpvr"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (Hub)


Will try another power source if an apt-get upgrade does not sort it.

---

### Post by bleve on 2013-06-03
I am still fighting this one.  I have tried another 5v power source.  Moved the HDPVR away from the set top box and turned it on its side.  But still only get anywhere from 5 to 30 minutes of recordings usually before I get the messages above.  The only way to get it out of this state is to bounce the HDPVR and the myth BE.  When it gets into this state the red recording light on the front of the HDPVR stays lit even after myth shows the recording as ended.  

Any other ideas?

---

### Post by bleve on 2013-06-04
I have an email exchange going back and forth with Jerry at Hauppauge on this.  He thinks it may be the driver (not sure if that is internal or external to the HDPVR).  He told me that he wants me tor reproduce on Windows so I guess I will need to move my wife's windows machine over to where the STB is and try and reproduce.  This is beyond frustrating to say the least as hundreds if not thousands seem to have this working without issues.

---

### Post by gordintoronto on 2013-06-05
It is possible that people could give you better help if you provided a complete description of your system: CPU, memory, video adapter, hard drive, what operating system you are using, brand and model of your TV device. Running backend and frontend on the same computer?

---

### Post by bleve on 2013-06-05
Hi Gordon,

I have reproduced this two different backends with two different Video cards.  The current machine is a Dell OptiPlex 745 with 8gb of RAM.  The video card is PCIe X16 Nvideo 8400 gs based card with 512mb of RAM.  Operating system is Mythbuntu 12.04 with .25 of Mythtv.  My backend is running a frontend as well and I have two other frontends in my house that are not running as backends.  I have the latest from the mythbuntu repos installed.  

What I am seeing does not seem like it is related to the hardware so much outside of the HDPVR.  I did do as Jerry from Hauppauge asked me to do last night and hooked the HDPVR to a windows machine hooked up to the same cable box and was able to record onto the Windows machine without errors.  I am not at home now to see which kernel I am currently on, but this reproduced with the base 12.04 Mythbuntu kernel as well as the one picked up from the repos as configured from the Mythbuntu Control Center.  I am a bit concerned that others are reporting the same issue, as I can reproduce this reliably in either one of the machines I am using as the backend.  The other one I tried is an older Intel based homemade machine with a 32bit processor so I used the 32bit release of Mythbuntu but the current backend has the 64bit installed.  The 32bit system also had a different Nvidia card in it as it was 6200 based and AGP not PCIe and had a lot less RAM.  

The only other thing that may be different than others is this backend does have a Hauppauge PVR-350 in it as well capturing basic cable which continues to work flawlessly.

---

### Post by one30nav on 2013-06-05
What kind of set top box do you have? Are you using analog audio or SPDIF? Have you tried without the PVR-350? How about perhaps trying Mythtv 0.26 (which is running stable for me).

---

### Post by bleve on 2013-06-06
I went to .26 today and thought I had this licked bit it came back.  The set top box is a Pace HD.  I am using Analog sound and after first going to .26 I did not have any issues and was for the first time able to record several hours of shows without an issue.  Then out of nowhere the frontend hung and would not start nor would the mythtv-setup although I had it working for several hours.  They were both getting messages like:

> Jun  5 21:44:20 mythtv01 mythlogserver: mythtv-setup[3299]: I CoreContext mythmainwindow.cpp:1058 (Init) Using the Qt painter
Jun  5 21:44:21 mythtv01 mythlogserver: mythtv-setup[3299]: I CoreContext dbcheck.cpp:463 (UpgradeTVDatabaseSchema) Waiting for database schema upgrade lock
Jun  5 21:45:22  mythlogserver: last message repeated 61 times
Jun  5 21:46:21  mythlogserver: last message repeated 58 times
Jun  5 21:46:21 mythtv01 mythlogserver: mythtv-setup[3299]: I CoreContext dbcheck.cpp:470 (UpgradeTVDatabaseSchema) Failed to get schema upgrade lock


It took me a while to sort this out and still do not know what was causing it but after rebooting several times and finally killing mysql and kicking off mythtv-setup it went through upgrading some schema objects again.  When I got into mythtv-setup my capture cards were gone so I added them back and the inputs and was able to get my other front ends running again.   Anyway, this has nothing to do with the problem.  

So it is running again now with both of my remote FEs running.  I did not test without the PVR-350 but would be willing to try that.  I just tried to record a show again got the dreaded:

> Jun  5 23:54:57 mythtv01 mythlogserver: mythbackend[2825]: W RecThread mpegrecorder.cpp:818 (SetV4L2DeviceOptions) MPEGRec(/dev/video0): Unable to set audio input.
Jun  5 23:54:59 mythtv01 mythlogserver: mythbackend[2825]: W RecThread mpegrecorder.cpp:1308 (StartEncoding) MPEGRec(/dev/video0): StartEncoding failed#012#011#011#011eno: Resource temporarily unavailable (11)
Jun  5 23:55:03 mythtv01 mythlogserver: mythbackend[2825]: E DeviceReadBuffer DeviceReadBuffer.cpp:518 (Poll) DevRdB(/dev/video0): Poll giving up 2
Jun  5 23:55:03 mythtv01 mythlogserver: mythbackend[2825]: E RecThread mpegrecorder.cpp:1009 (run) MPEGRec(/dev/video0): Device error detected
Jun  5 23:55:06 mythtv01 mythlogserver: mythbackend[2825]: W RecThread mpegrecorder.cpp:818 (SetV4L2DeviceOptions) MPEGRec(/dev/video0): Unable to set audio input.
Jun  5 23:55:08 mythtv01 mythlogserver: mythbackend[2825]: W RecThread mpegrecorder.cpp:1308 (StartEncoding) MPEGRec(/dev/video0): StartEncoding failed#012#011#011#011eno: Resource temporarily unavailable (11)


Did you just go to .26 and are still on 12.0.4 or did you go to 12.10?  It is getting late here, so I will test tomorrow without the PVR-350, but not sure how that would be causing an issue.  The one big difference I see between .25 and .26 is when I do get into this issue, if I reboot the backend it frees up the HDPVR where as before I had to bounce both.

---

### Post by one30nav on 2013-06-06
I used a fresh install of Mythbuntu 12.04 which came with Mythtv 0.25, then I selected 0.26 from the Mythbuntu Control Centre.

My $0.02:

I'd caveman, troubleshoot by eliminating any potential conflicting devices, such as your PVR-350.

Things to consider:

- Re-check that you updated your HD-PVR firmware from a windows box with the latest.
- Make sure your Dell has the newest BIOS to rule out USB port issues.
- If you're using an IR Blaster, 1.) Ensure you have at 12,000 ms tuner timeout delay to allow channel lock, 2.) Ensure you've disabled the HD-PVR port if you aren't using it (unload module).
- Upgrades from earlier versions of Mythbuntu to newer ones sometimes breaks Linux stuff. In other words, rule this out by starting with the 12.04 LTS.

For reference, my hardware:

DCT-6200 set top box (component video and audio out; channel changing by firewire)
PVR-500 using /dev/video0 and /dev/video1
HD-PVR using /dev/video2

---

### Post by bleve on 2013-06-06
Thanks, this is good advice.  I did a fresh install of the 32bit release on another box and had the same exact issues before trying on this Dell.  I did test with the PVR-350 card out today and saw the same behavior just now.  I am getting the signal lock as I always get at least 15 minutes of recordings before it goes to lunch.  I also upgraded to .26 release the same way last night.  

I just increased the ring buffer in mythtv-setup, lets see if that makes a difference.  I bumped it to 25mb.  

Good info and and thanks for the reference hardware.  I will see if there is a newer bios as well as I do see where that could be an issue.  Still another possibility is the wall wort supplying the 5 volts DC to the HDPVR.  

I will verify the the firmware as well when I can get my wife's laptop over to the system again and run the verification utility.

---

### Post by bleve on 2013-06-06
Just hit it again with the ring buffer increased.

---

### Post by bleve on 2013-06-07
Upgraded the BIOS on the Dell BE and nothing worked so got frustrated and did a full reinstall.  Just now get the IR blaster working and added both cards in.  Will do more testing tomorrow.

---

### Post by bleve on 2013-06-07
Now on to plan "D".  After a reinstall and upgrading back to .26 it still reproduced, so I took a STB which is another another vendor from downstairs and brought it upstairs.  Now doing recordings to it.  Next step after that, if that does not correct it is going to be to purchase another HDPVR (plan "E") and if that fixes it, will return the one I have.  If that does not fix it, I am out of ideas.  I have changed just about everything out at this point other than the composite cables.  Which maybe be plan "F", but I do not have high expectations that will resolve anything.

---

### Post by bleve on 2013-06-07
I forgot about plan "D.2" which was to look at the console when the problem happens.  I went to a virtual terminal by hitting ctrl-alt-F1 and saw messages streaming complaining about lirc_zilog.  I commented out the module from the /etc/lirc/hardware.conf and rebooted.  I am now on my second recording without issue.  I will keep testing.  If this proves to be the issue, I will be off to get a firewire card and IR transmitter.

---

### Post by one30nav on 2013-06-07
Yep, my sense is that it's been your IR-Blaster setup all along.

From the wiki:

**Note:** As of April 2011, numbers of users have reported  instability if the HD-PVR is configured as an IR receiver. To workaround  this, make sure that "options lirc_zilog tx_only=1" is set in the  modprobe.conf or /etc/modprobe.d/hdpvr.conf depending on the  distribution.

There are more tweaks on the wiki for lirc if you still want to go down that path. Firewire is so much easier, though. However, some STBs don't have that port.

---

### Post by bleve on 2013-06-07
Yeah, the one I brought upstairs from downstairs does, but the one that was upstairs does not.  I am going to swing by my cable providers office and swap out boxes, as I can't bring the one from upstairs downstairs as I don't have component setup downstairs and the older Pace STB does not support HDMI or firewire.  I am grinning ear to ear right now.  I am going to keep testing and will stop by Best Buy or Tiger Direct this weekend and get a firewire card and cable.  I will also test with lirc_zilog setting as well to see if that is stable, but sounds like firewire is the most stable for channel changing.

---

### Post by bleve on 2013-06-08
After setting  "options lirc_zilog tx_only=1" the system is now stable.  For those that suggested to not use the IR blaster built into the HDPVR your were dead on.  one30nav and others had mentioned that the this may be an issue.   Setting this to resolved, and hopefully others can benefit from the thread.

---

### Post by jeffhoye on 2013-09-02
Hi I'm having the same problem.  I'm trying to use my existing PVR-350 for IR input, but disable the HDPVR for IR input, and use the HDPVR blaster for IR output.  I did what was suggested to disable it in hdpvr.conf, but it doesn't work.  

I'm using a QIP 7100 2 STB (Verizon FIOS)  I originally installed Mytbuntu 12.04.1 and got it working fine with SD, but recently upgraded to HD and added an HDPVR.  I'm using Composite cables.  The system will record for a few minutes then it crashes.

```
Sep  2 09:39:09 mythbuntu3 mythbackend[1911]: I ProcessRequest mainserver.cpp:13
60 (HandleAnnounce) MainServer::ANN Playback
Sep  2 09:39:09 mythbuntu3 mythbackend[1911]: I ProcessRequest mainserver.cpp:13
62 (HandleAnnounce) adding: mythbuntu3 as a client (events: 0)
Sep  2 09:39:09 mythbuntu3 mythbackend[1911]: E ProcessRequest mainserver.cpp:37
20 (HandleRecorderQuery) MainServer::HandleRecorderQuery() Unknown encoder: 1
Sep  2 09:39:09 mythbuntu3 mythbackend[1911]: I TVRecEvent tv_rec.cpp:1029 (Hand
leStateChange) TVRec(2): Changing from None to WatchingLiveTV
Sep  2 09:39:09 mythbuntu3 mythbackend[1911]: I TVRecEvent tv_rec.cpp:3495 (Tuni
ngCheckForHWChange) TVRec(2): HW Tuner: 2->2
Sep  2 09:39:09 mythbuntu3 mythbackend[1911]: I TVRecEvent v4lchannel.cpp:661 (S
etInputAndFormat) V4LChannel(/dev/video0): SetInputAndFormat(4, NTSC) (v4l v2) i
nput_switch: 0 mode_switch: 1
Sep  2 09:39:09 mythbuntu3 mythbackend[1911]: N CoreContext autoexpire.cpp:263 (
CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
Sep  2 09:39:10 mythbuntu3 mythbackend[1911]: E SignalMonitor analogsignalmonitor.cpp:84 (VerifyHDPVRaudio) AnalogSM(/dev/video0): Audio desired 4, current 3 min 3 max 4
Sep  2 09:39:10 mythbuntu3 mythbackend[1911]: E SignalMonitor analogsignalmonitor.cpp:94 (VerifyHDPVRaudio) AnalogSM(/dev/video0): Changed audio encoding from 3 to 4.
Sep  2 09:39:12 mythbuntu3 mythbackend[1911]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
Sep  2 09:39:18 mythbuntu3 mythbackend[1911]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(2:/dev/video0): GetKeyframePositions(1,9223372036854775807,#0) out of 1
Sep  2 09:39:18 mythbuntu3 mythbackend[1911]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(2:/dev/video0): GetKeyframePositions(1,9223372036854775807,#0) out of 1
Sep  2 09:39:20 mythbuntu3 mythbackend[1911]: I Metadata_10794 jobqueue.cpp:2151 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for Today recorded from channel 1004 at 2013-09-02T09:39:09
Sep  2 09:39:21 mythbuntu3 mythbackend[1911]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Sep  2 09:39:21 mythbuntu3 mythbackend[1911]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu3 as a client (events: 0)
Sep  2 09:39:21 mythbuntu3 mythbackend[1911]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Sep  2 09:39:21 mythbuntu3 mythbackend[1911]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu3 as a client (events: 1)
Sep  2 09:39:34 mythbuntu3 mythbackend[1911]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Sep  2 09:42:06 mythbuntu3 mythbackend[1911]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1004 at 2013-09-02T09:39:09 => Today
Sep  2 09:44:39 mythbuntu3 mythbackend[1911]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread

```

Device Error:
```
Sep  2 09:48:02 mythbuntu3 mythbackend[1911]: E DeviceReadBuffer DeviceReadBuffer.cpp:513 (Poll) DevRdB(/dev/video0): Poll giving up 2
Sep  2 09:48:02 mythbuntu3 mythbackend[1911]: E RecThread mpegrecorder.cpp:1010 (run) MPEGRec(/dev/video0): Device error detected
Sep  2 09:48:15 mythbuntu3 mythbackend[1911]: W RecThread mpegrecorder.cpp:818 (SetV4L2DeviceOptions) MPEGRec(/dev/video0): Unable to set audio input.

```


Here's more info:

```

jeffh@mythbuntu3:~$ uname -r
3.5.0-39-generic

jeffh@mythbuntu3:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise

```


Using the firmware version hdpvr_1.7.1.30059:
```

jeffh@mythbuntu3:~$ dmesg | grep hdpvr
[   16.813364] hdpvr 2-1:1.0: firmware version 0x1e dated Mar  7 2012 08:25:15
[   16.813367] hdpvr 2-1:1.0: untested firmware, the driver might not work.
[   17.360294] hdpvr 2-1:1.0: device now attached to video0
[   17.360319] usbcore: registered new interface driver hdpvr
[ 1508.301008] hdpvr 2-1:1.0: device video0 disconnected
[ 1520.767399] hdpvr 2-1:1.0: firmware version 0x1e dated Mar  7 2012 08:25:15
[ 1520.767403] hdpvr 2-1:1.0: untested firmware, the driver might not work.
[ 1521.063476] hdpvr 2-1:1.0: device now attached to video0

```


One problem is that I don't think I have a full hdpvr.conf.  Where can I get that?  Does this indicate that I didn't install a required component?

```

jeffh@mythbuntu3:~$ cat /etc/modprobe.d/hdpvr.conf
options lirc_zilog tx_only=1

jeffh@mythbuntu3:~$ ls -l /etc/modprobe.d/
total 52
-rw-r--r-- 1 root root 2507 Feb 15  2012 alsa-base.conf
-rw-r--r-- 1 root root  325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 Mar 18  2011 blacklist.conf
-rw-r--r-- 1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r-- 1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Feb 15  2012 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Aug 25 13:06 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Mar 18  2011 blacklist-watchdog.conf
-rw-r--r-- 1 root root  127 Apr 22  2012 dkms.conf
-rw-r--r-- 1 root root   30 Sep  2 12:47 hdpvr.conf
-rw-r--r-- 1 root root  153 Aug  8 20:33 nvidia-304_hybrid.conf
-rw-r--r-- 1 root root  157 Apr 12  2012 nvidia-current_hybrid.conf
lrwxrwxrwx 1 root root   47 Aug 25 13:07 nvidia-graphics-drivers.conf -> /etc/alternatives/i386-linux-gnu_nvidia_modconf
-rw-r--r-- 1 root root   30 May 18  2012 vmwgfx-fbdev.conf

```

and it doesn't disable the remote ( see the last few lines) dmesg:
```

[   16.813364] hdpvr 2-1:1.0: firmware version 0x1e dated Mar  7 2012 08:25:15
[   16.813367] hdpvr 2-1:1.0: untested firmware, the driver might not work.
[   16.858848] microcode: CPU0 sig=0x6fb, pf=0x1, revision=0xb3
[   16.867907] gpio_ich: GPIO from 195 to 255 on gpio_ich
[   16.928087] microcode: CPU1 sig=0x6fb, pf=0x1, revision=0xb3
[   16.929655] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   17.192630] ivtv: Start initialization, version 1.4.3
[   17.192692] ivtv0: Initializing card 0
[   17.192694] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   17.192777] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   17.246271] tveeprom 0-0050: Hauppauge model 26582, rev F0B2, serial# 10141366
[   17.246275] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   17.246278] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   17.246280] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   17.246282] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   17.246284] tveeprom 0-0050: has no radio
[   17.246287] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   17.261105] kvm: disabled by bios
[   17.264918] kvm: disabled by bios
[   17.360044] Registered IR keymap rc-hauppauge
[   17.360177] input: i2c IR (HD-PVR) as /devices/virtual/rc/rc0/input5
[   17.360234] rc0: i2c IR (HD-PVR) as /devices/virtual/rc/rc0
[   17.360237] ir-kbd-i2c: i2c IR (HD-PVR) detected at i2c-1/1-0071/ir0 [Hauppage HD PVR I2C]
[   17.360294] hdpvr 2-1:1.0: device now attached to video0
[   17.360319] usbcore: registered new interface driver hdpvr

```

they're both still activated in ir-keytable:

```

cat /proc/bus/input/devices

...

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="i2c IR (HD-PVR)"
P: Phys=i2c-1/1-0071/ir0
S: Sysfs=/devices/virtual/rc/rc0/input5
U: Uniq=
H: Handlers=kbd event5
B: PROP=0
B: EV=100013
B: KEY=10afc312 2142017 0 0 0 0 118000 41a8 4801 9e16c0 800018 41001 12090ffe
B: MSC=10

...

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="i2c IR (Hauppauge WinTV PVR-350"
P: Phys=i2c-2/2-0018/ir0
S: Sysfs=/devices/virtual/rc/rc1/input8
U: Uniq=
H: Handlers=kbd event8
B: PROP=0
B: EV=100013
B: KEY=10afc312 2142017 0 0 0 0 118000 41a8 4801 9e16c0 800018 41001 12090ffe
B: MSC=10

jeffh@mythbuntu3:~$ sudo ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event5) with:
        Driver ir-kbd-i2c, table rc-hauppauge
        Supported protocols: RC-5
        Enabled protocols: RC-5
        Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event8) with:
        Driver ir-kbd-i2c, table rc-hauppauge
        Supported protocols: RC-5
        Enabled protocols: RC-5
        Repeat delay = 500 ms, repeat period = 125 ms

jeffh@mythbuntu3:~$ sudo ir-keytable -d /dev/input/event5 -t
Testing events. Please, press CTRL-C to abort.
1378143398.641482: event MSC: scancode = 1e15
1378143398.641486: event key down: KEY_DOWN (0x006c)
1378143398.641487: event sync
1378143398.892151: event key up: KEY_DOWN (0x006c)
1378143398.892152: event sync

```

Let me know what additional info would be helpful for me to provide.

Thanks for your help!  
-Jeff

---

