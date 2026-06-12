---
title: "Newwwbie. Serpentine doesnt Recognize my Burner..."
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by keh7d on 2006-07-17
I can play audio cds, am given the option to burn to blank cds, but Serpentine tells me that it cannot find a recording device. 

I have no idea what to do...

---

### Post by Paerez on 2006-07-17
what does it say in preferences for serpentine? Is it the right drive?

---

### Post by keh7d on 2006-07-17
> **Paerez said:**
> what does it say in preferences for serpentine? Is it the right drive?

Under preferences the "writing device" drop down menu doesnt offer any options. Device is set to nothing...

---

### Post by Paerez on 2006-07-17
OK can you post the file "/etc/fstab"? Thanks.

---

### Post by keh7d on 2006-07-17
> **Paerez said:**
> OK can you post the file "/etc/fstab"? Thanks.

In terminal Bash tells me "permission denied"...  me = noob...

---

### Post by Paerez on 2006-07-17
ah sorry, like this:
```
cat /etc/fstab
```
meow

---

### Post by keh7d on 2006-07-17
keh7d@giant:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

This is what is printed...

---

### Post by Paerez on 2006-07-17
hmm it seems like everything's all set. Try reconfiguring serpentine:
```
sudo dpkg-reconfigure serpentine
```
if it asks you any questions you can just hit enter, but if it asks for a path to your cd, put "/dev/hdc".

---

### Post by keh7d on 2006-07-17
> **Paerez said:**
> hmm it seems like everything's all set. Try reconfiguring serpentine:
```
sudo dpkg-reconfigure serpentine
```
if it asks you any questions you can just hit enter, but if it asks for a path to your cd, put "/dev/hdc".

keh7d@giant:~$ sudo dpkg-reconfigure serpentine
Password:
keh7d@giant:~$
keh7d@giant:~$


I didnt get any output... and unfortunately Serpentine still doesnt read my burner. Same error...

---

### Post by knowmad on 2006-10-11
> **keh7d said:**
> keh7d@giant:~$ sudo dpkg-reconfigure serpentine
Password:
keh7d@giant:~$
keh7d@giant:~$


I didnt get any output... and unfortunately Serpentine still doesnt read my burner. Same error...


Ditto.... Running Dapper Drake. My /etc/fstab looks nearly identical.

---

