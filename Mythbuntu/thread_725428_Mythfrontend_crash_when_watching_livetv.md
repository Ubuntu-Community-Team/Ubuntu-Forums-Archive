---
title: "Mythfrontend crash when watching livetv"
date: 2008-03-15
forum: Mythbuntu
---

### Post by pdragon04 on 2008-03-15
After upgrading to .21 and also doing a kernel update, I'm now having the Frontend crash, and something in the backend break, when a recording starts or stops while I'm watching LiveTV. For example, if I'm watching LiveTV and something is scheduled to start recording, the screen will freeze, the Frontend will crash, and what was supposed to start recording will never start. And nothing else that's scheduled to start recording later will start recording until I reboot. The backend reports no problems and somehow thinks things are still recording as normal. Both Mythweb and the Program Guide will say the program is recording, but the Tuner is not actually in use and I can change channels (only a single tuner). The only thing that gets everything back to normal is a full reboot of the system

The backend contains no errors at all. It thinks things are running fine even if no recording is actually happening. But, when the frontend crashes it fills up with the following until I "kill" it:

2008-03-15 02:59:30.716 TV: ASK_RECORDING 1 29 0 0 hasrec: 0 haslater: 0
2008-03-15 02:59:30.842 couldn't find base dialog
2008-03-15 02:59:32.883 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:34.902 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:36.916 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:38.936 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:40.957 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:42.996 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:45.012 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:47.030 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:49.048 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:51.066 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:53.087 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:55.107 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:57.125 NVP: Timed out waiting for free video buffers.
(last line repeating every 2 seconds until frontend is killed)

03:00 is when a program was scheduled to start recording and I had LiveTV running.

I found the following in the MythTV Wiki concerning this error:

