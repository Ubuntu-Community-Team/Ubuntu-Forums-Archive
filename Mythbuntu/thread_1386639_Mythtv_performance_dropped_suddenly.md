---
title: "Mythtv performance dropped suddenly"
date: 2010-01-20
forum: Mythbuntu
---

### Post by Dartr on 2010-01-20
I've had a successful install of Mythtv running for almost a year with zero issues.  Normally able to record 2 HD shows simultaneously while delayed watching one of them on the same machine (single front/backend).

Our last successful clean recording was about a week ago, and now whether recording one or two shows, or watching live TV, the playback will randomly skip segments up to maybe 15 seconds in length.  Recording playback can be smooth for 5 mins or more, but then a big chunk will be missing in close timing.  Live TV playback is generally smooth, but drops 1-2 sec chunks.  We recorded 24 and tried watching it...seemed like a few words here and there were missing.  When we downloaded the show from Amazon we discovered that it really was skipping complete sentences of dialog... even part of a conversation between a few people.

The skips don't have clean breaks (like you'd see from commercial skip).  It's accompanied with visual artifacting.

Haven't made any system changes.  Made a network topology change a month ago, but have had successful recordings after that.

Have plenty of disk space.  Re-checked antenna alignment, reconfigured network to old setup, etc.  I'm guessing a recent software update?  I know enough to have gotten this setup up and running, but really am a newbie when it comes to troubleshooting in Linux (windows convert).

Appreciate any help on where to start looking!

Here's the setup:


Motherboard: ASUS M3N78-EM
CPU: AMD Athlon X2 5050e 2.6GHz 45w
RAM: Corsair 4GB (2x2GB) 800MHZ DDR2
Video Card: Onboard Nvidia 8300 512MB shared from system RAM
Sound Card: Onboard Realtek
HDD: Western Digital Raptor 150GB system/data
HDD: Western Digital Caviar 250GB recordings
DVD: NEC 3500 w/ bitsetting firmware
Remote: Streamzap
Tuners: Silicondust HD Homerun
Country: US
TV provider: Antenna
TV signal type: 8-VSB ATSC
Playback quality: High
Case: Nexus Clodius
PSU: Nexus 430w Compact PSU (16db!)
Case Fans: 2 x Nexus Silent 120mm fans
CPU Cooler: Nexus AXM-8200 CPU cooler
Monitor: HP LP2275w
OS: Jaunty 64 w/ Gnome desktop + MythTV

---

### Post by Dartr on 2010-01-22
Haven't been able to get far with this, but so far I've ruled out:

