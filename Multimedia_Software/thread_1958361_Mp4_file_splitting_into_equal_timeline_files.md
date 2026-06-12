---
title: "Mp4 file splitting into equal timeline files ?"
date: 2012-04-14
forum: Multimedia Software
---

### Post by sr1 on 2012-04-14
Hi,

I have a problem in splitting mp4 file in Ubuntu 10.04. The file is quite big its is 3.8GB (1080p HD) in size. I generally use MP4Box (installed from gpac) to split mp4 files.

I want the file to split into equal fragments like 15 minutes each part. So I used following command in terminal :

Firstly I converted file into KiloByte.

3.8*1024*1024 = 3984588 KB

Now, the total length of file is 89 mins, so I split it into 6 parts so as to get approx 15 min each part (15min is maximum limit).

3984588/6 = 664098 KB

I used following command :

MP4Box splits 664098 filename.mp4

Now, the file is spilitted but not equally, some of parts were of 12 mins some are of over 16 minutes. I wanted them to be splitted equally. Can anyone from you experienced people guide me how to achieve it ?

Thanks a lot!

---

### Post by shantiq on 2012-04-14
with mencoder


VIDEO SPLIT IN 15 MINUTE CHUNKS
==============================

> 
mencoder  -ss 00:00:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_1.mp4  &&

mencoder  -ss 00:15:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_2.mp4  &&

mencoder  -ss 00:30:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_3.mp4   &&

mencoder  -ss 00:45:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part4.mp4    &&

mencoder  -ss 01:00:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_5.mp4   &&

mencoder  -ss 01:15:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_6.mp4


---

### Post by ron999 on 2012-04-14
Hi
There are two similar commands for MP4Box.

**-split** time_in_seconds
              splits  in  files  of desired maximum duration.

**-splits** size_in_kilobytes
              splits in files of desired maximum size.
 
So to split the file into 15 minute fragments the command is:-
```
MP4Box -split 900 filename.mp4
```

---

### Post by shantiq on 2012-04-14
> **ron999 said:**
> Hi
There are two similar commands for MP4Box.

**-split** time_in_seconds
              splits  in  files  of desired maximum duration.

**-splits** size_in_kilobytes
              splits in files of desired maximum size.
 
So to split the file into 15 minute fragments the command is:-
```
MP4Box -split 900 filename.mp4
```



yours is better and neater:KS

---

### Post by sr1 on 2012-04-15
> **ron999 said:**
> Hi
There are two similar commands for MP4Box.

**-split** time_in_seconds
              splits  in  files  of desired maximum duration.

**-splits** size_in_kilobytes
              splits in files of desired maximum size.
 
So to split the file into 15 minute fragments the command is:-
```
MP4Box -split 900 filename.mp4
```

Wow! thank you so much dude! Let me try it, one more question, Is there any way to split mkv files in ubuntu (in 15 min time period each file).

---

### Post by shantiq on 2012-04-15
hi again now there sr1    

this will do it  [also for pretty much all video formats]  change times and extensions to suit



> mencoder -ss 00:00:00 -endpos 00:15:00 -oac copy -ovc copy originalfile.mkv -o part_1.mkv &&

mencoder -ss 00:15:00 -endpos 00:15:00 -oac copy -ovc copy originalfile.mkv -o part_2.mkv &&

mencoder -ss 00:30:00 -endpos 00:15:00 -oac copy -ovc copy originalfile.mkv -o part_3.mkv &&

mencoder -ss 00:45:00 -endpos 00:15:00 -oac copy -ovc copy originalfile.mkv -o part4.mkv &&

mencoder -ss 01:00:00 -endpos 00:15:00 -oac copy -ovc copy originalfile.mkv -o part_5.mkv &&

mencoder -ss 01:15:00 -endpos 00:15:00 -oac copy -ovc copy originalfile.mkv -o part_6.mkv


with some formats it will say    cannot copy oac with this format    in which case you have to replace  -oac copy with -oac pcm   which increases the size but **works**

---

### Post by ron999 on 2012-04-15
> **sr1 said:**
> Is there any way to split mkv files in ubuntu (in 15 min time period each file).
Yes, use **mkvmerge-gui**
```
sudo apt-get install [s]mkvmerge-gui[/s] mkvtoolnix-gui
```

Then...
mkvmergeGUI > add
Global > Enable splitting ...after this duration > 900s
Start muxing

Or with command-line:-
```
mkvmerge -o new_filename.mkv --split 900s filename.mkv
```

---

### Post by sr1 on 2012-04-22
> **ron999 said:**
> Yes, use **mkvmerge-gui**
```
sudo apt-get install mkvmerge-gui
```Then...
mkvmergeGUI > add
Global > Enable splitting ...after this duration > 900s
Start muxing

Or with command-line:-
```
mkvmerge -o new_filename.mkv --split 900s filename.mkv
```

root@server1:~# sudo apt-get install mkvmerge-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mkvmerge-gui
root@server1:~# sudo apt-get install mkvmerge    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mkvmerge

Plz help.

Thanks

---

### Post by shantiq on 2012-04-22
the line should be



```
sudo apt-get install mkvtoolnix-gui
```  :KS





then find mkvmerge-gui under sound & vision

---

### Post by ron999 on 2012-04-22
> **shantiq said:**
> the line should be

```
sudo apt-get install mkvtoolnix-gui
```
My bad :redface:

---

### Post by sr1 on 2012-04-25
Thank you so much! I'll try out this later. One more thing, I'm using Mozilla Firefox 3.6, and problem is Mediafire upload page is not opening in that, it is saying upgrade your browser and I don't want to upgrade it as it becomes too slow after upgrading to latest version of Firefox.

I also tried installing flash but it didn't solved the problem. Regarding Java, I'm unable to install it. What I'm doing wrong, please let me know, or is it not possible to open that Mediafire Upload page without upgrading it?

Thanks

---

### Post by shantiq on 2012-04-26
your version is ancient here   3.6  :KS   just checked mine and it says 11.0   so yes probably update

---

