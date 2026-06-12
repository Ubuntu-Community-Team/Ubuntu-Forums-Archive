---
title: "mythfrontend segfault error 4 in libc-2.12.1.so"
date: 2010-10-10
forum: Mythbuntu
---

### Post by DrJohn999 on 2010-10-10
Fresh install to wiped disks of 10.10 final release: when changing to some HD broadcast channels mythfrontend segfaults:
```
Oct 10 13:51:37 m3n78em kernel: [  381.397913] mythfrontend.re[2296]: segfault at 93d05918 ip 0655a5f8 sp a68a8230 error 4 in libc-2.12.1.so[652b000+157000]

```
the session terminates, and a normal login screen displays. Logging in again starts the frontend again but same problem occurs. Changing the default channel back to 2_1 (for example) from the backend setup clears the problem until tuning to one of the channels that causes it. Not all HD channels do this, just two of five or so.

The setup: HDHomeRun box with latest firmware (hdhomerun_atsc_firmware_20100828.bin); gigabit ethernet, fixed IP addresses; Asus M3N78-EM board, 2GB, HDMI, iMon VFD (but not yet set up), /dev/sdb is a 320 GB boot drive with root at /dev/sdb1 (ext4), /dev/sda1 is a 1 TB XFS mounted at /var/lib/mythtv. nVidia current proprietary graphics driver. No changes to video display mode but did change the size of the GUI (otherwise it runs off the side of the TV) and so am using fullscreen for video output and separate smaller size for GUI. Other than that, its using the defaults as much as possible (IP addresses, SchedulesDirect info, etc as required of course).

This never occurred with any prior releases from 8.10 --> 10.04. At least I can wipe all and go back since any need-to-keep files are backed up elsewhere.

---

### Post by superm1 on 2010-10-11
It would be worthwhile to turn on apport to capture the details of this crash.  That will allow the report to be filed and tracked down.  It could easily be a myth bug that was introduced in 0.23.1 or a bug elsewhere in the system.

To turn on apport, modify /etc/default/apport and restart your system after it's turned on.  Next time myth crashes, it should ask you to file a report that will hopefully get a good backtrace submitted.

---