1. the network switch (no improvement when gong back to the original one) 
2. the antenna (it has also been supporting an OTA d/a converter box for an older TV... signal there is 80-90% consistently).
3. drive space (all partitions 30% or more free plus I've never had an issue when the recordings partition was full)

I do the regular Ubuntu updates, but I would suspect more people would be complaining if that was the source of my troubles.

---

### Post by myth1914 on 2010-01-22
First, Love Milwaukee!

Anyway...  It sounds like the card is losing the signal briefly.  Similar to if you have a bad signal, but you stated you have 80%+.  I would look at your system load/CPU usage while it's recording.

I don't know why it happened so suddenly as I have only seen issue arise after the upgrade to .22 which I suspect will be worked out as it seems they have had their hands full with the mythui change.

Have you tried doing a new channel scan to ensure the channel lock is stable?

---

### Post by Dartr on 2010-01-22
> **myth1914 said:**
> First, Love Milwaukee!

Anyway...  It sounds like the card is losing the signal briefly.  Similar to if you have a bad signal, but you stated you have 80%+.  I would look at your system load/CPU usage while it's recording.

Have you tried doing a new channel scan to ensure the channel lock is stable?

I take it you've visited?

The system load while recording 2 HD programs is quite high... around 9.5.  I don't remember it being that nearly that high in the past, but I can't say for sure.  CPU usage alternates between the two cores pretty consistently from 25% to 90% usage.  Is there a way to monitor these two in a log so I can verify I don't have any spikes after the recording is done?

I hadn't thought of rescanning channels.  I'll try that tonight.  Thanks for the tip... keep the ideas coming! (it's been too long since I've built this rig that I don't remember all of the components/variables.)

---

### Post by mathog on 2010-01-22
My bet is that one of the Ubuntu upgrades changed your Nvidia or ATI binary driver from one that worked to one with a bug that slows down your system.

Anything in /var/log/messages or the mythtv log files?  

Did you check the SMART status of your disk(s)?  Or is the disk really full?  Either way disk IO could become a problem.  One way to test is:

smartctl -t long /dev/hda  # or sda, as appropriate
# wait as long as it tells you to, varies by disk
smartctl -a /dev/hda # or again, sda

You might also want to check the disk IO speeds, just in case some Ubuntu upgrade messed that up.  Use bonnie++ to test for that.  Anything reasonble, like 50Mb/s or more for read and write, then this isn't the issue.

---

### Post by LowSky on 2010-01-22
there has been a good many thread lately of the newer updates messing up mythtv.

---

### Post by fcrowder on 2010-01-22
not sure but would something like this happens on my machine if I set it to look for commercials at the same tim it is recording another show the system usage goes way up.. perhaps it is encoding the shows or something of that nature while it is recording and bringing your system to a crawl..
I'm still a newb. but I thought you might check this anyhow.

---

### Post by Dartr on 2010-01-22
> **mathog said:**
> My bet is that one of the Ubuntu upgrades changed your Nvidia or ATI binary driver from one that worked to one with a bug that slows down your system.

Anything in /var/log/messages or the mythtv log files?  

Did you check the SMART status of your disk(s)?  Or is the disk really full?  Either way disk IO could become a problem.  One way to test is:

smartctl -t long /dev/hda  # or sda, as appropriate
# wait as long as it tells you to, varies by disk
smartctl -a /dev/hda # or again, sda

You might also want to check the disk IO speeds, just in case some Ubuntu upgrade messed that up.  Use bonnie++ to test for that.  Anything reasonble, like 50Mb/s or more for read and write, then this isn't the issue.

All good info for me... thanks!  I just ran a channel rescan on both tuners and am about to run another 2 HD program recording test.  Will post results.

Regarding log files, there is a lot in the mythtv logs and I just don't know what any of it means.  Should I post it here?

Too bad that an Ubuntu update could be a culprit... not fun.  I saw the most recent thread from another user's experience, but it doesn't sound like it fits my system.  I'll have to comb the other threads.

---

### Post by Dartr on 2010-04-16
I spent some time working with someone at Silicondust to troubleshoot the HDHR and network, but both passed with flying colors.

Here's the output from the smartctl test on the recordings disk.  Not sure what to make of it. Does it reveal any issues?



```
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD2500KS-00MJB0
Serial Number:    WD-WCANK9665790
Firmware Version: 02.01C03
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Apr 16 21:37:29 2010 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (7680) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  90) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   239   183   021    Pre-fail  Always       -       3008
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1184
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   067   067   000    Old_age   Always       -       24096
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       872
190 Airflow_Temperature_Cel 0x0022   058   041   045    Old_age   Always   In_the_past 42
194 Temperature_Celsius     0x0022   108   091   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     24084         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

Will have to run a test on the system disk next.

---

### Post by ian dobson on 2010-04-17
> **Dartr said:**
> I take it you've visited?

The system load while recording 2 HD programs is quite high... around 9.5.  I don't remember it being that nearly that high in the past, but I can't say for sure.  CPU usage alternates between the two cores pretty consistently from 25% to 90% usage.  Is there a way to monitor these two in a log so I can verify I don't have any spikes after the recording is done?

I hadn't thought of rescanning channels.  I'll try that tonight.  Thanks for the tip... keep the ideas coming! (it's been too long since I've built this rig that I don't remember all of the components/variables.)

Wow a load of 9.5 is really high, on my Quad recording 3 programs at the same time (2HD one SD) and commflagging at the same time to load doesn't rise to more than 2-2.5. What file system are you using for your recordings? How much ram do you have in your backend?

Maybe run a fsck on your recording file system.

Regards
Ian Dobson

---

### Post by Dartr on 2010-04-17
Here are the smartctl results of the system/data drive:

```
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Raptor family
Device Model:     WDC WD1500ADFD-00NLR1
Serial Number:    WD-WMAP41268601
Firmware Version: 20.07P20
User Capacity:    150,039,945,216 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 published, ANSI INCITS 397-2005
Local Time is:    Sat Apr 17 09:02:26 2010 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (4101) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  62) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   168   159   021    Pre-fail  Always       -       4633
  4 Start_Stop_Count        0x0032   100   100   040    Old_age   Always       -       919
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   069   069   000    Old_age   Always       -       22925
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       875
194 Temperature_Celsius     0x0022   117   097   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       849
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     22915         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by Dartr on 2010-04-17
> **ian dobson said:**
> Wow a load of 9.5 is really high, on my Quad recording 3 programs at the same time (2HD one SD) and commflagging at the same time to load doesn't rise to more than 2-2.5. What file system are you using for your recordings? How much ram do you have in your backend?

Maybe run a fsck on your recording file system.

Regards
Ian Dobson

Yeah, normally I was able to record 2 and watch 1 HD simultaneously with no real load issues.  Really scratching my head on this one.

Thanks for the lead.  Any tips on fsck usage?  I'll have to read up a bit on that.

---

### Post by iponeverything on 2010-04-17
Did vdpau stop working.

---

### Post by Dartr on 2010-04-17
> **iponeverything said:**
> Did vdpau stop working.

Up until last week I have been using Jaunty at High Quality setting in .21.  Last week I upgraded to Karmic and .22 to see if that would improve things and the symptoms are exactly the same.  Then tried VDPAU at all levels and still same symptoms.

---

### Post by Dartr on 2010-04-17
Alright, it seems to be an issue with the way my setup is recording.  I found some older recordings in High Quality that are playing back perfectly.  Not sure why I didn't think to check these first.

So now it seems that my machine can't create a new recording (and thus, play that recording back) cleanly.  Playback of older HQ recordings is fine.

Live TV is still affected as well.

---

### Post by iponeverything on 2010-04-18
are real time priority threads turned on?

---

### Post by ian dobson on 2010-04-18
Hi,

Try running a fsck on your recording file system.

What do you see when you do a iostat when your recording?
I see this when recording 4 programs at the same time.

```

 iostat
Linux 2.6.31-20-generic (alpha2)        04/18/2010      _x86_64_        (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.33   80.79    9.75    0.79    0.00    7.34

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              35.30       969.75      1168.49   57097650   68799344
sdb              34.96       962.33      1163.37   56660704   68498280
sdc              35.07       957.09      1170.64   56352224   68926016
sdd              34.91       965.30      1162.42   56836034   68441872
sde               0.00         0.06         0.00       3344          0
sdf               0.00         0.05         0.00       3216          0
md2               0.01         0.06         0.00       3560          0
md0              25.53        21.36       199.41    1257674   11741176
md1             253.21       486.90      1967.79   28668282  115861192

```

iowait is the most interesting value.
Also what file system are you using for your recording file system (ext3/4/xfs)?

Regards
Ian Dobson

---

### Post by nickrout on 2010-04-18
I had a weird high load on my backend recently. dmesg revealed a lot of disk related errors, which I googled and was able to fix.

---

### Post by Dartr on 2010-04-18
> **ian dobson said:**
> Try running a fsck on your recording file system.

Alright, I'm a real newb at this system troubleshooting bit...  Here's the response;

```
sudo fsck /dev/sdb
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?
```

Not sure what to do.  The recordings drive is really an ext3 partition on a separate disk.  It's mounted so I can reference it as /MythTV/recordings/

The remainder of the disk has swap and some static data storage (not accessed very often, just archived data).

---

### Post by novellahub on 2010-04-18
> **Dartr said:**
> Alright, I'm a real newb at this system troubleshooting bit...  Here's the response;

```
sudo fsck /dev/sdb
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?
```

Not sure what to do.  The recordings drive is really an ext3 partition on a separate disk.  It's mounted so I can reference it as /MythTV/recordings/

The remainder of the disk has swap and some static data storage (not accessed very often, just archived data).

Reboot choosing a recovery mode in the grub boot menu and then do your fsck.

---

### Post by Dartr on 2010-04-18
> **nickrout said:**
> I had a weird high load on my backend recently. dmesg revealed a lot of disk related errors, which I googled and was able to fix.

looking at /var/log/dmesg, the only warnings/errors reported are:

```
[    0.320425] ACPI Warning: Incorrect checksum in table [OEMB] - 04, should be F7 20090521 tbutils-246
...

[   25.642942] nForce2_smbus 0000:00:01.1: Error probing SMB2.
...

[   25.750604] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   25.750605]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   25.750606]     Might be a BIOS bug, if BIOS says ECC is enabled
[   25.750607]     Use of the override can cause unknown side effects.
...

[   25.768001] amd64_edac: probe of 0000:00:18.2 failed with error -22
...

[   26.621186] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended

```

The first several are all related to bugs, but all of this is beyond me.  The last one sounds interesting, as I didn't think I had that many mounts??

---

### Post by Dartr on 2010-04-18
> **novellahub said:**
> Reboot choosing a recovery mode in the grub boot menu and then do your fsck.

Just to be sure... I selected recovery mode, then chose command prompt.

Typing sudo fsck /dev/sdb gave me the same error.

---

### Post by ian dobson on 2010-04-18
> **Dartr said:**
> Just to be sure... I selected recovery mode, then chose command prompt.

Typing sudo fsck /dev/sdb gave me the same error.

OK, boot from a LiveCD and then run a fsck.

Regards
Ian Dobson

---

### Post by Dartr on 2010-04-19
Great... so what does it mean when I get the same error with a LiveCD?

Does it matter that I have a linux-swap partition on this drive?

---

### Post by ian dobson on 2010-04-19
Hi,

Did you partition your drive before formatting it? If so then your filesystem is on /dev/sdb1, so you need to do a fsck /dev/sdb1.

If you go to the command line and do a fdisk -l you'll see a list of partitions on your drive:-

```

fdisk -l

Disk /dev/sda: 8019 MB, 8019099648 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06f006ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         927     7446096   83  Linux
/dev/sda2             928         974      377527+   5  Extended
/dev/sda5             928         974      377496   82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06f006ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux
 
```

Regards
Ian Dobson

---

### Post by Dartr on 2010-04-19
> **ian dobson said:**
> Hi,

Did you partition your drive before formatting it? ... Regards
Ian Dobson

I did.  It has 3 partitions: Myth recordings, personal files, and linux-swap.  So fsck is to be executed against a partition, and not the disk?  I'll try that tonight.

---

### Post by nickrout on 2010-04-19
you don't fsck the drive , you fsck the partition. so fsck /dev/sdb1 not fsck /dev/sdb

---

### Post by Dartr on 2010-04-19
Ok, now we have some progress...

```
sudo fsck /dev/sdb2
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
MythTV has been mounted 126 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
MythTV: 24453/13393920 files (14.0% non-contiguous), 47876351/53564718 blocks

```


Also, I no longer need the personal files partition on this drive.  Would I improve things to remove it and expand the recordings partition?  Is there a better filesystem to use than ext3 for recordings?  And one more thing, is it beneficial/required to have a linux-swap partition on this drive?

So in running this check, are any fixes taking place, or is this just a report-only function?

---

### Post by Dartr on 2010-04-20
> **ian dobson said:**
> What do you see when you do a iostat when your recording?

Ian, here are the results.  They look a lot different than yours...

```
iostat
Linux 2.6.31-20-generic (br-ubu-desk) 	04/20/2010 	_x86_64_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.87    0.44    2.34    2.12    0.00   94.22

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.58        24.44        14.32    2095384    1228124
sdb               1.76       195.67       109.12   16775968    9355929

```

This is while recording to HD programs (one 1080i, the other 720p) with VDPAU slim, IIRC.

---

### Post by Dartr on 2010-04-20
For comparison, here's what the iostat reports when no recordings are being made:

```
iostat
Linux 2.6.31-20-generic (br-ubu-desk) 	04/20/2010 	_x86_64_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.91    0.44    2.44    2.49    0.00   93.72

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.60        24.31        14.59    2100000    1260156
sdb               1.77       194.20       125.97   16776200   10882569

```

---

### Post by ian dobson on 2010-04-20
Hi,

Your iowait seems quite high when not recording. Could it be that something else is using the harddisk (commflagging?).

Regards
Ian Dobson

---

### Post by nickrout on 2010-04-20
is dma activated on the drive(s)?

---

### Post by Dartr on 2010-04-20
> **ian dobson said:**
> Hi,

Your iowait seems quite high when not recording. Could it be that something else is using the harddisk (commflagging?).

Regards
Ian Dobson

I hadn't thought of that... it could've still been commflagging when I ran those post-record checks.  Will try again tonight w/o recording.  However, CPU usage was nonexistent, so I suspect it wasn't commflagging at the time. (??)

Is there a way to see which processes/packages are creating disk usage load/spikes?

---

### Post by Dartr on 2010-04-20
> **nickrout said:**
> is dma activated on the drive(s)?

Will have to check, thanks.

---

### Post by Dartr on 2010-04-20
Here's iostat with no recent computer activity (that I'm aware of):

