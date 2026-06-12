---
title: "Ripping DVD's"
date: 2017-07-21
forum: Multimedia Software
---

### Post by shane_faulkinbury2 on 2017-07-21
I'm trying to back up all of my DVD's onto hard drive and most them I was successful using Handbreak and ffmpeg, however some of them just won't rip.  I've been told that vobcopy in CLI will do the trick, but I don't know how to use it.  Is there a link to learn or can someone help me?

---

### Post by TheFu on 2017-07-21
vobcopy doesn't always work, but should handle about 90%.  It is easier than the methods necessary for that last 10%, IME.

My typical use is:
$ vobcopy -F 5 -m /cdrom/

This will create a mirror of the disk into the current directory assumes that /cdrom/ already has the DVD mounted.

Like all Unix commands on your system, there is a nice manpage which explains the options and other uses. **man vobcopy** will access it.  You can also try asking for help from the program **vobcopy --help** is the normal method. You can also use a websearch for the program with 'man vobcopy' and that will show _*a version*_ of the manpage, though it may not be for the specific version on your machine.  There have been slight changes made to the options over the years.

Plus never underestimate the knowledge gained by trial and error.  You cannot harm the read-only DVD. Try some options based on your needs, which are almost certainly different from mine.

Have the appropriate amount of fun with this stuff.

---

### Post by shane_faulkinbury2 on 2017-07-21
Do these mean the path to my dvd is wrong or this dvd can't be ripped?

---

### Post by TheFu on 2017-07-21
Read the messages. They point out a few issues WITH corrective steps.  
* you don't have libdvdread installed
* there is a pointer to a guide already ON YOUR MACHINE with instructions.
* did you mount the DVD to /cdrom?  If not, that command will never work.

---

### Post by shane_faulkinbury2 on 2017-07-21
How do I mount the DVD to /cdrom?

---

### Post by #&amp;thj^% on 2017-07-21
Basic.
```
vobcopy -l
```
More Info found here: [https://ubuntuforums.org/showthread.php?t=1701545](https://ubuntuforums.org/showthread.php?t=1701545)
And:     [http://vobcopy.org/projects/c/c.shtml](http://vobcopy.org/projects/c/c.shtml)

---

### Post by mc4man on 2017-07-21
By default in Ubuntu dvds will be at /dev/sr0 or if you have 2 drives possibly /dev/sr1 on the other drive.
Vobcopy will default to /dev/sr0 so try without any path in command. If a commercial disk then you'll need to have libdvdcss2 installed, instructions here - [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
(- what they say about following the instructions while installing libdvd-pkg means after it's installed run this to actually add libdvdcss2
```
sudo dpkg-reconfigure libdvd-pkg
```

vobcopy has no ability to handle most structure protections, if you start seeing a lot of read errors then probably a waste of time.

Basic command would be ( -F 16 just means read in blocks of 16 sectors which can make reads a bit faster as 16 aligns better
```
vobcopy -v -m -F 16
```

If there is structure nonsense that vobcopy or handbrake can't handle & you're only ripping to playback then many times one could use dvddisaster to produce an encrypted, structure protected iso that will play back on the machine you created the iso with.
[https://ubuntuforums.org/showthread.php?p=6365060#post6365060](https://ubuntuforums.org/showthread.php?p=6365060#post6365060)

---

### Post by TheFu on 2017-07-21
If I see any issues, then ddrescue gets the call.  Something about getting all the data off onto a HDD seems to solve it.  

If that fails, _other_ methods are deployed. Worst case, the analog hole is used.

---

### Post by shane_faulkinbury2 on 2017-07-22
Thanks TheFu for the tutorial, that's just what I was looking for!  Thanks 1fallen, that's exactly what I needed to get my rips going!  At 3% taking 12 hours it should only take about 16 days for one rip!  :D:D:lolflag:

---

### Post by TheFu on 2017-07-22
Some disks are completely corrupted.  If it takes over 4 hrs, find a different method. 

If the disk doesn't play correctly on a real, normal, $50 DVD player, then it is broke, corrupted, very dirty.  Look at the shinny side - dirty? Scratched? Broken in some way?  Oily finger printer can be cleaned away.  Other issues, not so much.

---

### Post by shane_faulkinbury2 on 2017-07-22
Will do, thanks!

---

