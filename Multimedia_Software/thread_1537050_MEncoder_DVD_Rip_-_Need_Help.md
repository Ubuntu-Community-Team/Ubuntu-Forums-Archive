---
title: "MEncoder: DVD Rip - Need Help"
date: 2010-07-23
forum: Multimedia Software
---

### Post by Ruturaaj on 2010-07-23
Hello All!

I'm facing a problem that I want to consult with all of you. I'm using MEncoder to Rip (Convert) DVD Video to AVI/MPEG. So far I've achieved conversion of specific DVD Title as well as the Chapter under specific Title. But what I want is beyond this. 

Is there any option available for MEncoder like FFMPEG where we can specify a time span to convert? In other words, is there any option available for MEncoder that will allow me to specify the "Start Time" and "Total time of video clip" for the specified dvd://[title] [chapter]? 

I know there is such option available for FFMPEG. We can put -ss [start time tt:tt:tt] -t [total time tt:tt:tt], but I didn't find any such option for MEncoder. I searched for lavcopt and failed to locate the desired option. I could have used FFMPEG itself, but then I don't know how to map the Titles and Chapters in terms of VOB files on disc. IFO didn't provide this information to me. 

If in case MEncoder is not the tool that can do the desired stuff then is there any other command line tool available that will offer the command set as required and yet capable of converting video to AVI/MPEG?

Eagerly waiting for your reply...

Thanks & Best Regards,

Ruturaaj.

---

### Post by Nick_Jinn on 2010-07-23
Have you tried using the GUI tool called DeVeDe?

---

### Post by Ruturaaj on 2010-07-23
No; I've not tried it, simply because command line tool is the need. Command line tools allow me to automate certain things as I want. Also, the WIN32 builds of MEncoder and FFMPEG as offered me a chance to continue using same quality on Windows too. 

BTW, do you know if DeVeDe is a GUI wrapper around a command line tool or it's a genuine GUI tool? If you can help me to get the things work with MEncoder or any alternative then that will be a great help to me.

Thanks so much for your interest in this topic and I look forward valuable help from you and all the forum fellow members ...

Best Regards,

Ruturaaj.

---

### Post by andrew.46 on 2010-07-23
Hi Ruturaaj,

> **Ruturaaj said:**
> 
Is there any option available for MEncoder like FFMPEG where we can specify a time span to convert?

I hope I have not misunderstood your question but I believe you are after the *-ss* and *-endpos* options.

All the best,

Andrew

---

### Post by Ruturaaj on 2010-07-23
Sounds like the solution Bro! Can you please show me the use if with a simple command line? Consider the scenario where let's say we need to convert the 20 second video clip from Chapter 10 of Title 1, starting at 00:22:10 time.

Sorry for the trouble ... but I'm excited to see how these two params will work.

Waiting for your reply...

Regards,

------------------------
[B][I]
Update -1:[/I]
[/B]
I tried to use these two options ... and I could use them without a problem! Thanks so much for giving this solution to me. Just one thing though ... when I use the same command line with mpeg1video as vcodec, I get an error saying failed to load codec. But the same option works fine for FFMPEG. Why so? Am I missing anything? 

Can someone please show me the command line that will allow me to convert DVD title/chapter to MPEG 1/2 without codec error?

Thanks!!

---

### Post by andrew.46 on 2010-07-23
Hi Ruturaaj,

> **Ruturaaj said:**
> Sounds like the solution Bro! Can you please show me the use if with a simple command line? Consider the scenario where let's say we need to convert the 20 second video clip from Chapter 10 of Title 1, starting at 00:22:10 time.

I have not tested this but the following should be at least a start:

```
mencoder dvd://1 -chapter 10 -ss 00:22:10 -endpos 00:42:10 etc etc...
```

The man pages have reasonably comprehensive directions:

```

       -endpos <[[hh:]mm:]ss[.ms]|size[b|kb|mb]> (also see -ss and -sb)
              Stop at given time or byte position.
              NOTE: Byte position is enabled only for MEncoder and will not be
              accurate, as it can only stop at a frame boundary.  When used in
              conjunction  with -ss option, -endpos time will shift forward by
              seconds specified with -ss.

              EXAMPLE:
                 -endpos 56
                      Stop at 56 seconds.
                 -endpos 01:10:00
                      Stop at 1 hour 10 minutes.
                 -ss 10 -endpos 56
                      Stop at 1 minute 6 seconds.
                 -endpos 100mb
                      Encode only 100 MB.


```

Andrew

---

### Post by Ruturaaj on 2010-07-23
Thanks so much! I will follow your instructions and also the documentation and will get back here with my results.

---

### Post by Ruturaaj on 2010-07-25
I'm glad to convey that I could make MEncoder to work as desired with -ss and -endpos options. I actually misinterpreted -endpos initially; I thought it's the "end time". But in the testing and trial-error, I realized that it's the total time for video clip, which is same as "-t" option of FFMPEG. 

Another thing that I noticed is that, if I specify "-chapter" option, MEncoder skips -ss and -endpos at times. I don't know if this is an error or if I'm doing anything wrong or don't know if MEncoder works just like that. 

In the process of conversion, there is a lot of text written console. The one that I'm more concerned about is:

> *** libdvdread: CHECK_VALUE failed in libdvdread4/nav_read.c:264 ***
*** for dsi->dsi_gi.zero1 == 0 ***

This block is repeated several times, just before the actual conversion process starts. Also, here is how the conversion progress line looks like:

> Pos:  10.0s    253f (16%) 34.01fps **Trem:**   0min   9mb ** A-V**:-0.035 [**1125:248**]

I'm curious to know what are those terms which are highlighted in Bold in above line. Can someone please tell me more about it?

Apart from that, it will be great if someone write a set of tutorials with command line parameters to convert video to modern day video formats, such as FLV, 3GP etc. I found some text for MPEG-1 and MPEG-2. But not able to find command line options or anything for converting video to FLV. 

So far ... it's working as expected. However, I will still keep this thread open for some days; let's see if something unusual comes up. 

Thanks so much for your help and your insightful views to help me achieve what I'm looking for!

Regards,

Ruturaaj.

---

### Post by andrew.46 on 2010-07-26
Hi Ruturaaj,

Before you get too involved with MEncoder you should keep in mind that it is essentially unmaintained at the moment and has been this way for a fair while. Many are using FFmpeg instead for transcoding...

Andrew

---

### Post by Ruturaaj on 2010-07-26
Hi Andrew, 

Thanks so much for your kind suggestion. Personally, I've no problem in using FFMPEG instead of MEncoder. But my problem is, I don't know how to make FFMPEG to recognize the DVD in DVD Drive in terms of Titles and Chapters. 

MEncoder accepts "dvd-device" and "dvd://[title #] [-chapter #]" convention that allows me to select and rip one specific Title, Chapter from DVD. Can you please show me how you do the same with FFMPEG? If FFMPEG is capable of doing it then I've no problem in moving away from a unmanaged MEncoder.

Waiting for your valuable reply...

Best Regards,

Ruturaaj.

---