```
iostat
Linux 2.6.31-20-generic (br-ubu-desk) 	04/20/2010 	_x86_64_	(2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.00    0.34    2.31    1.74    0.00   94.62

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.50        19.65        15.12    2463604    1895396
sdb               1.23       133.84        86.80   16782568   10883481

```

---

### Post by Dartr on 2010-04-20
I checked around about DMA... apparently not needed for SATA?

Here's the hdparm results for the recordings drive:

```
sudo hdparm /dev/sdb

/dev/sdb:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0

```

And for system...

```
sudo hdparm /dev/sda

/dev/sda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 18241/255/63, sectors = 293046768, start = 0

```

---

### Post by matt06 on 2010-04-21
My thoughts..

**DMA:** I have a SATA drive in my backend for recordings, but my BIOS is set to "IDE Legacy" for SATA mode and hdparm reports the following (of course I have no clue how accurate any of this is...DMA may very well not apply to SATA?)

```
matt@mythtv:~$ sudo hdparm -i /dev/sde

/dev/sde:

 Model=Hitachi, FwRev=ST6OA31B, SerialNo=xxxxxxxxxxxxxx
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=56
 BuffType=DualPortCache, BuffSize=15001kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 **UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6**
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 *** signifies the current active mode**
```
**iostat:**  is this a meaningful metric for system load/performance? with a refresh interval vs. single reading?  a single reading, simply 'iostat', seems to be an overall average perhaps??  go easy on me if I'm wrong here cause I really don't know, but..

