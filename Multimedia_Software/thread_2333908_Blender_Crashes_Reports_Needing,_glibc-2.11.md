---
title: "Blender Crashes: Reports Needing, glibc-2.11"
date: 2016-08-14
forum: Multimedia Software
---

### Post by yogich246 on 2016-08-14
Latest LTS Ubuntu is on this machine, and it refuses to run Blender:

```

yogich@HP:~$ blender-2.77a-linux-glibc211-x86_64/blender
bash: blender-2.77a-linux-glibc211-x86_64/blender: cannot execute binary file: Exec format error

```
Any idea how I can overcome, this? Ubuntu 14.04 & Suse 13.2 both run, this, but I'd rather be on 16, if at all possible. I'm more familiar with Ubuntu & like it, much, better.

---

### Post by Bucky Ball on 2016-08-14
*Thread moved to **Multimedia Software**.*

Better here as not really to do with Desktop Environments. 

Did you install Blender through the official Ubuntu repositories?

---

### Post by &amp;KyT$0P# on 2016-08-14
That's not an install from the repositories, that's extracting a tarball downloaded from the website into the home directory.  And in my experience Blender versions are badly incompatible to each other (both forward- and backward-), so I'm guessing that installing from the repositories, which has a different Blender version, would not be a viable solution.

Can you please post the output of these commands?
```
uname -a
file blender-2.77a-linux-glibc211-x86_64/blender
file -i blender-2.77a-linux-glibc211-x86_64/blender
```

I've successfully run Blender in a virtual machine (it's a bit finicky to set up, but does work).  Can you use a VM of Lubuntu 14.04 at least for now?

---

### Post by Bucky Ball on 2016-08-14
Only reason I ask is because the version from the repositories in both 14.04 and 16.04 has been and does work faultlessly for me. Unless there is a specific reason to install from a third-party, why not install the official repo version for your release?

What is a solution may be to remove what Blender you have and reinstall from the repos unless you have a specific reason to not want that version. :-k

---

### Post by yogich246 on 2016-08-16
> **Bucky Ball said:**
> Only reason I ask is because the version from the repositories in both 14.04 and 16.04 has been and does work faultlessly for me. Unless there is a specific reason to install from a third-party, why not install the official repo version for your release?

What is a solution may be to remove what Blender you have and reinstall from the repos unless you have a specific reason to not want that version. :-k

I have been using it on Windows10, with Avastar & ManuelBastioniLAB 1.30, and wished to have the same setup. It is really that, simple. :KS

