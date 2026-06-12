---
title: "Newbie:  Adding Music"
date: 2009-01-31
forum: Mythbuntu
---

### Post by ptmuldoon on 2009-01-31
I'm pretty much a rookie at Mythbuntu, trying to put myself through the learning curve, and learning what I can about linux at the same time.

I installed 8.10 as part of my existing windows.  And I can boot into either WinXP or Mythbuntu upon boot up.  Now, my existing WinXP has a few gig of music I'd like to play/use on Mythbuntu.  But I can't seem to figure out how to add/import the music from the WinXP partition into Mythbuntu.

Do I need to move all the data off on WinXP to portable USB drive to do so?  I would hate to think that as all the media is currently on the same HD, just partitioned in half.

Again, I'm pretty new to Mythbuntu, and perhaps its much easier than I think, just haven't found the steps yet.

Any help, would be greatly appreciated.  I long term goal is nice backend server and a couple of front ends around the home.

Thanks
PT

---

### Post by korgman on 2009-01-31
How you want to do it is up to you, but you need to copy/add/mount your music files to your mythbuntu filesystem under /var/lib/mythtv/music.

---

### Post by ptmuldoon on 2009-02-01
Thanks, thats what I figured as well.  But I'm unsure of how you locate and mount the other partition to copy it over the mythbuntu partition.

FYI.  I'm about to uninstall/remove mythbuntu and start again as I having getting no sound and have some strange video issues playing a dvd ( the video is showing in split screen/duplicate on the display).

But how do you find the WinXP partition to mount it and copy the files?  Or can I keep the files where there are, and just mount and play them from there as if its remote storage?

---

### Post by korgman on 2009-02-01
You'll probably want to add a line to your /etc/fstab file to automount at boot.  Its been a while since I did that.  Check under /dev to make sure the drive is available.  I don't know if "df" will show you the device if it is not already mounted.  

The fstab file should get and entry similar to this:
/dev/sdb1 /media/localMntName ntfs auto,gid=1003,unmask=0002 0 0

Then I think you run "mount -a" from the cmd line to see if it took.  Then it should be automatic upon reboot.  Again, no expert in Linux SA stuff.  Google around if this doesn't help.

---