2 HD recordings/2 commflags starting, /dev/sda is OS and DB, /dev/sde is of course my recordings drive and the rest are (mostly) idle samba network shares.

```
matt@mythtv:~$ iostat 3
Linux 2.6.31-20-generic (mythtv)   04/21/2010      _i686_  (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.06    3.98    2.59    1.02    0.00   89.35

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               3.71        95.63        29.89  132784158   41505817
sdd               0.13        11.35         0.15   15752594     204336
sde               9.14      1838.01       635.46 2552002418  882313168
sdc               0.16         9.21         0.13   12784438     183728
sdb               0.02         1.25         0.06    1735858      79800

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.95   53.25    8.44    3.41    0.00   32.95

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.33         5.33        16.00         16         48
sdd               1.67       128.00         0.00        384          0
sde              88.00     36034.67      5242.67     108104      15728
sdc               0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.40   50.73    9.56    6.48    0.00   29.82

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.33        61.33         0.00        184          0
sdd               0.67       114.67         0.00        344          0
sde              85.00     35792.00      5213.33     107376      15640
sdc               0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.58   51.95    8.47    6.84    0.00   29.15

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               7.67        10.67        69.33         32        208
sdd               0.00         0.00         0.00          0          0
sde              73.00     26480.00      4018.67      79440      12056
sdc               0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0
```

