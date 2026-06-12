---
title: "help with avconv and libx264"
date: 2012-07-13
forum: Multimedia Software
---

### Post by lucacerone on 2012-07-13
Dear all,
I have to make some videos out of certain simulations I have run.
The videos are really simple, contain few colors, a lot of the images is
still, and last only 30sec (at 25fps). I guess I should be able to get a good quality video and a decent filesize.

I've tried a lot, but I  can't get the right settings to get good quality
videos using avconv.

There are two kind of conversion that I need to do: one is to crop certain videos that I already have (not made by me)

```
 avconv -y -f avi -c:v h264 -i input_file.avi -f avi -me_method full -c:v libx264 -c:a n -b 512k -qcomp 0.5  -r 50 -vf crop=395:395:135:35 output_file.avi
```

The other is to produce movies from a sequence of images:

```
 avconv -y -f avi -c:v h264 -i img%04d.png -f avi -me_method full -c:v libx264 -c:a n -b 512k -qcomp 0.5  -r 50 -s 480x320 output_file.avi
```

The size would be also ok, (about 5mb, even though I'd prefer a smaller file), but the quality is not that good.. there are pixels around the contours, the resolution is not that good...

Could you please give me some good advice on how to set the parameters right? (and can you explain me also what they do, and why mine are wrong???)

Thanks a lot in advance for the help,
Cheers, -Luca

---

### Post by beandog on 2012-07-17
For the second one:

>  avconv -y -f avi -c:v h264 -i img%04d.png -f avi -me_method full -c:v libx264 -c:a n -b 512k -qcomp 0.5  -r 50 -s 480x320 output_file.avi


First of all, don't use AVI, ever, unless you really need to.  Use MP4 instead.

Secondly, that bitrate is really low, which is why they look poor.

Try something much simpler, and then go from there:

> avconv -y -c:v h264 -i img%04d.png -c:v libx264 -c:a n -r 50 -s 480x320 output_file.mp4

---

### Post by lucacerone on 2012-07-17
Hi Beandog,
first of all thanks for the help.
Unfortunately I am forced to use .avi, as it is a requirement of the journal.
Using higher bitrates I get too big files, though.
In any case I'll try your command, but then I don't know which are the possible parameters that determine a good compromise between the quality
of the video and its size.
Any suggestions?
Thanks a lot for the help,
Luca

---

### Post by beandog on 2012-07-17
> **lucacerone said:**
> Hi Beandog,
first of all thanks for the help.
Unfortunately I am forced to use .avi, as it is a requirement of the journal.
Using higher bitrates I get too big files, though.
In any case I'll try your command, but then I don't know which are the possible parameters that determine a good compromise between the quality
of the video and its size.
Any suggestions?
Thanks a lot for the help,
Luca

Using x264, it'll default to a quality level of 23, which is pretty good.  It goes from 0 to 51, with the smaller numbers being bigger quality (and much bigger size).  I wouldn't go above 20.  You can change the value with -crf

So, "ffmpeg -i input -crf 20 output.avi" would change it to 20

Other than that, I'd try a better x264 preset, which you can pass with -vpre

For example,

ffmpeg -i input -crf 20 -vpre slow output.avi

There's some good ffmpeg x264 encoding guides out there, just look around. :)

---

### Post by lucacerone on 2012-07-17
Thanks again!
The things that bothers me about the presets is that they seem to be changed at every new version, that is not ideal! (at least the name have changed since my first encoded video). 
Also, I'd rather use avcon than ffmpeg (ubuntu says it is deprecated) would your advices still hold?
Cheers, -Luca

---

### Post by beandog on 2012-07-17
> **lucacerone said:**
> Thanks again!
The things that bothers me about the presets is that they seem to be changed at every new version, that is not ideal! (at least the name have changed since my first encoded video). 
Also, I'd rather use avcon than ffmpeg (ubuntu says it is deprecated) would your advices still hold?
Cheers, -Luca

Eh, the presets don't really change.

avconv (libav) is fine, they use the same syntax for the most part

---

### Post by lucacerone on 2012-07-19
Thanks for the advices,
actually I've found your page on the Gentoo website, 
so at least now I know which presets are in use and what values they use :)
As I have found some presets to encode to tablets etc etc, where should I put 
these presets to have them both only for me, both system-wide?

