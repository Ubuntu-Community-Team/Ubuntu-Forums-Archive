---
title: "how do i burn flac?"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by iateshaggy on 2007-12-05
i tried using brasero and get this error (Make sure the appropriate codec is installed.)  i thought this app is supposed to work out the box?

---

### Post by Yellow Pasque on 2007-12-06
How about:
```
sudo apt-get install libflac8
```

---

### Post by iateshaggy on 2007-12-06
the above mentioned codec is already installed and reinstalled.  when i try to make a traditional adio cd with brasero i get this error.  i can however play flac with my media players.

"01 - DJ Isaac - Super DJ.flac" can't be handled by gstreamer:
Make sure the appropriate codec is installed.

---

### Post by iateshaggy on 2007-12-06
update: i installed everything gstreamer in synaptic that had an ubuntu symbol next to it and it now reads flac, but when i hit the burn button ittells me that my cd is not writable.

The disc in "CR-48X9TE" is not writable:
replace the disc with a recordable CD.

i've tried several brands with out luck.  the drive also has no trouble reading disk.  is this a driver issue and if so, how do i fix it?

---

### Post by Yellow Pasque on 2007-12-06
I guess it's a plugin for gstreamer you need then:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
 
```

---

### Post by iateshaggy on 2007-12-06
right, i figured that out, how about why it won't burn?

---

### Post by Yellow Pasque on 2007-12-07
what does your /etc/fstab file look like?

---

### Post by iateshaggy on 2007-12-07
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8bb327b3-794d-462e-b9fa-c651895779b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b0cd3829-56ef-406d-8962-b892a442adb4 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by iateshaggy on 2007-12-07
> **iateshaggy said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8bb327b3-794d-462e-b9fa-c651895779b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b0cd3829-56ef-406d-8962-b892a442adb4 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
bump

---

### Post by logos34 on 2007-12-07
try Serpentine or gnomebaker

---

### Post by iateshaggy on 2007-12-07
tried both, if i could join the two together, i'd have a good program.  how is k3b?

---

### Post by logos34 on 2007-12-07
k3b is the best.  get the libk3b2 pkg too--has the flac decoder

---

### Post by iateshaggy on 2007-12-08
it came with it default.  i like this one, it burns my flac albums gapless and make data disk out of my mp3's.  that's just how life is supposed to be.  now if only there was a way to have a gapless mp3 disk.

---

### Post by logos34 on 2007-12-08
> **iateshaggy said:**
> it came with it default.

hmm, so it does.  Thought it need to be installed with the additional pkg.

> **iateshaggy said:**
>  i like this one, it burns my flac albums gapless and make data disk out of my mp3's.  that's just how life is supposed to be.  now if only there was a way to have a gapless mp3 disk.

$ lame --longhelp
> 
...
--nogap <file1> <file2> <...>
                    gapless encoding for a set of contiguous files 

maybe that would work

You can rip gapless with **abcde** using this option:

> -g     Enable  lame&#8217;s --nogap option.  See the NOGAP variable. WARNING:
              lame&#8217;s --nogap disables the Xing mp3 tag.  This tag is  required
              for  mp3 players to correctly display track lengths when playing
              variable-bit-rate mp3 files.

So maybe that means the only problem you'll have will be that the track lengths won't be displayed on VBR mp3 songs.

Hope that helps a little.

---