and here practically idle:

```
matt@mythtv:~$ iostat 3
Linux 2.6.31-20-generic (mythtv)   04/21/2010      _i686_  (2 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           3.07    3.99    2.59    1.03    0.00   89.33

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               3.72        95.80        29.90  133065918   41531089
sdd               0.13        11.36         0.15   15778722     204424
sde               9.15      1841.19       636.42 2557440986  884004576
sdc               0.16         9.20         0.13   12784502     183728
sdb               0.02         1.25         0.06    1735858      79800

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           4.99    0.00    2.65    4.21    0.00   88.14

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0.33         0.00         8.00          0         24
sdd               2.33         0.00        21.33          0         64
sde               2.67        13.33        24.00         40         72
sdc               0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           4.98    0.00    2.02    0.62    0.00   92.38

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0.67         0.00         5.33          0         16
sdd               0.33        85.33         0.00        256          0
sde               2.00        16.00         0.00         48          0
sdc               0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           4.84    0.00    3.12    3.43    0.00   88.61

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0.00         0.00         0.00          0          0
sdd               0.33        85.33         0.00        256          0
sde               2.33        10.67        24.00         32         72
sdc               0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0
```

HTH, YMMV, etc.

---

### Post by Dartr on 2010-04-21
speaking of commflagging, I used to be able to run it while recording.  now, even with it delayed until after recording, my recordings momentarily freeze and/or drop frames.

---

### Post by Dartr on 2010-04-21
> **matt06 said:**
> My thoughts..

