---
title: "Video stuttering: messages about RingBuf, video buffers"
date: 2012-09-30
forum: Mythbuntu
---

### Post by Kantalias on 2012-09-30
I'm having playback issues on a combined frontend/backend myth system.  I've been using MythTV for about three years now with no playback issues.  I've upgraded hardware several times, most recently replacing a single WD20EARS with an SSD for the system and a WD20EARX for videos. Now I get errors like this during video playback or while watching live TV:
```
Sep 29 21:40:22 mythtv mythfrontend[8385]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/second_drive/recordings/3130_20120103210000.mpg): Waited 2.0 seconds for data #012#011#011#011to become available... 0 < 32768
Sep 29 21:40:22 mythtv mythfrontend[8385]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(g): Waited 3719ms for video buffers AAAAAAAAAAALff
Sep 29 21:40:22 mythtv mythfrontend[8385]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(g): Waited 3823ms for video buffers AAAAAAAAAAALff
Sep 29 21:40:22 mythtv mythfrontend[8385]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(g): Waited 3926ms for video buffers AAAAAAAAAAALff
Sep 29 21:40:22 mythtv mythfrontend[8385]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(g): Waited 4029ms for video buffers AAAAAAAAAAALff
```

If a recording is being made while watching a different recording or live TV the problem is exacerbated.  

Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-31-generic-pae i686)
MythTV Version : v0.25.2-15-g46cab93
MythTV Branch : fixes/0.25
Playback is set to VDPAU slim
Combined frontend/backend on[INDENT]Intel i5-2400S
ASUS ENGT520 SL/DI/2GD3
Crucial CT64M4SSD2
Western Digital WD20EARX
[/INDENT]I searched for related issues and found several threads, most nearly a year old, regarding various issues like playback from a NAS, using multiple frontends, etc.  But none of the cases I've found represent my situation.

What might cause these issues?

---

### Post by Rotak on 2012-09-30
What filesystem are you using?

A friend of mine had issues about R/W speed with an SSD drive. A BIOS update fixed that. No idea if your issue could be related to BIOS as well.

---

### Post by Kantalias on 2012-09-30
Thanks for the reply.

> **Rotak said:**
> What filesystem are you using?

The operating system ('/') resides on an ext4 partition on the SSD.  All recordings are written to an XFS partition on the 2 TB WD drive.

```
$ df
Filesystem      1K-blocks      Used  Available Use% Mounted on
/dev/sda2        57927924   6128544   48856816  12% /
udev              2047276         4    2047272   1% /dev
tempfs            2054548      3788    2050760   1% /tmp
tmpfs              821820      1064     820756   1% /run
none                 5120         4       5116   1% /run/lock
none              2054548       148    2054400   1% /run/shm
/dev/sdb1      1952559608 881549900 1071009708  46% /second_drive

$ sudo parted /dev/sda
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA M4-CT064M4SSD2 (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 2      1018kB  60.3GB  60.3GB  ext4
 3      60.3GB  64.0GB  3758MB  linux-swap(v1)

$ sudo parted /dev/sdb
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print
Model: ATA WDC WD20EARX-008 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  xfs

```> **Rotak said:**
> A friend of mine had issues about R/W speed with an SSD drive. A BIOS update fixed that. No idea if your issue could be related to BIOS as well.

I haven't looked for motherboard BIOS updates recently but last time I checked I was at the latest version.  The MB is an ASUS P8H67-M PRO/CSM.  Checking the website just now, it appears there are no downloads (BIOS or otherwise) which, presumably, is either a bug or an indication that the product is deprecated ([http://usa.asus.com/Motherboards/Intel_Socket_1155/P8H67M_PROCSM/#download](http://usa.asus.com/Motherboards/Intel_Socket_1155/P8H67M_PROCSM/#download)).  

Were your friend's recordings written to the SSD?

---

### Post by Rotak on 2012-09-30
I will ask my friend. I know it was an ASUS board, too.

He changed his setup a few months ago. He's now only writing LiveTV to the SSD and is storing recordings on a NAS.

Maybe you can "benchmark" your HDDs by using:

```
sudo hdparm -tT /dev/sda
```(and sdb, of course)

Here is the output of my myth server, while I was watching TV (system not idle):
```
sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   14488 MB in  2.00 seconds = 7252.89 MB/sec
 Timing buffered disk reads: 166 MB in  3.02 seconds =  54.88 MB/sec

```