[http://www.mythtv.org/wiki/index.php/Troubleshooting:NVP:_Timed_out_waiting_for_free_video_buffers](http://www.mythtv.org/wiki/index.php/Troubleshooting:NVP:_Timed_out_waiting_for_free_video_buffers)

The thing is, everything was working perfectly fine before the last update. When I was watching LiveTV and something would want to start recording, I'd get the message popup asking what I would like to do (keep watching, or change to recording show). Now it crashes every time without fail. 

Is there anything in the last kernel/mythtv update that would just start causing this to happen? I'm commenting out the loading of the glx module to see if it fixes things. Just concerned that something broke with the transition to .21. Posting here to see if this is an isolated incident before reporting a bug.

---

### Post by pdragon04 on 2008-03-15
I commented out the module to load glx in my xorg.conf. This fixed the problem of the whole system crashing when I'm watching LiveTV and a scheduled show wants to start recording. But, it's now giving another error when that show is done being watched and it tries to switch back to normal LiveTV viewing. It froze for a few seconds then came up with an error box that a video error had occured. It let me hit OK, then it went back to the MythTV main menu. 

Any help would be appreciated. Was hoping I wouldn't have to reload from scratch when 8.04 comes out, but if these keeps up I probably will.

Show was scheduled to stop at 19:00. Below is the frontend log.

2008-03-15 18:59:52.281 NVP: prebuffering pause
2008-03-15 18:59:52.344 RingBuf(/opt/mythtv/recordings/1059_20080315183000.mpg): Waited 1.0 seconds for data to become available...
2008-03-15 18:59:52.344 Checking to see if there's a new livetv program to switch to..
2008-03-15 18:59:53.346 RingBuf(/opt/mythtv/recordings/1059_20080315183000.mpg): Waited 2.0 seconds for data to become available...
2008-03-15 18:59:53.347 Checking to see if there's a new livetv program to switch to..
2008-03-15 18:59:53.636 NVP: Prebuffer wait timed out 10 times.
2008-03-15 18:59:54.975 NVP: Prebuffer wait timed out 10 times.
2008-03-15 18:59:55.349 RingBuf(/opt/mythtv/recordings/1059_20080315183000.mpg): Waited 4.0 seconds for data to become available...
2008-03-15 18:59:55.350 Checking to see if there's a new livetv program to switch to..
2008-03-15 18:59:56.309 NVP: Prebuffer wait timed out 10 times.
2008-03-15 18:59:57.643 NVP: Prebuffer wait timed out 10 times.
2008-03-15 18:59:58.974 NVP: Prebuffer wait timed out 10 times.
2008-03-15 18:59:59.354 RingBuf(/opt/mythtv/recordings/1059_20080315183000.mpg): Waited 8.0 seconds for data to become available...
2008-03-15 18:59:59.354 Checking to see if there's a new livetv program to switch to..
2008-03-15 19:00:00.305 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:01.636 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:02.970 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:04.301 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:05.633 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:06.969 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:07.360 RingBuf(/opt/mythtv/recordings/1059_20080315183000.mpg) Error: Waited 16 seconds for data, aborting.
2008-03-15 19:00:07.674 [mpeg2video @ 0xb73d0148]00 motion_type at 28 18
2008-03-15 19:00:07.677 [mpeg2video @ 0xb73d0148]Warning MVs not available
2008-03-15 19:00:07.735 [mpeg2video @ 0xb73d0148]ac-tex damaged at 39 10
2008-03-15 19:00:07.736 [mpeg2video @ 0xb73d0148]Warning MVs not available
2008-03-15 19:00:07.739 LiveTV forcing JumpTo 1
2008-03-15 19:00:08.304 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:09.635 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:10.966 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:12.299 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:13.637 NVP: Prebuffer wait timed out 10 times.
2008-03-15 19:00:14.751 RingBuf(/opt/mythtv/recordings/1059_20080315190005.mpg): Invalid file (fd -1) when opening '/opt/mythtv/recordings/1059_20080315190005.mpg'.
2008-03-15 19:00:14.751 NVP, Error: JumpToProgram's OpenFile failed.
2008-03-15 19:00:14.751 NVP, Error: Unknown error, exiting decoder
2008-03-15 19:00:14.752 TV: Attempting to change from WatchingLiveTV to None
2008-03-15 19:00:22.532 TV: Changing from WatchingLiveTV to None
2008-03-15 19:00:22.597 DPMS Reactivated.

---

### Post by Fuzzywuzzy on 2008-03-17
I believe the problem you are experiencing is related to the changes that were made to the decoder filters & playback profiles that rolled out last week.


Go to Utilities/Setup -> Setup -> TV Settings -> Playback -> (page 3 of 9)
If your Current Video Playback Profile shows something like "CPU+" or "CPU--", then you will need to change it to something like "High Quality" or "Slim"

Unfortunately, NVP likes to throw out errors like this for just about any reason.

Also, the  RingBuf errors are telling you that the mount that the recordings directory is on can't keep up with the stress of LiveTV.

Please post the results of the following commands ($ indicates new command) and I'll see what I can do about that issue, too:

$ mount
$ dmesg | grep [sh]d
$ sudo hdparm -i /dev/[sh]d[a-d]

---

### Post by pdragon04 on 2008-03-18
My LiveTV recordings are going to an XFS partition on the same physical disk as the OS is installed (/opt/mythtv). OS is installed on a smaller ext3 partition. I have another large drive attached (/opt/mediadata) just for file storage since I use my myth box as a file server as well. Just don't understand why all this was working fine since  before I did the last kernel update and the upgrade to .21. Haven't had a problem since the day I installed 7.10 when it was released.

Thanks very much for your help!

result of mount:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /opt/mythtv type xfs (rw)
/dev/sdb1 on /opt/mediadata type xfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)



result of dmeg:
[   15.801740]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pi                        o
[   15.801756]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pi                        o
[   17.230319] hdc: LITE-ON COMBO SOHC-4832K, ATAPI CD/DVD-ROM drive
[   18.440456] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   18.440513] sd 0:0:0:0: [sda] Write Protect is off
[   18.440517] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.440556] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does                        n't support DPO or FUA
[   18.440668] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   18.440682] sd 0:0:0:0: [sda] Write Protect is off
[   18.440685] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.440705] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does                        n't support DPO or FUA
[   18.440714]  sda: sda1 sda2 sda3
[   18.465717] hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   18.466949] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.471161] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB                        )
[   18.471185] sd 1:0:0:0: [sdb] Write Protect is off
[   18.471189] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   18.471211] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, does                        n't support DPO or FUA
[   18.471324] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB                        )
[   18.471338] sd 1:0:0:0: [sdb] Write Protect is off
[   18.471341] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   18.471360] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, does                        n't support DPO or FUA
[   18.471364]  sdb: sdb1
[   18.489087] sd 1:0:0:0: [sdb] Attached SCSI disk
[   18.495829] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.496149] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   32.667754] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:9                        96020k
[   33.008072] EXT3 FS on sda1, internal journal
[   33.512079] XFS mounting filesystem sda3
[   33.603795] Ending clean XFS mount for filesystem: sda3
[   33.628966] XFS mounting filesystem sdb1
[   33.721003] Ending clean XFS mount for filesystem: sdb1
[   46.526999] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   47.792156] vboxdrv: Trying to deactivate the NMI watchdog permanently...


