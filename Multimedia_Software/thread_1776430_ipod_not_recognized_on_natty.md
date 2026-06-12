---
title: "ipod not recognized on natty ??"
date: 2011-06-06
forum: Multimedia Software
---

### Post by shantiq on 2011-06-06
Hi my daughter has an ipod and she wants me to change tracks on it but when i plug it in on natty this message appears 


```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdg2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

i do not understand this message try dmesg what is this?


Hope some of you understand this:KS

---

### Post by shantiq on 2011-06-06
tried   ```
dmesg | tail
```



```
dmesg | tail 
[ 9055.312705] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 9055.312713] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[ 9055.890922] sd 9:0:0:0: [sdg] Bad block number requested
[ 9055.890955] hfs: unable to find HFS+ superblock
[ 9056.250089] sd 9:0:0:0: [sdg] Bad block number requested
[ 9056.250125] hfs: unable to find HFS+ superblock
[11045.500091] sd 9:0:0:0: [sdg] Bad block number requested
[11045.500139] hfs: unable to find HFS+ superblock
[11075.030074] sd 9:0:0:0: [sdg] Bad block number requested
[11075.030120] hfs: unable to find HFS+ superblock
```


what does it mean.   anyone?

---

### Post by nothingspecial on 2011-06-06
It means it has been formatted with a mac using the hfs+ file system. I believe to get linux to mount it you have to disable journaling from a mac, but as the only one I have ever seen was in a shop I have no idea how to do that.

If you have a friend running windows and itunes you could reformat it on that and then it will mount.

Bear in mind, if the ipod is running the latest apple firmware, you will not be able to add and remove songs on it with natty anyway as it stands at this time. So if you do reformat it, you will be left with a brick.

If it is running older firmware, you will be fine. And people are working on getting the latest firmware working. It's just a matter of time.

---

### Post by shantiq on 2011-06-06
thank you for the info.:KS

---

