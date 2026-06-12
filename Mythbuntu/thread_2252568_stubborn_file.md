---
title: "stubborn file"
date: 2014-11-12
forum: Mythbuntu
---

### Post by deanie44 on 2014-11-12
Hi everyone.  I made a ntfs partition and mounted it using the instruction from [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab).
The partition is in the root folder and I cannot delete it.  I tried gksudo, but it did not work.  Is there any way that i can remove the partition 
from the root folder and have a rewriteable?  Any suggestions will be appreciated. deanie44

---

### Post by dannyboy79 on 2014-11-13
i don't think you fully understand how linux works as far as partitions and folders/mount points work and that's ok, we all learn as we go. i know when I first started learning linux i got stuck on mount points also because it's different than how windows handles it.

in linux folders are just folders until a partition is mounted to it. in linux the highest folder is / (the root folder) and that's normally where your main partition is mounted. within that folder there's file and folders, some of the folders are named /boot, /home, /etc, and various other names. you have to realize that it's possible to mount a partition onto 1 of these sub-folders which would allow you to see what's on that partition. so if you followed that guide you should have a folder called /windows which is being used to show the contents of some partition. 

You say you have some file you can't delete, what's the files name? Are you sure it's not a folder (called directory in linux)? Most likely it's a directory and if you mounted a windows partitions into this folder and you delete the folders contents, you're actually deleting files from your windows partition.

Let's see what you're working with here. First install pastebinit so we can easily upload std output to pastebin.
```
sudo apt-get install pastebinit
```
it will ask for you password, enter it and hit the enter key. if it's already installed than perfect. lets upload what your / partition looks like to see this so called stubborn file, do so by issuing this command
```
ls -la / | pastebinit
```

lastly, what is the file you think is being stubborn?

---

### Post by deanie44 on 2014-11-13
Hi.  I did a backup of the system two weeks ago, so i restore it.  thanks anyway.deanie44

---