---

### Post by Kantalias on 2012-10-02
> **Rotak said:**
> 
Maybe you can "benchmark" your HDDs by using:

```
sudo hdparm -tT /dev/sda
```(and sdb, of course)


Cool utility...I didn't know there was a quick way to check disk performance.

Here are some results:
[IMG]http://i1075.photobucket.com/albums/w427/Kantalias/HDReadPerformance.jpg[/IMG]

Looks like (by this metric at least) there should be sufficient throughput on /dev/sdb and the SSD on /dev/sda appears to perform as expected for an SSD.  

On a whim, I watched atop while viewing a recording and another one was being written to disk.  I saw this during smooth playback:

```
DSK |          sdb  | busy     17%  | read      70 |  write     47 |  KiB/r    244 |               | KiB/w    357  | MBr/s   1.67  | MBw/s   1.64 |  avq     1.49 |  avio 14.7 ms |

```

When a playback stall occurred, I saw this:

```
DSK |          sdb  | busy     98%  | read      22 |  write      7 |  KiB/r    302 |               | KiB/w    258  | MBr/s   0.65  | MBw/s   0.18 |  avq     6.74 |  avio  334 ms |

```

Obviously the busy percentage is a problem.  The other obvious issue is avio (far right, you have to scroll over in the code section of the post), which I assume is some measure of access time based on its healthy number. 

I've never seen anything like this before.  Any thoughts on what might cause intermittent high disk latency?

---

### Post by Rotak on 2012-10-05
Phew. I experimented with file systems a long time ago (Mythbuntu 10.04).

With kernel 2.6, I (sooner or later) experienced speed problems with any journaling file system. Therefore, I switched to ext2.

