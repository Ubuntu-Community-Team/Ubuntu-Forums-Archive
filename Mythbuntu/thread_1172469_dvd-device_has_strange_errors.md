---
title: "dvd-device has strange errors"
date: 2009-05-28
forum: Mythbuntu
---

### Post by Serie 9 on 2009-05-28
Hi Mythbunt community
I have installed Mythbuntu 9.04 on my PC a few days ago and i have some problems i cant solve myself. At the moment the Problem that matters most is that i can not play audio-cds. wehn i insert an audio-cd nothing happens (no device is displayed) (mythv-frontend closed). in audacious->open, the audio-disk is displayed. But when i try to open it, the error message pops up:
> The folder contents could not be displayed

Cannot change to folder because it is not local 

When i insert an Video or data dvd/cd everything works fine. Exept one thing. When i press the eject-button (hardware) the error message pops up: > the medium »/org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_103« could not be ejected 
the device »/org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_103« is not an valid medium i tried to translate the second error massage from german. the orriginal is: > Der Datenträger »/org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_103« konnte nicht ausgeworfen werden.

Das Gerät »/org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_103« ist kein gültiger Datenträger.

But i can eject them doing right-click -> eject.

i dont have the eject-Problem with audio-cds. 
I don't know wether the two Problems habe anything to do with each other so i mentioned both. 
pls help. want to hear music.

Would be happy if anyone could help me.

Serie 9

&#8364;: here is my /etc/fstab:
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0628ccba-777f-44a8-9670-62b4aec12c10 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fff5a80c-a487-4b55-9b98-1b9548d99be7 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=4f0641d9-941d-495b-86e1-d732e4fffef9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


&#8364;²: i found out how to play an audiocd with audacious per termial:
> $audacious cdda://
but this doesn't really solve the problem.

---