**DMA:** I have a SATA drive in my backend for recordings, but my BIOS is set to "IDE Legacy" for SATA mode and hdparm reports the following (of course I have no clue how accurate any of this is...DMA may very well not apply to SATA?)

With the -i switch, my hdparm output looks similar...

```
/dev/sdb:

 Model=WDC, FwRev=02.01C03, SerialNo=WD-WCANK9665790
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=488397168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

...so I guess I'm okay there.

---

### Post by Dartr on 2010-04-21
another attempt:  I just tried switching from relatime to noatime on the recordings mount... same symptoms.

---

### Post by Dartr on 2010-04-21
Would this help to determine the io hog?

[http://pvaneynd.blogspot.com/2007/03/what-is-causing-all-this-io.html](http://pvaneynd.blogspot.com/2007/03/what-is-causing-all-this-io.html)

Not sure if it would work in Ubuntu as written, but seems that it should pinpoint app(s) that are to blame.

Or do I still need to consider that my disk may be at fault?

---

### Post by Dartr on 2010-04-21
Gave that dmesg script a whirl and it resulted in this:

```
dmesg | gawk '/(READ|WRITE|dirtied)/ {activity[$2]++} END {for (x in activity) print activity[x],x}'| sort -nr | head -n 10
652 kjournald(476):
409 pdflush(32):
272 kjournald(1069):
91 rsyslogd(14808):
43 gedit(14834):
36 mono(3877):
34 gconfd-2(3770):
24 gnome-terminal(14723):
21 mythbackend(12100):
18 mono(3320):
```

So are kjournald and pdflush the culprits here?

---

### Post by matt06 on 2010-04-21
I'm afraid I'm way outta my league now, but I did quickly find a couple threads.

[kjournald constantly accessing disk]("http://ubuntuforums.org/showthread.php?t=369759")
[http://ubuntuforums.org/showthread.php?t=369759](http://ubuntuforums.org/showthread.php?t=369759)

[[SOLVED] kjournald and pdflush constantly writing to HD]("http://ubuntuforums.org/showthread.php?t=833301")
[http://ubuntuforums.org/showthread.php?t=833301](http://ubuntuforums.org/showthread.php?t=833301)

No clue if they apply to your Ubuntu version.  Any experts have any suggestions to pinpoint the problem?  Are we barking up the wrong tree?

---

### Post by Dartr on 2010-04-22
Perhaps I spoke too soon.  The above dmesg stats are from when the machine had been sitting idle all day, so that could explain the higher kjournald counts (all of which are on the / and /home mounts).  Here's the output while watching live tv:

```
dmesg | gawk '/(READ|WRITE|dirtied)/ {activity[$2]++} END {for (x in activity) print activity[x],x}'| sort -nr | head -n 10
3718 mythbackend(16496):
39 kjournald(476):
20 kjournald(5985):
17 pdflush(32):
3 mythbackend(16495):
3 kjournald(1069):
2 mono(3320):
1 mysqld(7934):

```

Possibly more in line?

And here's one more, just a few minutes into live tv:

```
dmesg | gawk '/(READ|WRITE|dirtied)/ {activity[$2]++} END {for (x in activity) print activity[x],x}'| sort -nr | head -n 10
2916 mythbackend(16496):
903 pdflush(32):
26 kjournald(476):
19 kjournald(5985):
6 rsyslogd(16394):
4 mysqld(7934):
4 mysqld(7276):
4 mono(3877):
4 kjournald(1069):
3 mythbackend(16495):

```

---

### Post by matt06 on 2010-04-22
I was going to run the script next time I was recording a few shows, which is now, but it outputs absolutely nothing.  I've tried sudo everywhere possible and I'm afraid to break the current recordings if I do anything more drastic.  Perhaps I don't have a required package installed or I'm copying the command wrong?

```
matt@mythtv:~$ dmesg | gawk '/(READ|WRITE|dirtied)/ {activity[$2]++} END {for (x in activity) print activity[x],x}'| sort -nr | head -n 10
matt@mythtv:~$
```

---

### Post by Dartr on 2010-04-22
Thanks for trying.  2 things I've noticed about this script... first, I have to run it as root, not with sudo.  ("sudo su" to get root).  Second, the script needs to be compatible with your dmesg format.  If yours looks like my sample below (just type "dmesg"), then the script should work.  There is at least one other variant of the script in the link I posted earlier.

Sample format from my dmesg output:

```
[307664.730665] bash(18364): dirtied inode 2001006 (.bash_history) on sda7
[307665.861097] mono(3320): dirtied inode 876545 (shared_data-br-ubu-desk-Linux-x86_64-328-12-0) on sda7
[307667.010539] kjournald(1069): WRITE block 134452888 on sda7