Maybe a filesystem geek could comment this. 8-[

---

### Post by Kantalias on 2012-10-05
> **Rotak said:**
> With kernel 2.6, I (sooner or later) experienced speed problems with any journaling file system. Therefore, I switched to ext2.

Huh...hadn't considered that angle.  In hopes of expert filesystem insight, here's my fstab (parameters for the XFS partition that all recordings go on are "defaults"):
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=0efa47e2-b174-49be-8726-dfcca4fb9c10 /               ext4    errors=remount-ro 0       1
UUID=e728f64d-4c7a-4d1a-bd1a-efce96c6274e none            swap    sw              0       0
tempfs          /tmp            tmpfs   nodev,nosuid        0       0
UUID="35fa6798-8564-46e2-8714-6c5385df220b" /second_drive xfs     defaults        0       0

```

---

### Post by Rotak on 2012-10-06
I am hesitant to give any advice on XFS mount options or on using and fs-tools to set options, because I have no XFS partition running.

As far as I remember, it's not possible to turn off journaling on XFS. But maybe somebody knows other optimization options. I read of some optimizations, but those have to be done when creating the filesystem. :(

---

### Post by nickrout on 2012-10-07
It is unlikely that your filesystem is to blame. There was a bug I saw fixed for 0.26 about the livetv buffer being out by a factor of 10 (ie 1/10th the size it should have been). I recall seeing the fix committed for 0.26, not sure if it was for 0.25 or 0.24. I cannot find the damned commit now and therefore can't confirm.

Try pausing, let the buffer build up a bit and restart. Should only take a short pause. If that works we have probably at least found the bug, even if the workaround is a PITA. (albeit an easy to implement PITA).

---

### Post by nickrout on 2012-10-07
Got it, it's ticket 10428 in track and commit 483e06f in git. Unfortunately not backported to 0.25 so far as I can see.

[http://code.mythtv.org/trac/ticket/10428](http://code.mythtv.org/trac/ticket/10428)

[https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9](https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9)

Time to try 0.26?

---

### Post by Rotak on 2012-10-07
@nickrout:
But why does atop output such a high busy-percentage in the moment it stutters?

Maybe, both problems together cause it: Buffer too small + filesystem too busy!?!

---

### Post by Kantalias on 2012-10-09
> **nickrout said:**
> Try pausing, let the buffer build up a bit and restart. Should only take a short pause. If that works we have probably at least found the bug, even if the workaround is a PITA. (albeit an easy to implement PITA).

I've heard of this bug and have tried pausing and then resuming play.  Pausing, even for seconds, doesn't help my issue.  Additionally, please note that I have stuttering in live TV *and* when playing back a recording (with *no* live TV involved).

Based on the underlying I/O performance and its correlation to the playback problem this does seem to be a system level issue.  If it's not a filesystem problem is it likely lower level (hardware) or higher level (??? what sits between the front end and the filesystem)?

---

### Post by Rotak on 2012-10-09
The kernel and some other stuff is sitting between the backend and the hardware.

Did you think about backup recordings -> format hdd with (e.g.) ext2 -> restore recordings?

---

### Post by Kantalias on 2012-10-09
> **Rotak said:**
> Did you think about backup recordings -> format hdd with (e.g.) ext2 -> restore recordings?

I am strongly considering doing something like that, yes.  Is ext2 the preferred filesystem (over XFS, over ext4)?

---

### Post by nickrout on 2012-10-09
> **Kantalias said:**
> I am strongly considering doing something like that, yes.  Is ext2 the preferred filesystem (over XFS, over ext4)?
No, xfs id the preferred. ext2 is ancient and has no journalling.

Is this a combined BE/FE or networked? If so is it wired or wireles. if wireless, that is your likely problem.

---

### Post by Kantalias on 2012-10-09
> **nickrout said:**
> Is this a combined BE/FE or networked?

I have a combined frontend/backend.  (And, incidentally, all networks connections are wired.)  

This hardware has worked fantastically for me in various incarnations with different versions of Ubuntu and Myth for several years.  These issues seem to have come up with a recent hard drive upgrade brought on by a failing drive.  This modification moved me from a single WD20EARS to a Crucial M4 SSD2 for the system and a WD20EARX for recordings.  At the hardware level I'm primarily concerned about the "new"(ish) EARX which is a SATA III version of the EARS (SATA II). 

I've applied all the Ubuntu and Myth updates as of a week ago hoping to get an updated kernel driver that would support this disk.  Since you feel strongly that the filesystem isn't to blame, I'm tempted to move to a different physical disk.

Thoughts?

---

### Post by nickrout on 2012-10-09
I guess it could be the disk. Hard to say, if you can borrow another and try it out, you'd know, but if you have to buy one it's an expensive punt. 

anything in dmesg or other kernel logs?

Just thought, you almost undoubtedly have a 4k block disk drive. Do you have the partitions properly aligned? There's a lot of stuff on the net about this issue.

---

### Post by Kantalias on 2012-10-09
> **nickrout said:**
> anything in dmesg or other kernel logs?

Nothing in dmesg.  How do I check kernal logs?

> **nickrout said:**
> Just thought, you almost undoubtedly have a 4k block disk drive. Do you have the partitions properly aligned? There's a lot of stuff on the net about this issue.

I saw lots about alignment when I was partitioning the drive.  I *think* I checked that, but I'll double check.

---

### Post by nickrout on 2012-10-10
> **Kantalias said:**
> Nothing in dmesg.  How do I check kernal logs?
/var/log/kern.log> 


I saw lots about alignment when I was partitioning the drive.  I *think* I checked that, but I'll double check.Performance suffers greatly with misaligned partitions.

How about setting your LiveTV Storage Group to somewhere on the SSD and seeing how it goes?

---

### Post by Rotak on 2012-10-10
> **nickrout said:**
> No, xfs id the preferred. ext2 is ancient and has no journalling.

Hmmm. No journaling is why I preferred ext2. It's fast. :D And I don't see any benefit of journaling for a recordings HDD on a MythTV box. But I agree, that ext2 is ancient, so ext4 with disabled journaling may be an alternative. I didn't consider it, because when I installed my MythTV box, ext4 was an alpha release.

---

### Post by Kantalias on 2012-10-10
> **nickrout said:**
> /var/log/kern.log

Nothing there either (like dmesg, the last entry is ~20 seconds after boot).

> **nickrout said:**
> Performance suffers greatly with misaligned partitions.

The alignment looks good:
 ```
$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001c877

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            [COLOR=Red]2048[/COLOR]  3907028991  1953513472   83  Linux
```Unfortunately, I can't say the same for the sector size of the partition:
```
$ sudo xfs_growfs -n /dev/sdb1
meta-data=/dev/sdb1              isize=256    agcount=32, agsize=15261824 blks
         =                       [COLOR=Red]sectsz=512[/COLOR]   attr=2
data     =                       bsize=4096   blocks=488378368, imaxpct=5
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal               bsize=4096   blocks=238466, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
```Looks like I'll be redoing the partition...  

> **nickrout said:**
> How about setting your LiveTV Storage Group to somewhere on the SSD and seeing how it goes?

My problem isn't limited to LiveTV.  I have issues playing back recordings.  It's worse when other recordings are being made in the background, but it still happens (on occasion) when the system is doing nothing else beside playing back what I'm watching.

---

### Post by nickrout on 2012-10-11
putting some recordings or livetv on the ssd was simply for a test. To see if things worked ok on another drive.

---

### Post by davidryderuk on 2012-10-19
> On a whim, I watched atop while viewing a recording and another one was being written to disk. I saw this during smooth playback:

Code:

DSK |          sdb  | busy     17%  | read      70 |  write     47 |  KiB/r    244 |               | KiB/w    357  | MBr/s   1.67  | MBw/s   1.64 |  avq     1.49 |  avio 14.7 ms |

When a playback stall occurred, I saw this:

Code:

DSK |          sdb  | busy     98%  | read      22 |  write      7 |  KiB/r    302 |               | KiB/w    258  | MBr/s   0.65  | MBw/s   0.18 |  avq     6.74 |  avio  334 ms |

Obviously the busy percentage is a problem. The other obvious issue is avio (far right, you have to scroll over in the code section of the post), which I assume is some measure of access time based on its healthy number.


Have you looked at which processes are reading or writing to disk? atop has a mode for listing processes according to the amount of data they are reading or writting.

Here is the output I get watching a low definition video using mplayer, recorded using mythtv.

```
atop -d
```

```

MEM | tot     3.5G | free  133.9M |  cache   1.8G | dirty   0.1M | buff  136.2M | slab  200.2M |               |              |              |
SWP | tot     3.5G | free    3.5G |               |              |              |              |               | vmcom   4.2G | vmlim   5.2G |
DSK |          sda | busy      1% |  read      24 | write      4 | KiB/r    128 | KiB/w      7 | MBr/s   0.30  | MBw/s   0.00 | avio 3.43 ms |

  PID                     RDDSK                     WRDSK                    WCANCL                     DSK                    CMD         1/2
29994                     3072K                        4K                        0K                    100%                    mplayer
  239                        0K                        8K                        0K                      0%                    jbd2/sda4-8
 2574                        0K                        4K                        0K                      0%                                      

```

And here is a benchmark for my hard drive.

```
sudo hdparm -tT /dev/sda
```

```
/dev/sda:
 Timing cached reads:   3524 MB in  2.00 seconds = 1763.12 MB/sec
 Timing buffered disk reads: 226 MB in  3.00 seconds =  75.26 MB/sec

```

---

### Post by bbzzdd on 2012-11-12
I've got a new Myth install and am experiencing the same issue.  It happens intermittently and on live tv only.

```
Nov 12 21:01:37 dvr mythlogserver: mythfrontend[2447]: N CoreContext mythplayer.cpp:2095 (PrebufferEnoughFrames) Player(0): Waited 102ms for video buffers AAfAALAAfAAAAA
Nov 12 21:01:37 dvr mythlogserver: mythfrontend[2447]: N CoreContext mythplayer.cpp:2095 (PrebufferEnoughFrames) Player(0): Waited 204ms for video buffers AAfAALAAfAAAAA
Nov 12 21:01:37 dvr mythlogserver: mythfrontend[2447]: N CoreContext mythplayer.cpp:2095 (PrebufferEnoughFrames) Player(0): Waited 306ms for video buffers AAfAALAAfAAAAA
Nov 12 21:01:37 dvr mythlogserver: mythfrontend[2447]: N CoreContext mythplayer.cpp:2095 (PrebufferEnoughFrames) Player(0): Waited 408ms for video buffers AAfAALAAfAAAAA
Nov 12 21:01:37 dvr mythlogserver: mythfrontend[2447]: N CoreContext mythplayer.cpp:2095 (PrebufferEnoughFrames) Player(0): Waited 510ms for video buffers AAfAALAAfAAAAA
Nov 12 21:01:38 dvr mythlogserver: mythfrontend[2447]: N CoreContext mythplayer.cpp:2095 (PrebufferEnoughFrames) Player(0): Waited 612ms for video buffers AAfAALAAfAAAAA
Nov 12 21:01:38 dvr mythlogserver: mythfrontend[2447]: N CoreContext mythplayer.cpp:2095 (PrebufferEnoughFrames) Player(0): Waited 102ms for video buffers AAAAAfLAAALAAA

```

Generally video playback is silky smooth.  Using VDPAU advanced.  Recorded playback is 100% solid.  It seems I get these issues strange enough when commercial breaks come up or I start a program.  I am not running the commercial detector real-time.  This is Myth 0.26 on Mythbuntu 12.04.  I'd be happy to provide any info to help diagnose this.

I don't think it's disk-related.  I am able to hammer the disk even defragging during playback with no onscreen stutter or PrebufferEnoughFrames log errors.  Drive seems fast enough:

```

sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   6998 MB in  2.00 seconds = 3501.06 MB/sec
 Timing buffered disk reads: 294 MB in  3.00 seconds =  97.86 MB/sec

```



I ran the 'atop -d' command as described above and no out of the ordinary disk access when the problem happens:

```

ID           RDDSK           WRDSK           WCANCL           DSK           CMD        1/3
 1502              0K          17344K               0K          100%           mythbackend
  269              0K             12K               0K            0%           jbd2/sda6-8
 1206              0K              4K               0K            0%           mysqld
 2447              0K              0K               0K            0%           mythfrontend.r
 2024              0K              0K               0K            0%           mythlogserver

```

CPU is generally nil on playback with ~97% idle time according to nmon.  No processes are spiking.

I am wondering if it's an issue with the source?  I am using digital cable clearqam channels and the Hauppauge 1213 WinTV-HVR-2250.

---

### Post by Kantalias on 2012-11-12
> **bbzzdd said:**
> I've got a new Myth install and am experiencing the same issue.  It happens intermittently and on live tv only.  

> **bbzzdd said:**
> Generally video playback is silky smooth.  Using VDPAU advanced.  Recorded playback is 100% solid.  

This issue with Live TV only has been "managed" by many with the practice of pausing plackback for a few seconds at the start of watching Live TV.  



I've redone the partition on my disk to fix the sector size:
```
$ sudo xfs_growfs -n /dev/sdb1
meta-data=/dev/sdb1              isize=256    agcount=32, agsize=15261825 blks
         =                       [COLOR=Red]sectsz=4096[/COLOR]  attr=2
data     =                       bsize=4096   blocks=488378390, imaxpct=5
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal               bsize=4096   blocks=32768, version=2
         =                       [COLOR=Red]sectsz=4096[/COLOR]  sunit=1 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
```Immediately afterwards I got stuttering on Live TV with the typical error messages.  I tried the pause trick but it didn't work.  I'm going to keep an eye on it to see if there is any change in the rate of incidence.  

I'm really starting to think these WDxxEAR**X** drives are no bueno on existing kernels.  If I've still got trouble my next step is to put my last, "legacy" WDxxEAR**S** drive in.

---

### Post by bbzzdd on 2012-11-13
> **Kantalias said:**
> 
I'm really starting to think these WDxxEAR**X** drives are no bueno on existing kernels.  If I've still got trouble my next step is to put my last, "legacy" WDxxEAR**S** drive in.

Yipes!

```

sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC **WD20EARX**-00PASB0                    
	Serial Number:      WD-xxxxxxxxxxxx
	Firmware Revision:  51.0AB51
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0

```

Seems like a common thread...

---

### Post by bbzzdd on 2012-11-13
One thing I noted in my original post and I am monitoring and noticing now is this seems to happen right around the start and end of commercial breaks.  I know it's the oddest thing ever but this info sort of has me leaning toward the source.  I don't know enough about broadcast to speculate what may be going on but all I can say is the program playback itself is smooth and the vast majority of  PrebufferEnoughFrames issues seem to happen around either the start or end of breaks, intermittently.

I also notice this one around the start of a show which is most likely due to flipping the ringbuffer:

```

Nov 13 07:00:01 dvr mythlogserver: mythfrontend[2447]: N CoreContext avformatdecoder.cpp:783 (SetEof) AFD: Resetting byte context eof (livetv 1 was eof 0)
Nov 13 07:00:02 dvr mythlogserver: mythfrontend[2447]: E Decoder ringbuffer.cpp:271 (Reset) RingBuf(/var/lib/mythtv/livetv/1041_20121113120000.mpg): RingBuffer::Reset() nonzero readpos.  toAdjust: 1 readpos: 289432 readAdjust: 2548077928
Nov 13 07:00:02 dvr mythlogserver: mythfrontend[2447]: N Decoder avformatdecoder.cpp:783 (SetEof) AFD: Resetting byte context eof (livetv 1 was eof 0)

```

Might symlink /var/lib/mythtv/livetv to my WD7501AALS to rule out the WD20EARX but starting to think it's not disk related.  Still maddening.

---

### Post by Kantalias on 2012-11-13
Yeah, I'd say there's some similarity in HDDs:
```
$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD20EARX-008FB0                     
	Serial Number:      WD-xxxxxxxxxxxx
	Firmware Revision:  51.0AB51
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
```

> **bbzzdd said:**
> One thing I noted in my original post and I am monitoring and noticing now is this seems to happen right around the start and end of commercial breaks.

In my case the stuttering happens randomly in the middle of watching a recording or Live TV.  There's no correlation to commercial skipping (in the case of recordings) or breaks (in the case of Live TV).  

I didn't have this problem until I got the EARX.  I've used MythTV for several years with multiple different hardware setups (including a hardware change under 12.04).  This stuttering had never occurred before.  As soon as I work up the motivation to deal with copying 1 TB of data *again* I'll put an EARS back in.

---

### Post by nickrout on 2012-11-14
> **Kantalias said:**
> Yeah, I'd say there's some similarity in HDDs:
```
$ sudo hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD20EARX-008FB0                     
	Serial Number:      WD-xxxxxxxxxxxx
	Firmware Revision:  51.0AB51
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
```



In my case the stuttering happens randomly in the middle of watching a recording or Live TV.  There's no correlation to commercial skipping (in the case of recordings) or breaks (in the case of Live TV).  

I didn't have this problem until I got the EARX.  I've used MythTV for several years with multiple different hardware setups (including a hardware change under 12.04).  This stuttering had never occurred before.  As soon as I work up the motivation to deal with copying 1 TB of data *again* I'll put an EARS back in.

That drive (ie the new one) will have 4k sectors and if your patitions are not aligned properly it WILL have performance issues.

You may have already taken that into account and I have not read the whole thread, sorry if this has already been dealt with.

---

### Post by bbzzdd on 2012-11-14
Just grasping at straws here but have you tried disabling the WD head parking on that drive?

[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

I disabled it and it did not make a difference in my case but it seems you timeouts are much more dramatic than mine.  Mine are < 1000ms and yours are well over.

---

### Post by Kantalias on 2012-11-14
> **nickrout said:**
> That drive (ie the new one) will have 4k sectors and if your patitions are not aligned properly it WILL have performance issues.

As far as I understand the issue I do have the partition aligned:
```
$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd8607c12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   83  Linux

```2048*512/4096=256 -> aligned (I think).

> **bbzzdd said:**
> Just grasping at straws here but have you tried disabling the WD head parking on that drive?

Yes, I do have the head parking set as least aggressively as possible -- as it can't be entirely disabled -- because I believe the WD20EARS that died leading to the acquisition and installation of this WD20EARX was killed by this very issue. I set the parking timeout to max at boot:
```
$ cat /etc/rc.local
/sbin/hdparm -S 242 /dev/sdb

exit 0

```> **bbzzdd said:**
> ...it seems  you timeouts are much more dramatic than mine.  Mine are < 1000ms and  yours are well over.

I pasted in the worst of the worst.  I see messages ranging from hundreds of milliseconds up to seconds.  The hundreds of milliseconds don't seem to hurt anything.  Just glancing through the front end log and picking a few of 12,046 lines containing "PrebufferEnoughFrames" since October 4:

```
Oct 15 20:08:06 mythtv mythfrontend[4247]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(7): Waited 102ms for video buffers AAAAAAAAAAAALf
...
Oct 15 20:08:06 mythtv mythfrontend[4247]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(7): Waited 203ms for video buffers AAAAAAAAAAAALf
...
Oct 18 21:20:04 mythtv mythfrontend[4247]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(e): Waited 101ms for video buffers AAAAAAAfAAALAA
...
Oct 22 18:59:56 mythtv mythfrontend[4247]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(h): Waited 1119ms for video buffers AAAfAAAAAAAALf
...
Oct 23 21:39:57 mythtv mythfrontend[4247]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(k): Waited 104ms for video buffers AAAAAAAAAAAAAA
...
Oct 27 20:37:57 mythtv mythfrontend[6554]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 3463ms for video buffers AALAAAfAAAAfAA

```Incidentally, any idea what the parameter in parenthesis after "Player" is?

---

### Post by nickrout on 2012-11-15
> **Kantalias said:**
> As far as I understand the issue I do have the partition aligned:
```
$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd8607c12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   83  Linux

```2048*512/4096=256 -> aligned (I think).

As far as I know starting on 2048 is fine. Whether the end point matters I can't remember :)

---

### Post by Kantalias on 2012-11-15
> **nickrout said:**
> As far as I know starting on 2048 is fine. Whether the end point matters I can't remember :)

It's all about the starting point.  As long as the partition begins on a physical sector boundary then every block of the whole partition starts on a physical sector boundary.  

The trouble with these dumb Western Digital drives is that they lie about their logical sector size (claiming 512 bytes when it's really 4096) so you have to be careful about the block size of your partition *in addition to* the alignment.

---

### Post by nickrout on 2012-11-15
> **Kantalias said:**
> It's all about the starting point.  As long as the partition begins on a physical sector boundary then every block of the whole partition starts on a physical sector boundary.  

The trouble with these dumb Western Digital drives is that they lie about their logical sector size (claiming 512 bytes when it's really 4096) so you have to be careful about the block size of your partition *in addition to* the alignment.I am not sure quite what you mean, but what command tests that?

---

### Post by Kantalias on 2012-11-15
> **nickrout said:**
> I am not sure quite what you mean, but what command tests that?

The logical sector stuff?  It's in my post above -- "512/4096" for "logical/physical" from fdisk -lu. 

This looks like a good reference for the topic: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-twtr4KB-Disksdth-LX]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-twtr4KB-Disksdth-LX").

---

### Post by frankO on 2012-11-21
Could it have anything to do with the video card. I have had the same error for months now. I updated to 12.04 to see if it would fix the problem. It did not. Mine is a front end only. I have other front ends and they work fine. They are all connected by LAN.
```
Nov 18 17:24:33 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 113ms for video buffers AAAAAADAAAAAAA
Nov 18 17:24:33 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 114ms for video buffers AAALAAAAAADAAA
Nov 18 17:24:33 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 114ms for video buffers AAADAAAAAAAAUA
Nov 18 17:24:34 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 113ms for video buffers AAAAAAAAAAAUDA
Nov 18 17:24:34 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 113ms for video buffers AAAAAAAAAAADAU
Nov 18 17:24:34 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 113ms for video buffers AAAAAAAAAUAAAD
Nov 18 17:24:35 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 117ms for video buffers AAAAAAAAAAAAAA
Nov 18 17:24:35 darkstar2 mythfrontend[1409]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(5): Waited 102ms for video buffers AAAAAAAAADAAAA


```
So my problem is not caused by a disk. This buffer would be in memory I presume, either the cpu or video card ram.

---

### Post by Kantalias on 2012-12-02
> **frankO said:**
> Could it have anything to do with the video card.

In general, I don't know if video card issues could cause ringbuf errors in the frontend.  

In my case, I don't think the video card is involved -- when I watch a recording (or live TV) while another recording is in progress the incidence of stuttering and accompanying ringbuf errors increases dramatically.  Since making a recording only involves getting the data over the network and writing it to disk, I don't think the video card is involved for me.

I have reformatted a WD20EAR**S** to XFS, copied all my recordings over, and swapped it out in place of the WD20EAR**X**.  I can't be certain this has had any effect yet since I only did it today.  However, I did watch at least an hour of a prior recording while new recording was being made and, separately, hours of live TV with no issue.  I will report back in a week or so when I can be certain of the status of my system.

---

### Post by Kantalias on 2012-12-09
No stuttering all week so I think I've solved my problem.  Thanks everyone for your help and suggestions.

---

### Post by bbzzdd on 2012-12-09
Glad to hear it's solved on your end Kantalias. 

I still have stuttering during commercials which I don't think will ever be solved.  The same commercial can play at a different time and day and it will stutter at the exact same place.  My problem is probably on the cable co's side.

---