Thanks a lot, again!

---

### Post by FakeOutdoorsman on 2012-07-20
> **lucacerone said:**
> The things that bothers me about the presets is that they seem to be changed at every new version

The preset system has gone through some changes, and although it can be frusutrating to users in the long run the changes have been good. The old x264 preset files were depreciated and removed because presets are now accessed directly via libx264.

> **lucacerone said:**
> As I have found some presets to encode to tablets etc etc, where should I put 
these presets to have them both only for me, both system-wide?

You should not simply copy preset files and expect them to work with ffmpeg. This is a common misconception. The presets are very specific to the version of ffmpeg that they come with. You should only use the presets that come with your version of ffmpeg. Kind of a moot point now since recent ffmpeg now uses the actual x264 presets instead of emulating them with a text file.

General usage is to:
[list=1]
[*]Choose your crf value as beandog explained. A lower value is a higher quality. A sane range is 18-28. Use the highest value that still looks good to you.

[*]Use the slowest preset you have patience for. A preset is a collection of options that gives a certain encoding speed/compression ratio. See "x264 --help" for a list of available presets and ignore the "placebo" preset as it is a waste of time.

[*]Use these settings for the rest of your set of videos.
[/list]

Example:
```
ffmpeg -i img%04d.png -c:v libx264 -preset slow -crf 24 output
```

You don't need *-me_method* or *-qcomp*. The preset will take care of the details. Also remove the "-f avi -c:v h264" before your *-i*. Options before *-i* are intended as input options and in this case you're telling ffmpeg to decode the png images as H.264.

---

### Post by rabit1 on 2012-10-03
Thanks but if the image sequence file numbering doesn't start with 0 or 1 this command doesn't work.

I have lots of sequence files that I'd like to convert to high quality MP4. Unfortunately the numbering of the files don't always start with 0 or 1. For example

sc_101a1050.png
...
...
sc_101a1100.png

How to correctly use the %04d  as parameter for the avconv command?
When I try the command gave me this error:
---------------------
$ avconv -f image2 -i sc_101a%04d.png -r 30 -crf 20 -c:v libx264 output.mp4
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
sc_101a%04d.png: No such file or directory
--------------------

Any chance to change and fix the command so that it'll work on any file numbering?

Thanks in advance:

---

### Post by rome-NY on 2013-03-31
beandog.....your an idiot. everyone in the linux world firstly gives an answer to my question -how to convert mkv to avi, to use this that but only a few mention avconv. secondly everyone wants to ignore the avi for this mkv crap. HELLO...some of us have dvd players that play avi....NOT sh&*^)(, F(*&(&*king MKV. I have three divx players and avi's look and play nicely....I'm not going to spend another 300-500 bucks buying new players. AVI's are excellent....freaking idiots

---

### Post by evilsoup on 2013-04-01
First of all, rome-NY, there's no reason to take that tone. I'm sure beandog was trying to help in good faith (taking time out of his day to help you *for free*), it just so happens that his information is out-of-date.

If your player requires AVI, chances are that it can't use h.264 video - the proper AVI container doesn't support h.264, and it's a lottery as to whether your player will accept the version of AVI that has been hacked together to support h.264. Use h.264 in an MP4 (which modern hardware players will support, including current-gen games consoles), or don't use it at all.

For legacy hardware players, I would recommend MPEG4 (xvid/divx) in an AVI, as described in [this blog post](http://evilsoup.wordpress.com/2013/02/10/general-ffmpeg-encoding-guide-2/) and [this ffmpeg wiki page](http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20encode%20Xvid%20/%20DivX%20video%20with%20ffmpeg). An example usage would be:

```

ffmpeg -i input.file -c:v mpeg4 -q:v 3 -tag:v xvid -c:a libmp3lame -q:a 4 output.avi

```

...these options should work with avconv as well.

---

