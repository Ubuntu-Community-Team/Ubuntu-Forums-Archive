---
title: "How to play video CDs (SOLVED)"
date: 2024-04-11
forum: Multimedia Software
---

### Post by satimis on 2024-04-11
Hi all,

I found old video CDs on my stock of audio CDs but I couldn't play the old video CDs.  VLC media player has been running.

$ apt policy vlc```

vlc:
  Installed: 3.0.16-1build7
  Candidate: 3.0.16-1build7
  Version table:
 *** 3.0.16-1build7 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

$ apt policy ibdvdread4```

N: Unable to locate package ibdvdread4

```

$ apt policy libdvdnav4
```
           
libdvdnav4:
  Installed: 6.1.1-1
  Candidate: 6.1.1-1
  Version table:
 *** 6.1.1-1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```
Already installed

Please advise.  Thanks

Regards

---

### Post by Holger_Gehrke on 2024-04-11
Have you tried File->Open Medium->VCD/SVCD ? At least that's what [the wiki]("https://wiki.videolan.org/Video_CD") says to do.

Holger

---

### Post by ajgreeny on 2024-04-11
Were these commercially produced DVDs that need libdvdcss?
See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for all the information about installing and configuring libdvd-pkg that could be your solution.

---

### Post by satimis on 2024-04-11
> **Holger_Gehrke said:**
> Have you tried File->Open Medium->VCD/SVCD ? At least that's what [the wiki]("https://wiki.videolan.org/Video_CD") says to do.

Holger
Hi Holger,

Thanks for your advice,

Please see attached screenshots.  That are all found by me

Regards

---

### Post by satimis on 2024-04-11
> **ajgreeny said:**
> Were these commercially produced DVDs that need libdvdcss?
See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for all the information about installing and configuring libdvd-pkg that could be your solution.
Hi ajgreeny,

Thanks for your advice.

That link is for older version of Ubuntu.  I'm now running Ubuntu 22.04.

It is very strange to me.  I have smplayer installed and running.  But it can't play the video CD

Regards
[B][COLOR="#FF0000"]
Edit
 ====
 smplayer;[/COLOR][/B]
 
 After reconfig;
 Open -> Disc -> VCD
 
 Now I can play old video CDs.
 
Is there any way ripping video CD as .mp4 file and save it to hard drive?  
I have very old film video CDs such as;
[B][COLOR="#FF0000"]Gone with the Wind
Casablanca
The Guns of Navarone
Lethal Weapon[/COLOR][/B]
etc.

**[COLOR="#FF0000"]HandBrake ?[/COLOR]**

Thanks

---

### Post by ajgreeny on 2024-04-12
Yes, handbrake should do it for you.

Depending on your hardware it may take a long time to encode the video file chosen.

---

### Post by satimis on 2024-04-12
> **ajgreeny said:**
> Yes, handbrake should do it for you.

Depending on your hardware it may take a long time to encode the video file chosen.
Hi ajgreeny,

I have handbrake installed on  REPO

I found following URL
How to Convert DVD to MP4
[https://www.wikihow.com/Convert-DVD-to-MP4](https://www.wikihow.com/Convert-DVD-to-MP4)

and follow the steps on;
Method 1 - Using HandBrake

But unable to find the source of VCD.  Pls refer to attached files.

It is quite strange to me.  I can play the video CD without problem

Regards

---

### Post by ajgreeny on 2024-04-12
I suspect what you have is not a normal DVD but a DVD disk with video files on it.
Unfortunately I have no experience or knowledge of how best to deal with those.
What, if anything, does the file manager of you system show if you look at the DVD using that, assuming you can mount it to show the files, of course.

---

### Post by satimis on 2024-04-13
> **ajgreeny said:**
> I suspect what you have is not a normal DVD but a DVD disk with video files on it.
Unfortunately I have no experience or knowledge of how best to deal with those.
What, if anything, does the file manager of you system show if you look at the DVD using that, assuming you can mount it to show the files, of course.
Those Video CDs are very old CDs.  I don't think they are DVD.  The films recorded on them are very old films.  I suspect whether DVD came to birth at that time.

Gone with the wind
Casablanca
The Guns of Navarone
etc.
are very old films.  I purchased them long time ago.  Unfortunately there is no indication on those video CDs, only showing 'Video CD"

They can be converted to .mp4 directly running VLC to .mp4.  On another thread I made a mistake.  The filename "Track 10.wav" was assigned by VLC automatically.  Actually I can rename them before OR after conversion to "filename.mp4".  It is NOT necessary running ffmpeg again to convert them to .mp4 on Terminal.

Those Video CDs can be mounted automatically or manually.  Their contents are shown on the screenshot of my posting above.

Regards

---

### Post by qyot27 on 2024-04-15
[Video CD](https://en.wikipedia.org/wiki/Video_CD) is the precursor format to DVD.  It was developed in the early 90s by Sony, Philips, etc., and published as one of the color book standards like audio CDs.

DVD uses MPEG-2 at standard definition resolutions (for the most part).  VCD uses MPEG-1 at VHS-level resolution.  VCD is also not encrypted, although there are blurbs in the Wikipedia article about *some* later discs in Asia having some sort of copy protection on them (but otherwise no information on what kind it is).  But AFAIK, the White Book standard itself does not define anything of that nature the way DVD and Blu-ray both mandated particular DRM schemes for inclusion (not mandatory to use, but a company couldn't use some other weird DRM instead of the ones in the standard).

What that means is that, it's highly likely (read: near 100% certainty, barring the above-mentioned blurb) that just copy and pasting the .dat files from the MPEGAV directory to the hard disk and renaming them from .dat to .mpg is enough to get literally any player to recognize them if they aren't smart enough to recognize them by MIME type alone or from FFmpeg's format probing.  The .dat files are just standard MPEG-1 Program Streams, although when authoring them there is a parameter that mplex has to set to create VCD-compliant files.

---

### Post by satimis on 2024-04-15
> **qyot27 said:**
>  - snip- 
....
The .dat files are just standard MPEG-1 Program Streams, although when authoring them there is a parameter that mplex has to set to create VCD-compliant files.
Thanks for your advice.

I'm aware that I can't proceed converting on .dat direct to .mp4.  I have to create on .dat .wav files first.  I'm still searching its steps.

Do you have this information?  Thanks

Regards

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
I'm now converting video CDs to .mp4 on VLC Media player.  It works seamlessly.

---

### Post by satimis on 2024-04-16
Hi all,

Now I can convert VCD to MP4 with following steps:

**[COLOR="#FF0000"]Steps[/COLOR]**
1) Copy files from VCD to PC first;
1.1  Install vcdimager
1.2. Insert the VCD into the drive. It does not need to be mounted.
1.3  Open on Terminal and navigate to the folder on your PC where you want the files from the VCD.
1.4  Run vcdxrip -vpC
Files of VCD will be copied to the folder including converting .dat to .mpg automatically

2) Convert .dat to .mp4, run;```

