---
title: "problems ripping certain CDs with rubyripper"
date: 2011-01-23
forum: Multimedia Software
---

### Post by aravenscroft on 2011-01-23
so I've been using the rubyripper gui on 10.04 for a while now, using my samsung se-so84 external dvd writer and I really like it. the problem is, I seem to have found that a small handful of my CDs will not rip at all. it says that it is ripping the first trial of the first track and never progresses past this. I check the files and the temporary .wav file. usually, when this file is created it is of size 44 bytes and increases to a number of MB in a matter of seconds. in the case of the albums that do not work, the file remains very small, all being 32KB, with the exception of one that is 64KB and another that remained 44 bytes. I check the log files and they all read:

```

STATUS

Starting to rip track 1, trial #1
Filesize is not correct! Trying another time
Starting to rip track 1, trial #1

```however, this appears to be normal as I checked the log of an album that ripped correctly and it started with this.

so I tried using the command line mode and that didn't work either. the ouput was:

```

STATUS

Ripping progress (0 %)
Ripping track 1
Expected filesize for track 1 is 66389948 bytes.

```and then it exits. in the directory, an empty temp folder has been created and the album's folder contains a log file that ends after STATUS. I tried using a CD that works on the gui and the command line did the same thing. could this be something to do with the incorrect filesize that the log showed for all CDs?

but anyway, I'm not as fussed about getting the command line mode working, what I really want to do is be able to rip these albums. in case it helps, the problematic albums are:

john frusciante - to record only water for ten days
john frusciante - shadows collide with people
john frusciante - curtains
new order - substance [2 discs, neither will rip]

the only link I can see is that all but one (curtains) were released by warner. copy protection crossed my mind as an explanation and I know warner have used it in the past.

so does anyone have any suggestion on what the problem may be? thanks.

---

### Post by shantiq on 2011-01-24
well do not know what the problem might be on the rubyripper front but if it is copy-protection you could try this maybe


Do it for one disc then try RR again with the new disc see it protection was the problem   (at least you will know that ::::)))





[from]("http://www.suslik.org/Writings/musicrip.html")     




To extract tracks 1-10 from a protected music disc in your main CD ROM drive:

cdparanoia -d /dev/cdrom -Y -v --output-wav --batch --force-read-speed 1 1-10

This dumps the tracks in the current directory in WAV file format under the names track01.cdda.wav etc. It forces the CD ROM drive to read at single speed, hopefully reducing the number of retries that the software will make in reading tracks with copy-protect noise. It also instructs (with the -Y flag) the program to ignore normal errors as far as possible. Obviously, if your protected disc is also scratched then you're fairly screwed. :-)

If you're using a different CD ROM drive then change the argument to -d appropriately; for my SCSI CD ROM drive I use -d /dev/scd0 for example.

Play each track in turn with:

 play track01.cdda.wav

to ensure that it's free of artefacts.

Now you can record a CD-R with these tracks, essentially producing a duplicate of the original disc but without the corrupting noise; ironically, you have produced a proper CD from an incorrectly formatted disc. Insert a blank CD-R into your CD recorder drive (assumed to be a SCSI drive with ID 3) and type:

cdrecord -v speed=8 dev=0,3,0 -audio -pad track*.wav

This command records at 2x speed; you can adjust this to 4x speed or greater if your CD writer supports it. You need to change the 0,3,0 to 0,X,0 where X is the SCSI ID of your CD writer.

This should produce an audio CD that will play in any CD-ROM drive, computer-based or otherwise. You can then rip from the CD in your own time with your usual software.

---

### Post by aravenscroft on 2011-01-24
interesting, thank you. like I said before, copy protection was simply a guess, but I shall definitely try this if I can't find anything rr specific.

---

