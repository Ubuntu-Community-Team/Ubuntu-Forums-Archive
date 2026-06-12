---
title: "jack and /tmp"
date: 2007-05-15
forum: Multimedia Production
---

### Post by btartsa on 2007-05-15
I am wondering if anyone has any experience or opinions on modifying /etc/fstab as described here :
  [http://jackit.sourceforge.net/cgi-bin/lxr/http/source/README](http://jackit.sourceforge.net/cgi-bin/lxr/http/source/README)

Also I would like your input on filesystem tuning. Do you use options such as:
noatime,data=writeback  and tune2fs usage like dir_index? More details available here:
[http://ck.kolivas.org/faqs/audio_hints.txt](http://ck.kolivas.org/faqs/audio_hints.txt)

Thanks all!

---

### Post by jondecker76 on 2007-05-15
I haven't tried either of those modifications, but in my experience - i don't really like to modify anything if I can help it because every time I have it has come back to bite me (usually much later when there is a distribution update). If you are good at keeping track of the changes you have made and undo them whenever anything major changes, I don't see the harm.

On the same note, if these really do help, I think it is something that should be officially added to Ubuntu Studio and we should push for that.

Beyond that, I run jack with the lowlatency kernel right now with no problems staying at 3ms and overloading it pretty good. Therefore I doubt I would gain much of anything by doing these. Your case might be different, however.

What kind of performance are you getting from jack right now?

---

### Post by btartsa on 2007-05-15
I have not really put my system under a heavy load yet, but I have installed the realtime kernel and laid a few tracks. Latency is around 10msec with conservative jack settings with no quality loss or pops! On a slow machine too ( 1 ghz w/ 768mb ram)  so I'm impressed! As far as those settings I mentioned...this is my first time away from Arch Linux since around 1994. Arch is a very experimental distro...so I have become a chronic tinkerer. I will experiment with these settings and report.

I also switched over to openbox because I seemed to be dragging a bit on the desktop. Seems to have helped me out a lot.

---

### Post by jondecker76 on 2007-05-15
It will be good to see your results

Right now I'm still trying to learn how to use everything. Most of my tests have been just running hydrogen through a bunch of plugins trying to bogg it down.

I am also very impressed, i just wish i could learn a bit quicker - FL Studio kind of spoiled me because i found it very intuitive - I'm anxiously awaiting when i get this all figured out and dump my windows install all together

---

### Post by ricrac on 2007-05-17
The first tmpfs suggestion I would use on an as needed basis.  You would be better served by leaving tmp alone and creating a ram tmpfs just for the programs that require it. 
The notes at this location are more appropriate, note the "/tmp/jack" vs. "/tmp"
[http://proaudio.tuxfamily.org/wiki/index.php?title=DAW_Digital_Audio_Workstation#Jack_configuration](http://proaudio.tuxfamily.org/wiki/index.php?title=DAW_Digital_Audio_Workstation#Jack_configuration)
The other tmpfs and shmfs settings may only make a difference (otherwise could actually be detrimental) if you re-compile jack with the correct options set.  Check to see which settings were used in the packaged jack you have installed.

noatime is commonly used and should be set on data drives/partitions.
writeback may help, personally I don't use journals on my "audio write" disks.
No swap partition or no swap mounted during recording, swap on separate physical drive if needed during non-linear editing only.

Slightly out of date but still valid info from cinelerra [http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_20.html](http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_20.html)
By far the fastest file system is
mke2fs -i 65536 -b 4096 my_device
tune2fs -r0 -c10000 my_device
This has no journaling, reserves as few blocks as possible for filenames, and accesses the largest amount of data per block possible.

A slightly slower file system, which is easier to recover after power failures is
mke2fs -j -i 65536 -b 4096 my_device
tune2fs -r0 -c10000 my_device
This adds a journal which slows down the writes but makes filesystem checks faster. 
...


You should have separate physical drives for audio/video data.
If you're mixing you should have 3 physical drives, one for OS system, one for sample/track reads, one for mixed output writes.


For a system that is limited by the user's ability:
3 physical drives, formatted as standard EXT3 for OS, no journal and no access times for audio read and write drives

No swap partition, enough memory so this is not an issue, never exceed 65% memory load with all apps/plugins/etc. loaded.  The rest of memory is for disk buffers.  The percentage shrinks if you have a large memory system.  You should have  >256mb available ram fully loaded, more is better.

For a gross approximation of CPU utilization, start up a standard mix session with all plugins loaded and functioning, softsynth playing, etc. and then run top.
Your Cpu idle percentage should be greater than 50%.

XFCE, no arts or esd, no gnome, no beagle, static IP. remote syslog, no cd autodetect, no printing support turned on (enable as needed).  

Low-latency or realtime kernel, each has their own uses, usually use low-latency.




To load test, I'm viewing/editing  6 video tracks, 640 x 480 and 16 audio tracks 48k 128kbit simultaneously while downloading an iso, running mysql and apache (idle), plus running vmware with a ubuntu 7.04 client running a few firefox browser instances, each with many tabs open.  I have 260mb free ram plus plenty of cache buffers and around 70% cpu idle on a AMD64 3700 while doing all of this.

Rebooting is still needed for performance systems. 
To determine if you need to reboot:
Write a script to start and stop an app 1000 times.
Run this script with each of your programs.  If free memory ever goes near zero, you probably have a memory leak and rebooting periodically will be necessary..
My system can stay up for months with many random apps.
I can also crash the system in a few moments with a bad app.
Every distro I've tried (and I've tried more than most) still has at least one app with a memory leak. Audio and video apps move and allocate memory and more often than others have memory leak issues.  Another reason I like using virtual systems is they're great for debugging.  A cpu or memory hog client will kill the VM but not the parent system.  

Hopefully in the future the Ubuntu studio project will switch to XFCE and build the system up from Ubuntu server which is a cleaner base system than Xubuntu.  If designed for production vs. desktop gadgetry performance should easily be doubled.  

Somewhat Offtopic:
Take for example EMC, a cnc distro built on Ubuntu.  Barely runs on a pentium III, lost steps, UI delays, etc..
After system tuning runs fine on Pentium III even on Pentium II (after convert to Xubuntu, static ip, remove unneeded daemons, etc.)

---

### Post by btartsa on 2007-05-17
Wow. Thanks a lot for your time and info! If I could get your opinion on using chrt to prioritize IRQ&#347; I would greatly appreciate it too. 

Thanks!

---

### Post by ricrac on 2007-05-17
It's generally not necessary on "standard" multimedia low-latency kernels, do you know how your kernel was built?

Use chrt for "Complete Preemption (Real-Time)" kernels. These kernels need tuning of apps so most distros build Preemptible Kernel (Low-Latency Desktop).  I build my own though so I can't speak on distro supplied kernels.

[http://tapas.affenbande.org/wordpress/?page_id=6](http://tapas.affenbande.org/wordpress/?page_id=6)

---

### Post by btartsa on 2007-05-17
There is an realtime patched kernel here:
[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

Seems to work well!  I was was thinking of setting higher priorities for rtc and my soundcard irq's.

On another note : I agree that there is a LOT of fat to cut from ubuntu studio. I switched to openbox right off the bat.

---

### Post by btartsa on 2007-05-17
Oh, and I want to be be the first one to say.... Stubuntu!

---

### Post by ricrac on 2007-05-20
Some recent LJ posts with samples to show current state of the art:

Adour2
[http://www.linuxjournal.com/node/1000224](http://www.linuxjournal.com/node/1000224)

[http://www.linuxjournal.com/node/1000216](http://www.linuxjournal.com/node/1000216)

[http://www.linuxjournal.com/node/1000208](http://www.linuxjournal.com/node/1000208)

[http://www.linuxjournal.com/node/1000208](http://www.linuxjournal.com/node/1000208)

---

