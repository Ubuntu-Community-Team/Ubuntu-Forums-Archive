---
title: "Problems transferring music to Sony Walkman NWZ-S545"
date: 2010-09-06
forum: Multimedia Software
---

### Post by lynyl on 2010-09-06
I have a Sony Walkman NWZ-S545. I have Rhythmbox 0.12.8.  I have a System 76 amd64 computer. I have run Ubuntu (now 10.1) for a couple of years and before that Linspire and haven't had MS Windows for years. But in no case am I anything but a newbie! 

   What I want is to be able to simply transfer music files from my computer to the Walkman. Nothing fancy. Drag and drop is fine. (I was hoping that it would be shown on the desktop, that I could open it and access it and drag files to it.) 

   I looked in Ubuntu help and found: "Ubuntu will work with most portable audio players, including iPods. Normally, all you have to do is plug the player into your computer and then use Rhythmbox to copy songs to and from the player." 

   When Rhythmbox didn't recognize it and no icon appeared on my computer screen indicating it was plugged in as an external device, I went back to Ubuntu help and found and installed the mtpfs and mtp-tools packages and made sure that the MTV plugin in Rhythmbox was checked. Now Rhythmbox could see the Walkman BUT could not play any songs! And there was no Walkman icon on the desktop.

   When I tried to play the 5 sample songs on the Walkman, I got one of these 3 errors:
       a. Couldn't start playback - no file name specified for reading
       b. No URI set
       c. Unable to copy file from MTP device: PTP Layer error 02ff: LIBMTP_Get_Filemetadata(): call  to ptp_mtp_getobjectpropssupported() failed.
       (BTW, my Rhythmbox setting under preferences - music is for .ogg - can see other options under edit but cannot switch to them.  My mp3 songs transferred from my external hard drive to Ryhthmbox beautifully and play just fine)

   After further searching, I read I should confirm that libmtp8 was installed and I found that it was.

   So I went to Ubuntu Rhythmbox help and read:  "If Rhythmbox Music Player does not detect your device as a portable audio player, you can create an empty file named .is_audio_player at the top level hierarchy of the filesystem of your player."

   OK - I am stuck here at several levels: 
1)  Is this what really needs done? 
2)  If so, how? (I searched ".is_audio_player" and came up with   several comments and how-tos, all seeming to involve going into the root directory and inserting an empty file somewhere. First of all, I can't get into my root directory even as the administrator with full privileges! Secondly, I know enough to know that even if I could - I shouldn't!  I would need more specific guidance.
 
   Thanks for any help anyone can give me!!

---

### Post by Ozymandias_117 on 2010-09-06
> **lynyl said:**
> I have a Sony Walkman NWZ-S545. I have Rhythmbox 0.12.8.  I have a System 76 amd64 computer. I have run Ubuntu (now 10.1) for a couple of years and before that Linspire and haven't had MS Windows for years. But in no case am I anything but a newbie! 

   What I want is to be able to simply transfer music files from my computer to the Walkman. Nothing fancy. Drag and drop is fine. (I was hoping that it would be shown on the desktop, that I could open it and access it and drag files to it.) 

   I looked in Ubuntu help and found: "Ubuntu will work with most portable audio players, including iPods. Normally, all you have to do is plug the player into your computer and then use Rhythmbox to copy songs to and from the player." 

   When Rhythmbox didn't recognize it and no icon appeared on my computer screen indicating it was plugged in as an external device, I went back to Ubuntu help and found and installed the mtpfs and mtp-tools packages and made sure that the MTV plugin in Rhythmbox was checked. Now Rhythmbox could see the Walkman BUT could not play any songs! And there was no Walkman icon on the desktop.

   When I tried to play the 5 sample songs on the Walkman, I got one of these 3 errors:
       a. Couldn't start playback - no file name specified for reading
       b. No URI set
       c. Unable to copy file from MTP device: PTP Layer error 02ff: LIBMTP_Get_Filemetadata(): call  to ptp_mtp_getobjectpropssupported() failed.
       (BTW, my Rhythmbox setting under preferences - music is for .ogg - can see other options under edit but cannot switch to them.  My mp3 songs transferred from my external hard drive to Ryhthmbox beautifully and play just fine)

   After further searching, I read I should confirm that libmtp8 was installed and I found that it was.

   So I went to Ubuntu Rhythmbox help and read:  "If Rhythmbox Music Player does not detect your device as a portable audio player, you can create an empty file named .is_audio_player at the top level hierarchy of the filesystem of your player."

   OK - I am stuck here at several levels: 
1)  Is this what really needs done? 
2)  If so, how? (I searched ".is_audio_player" and came up with   several comments and how-tos, all seeming to involve going into the root directory and inserting an empty file somewhere. First of all, I can't get into my root directory even as the administrator with full privileges! Secondly, I know enough to know that even if I could - I shouldn't!  I would need more specific guidance.
 
   Thanks for any help anyone can give me!!

Root of the MP3 player, not of your system.

Plug your MP3 player into the computer, and post back the output of ```
sudo fdisk -l
``` (lowercase L, not the number one) and ```
mount
```

---

### Post by lynyl on 2010-09-06
OK did that and here is what I got:


root@lynslinux:/home/lyn# sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008d290

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris
root@lynslinux:/home/lyn# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lyn/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lyn)


What's next? BTW, nothing changed yet.  Thanks

---

### Post by lynyl on 2010-09-07
Well - now I can transfer songs with drag and drop! Working this am after I rebooted, then opened RB and then plugged in the Walkman!

---

### Post by noleks on 2010-10-18
Hi:
I'm running Karmic and also cannot get the drive recognized as MTP (which is the only supported mode for the 545, I believe).
I was hoping to use something (Rhythmbox?) to manage my Walkman, syncing playlists etc.
The WM appears as a drive on the desktop and is mounted under /media/WALKMAN, but no MTP interface seems to be working.

**mtp-detect output:**
[INDENT]libmtp version: 1.0.2

Listing raw device(s)
  No raw devices found.
[/INDENT]**sudo fdisk -l output:**
[INDENT]noleks-ub:~> sudo fdisk -l
[sudo] password for noleks: 
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x8eea190e
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19131   153669726   83  Linux
/dev/sda2           19132       19457     2618595    5  Extended
/dev/sda5           19132       19457     2618563+  82  Linux swap /
Solaris
 
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0xec760a0a
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS
Note: sector size is 2048 (not 512)
 
[COLOR=Red]Disk /dev/sde: 15.8 GB, 15816196096 bytes[/COLOR]
[COLOR=Red]184 heads, 23 sectors/track, 1824 cylinders Units = cylinders of 4232 * 2048 = 8667136 bytes Disk identifier: 0x00000000[/COLOR]

[COLOR=Red]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
[COLOR=Red]/dev/sde1               1        1825    15445474    b  W95 FAT32[/COLOR]
[/INDENT]

---

