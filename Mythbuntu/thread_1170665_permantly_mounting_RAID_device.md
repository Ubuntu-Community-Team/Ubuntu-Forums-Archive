---
title: "permantly mounting RAID device"
date: 2009-05-26
forum: Mythbuntu
---

### Post by scottac on 2009-05-26
So after much pain I am able to successfully mount a RAID device. This device, "dev/md0", was created using mdadm.

here is the code:
```
sudo mount /dev/md0 ~/2_TB_Raid5
```

after running this code the volume mounts without any issue. The problem is that when I reboot the drive is no longer mounted to this location.  

Is there a way to make this drive mount automatically after I log in?

Thanks guys...

Fredo

---

### Post by ian dobson on 2009-05-26
Hi,

Just add it to your /etc/fstab:-

/dev/md0                                    /home/USERNAME/2_TB_Raid5           ext3    rw,noatime  0       0  ##RAID 5 array

This mounts on boot but you could try adding the mount command to .bash_login or .profile scripts in your home directory.

Regards
Ian Dobson

---

### Post by scottac on 2009-05-26
I am very noobish with linux but am determined to get this to work.

Also, I am sort of intimidated by the fstab file as I know it can potentially screw stuff up if I am not careful about my entries. However one potential problem I see with the code entry you suggested is that my array is formated with xfs not ext3. would all I need to do to the line you gave me is change the xfs to ext3? 

I don't see any .login scripts in my home directory...  should there be.  I tried adding a file named mount2tbraid.profile to my home directory with this code inside it...

**note: I changed the mount point**
```

#
sudo mount /dev/md0 /mythmedia

```

but the drive didn't mount on reboot. 

I also tried adding this script to usr/share/mission-control/profiles because I did a search of the filesystem and this is where all the .profile files were located.

again.  I am a noob.  be easy on me I am still learning

thanks again

fredo

---

### Post by scottac on 2009-05-26
ok. so I found the .profile file in my home directory by unhiding it. and I added a line to the end of the file with the following code:
```

sudo mount /dev/md0 /mythmedia

```

still nothing. What am i missing here? 

p.s. I have tried removing the sudo from the beginning of the code and still nothing..

fredo

---

### Post by scottac on 2009-05-26
Solved.... 

I grew some balls and add a line to the etc/fstab file. 

here is the line I added
```

/dev/md0       /mythmedia      xfs      defaults      0      0

```

thanks for the help ian

regards,

fredo

---

