---
title: "Quite Slow Audio CD Ripping"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by Mr.nano on 2007-07-27
I ripped my cds with "RipperX" and "Grip" in Ubuntu Feisty 7.04 and it all went just fine inspite of one major problem it is almost 3 times slower than in Windows XP with Cdex 1.51 - something that lasted less than 6 minutes is done for 15 minutes and 20 seconds in Ubuntu
After I spent almost the whole day trying to figure it out and checked all threads with similar problems I am still at the same place from where I've started, so I will be quite happy if somebody could give me an advice or something.

*This comparison goes between Windows XP with Cdex 1.51 and Feisty Ubuntu with RipperX and Grip
* Same codec is on the run MP3 LAME Codec 1.3
*Same sething enabled 44KHz, 192kbits, High Quality + Checksum
*Nothing in the background (High resourse consumption process I mean)
* Same CD of course if somebody is thinking of that ;)))

---

### Post by deadgobby on 2007-07-27
Please have in your head that most of the free software for linux is written by some one with no money. Any hoo! I use Grip all the time to rip and it going to take time. You are telling the program to rip the CD to a restricted formate like mp3. If you rip to ogg formate. It shots, it scores, and it is game point. Or default wma formate. I rescued some very old CD's with so many scratches using Grip from my archive. It took some time and was very please with the results.
Gobby

---

### Post by Mr.nano on 2007-07-27
I also done the vorbis encoding and the time consumption is the same...  So I think i have a reasonable doubt that there is something wrong with my configuration rather than with the software or the encoder? Or may be I am wrong?
As far as I know Cdex comes with GPL license and I am migrating to Linux world due to the fact that it seems to me that everything is more robust, stable and quick not the opposite...

So the explanation to that inconvenience is that these thing are supposed to be done slower in Linux?

---

### Post by dscherry on 2007-07-31
Hi,
I found a couple things that help (in some cases, quite a bit).

First, in grip, turn off the error checking (at least for clean disks).  Both parenoia and scatch repair.

Second, check hdparm for your cd drive.  Make sure IO_Support, unmaskirq, and usingdma are all on (1).  Then for performance, you can try setting your hdparm readahead to 512 or 1024 (I think 256 is default).

I ran about 3 1/2 times faster with these settings.
hth,
Dan

---

### Post by Mr.nano on 2007-08-02
> **dscherry said:**
> 
Second, check hdparm for your cd drive.  Make sure IO_Support, unmaskirq, and usingdma are all on (1).  Then for performance, you can try setting your hdparm readahead to 512 or 1024 (I think 256 is default).

I ran about 3 1/2 times faster with these settings.
hth,
Dan

What is hdparm and from where to check it? And also from where i can adjust O_Support, unmaskirq, and usingdma?

---