result of hdparam
/dev/hdc:

 Model=LITE-ON COMBO SOHC-4832K, FwRev=OTK1, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode


/dev/sda:

 Model=WDC WD2500JD-22HBB0                     , FwRev=08.02D08, SerialNo=     WD-WCAL73635210
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode


/dev/sdb:

 Model=WDC WD7500AAKS-00RBA0                   , FwRev=30.04G30, SerialNo=     WD-WCAPT0227503
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

---

### Post by Fuzzywuzzy on 2008-03-18
Heh, I have the JS revision of the same 250gb drive, so we know it's a 3gb/s SATA drive.

Anyway, I have a possible theory, but I may be wrong.
I'm assuming the hardware hasn't changed since you posted it to the [working hardware list]("http://ubuntuforums.org/showthread.php?p=3476168#post3476168"), and that there wasn't a recent kernel upgrade in Feisty.

If I had to guess, I'd say that the new video filters in 0.21 aren't using hardware acceleration, and are eating too much RAM when you're watching LiveTV.
Since the swap space is on the same physical disk as the LiveTV storage, I'm betting that you're getting some thrashing on first HDD (/dev/sda).

As a test, try recording just LiveTV to /opt/mediadata.  If it works, then you'll need to either add a stick of RAM or move the SWAP partition somewhere else.  I'm afraid I'm still figuring out the new settings in Myth 0.21, but I think 
that if you run mythtv-setup and go to option 6 - Storage Groups, myth should let you do this. 

> **pdragon04 said:**
> My LiveTV recordings are going to an XFS partition on the same physical disk as the OS is installed (/opt/mythtv). OS is installed on a smaller ext3 partition. I have another large drive attached (/opt/mediadata) just for file storage since I use my myth box as a file server as well. Just don't understand why all this was working fine since  before I did the last kernel update and the upgrade to .21. Haven't had a problem since the day I installed 7.10 when it was released.

Thanks very much for your help!

result of mount:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /opt/mythtv type xfs (rw)
/dev/sdb1 on /opt/mediadata type xfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)

<...SNIP...>


/dev/sda:

 Model=WDC WD2500JD-22HBB0                     , FwRev=08.02D08, SerialNo=     WD-WCAL73635210
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode



---

### Post by laga on 2008-03-19
> **pdragon04 said:**
> 
2008-03-15 02:59:32.883 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:34.902 NVP: Timed out waiting for free video buffers.
2008-03-15 02:59:36.916 NVP: Timed out waiting for free video buffers.


I was getting threse messages when i enabled RTC video timing.. you can see the video timing method when starting ```
mythfrontend -v playback
```.. It's a long shot, though...

---

### Post by pdragon04 on 2008-03-19
Bit busy this week. Will try and try these fixes this weekend. Thanks for your help!

---

### Post by Fuzzywuzzy on 2008-03-19
> **laga said:**
> I was getting threse messages when i enabled RTC video timing.. 

Yeah, the RTC video timing is a [known bug]("https://bugs.launchpad.net/mythbuntu/+bug/139949").

There's an experimental fix in the Mythbuntu-Control-Center if you're willing to move up to the Hardy alphas.

Otherwise, there's always the old ```
 sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq 
``` trick.

---

### Post by laga on 2008-03-20
> **Fuzzywuzzy said:**
> Yeah, the RTC video timing is a [known bug]("https://bugs.launchpad.net/mythbuntu/+bug/139949").

I'm aware of that. I was getting those messages when I enabled RTC video timing in MCC.

---

