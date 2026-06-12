---
title: "MythFillDatabase &amp; Nice level"
date: 2009-04-16
forum: Mythbuntu
---

### Post by AKADAP on 2009-04-16
How do I tell myth back end to run mythfilldatabase at a higher nice level?

I am finding that when mythfilldatabase is running, firefox will hang for minutes at a time.
I checked the system monitor, and found that less than 5% of CPU was being used when this happens, but my disk LED is on solid. Mythfilldatabase also shows a nice level of zero.

I have also had issues of chunks of recorded programs missing that I believe is caused by this issue (perhaps not always mythfilldatabase, but something else bashing the hard drive durring a recording).

---

### Post by ian dobson on 2009-04-17
Hi,

Can you provide us with abit more information:-
1) What tuner do you have
2) What hardware is the backend running on (CPU,RAM,HD's)
3) Where are you recording your programs to (Which harddisk/directory)
4) Which grabber are you using to grab the EPG data.

If the harddisk light is on almost all the time then nice won't help you much. It sounds as if your harddisk/ram is the bottle neck, raher than CPU.

Regards
Ian Dobson

---

### Post by AKADAP on 2009-04-17
Tuners: 2 HD Home Run (each with tuners)
        1 ATI HD Blunder
(note than issue does not seem to correlate to tuner used, but I don't really know how to determine what tuner was used after the recording completes)

CPU: Intel i7 920 (stock speed)
Motherboard Asus P6T Delux
RAM: 6 Gb
HD: Seagate 1.5 Tb SATA
Video: ATI HD4850 running 2560x1600x60
OS Ubuntu 8.10 64 bit.
EPG data is coming from Schedules Direct.

I am not doing any analog recording, digital only, so there is no compression going on.

At most 4 simultaneous recordings are done, but never more than 2 HD recordings, and seldom more than 2 recordings simultaneous. Glitches do not appear to correlate to the number of simultaneous recordings.

Currently commercial scan happens after recording, but I have in the past had it simultaneous with the recording. Changing this did not seem to help. Commercial scan happens at a nice level of 19.

Two of the HD Home Run tuners are connected to two antennas (directed in different directions), the other three tuners are connected to cable. Recording is set to prefer cable as antenna reception can be problematic. (antenna problems have a different appearance than these glitches, so I can tell them apart. Garbage in the frame with no time loss as opposed to a mix of two frames with missing time between).

This system SHOULD have enough horse power & bandwidth to do what I am asking of it.

---

### Post by nickrout on 2009-04-17
sounds like the database is working hard during mythfilldatabase. Many say you shouldn't be using your database on the same disk as your recordings (if you can avoid that).

ionice might be your solution.

---

### Post by ian dobson on 2009-04-17
Hi,

Yep I would say that the problem is with I/O bandwidth to your harddisk. Mythfill database really hits the SQL database hard. Maybe you can try optimizing your database configuration. I used mysqltuner.pl ([http://mysqltuner.com/](http://mysqltuner.com/)) to configure MySQL for maximum performance.

Another way would be to install another harddisk for yu /var/log and mysql database.

Regards
Ian Dobson

---

### Post by AKADAP on 2009-04-17
> **nickrout said:**
> sounds like the database is working hard during mythfilldatabase. Many say you shouldn't be using your database on the same disk as your recordings (if you can avoid that).

ionice might be your solution.

ionice documentation says that the application inherits its ionice level from the applications nice level. In any case, I am just as lost as to how to set the ionice level as I am setting the nice level of mythfilldatabase. I'm not even sure setting the nice level of mythfilldatabase is the right thing as the database itself may have a different nice level.

I can see no reason to have mythfilldatabase running at the same priority as firefox. It does not matter how long it takes for this to complete. nothing is lost, unlike a recording, if its actions are delayed a couple of seconds.

---

### Post by nickrout on 2009-04-17
And I see no reason to run firefox at all on the backend.

You can set mythfilldatabase to run at set times, get it to run while you are asleep!

---

### Post by AKADAP on 2009-04-17
> **nickrout said:**
> And I see no reason to run firefox at all on the backend.

You can set mythfilldatabase to run at set times, get it to run while you are asleep!

So, you have multiple computers. I don't. I have a via Epia-M6000 computer. This is what I intended to run the backend on, but so far I have been unable to get any version of Linux to run on this system. All versions that I have successfully installed do not properly handle window scrolling. They get progressively slower over a matter of minutes until the system locks up hard. I know it is not the hardware, because windows 7 beta installed and ran on it without problems.

On a multi-tasking operating system, I expect to be able to run multiple things on one computer. If I can't, there is something wrong with the software. It is not like I am trying to do anything that comes even close to taxing the processor or disk drive (or wouldn't if the code was written/set up properly). 

The sole purpose of mythbackend, since I am doing no compression, and no transcoding, is to set up the tuners & transfer data from the tuners to the hard disk. Some times it even has to transfer data from the hard disk to mythfrontend, or maybe to the upnp, but when that happens, the computer is doing nothing else. None of this should come close to taxing the system to the point that another application should hang for minutes at a time.

Firefox can't scroll a window for a whole minute just because another application is accessing the hard disk? That is pathetic. The system should be able to tell the difference between foreground & background tasks and give priority to the user interface by itself. But since it can't, there should be a way for me to tell the OS "Hey, this is a background task, run it at a lower priority so it doesn't interfere what I'm doing in the foreground."

All I'm asking here, is how do I use/modify mythbackend so that when it runs mythfilldatabase, it runs it at a lower priority. This is what priorities are for: make sure that the time critical stuff gets done in a reasonable amount of time at the expense of the non-time critical stuff. 

If I had written the code myself, I'd know where to put the "nice" commands in the script to deal with the issue myself, and would not have asked the question. I did not write the code, so I have no clue where to begin looking. That is why I asked the question.

End of rant.

---

### Post by nickrout on 2009-04-18
you have simply run into the limits of a fairly old and underpowered system.

if you want to run mythfilldatabase your own way under nice then turn off the function to run it in myth and set up your own niced script to run under cron.

or move mythfilldatabase to another name, like mythfilldatabase.real and set up a new script called mythfilldatabase that is a wrapper applying nice to mythfilldatabase.real

or as i said before run mythfilldatabase at a time when it will not affect your user experience.

---

### Post by AKADAP on 2009-04-18
> **nickrout said:**
> you have simply run into the limits of a fairly old and underpowered system.

I assume you are talking about the via system that I am not using. It is under-powered, but not particularly old. I do not believe that it is incapable of running Linux, just unsupported.

> 
move mythfilldatabase to another name, like mythfilldatabase.real and set up a new script called mythfilldatabase that is a wrapper applying nice to mythfilldatabase.real


This is what I was looking for, Thanks. This should work at the very least to test to see if this will fix the issue. It may, however, screw things up when mythTV comes out with the next update.

---

### Post by AKADAP on 2009-04-18
This is definitely an improvement, but mysqld is still running at nice 0, and locking out Firefox (just not as often or as long as it did before). 

Where is mysqld run from, and is it possible to change its nice level?.

There appear to be 3 different daemons running for mysql. they are started by srcipts in /etc/init.d, but I am reluctant to alter these scripts. 
The man page for the script that starts mysqld, mysqld_safe indicates that it has a --nice=x parameter, but also indicates that there is a config file for mysql somewhere, but doesn't give the name for that file or where it is located.

---

### Post by nickrout on 2009-04-18
> **AKADAP said:**
> I assume you are talking about the via system that I am not using. It is under-powered, but not particularly old. I do not believe that it is incapable of running Linux, just unsupported.

some of the via chips are i586 cpus and *buntu is compiled for i686 I believe.


> 
This is what I was looking for, Thanks. This should work at the very least to test to see if this will fix the issue. It may, however, screw things up when mythTV comes out with the next update.

I gave you other options like running a custom script out of cron which will survive an upgrade.

Also on reconsideration a better idea than the one you quoted would be to set up the wrapper script as mythfilldatabase.nice, and then set that as the mythfilldatabase programme in setup. That too will survive an update. (This is all in setup>general)

---

### Post by bb_145 on 2009-04-18
I'm having a similar problem.  I'm running my backend on an old Thinkpad T40, and if Mythfilldatabase runs when a recording is happening, it causes the recording to skip.  I've been looking for an option to make it so it doesn't run when a recording is occurring, but I haven't found it yet.  It does appear to be a know issue, with 3 solutions listed here

[http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck](http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck)

The most interesting is to use CPU limit, with a how-to here

[http://ubuntuforums.org/showthread.php?t=992706](http://ubuntuforums.org/showthread.php?t=992706)

(Haven't tried it yet- was hoping for something simpler- like a check box ;) )

---

### Post by nickrout on 2009-04-19
> **bb_145 said:**
> I'm having a similar problem.  I'm running my backend on an old Thinkpad T40, and if Mythfilldatabase runs when a recording is happening, it causes the recording to skip.  I've been looking for an option to make it so it doesn't run when a recording is occurring, but I haven't found it yet.  It does appear to be a know issue, with 3 solutions listed here

[http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck](http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck)

The most interesting is to use CPU limit, with a how-to here

[http://ubuntuforums.org/showthread.php?t=992706](http://ubuntuforums.org/showthread.php?t=992706)

(Haven't tried it yet- was hoping for something simpler- like a check box ;) )


can you really not figure out a time of day when your box is unlikely to be recording anything? About 4 or 5 am perhaps?

---

### Post by AKADAP on 2009-04-19
> **nickrout said:**
> can you really not figure out a time of day when your box is unlikely to be recording anything? About 4 or 5 am perhaps?

No. I have several programs on the History Channel, and Discovery that show at random times. 

Also, Schedules Direct is attempting to spread its load by automatically suggesting times to run mythfilldatabase. Forcing mythfilldatabase to run at a fixed time would defeat this.

---

### Post by AKADAP on 2009-04-19
> **bb_145 said:**
> I'm having a similar problem.  I'm running my backend on an old Thinkpad T40, and if Mythfilldatabase runs when a recording is happening, it causes the recording to skip.  I've been looking for an option to make it so it doesn't run when a recording is occurring, but I haven't found it yet.  It does appear to be a know issue, with 3 solutions listed here

[http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck](http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck)

The most interesting is to use CPU limit, with a how-to here

[http://ubuntuforums.org/showthread.php?t=992706](http://ubuntuforums.org/showthread.php?t=992706)

(Haven't tried it yet- was hoping for something simpler- like a check box ;) )

The CPU limit won't work, CPU is barely in use when the system locks up. It is a disk access issue.

The best solution in that list is the additional hard drive, but that requires the system use more power and make more noise.

If I can get the nice level working, that would give disk priority to other tasks, and have a good chance of solving the problem.

---

### Post by nickrout on 2009-04-19
As a matter of curiosity, how many channels do you have in your setup? 

When mythfilldatabase runs it inserts a lot of info into the database and then re-schedules everything to take into account the changed lineup. It must also delete entries older than a week (it keeps the last week so you can check why something did/didn't record).

Thats quite a lot of load on the database system, you might also like to research improving mysql's performance. There have been some threads on the mythtv-users mailing list in recent months. Plus this was easy to find in the wiki.

[http://www.mythtv.org/wiki/Optimizing_Performance#MySQL_Database_Tweaks]("http://www.mythtv.org/wiki/Optimizing_Performance#MySQL_Database_Tweaks")

---

### Post by mathog on 2009-04-19
> **nickrout said:**
> can you really not figure out a time of day when your box is unlikely to be recording anything? About 4 or 5 am perhaps?

Will Myth schedule a wake event to run mythtfilldatabase, or is that only for recordings?

---

### Post by AKADAP on 2009-04-19
> **nickrout said:**
> As a matter of curiosity, how many channels do you have in your setup? 


Several hundred.

I have two antennas pointed in different directions, each has a separate list of the local OTA channels.
Since I have two different types of tuners, I had to have two complete lists of cable channels. This was recommended by one of the Wikis to prevent confusing the software.

So that means two copies of OTA channels, and two copies of cable.

---

### Post by AKADAP on 2009-04-19
> **mathog said:**
> Will Myth schedule a wake event to run mythtfilldatabase, or is that only for recordings?

I do not know. I do have my computer set up to power up when a recording is scheduled, but I do not know if it will wake for a scheduled mythfilldatabase run.

---

### Post by AKADAP on 2009-04-19
> **nickrout said:**
> some of the via chips are i586 cpus and *buntu is compiled for i686 I believe.


The disk I installed from claimed it was i386. If this were true, it would not have had a problem.

---

### Post by nickrout on 2009-04-20
> **AKADAP said:**
> Several hundred.

I have two antennas pointed in different directions, each has a separate list of the local OTA channels.
Since I have two different types of tuners, I had to have two complete lists of cable channels. This was recommended by one of the Wikis to prevent confusing the software.

So that means two copies of OTA channels, and two copies of cable.

Do the two lineups have different programming/lineups or the same programming? If they have the same programming they should be the same video source.

---

### Post by AKADAP on 2009-04-20
> **nickrout said:**
> Do the two lineups have different programming/lineups or the same programming? If they have the same programming they should be the same video source.

The two cable lineups are the same, the two antenna lineups are different.

I would have thought that the three cable tuners could have used the same lineup, but since one of those tuners is a different type, it was recommended to use a separate lineup for it to prevent confusing the software.

---

### Post by AKADAP on 2009-04-21
I did a bit of poking around yesterday. Found that the database for mythTV is only 80 MB. A friend of mine who works with databases on Windows and BSD (and reminds me often that BSD is NOT linux) points out that this is a trivially small database that should be entirely cached in memory, and so does not explain the solid disk activity light. In fact, for the amount of time the disk activity light is stuck solidly on, it could read and write that database several hundred times.

He suspects that mythfilldatabase is for some reason accessing the recordings on the disk. Neither of us could come up with a plausible reason why it would do so, but those are the only files big enough to account for the incredibly long disk accesses.

What command would I run to determine what files an application has open? My friend suggested "fstat", but that is a BSD command that does not exist on linux.

---

### Post by nickrout on 2009-04-21
```
lsof
```

generally needs to be run as root to be any use, so ```
sudo lsof
```

You might get more knowledge coming to light on the mythtv-user mailing list. Thats where the real expertise is!

Did you try the database tweaks I pointed to you in post #17?

---

### Post by AKADAP on 2009-04-21
I have not yet done the database optimizations, The rest do not seem to apply.

I just did an experiment, changed the nice level of mysqld and mysqld_safe to 5, and ran mythfilldatabase. This did not improve the issue. Still caused firefox to hang for minutes at a time. Looks like software is so badly broken I will have to use a hardware fix (additional hard drive for 80 MB database). Pathetic.

---

### Post by nickrout on 2009-04-22
> **AKADAP said:**
> I have not yet done the database optimizations, The rest do not seem to apply.

I just did an experiment, changed the nice level of mysqld and mysqld_safe to 5, and ran mythfilldatabase. This did not improve the issue. Still caused firefox to hang for minutes at a time. Looks like software is so badly broken I will have to use a hardware fix (additional hard drive for 80 MB database). Pathetic.

Stop your own pathetic moaning, you have been given solutions to try that you haven't even tried.

mythtv works well for thousands of people.

If you identify a bug file it. But I do suggest asking on mythtv-user mailing list first as there is more knowledge there than on this forum.

---

### Post by alexyz on 2009-04-27
FWIW, pretty sure the problem is neither CPU nor disk but I/O blocking.  

There may be a way to configure mysql to be less aggressive but I never figured it out.  For anyone who's interested you can find some discussion on the mythtv-users list.

---

### Post by nickrout on 2009-04-27
what is the difference between disk overload and io overload? in this case i suggest nothing.

---

### Post by alexyz on 2009-04-27
Can be overloading the bus not just disk I/O.  Here's a description of the problem.

[http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck](http://www.mythtv.org/wiki/Troubleshooting:Mythfilldatabase_IO_bottleneck)

I don't understand this stuff very well.  I looked into it a while ago and decided to just live with it.

---

### Post by nickrout on 2009-04-27
ok  i see what you mean.

---