### Post by DrJohn999 on 2010-10-11
Reproduced and reported via apport: [https://bugs.launchpad.net/bugs/658691](https://bugs.launchpad.net/bugs/658691)

Additional information (also will be added to the bug report shortly):

The crash occurs when tuning certain HD channels with TV Playback set to CPU+ and CPU--. Both of these invoke XvMC at my screen resolution. Other modes tried include CPU++, VDPAU normal, VDPAU high, normal, and high quality; all of these work and none of them include XvMC as a possibility.

---

### Post by superm1 on 2010-10-11
> **DrJohn999 said:**
> Reproduced and reported via apport: [https://bugs.launchpad.net/bugs/658691](https://bugs.launchpad.net/bugs/658691)

Additional information (also will be added to the bug report shortly):

The crash occurs when tuning certain HD channels with TV Playback set to CPU+ and CPU--. Both of these invoke XvMC at my screen resolution. Other modes tried include CPU++, VDPAU normal, VDPAU high, normal, and high quality; all of these work and none of them include XvMC as a possibility.

I think the apport retracer is still at this one or it's got some private data.  Could you double check (and remove) any private date you don't want shared and then mark it as a public bug?

---

### Post by DrJohn999 on 2010-10-11
Updated and made public.

---

### Post by blueeyesmike on 2010-10-11
I also am experiencing this crash. I would be happy to help out with crash reports if it would help.

Thanks for pointing out that different viewing modes act as a workaround.

---

### Post by superm1 on 2010-10-12
> **blueeyesmike said:**
> I also am experiencing this crash. I would be happy to help out with crash reports if it would help.

Thanks for pointing out that different viewing modes act as a workaround.

Yes, please follow the same above steps to enable apport and submit a crash report.  It never hurts to have another BT.  At worst the retracer will mark your bugs as duplicates after it's finished processing.

---

### Post by blueeyesmike on 2010-10-14
Bug report submitted via apport

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/660833](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/660833)

---

### Post by DrJohn999 on 2010-10-16
This problem recurs on another machine of mine, this time with Mythbuntu in a desktop frontend role with the previous machine as remote backend. Same symptoms, VDPAU does not have the problem. Both machines are similar: Asus m3n78em and Asus m4a78t. Bug report has been updated.

---

### Post by gusman21 on 2010-10-17
Same error.

Hauppauge HVR-1600

PC is front end and back end.

Only happens on OTA/digital tuner. Analog is fine.

---

### Post by maraschin on 2010-10-20
Hej,

I got a similar error in libc-2.12.1.so
I just did the latest update on 10.10 Server and got the following entry in the kernel log:

kernel: [  194.490772] zfs-fuse[3076]: segfault at 0 ip 00002ba4a9d3b426 sp 00002ba4da905b98 error 4 in libc-2.12.1.so[2ba4a9cba000+17a000]

PS: I'm running zfs-fuse and it was running normally until I update the system with the latest patch and restart the system.

---

### Post by gusman21 on 2010-10-21
seems to be resolved after updating and rebooting this morning.

---

### Post by DrJohn999 on 2010-10-22
Still crashing on CPU+ for me. System is up to date this morning 10-22-2010:

```
Linux m3n78em 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
```
```
MythTV Version   : 26437
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.7.0

```

---

### Post by TrevorBradley on 2010-10-29
Ugh, my mythtv backend just started hammering me with this error about once every two minutes for the past hour:

```
Oct 29 00:40:06 alexandria kernel: [54231.874634] mythbackend[26119]: segfault at abcfaffc ip b43e9ed6 sp abcfaff0 error 6 in libc-2.12.1.so[b4379000+157000]
Oct 29 00:42:30 alexandria kernel: [54376.241969] mythbackend[26194]: segfault at abdfcffc ip b4498ed6 sp abdfcff0 error 6 in libc-2.12.1.so[b4428000+157000]
Oct 29 00:44:53 alexandria kernel: [54519.091008] mythbackend[26253]: segfault at abdfaffc ip b446ded6 sp abdfaff0 error 6 in libc-2.12.1.so[b43fd000+157000]
Oct 29 00:47:18 alexandria kernel: [54663.850169] mythbackend[26333]: segfault at abefaffc ip b456eed6 sp abefaff0 error 6 in libc-2.12.1.so[b44fe000+157000]
Oct 29 00:49:42 alexandria kernel: [54807.637230] mythbackend[26401]: segfault at abcfaffc ip b4431ed6 sp abcfaff0 error 6 in libc-2.12.1.so[b43c1000+157000]
Oct 29 00:52:51 alexandria kernel: [54997.374962] mythbackend[26528]: segfault at abdfaffc ip b44b2ed6 sp abdfaff0 error 6 in libc-2.12.1.so[b4442000+157000]
Oct 29 00:55:17 alexandria kernel: [55143.351947] mythbackend[26780]: segfault at abdfaffc ip b4450ed6 sp abdfaff0 error 6 in libc-2.12.1.so[b43e0000+157000]
Oct 29 00:57:42 alexandria kernel: [55287.663830] mythbackend[26890]: segfault at abdfaffc ip b4555ed6 sp abdfaff0 error 6 in libc-2.12.1.so[b44e5000+157000]
Oct 29 00:59:58 alexandria kernel: [55423.541338] mythbackend[26994]: segfault at abdfaffc ip b44f8ed6 sp abdfaff0 error 6 in libc-2.12.1.so[b4488000+157000]

```

My recordings are being split up into at least a dozen little 2 minute files.  

Going to try a reboot...

---

### Post by NightStorm on 2010-10-29
I just discovered this thread after reporting this issue in another thread (here: [http://ubuntuforums.org/showthread.php?t=1608373](http://ubuntuforums.org/showthread.php?t=1608373)).  So "me too."

---

### Post by neubian on 2010-11-15
> **maraschin said:**
> Hej,

I got a similar error in libc-2.12.1.so
I just did the latest update on 10.10 Server and got the following entry in the kernel log:

kernel: [  194.490772] zfs-fuse[3076]: segfault at 0 ip 00002ba4a9d3b426 sp 00002ba4da905b98 error 4 in libc-2.12.1.so[2ba4a9cba000+17a000]

PS: I'm running zfs-fuse and it was running normally until I update the system with the latest patch and restart the system.


maraschin, I'm running Fedora 13 with this same version of libc and zfs-fuse has crashed for me as well.  I'm working with the zfs-fuse devs to try to find the answer.

[http://groups.google.com/group/zfs-fuse/browse_thread/thread/7e897ebf6acadc82](http://groups.google.com/group/zfs-fuse/browse_thread/thread/7e897ebf6acadc82)

Can you tell me what kernel you are running?

---

### Post by neubian on 2010-11-15
arr, no delete button :(

---

### Post by koma77 on 2010-12-28
I'm getting this as well.

I'm running mythbuntu, both frontend and backend on the same machine.
Using a Hauppage HVR 1900. Using analogue only.

I get:

mythbackend[17879]: segfault at 398f000 ip 00007f7c1c42de38 sp 00007f77e4836a98 error 4 in libc-2.12.1.so[7f7c1c3a7000+17a000]

---

