---
title: "out of drive space?!"
date: 2009-10-26
forum: Multimedia Software
---

### Post by kylegio on 2009-10-26
ok so a friend of mine had this problem every single time he installed linux, i always just assumed he messed up creating his partitions or something, but today i boot up my desktop, i only installed linux freshly on it less then a week ago. and bam a warning saying only 8kb of data left on "root". wtf? its a 80gig drive and has NOTHING but linux on it, its partitioned to 77gigs and then theres a 3gig swap on it. using the disk usage analyzer i see that my /var/log folder takes up 64.3GB of data?!

check it out, and there are several files in here that are crazy ridiculous large
kern.log.1            1.6MB
daemon.log.1      3.1MB
messages             19.1MB
user.log                32.0GB
syslog                   32.0GB


two 32 GB log files?!  i used the head command to pull up 50 lines or so from the logs. you might be wondering at this point why the hell i posted this in multimedia? well its because all of the lines in both logs read
> 
pulseaudio[2390]:  alsa-util.c: Unable to set sw params: too many open files
pulseaudio[2390]:  alsa-sink.c: Failed to set software paramaters: too many open files


so both the log files are exactly the same (for the first 50 lines atleast)... there are no files open, the computer just was sitting there all day. does anyone know whats going on?!

thanks for any help

---

### Post by fancypiper on 2009-10-26
Clean out (delete) all the old log files, the ones with numbers after them.  Also, you can remove the cached deb files by removing all the files in /var/cache/apt/archives.
HTH

---

### Post by Elfy on 2009-10-26
by removing all the files in /var/cache/apt/archives.

```
sudo apt-get clean
```

will do that

```
sudo apt-get clean
```

will remove those that are no longer needed

---

### Post by kylegio on 2009-10-29
thank you for your replies, i have already done both of those things. however after a couple days the log files are back similar to before. something is causing them to write that error to the log and loop it hundreds (or more) times in a second. 


any other thoughts

---

