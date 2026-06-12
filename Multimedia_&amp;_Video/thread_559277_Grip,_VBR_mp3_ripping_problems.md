---
title: "Grip, VBR mp3 ripping problems"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by le_vainqueur on 2007-09-25
I've been ripping my CD collection using Grip for some time using the following command for encoding:

> -V 2 --vbr-new %w %m

I have had no problems until recently when I started finding a lot of clicking in CDs that I just ripped.  I thought maybe I was overworking my computer so I closed down all other programs, including Compiz-Fusion, and tried again.  No luck...still plenty of clicking.  So I tried it removing the "new" encoding as follows:

> -V 2 %w %m

Same problem, so I alterred the Grip settings to wait until the album was ripped before it began encoding.  This has still not solved any of my problems with errors in the mp3 files.  I could not find any previous posts relating to this.  

Any advice/insight?

---

### Post by le_vainqueur on 2007-10-02
Still having the same problem, but I would like to add one.  I have the same problem when trying to rip in FLAC.  I really don't understand why I am having problems.  I have ripped many CDs using my current hardware without problems.  

Any help would be greatly appreciated.


Thanks
LV

---

### Post by le_vainqueur on 2007-10-03
Okay, let's take a slightly different approach.  Assume that I never had success with my current hardware, every CD I have ever ripped has flaws in the mp3/FLAC/etc file.  How would I go about determining what piece of hardware was causing the problem, or what settings within GRIP were acting up?

---

### Post by SharedGum on 2008-01-17
Hi, I've finally decided to create an account, since I haven't been able to find a solution to this problem by lurking elsewhere. 

I have had the exact same problem as the one you describe. I hear some clicking sound when I rip my cds. I do the 192 bit rate. The clicking can be heard on both the wave file and the mp3 file, but not on the cd itself when I play it. And it's only on some tracks, but it's enough to annoy me. Also, if I redo the rip, I have been able to get rid of it instantly, but I haven't had enough time to check the other tracks to see if this clicking sound appeared elsewhere. I've looked around but have been unable to find any solutions.

Thanks.

---

### Post by killermist on 2008-01-17
A couple of ideas that may or may not be beneficial.

1.)  If possible, (re)nice the ripping threads (automagically if possible helps) to a higher priority to help ensure that the data coming off the drive actually gets used and not dropped (one possible explanation for clicks).
2.)  See if there is a way to make the CD reader spin at a lower speed.  (also helps with not overwhelming the system, giving it too much stuff to process at a time).
3.)  If possible, isolate the ripping process to separate machine that can devote all of it's processing abilities to just the ripping process.  A machine running in just console mode with no instance of X to slow things down helps.  This option won't help much if you're trying to use your machine for anything else while you're ripping cds, but doing ANYTHING while your machine is ripping has the possibility of ruining rips.  Web browsers and file browsers are most notorious for hogging processor and/or IO time at just the wrong time.  File sharing programs are also not known for behaving themselves well while other programs that are dependent on smooth IO and CPU time are trying to run.

I prefer to use an independent machine for my ripping because it cuts down greatly on the number of unknowns that could be mucking up the rips.  Once they're on the machine in wave form, then processor and IO hiccups and instability ar no longer harmful because the most delicate part is done.

As I said, I don't know if any of this would be helpful or not.

---

### Post by julian67 on 2008-01-17
probably dma is not enabled on either the optical drive or the hard drive. Check this before doing anything else.

---

### Post by SharedGum on 2008-01-17
Thanks for such quick responses.

I am getting:

 using_dma     =  1 (on)

so I take it that this is not the issue. 

My computer is mostly used for ripping music; that's the very reason that I got it. But that's not to say that I didn't have stuff running at the time of these rips. I have looked, but do not know how to decrease the speed of the cd reader (I use Grip to rip my music). If someone knows, any help would be appreciated. I looked it up and tried doing it, but it doesn't seem very intuitive.

What's frustrating about this is that this is very difficult to test - the clicks are not consistent at all. After re-ripping the cd, if I don't hear one at the original location, it doesn't mean that another one didn't appear elsewhere during the same song, or on an entirely different location on the cd. 

I am really new to this mp3 business and have been using cds (I know, old school), but have now decided to back them all up, in case that they get scratched. I've caught this early in the process, but determining when I've fixed this problem prior to ripping tons of cds will be tricky. I was also wondering if it could be my cd drive, but that may be equally difficult to test.

Thanks again.

---

### Post by killermist on 2008-01-18
According to Grip's Manual page:
```
Grip is a cd-player and cd-ripper for the Gnome desktop. 
It has the ripping capabilities of cd-paranoia(1) builtin, but can 
also use external rippers (such as cdda2wav(1)).
```

According to cdparanoia's manual page:```

       -S --force-read-speed number
              Use this option explicitly to set the read rate of the 
              CD drive (where supported).  This can reduce 
              underruns on machines which have slow disks,
              or are low on memory.

```
According to cdda2wav's manual page:```

       -S  speed --speed
              sets the cdrom device to one of the selectable speeds for reading.

```

I'm not sure where to set these parameter in grip's settings to pass to the ripper processes for their rip cycles.

---

### Post by nick_h on 2008-01-18
When debugging this problem why not just use cdparanoia from the command line?  It gives some status output which may help.  You can then also add extra paramters easily.

---

### Post by SharedGum on 2008-01-23
Thanks everyone, once again. I am pretty sure that I have figured out what the problem was, and that was the speed of my drive. I also choose not to start encoding until all the ripping is done. 

Originally, I had used the ripper known as "grip (cdparanoia)" in Grip's config/rip pull-down ripper menu. That is the built-in version of ripper for Grip. I could not easily find a way to reduce the speed. Then, I got the cdparanoia external ripper, not to be confused with the aforementioned "grip (cdparanoia)". 

There, as some have suggested, I was able to slow down my drive from 16 to 20 times the speed to 2 to 4 times the speed. For instance, to slow it down to a 2x speed, you can simply go on the rip command line and type in S 2. See the link below and look for the rip command line. You can just add the "S 2" in the beginning of it.

[http://nostatic.org/grip/doc/ar01s04.html](http://nostatic.org/grip/doc/ar01s04.html)

Now, yes, it is going to take a while to rip all my cds, but in my ten test cases, I have not encountered any clicking sound (which was more prevalent towards the end of the cd). Perhaps a better drive should be able to handle the 16x or 20x speeds,and maybe my drive would handle 8x easily too,  but 2x or 4x works for me, and that's what I will go with. 

Thanks!

---