Meanwhile, I discovered something very, interesting:  Ubuntu 16.04.1 Live DVD runs the Blender.org version without, preamble. More, on this, here: [https://ubuntuforums.org/showthread.php?t=2333907](https://ubuntuforums.org/showthread.php?t=2333907) I find it disgusting, that the installed version does not emulate the Live DVD.

---

### Post by mc4man on 2016-08-16
Works fine here in 16.04 (64 bit install), both the 64 bit binary, scr. 1 & the 32 bit one, scr.2 (I have proper multi-arch libs installed.
So maybe answer post 3..

---

### Post by &amp;KyT$0P# on 2016-08-16
The "real" difference between live system and installed system is the installed packages.  Several ways to do it but I guess step 1 is to compare just the list of installed packages.  Run this command in a Terminal on the live system and the installed system
```
dpkg-query -W -f '${binary:Package}\n' > somefile.txt
```
(replacing somefile.txt by any file name you want as long as you have write permissions for and it's not going to disappear on rebooting the live system)

Then can you please post here the full output of running this command, as well as those I listed above?
```
diff (installed system packages list file) (live system packages list file)
```
If too big to fit in a terminal, dump the output in a file first, then post the contents of the file
```
diff (installed system packages list file) (live system packages list file) > differences.diff
```

---

### Post by mc4man on 2016-08-16
Also - 
that error would also occur if trying to exec a binary like a script, i.e. bash binary
Do you have an alias for "blender" or otherwise modified bash(rc)?

---

### Post by yogich246 on 2016-08-16
> **halogen2 said:**
> That's not an install from the repositories, that's extracting a tarball downloaded from the website into the home directory.  And in my experience Blender versions are badly incompatible to each other (both forward- and backward-), so I'm guessing that installing from the repositories, which has a different Blender version, would not be a viable solution.

Can you please post the output of these commands?
```
uname -a
file blender-2.77a-linux-glibc211-x86_64/blender
file -i blender-2.77a-linux-glibc211-x86_64/blender
```

I've successfully run Blender in a virtual machine (it's a bit finicky to set up, but does work).  Can you use a VM of Lubuntu 14.04 at least for now?

I went back to 14.04, temporarily, until I can get this figured out....am installing 16.04 on a USB stick, for now, and will post the results. What version of Blender is in the repositories, for 16.04?

---

### Post by &amp;KyT$0P# on 2016-08-16
[http://packages.ubuntu.com/xenial/blender]("http://packages.ubuntu.com/xenial/blender")
Looks like 2.76

---

### Post by yogich246 on 2016-08-16
I'm guessing that this version is from the repositories? If so, I might go, that direction. There can't be much difference between 2.77 & 2.77a, after all... can, there?

I cherry-picked a couple files, out of the 'diff' file which is supposed to have the uninstalled packages, in it... they *were* installed. That file is, most probably, full of already-installed software. What, now? I, give. I have the 32-bit version of Blender working, the 64-bit will not, work. Go, figure. I'm on the amd64 version of Ubuntu 16.04.1. Things have to make sense, to me. This, does not.

blender-2.77-linux-glibc211-i686, works, on Ubuntu 16.04.1 (amd64). blender-2.77-linux-glibc211-x86_64f does not, work. I'm leaving it, at that. Thanking everyone for their help. Thread is closed, I think, and I'm finished, here. lol

---

### Post by yogich246 on 2016-08-16
I'm guessing that this version is from the repositories? If so, I might go, that direction. There can't be much difference between 2.77 & 2.77a, after all... can, there?

Oh, ok..I have installed 16.04.1 on USB stick, and also run query, to find out what the differences, are. I have plenty of room, on the stick, so would like to just install everything that was in the 'differences' list...but cannot find, in man pages, where this is possible...?

> **halogen2 said:**
> The "real" difference between live system and installed system is the installed packages.  Several ways to do it but I guess step 1 is to compare just the list of installed packages.  Run this command in a Terminal on the live system and the installed system
```
dpkg-query -W -f '${binary:Package}\n' > somefile.txt
```
(replacing somefile.txt by any file name you want as long as you have write permissions for and it's not going to disappear on rebooting the live system)

Then can you please post here the full output of running this command, as well as those I listed above?
```
diff (installed system packages list file) (live system packages list file)
```
If too big to fit in a terminal, dump the output in a file first, then post the contents of the file
```
diff (installed system packages list file) (live system packages list file) > differences.diff
```

Sadly, I cannot post the files, here. They are much too, lengthy. However, I would hope there is a way to install from a list. I cannot find any reference, to that, in man pages (mentioned to another, in this thread, as well).

As to your observation concerning the file disappearing... the file would deffo, disappear, in Live System, since the persistent file system seems not to work, very well.

I decided to give the 2.76 Blender a try, and it bombed:
1. I cannot use the addons, I used, in 2.77
2. Collada output is 'Avastar' only! V2.77 has this, and a regular, non-avastar, collada output, as do all non-repository versions.
3. ManuelBastioniLAB 1.3 errors, when used, and doesn't work, properly.

---

### Post by &amp;KyT$0P# on 2016-08-16
That's what you would get if you run
```
sudo apt-get install blender
```
on a machine running Ubuntu 16.04.

No there isn't going to be much difference between 2.77 and 2.77a - if I'm remembering right how this works 2.77a is a bugfix-only release.  Based on my experience of how LTS versions of Ubuntu work, I'd guess that if the repositories have the version of Blender you want that you would also get the bugfixes from any a/b/etc releases of that version.

---

### Post by &amp;KyT$0P# on 2016-08-16
> **yogich246 said:**
> Sadly, I cannot post the files, here. They are much too, lengthy. 
Of those 3 files post only the diff file and do so over multiple posts if needed.

This would still be useful to help troubleshoot -
> **halogen2 said:**
> Can you please post the output of these commands?
```
uname -a
file blender-2.77a-linux-glibc211-x86_64/blender
file -i blender-2.77a-linux-glibc211-x86_64/blender
```

---

### Post by &amp;KyT$0P# on 2016-08-16
You're welcome, glad you got it working.  :KS

---

### Post by yogich246 on 2016-08-17
> **halogen2 said:**
> That's not an install from the repositories, that's extracting a tarball downloaded from the website into the home directory.  And in my experience Blender versions are badly incompatible to each other (both forward- and backward-), so I'm guessing that installing from the repositories, which has a different Blender version, would not be a viable solution.

Can you please post the output of these commands?
```
uname -a
file blender-2.77a-linux-glibc211-x86_64/blender
file -i blender-2.77a-linux-glibc211-x86_64/blender
```

I've successfully run Blender in a virtual machine (it's a bit finicky to set up, but does work).  Can you use a VM of Lubuntu 14.04 at least for now?

Thanks, but I did get this working --32-bit on 64-bit Ubuntu...64-bit offers up, errors, only. Will stick with what i have, for now. :KS

---