```

If your columns line up the same, you should be good to go.

---

### Post by Dartr on 2010-04-26
Good news! Playback has improved dramatically.  Haven't thoroughly tested it yet with 2 recordings while watching live tv, but we're getting there.  I made the following changes this weekend:

[LIST=1]
[*]grew the size of my primary swap partition on the system disk to make up for...
[*]removed the 2nd swap partition on the recordings disk
[*]removed the static data partition on the recordings disk
[*]resized the recordings partition to take up the entire disk so now it's the only partition on that disk
[*]reformatted the recordings partition to JFS.
[/LIST]

I can now watch TV with only the occasional dropped frame or playback freeze (once every 10 mins or so?).  The real test will be multiple recordings.  Will report back after this is done.

My iowait at idle is below 1.0, and below 3.0 while watching live tv.

Tried VDPAU at all three levels, but none played back smoothly.  The non-VDPAU High Quality works best.  Any ideas on that one?  I know there are others out there with this mobo and integrated 8300 GPU that have had success, so there must be something to it that I need to change.

Still baffeled though as to why my performance dropped originally...

---

### Post by Dartr on 2010-04-28
I was really hoping to report good news.  Started watching a 720p recording and had flawless playback for the first 25 minutes.  Then it started doing something I haven't seen before:  every 5-10 seconds the video would briefly freeze, there would be a quick buzz sound, the video would pixelate a bit and then everything would resume as normal.

I checked a 1080i recording that was made at the same time as a different 720p recording (that I haven't checked yet).  This 1080i recording plays flawlessly for the first 7 mins or so, then exhibits the same behavior as above for the remainder of the recording.

Haven't watched live tv long enough to see this.  However, occasionally when I browse the OSD for a different channel, then select a different channel, the screen goes black as if about to change, but then the frontend freezes there and needs to be force-quit.

---

### Post by nickrout on 2010-04-29
Sorry I haven't reviewed the thread to see if this has been covered, but it really sounds to me like you have signal problems, the resulting files can often cause anything from playback glitches to a complete frontend crash. 

Do the errors happen in the same place each time you play the file?

And what error messages is the frontend throwing out when the problems occur? (hint, ssh in from your laptop while running. ```
tail -f /var/log/mythtv/mythfrontend.log
``` will show you the log file as you watch.

---

### Post by novellahub on 2010-04-29
I recently had some playback issues with my Slave Backend / Frontend machine. The video was having issues with Prepausing issues and audio sync issues in the mythfrontend.log file. I tracked it down to a hardware issue.  Half of the capacitors on my video card failed (They bulge out in appearance) causing instability.  I ended up replacing the video card and everything works great again.

---

### Post by Dartr on 2010-04-29
> **nickrout said:**
> Sorry I haven't reviewed the thread to see if this has been covered, but it really sounds to me like you have signal problems, the resulting files can often cause anything from playback glitches to a complete frontend crash.

I have a TV and digital tuner hooked up to the same antenna (antenna has 2 outputs) and the picture is perfect.  Does this rule out signal, or are there imperceptible losses that can cause issues for MythTV?


> **nickrout said:**
> Do the errors happen in the same place each time you play the file?

It varies.  1st show it started 25 minutes in and continued for duration of the show.  2nd show started 6 minutes in and continued.  Tried live tv last night and was able to watch about 20 minutes or so before the symptoms started.


> **nickrout said:**
> And what error messages is the frontend throwing out when the problems occur? (hint, ssh in from your laptop while running. ```
tail -f /var/log/mythtv/mythfrontend.log
``` will show you the log file as you watch.

Will have to try this soon... thanks.

---

### Post by nickrout on 2010-04-29
> **Dartr said:**
> I have a TV and digital tuner hooked up to the same antenna (antenna has 2 outputs) and the picture is perfect.  Does this rule out signal, or are there imperceptible losses that can cause issues for MythTV?




It varies.  1st show it started 25 minutes in and continued for duration of the show.  2nd show started 6 minutes in and continued.  Tried live tv last night and was able to watch about 20 minutes or so before the symptoms started.




Will have to try this soon... thanks.

If you play the same file twice, does it fail in the same place each time?

---