$ ffmpeg -i file.mpg" -acodec copy -vcodec copy -f mp4 file.mp4

```

You are done.

---

### Post by ajgreeny on 2024-04-16
Great news!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by satimis on 2024-04-17
> **ajgreeny said:**
> Great news!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.
Hi ajgreeny,

OK.

Actually it is not completed solved.  Some VCD (not all), the quality of the converted .mp4 is not so clear/good compared to their original version, the VCD.  I don't know WHY?

I'll start a new posting later to find an alternative solution.

Regards.

---

### Post by satimis on 2024-04-18
Hi ajgreeny.

My problem mentioned before seems solved.

It may be on account of "ffmpeg supports remuxing of mpeg2 into .mp4 container in copy mode ....."

So I try with reencoding to h264 running;
$ ffmpeg -i newfile.mpg -c:a aac -c:v libx264 -preset slow -crf 20 newfile.mp4

It seems the problem gone.  I'll keep watching other conversions.

Besides, if running;```

vcdxrip -vpC

```
it extracts several .mpg files;```

avseq01.mpg
avseq01.mpg
avseq01.mpg
etc

```
Join them with "cat" command first;```

$ cat avseq01.mpg avseq02.mpg avseq013.mpg >> avseq-complete.mpg

```

before running "ffmpeg" for conversion.

Regards

---

