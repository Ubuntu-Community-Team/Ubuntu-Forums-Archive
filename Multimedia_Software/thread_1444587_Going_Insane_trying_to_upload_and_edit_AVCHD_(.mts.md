---
title: "Going Insane trying to upload and edit AVCHD (.mts) files! Help!"
date: 2010-04-01
forum: Multimedia Software
---

### Post by shipp on 2010-04-01
I cannot, for the life of me, find a decent open-source editing program that can handle the recordings I have from a Canon Vixia HF S10 camcorder.  I would really like an editing software that can handle directly avchd files (.mts extensions) or that can convert the files into a format that it handles best.  I tried using WinFF to convert these files into MPEG 2 and MPEG 4 files.  This worked out okay.  When played in VLC, they look almost flawless after the conversion (although I am sure a lot of quality was lost), but when I tried to play them in mplayer they looked like **** (mplayer says i need gstreamer - bad plugin)  When I tried editing them in Kdenlive and Lives, they crashed the software.  When I tried avidemux GTK+, the wouldn't load.   Before these programs crashed (maybe the missing plugin) the video and audio was super whack, so I didn't want to use them even if they'd work.    

I dont want to use gstreamer-bad-plugin because the last time i installed it, it led to a problem where songbird and banshee would crash and my software center wouldn't open, plus mad slowdown in processing speed.  

Does anyone have any suggestions on a way to convert the files, and edit them?  I just want to do basic stuff.  The best, of course, would be a software that would upload them from the usb device, and put them in front of me for editing.  Unchanged from the original format would be amazing, or converting them would be fine too.  Any ideas.   Can anyone maybe tell me how to get the preview version of VideoLan Movie Creator (the VLC project)  I want to try that.  

Thanks

---

### Post by bsmith1051 on 2010-04-01
I doubt you'll have much luck with open-source editors.  You might try the 14-day trial of Video Redo 4 (which is in open beta now; you can download it from their forums).  It's a Windows app, unfortunately.  It *mostly* works in WINE but not for HD files. You can open AVCHD files with it, make simple edits (e.g. cut out commercials) and then save to pristine MPEG2.

A better place to research AVCHD editors would be AVSforums . . .

---

### Post by s_ø on 2010-04-01
I have a Canon HF100 and use Kdenlive. I transcode using DNxHD. You can install the render profile from Kdenlive. Look in the 'Settings' menu for something like 'get new render profiles'. (dont know exact name - my Kdenlive is in danish).

---

### Post by shipp on 2010-04-02
Okay, so I don't really have a clue about any of this stuff, but let me ask another question.  What does transcode mean?  Say I want to use kdenlive, what format should my video files be converted to?  In other words, what format does kdenlive work best with.  Also, what format will kdenlive work with that retains the best quality?  Im new to ubuntu and I was kind of hoping for a software that I am familiar with: meaning, I plug my camera into the computer and *poof* a wizard pops up asking me to import the files, and then, well everything is done for me.  As it stands, I can't figure out what to do to make my files work in a video editing software.

---

### Post by s_ø on 2010-04-03
Ill try help you get that *poof* feeling.
Transcoding is re-encoding the clips in a different format. AVCHD is highly compressed and proprietary format, there is still problems working with it in a free environment. You can read aboout Kdenlive and AVCHD support here [http://www.kdenlive.org/forum/state-avchd-support-kdenlive-mlt-and-ffmpeg](http://www.kdenlive.org/forum/state-avchd-support-kdenlive-mlt-and-ffmpeg)

In Kdenlive go to **File > Transcode Clips**. Find the files you wish to edit - you can select multiple files at once. Then select DNxHD as your render profile (I use 120 Mb/s). This will give you high quality .mov files thats easy to work with. The transcoded clips will be about 7-8 times the size of the original clips.

If you dont have the DNxHD profiles you can install the from **Settings > Download New Render Profiles**

If you have installed Kdenlive from the Ubuntu repository you should follow these instructions to get the latest stable version. [http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages)

If you have trouble using Kdenlive ill be happy to help.

---

### Post by shipp on 2010-04-04
Thanks for the info, thats what I needed to know.  I started using openshot, but it seems lacking.  Exporting a small video file (3 minutes long) took about 4 hours.  WTF!  So, yeah, I'll try to use kdenlive now that it makes more sense to me.  Thanks for the help!

---

### Post by mackra on 2010-04-07
s_ø,

KDEnlive kept crashing just playing my .MTS files until I read your tip on transcoding clips.  Thank you!

Rich

---

### Post by LuridCinema on 2010-04-07
I do not have any AVCHD files to play with, but Im sure you can use ffmpeg to convert the files from .mts to .m2t

```
ffmpeg -i INPUT.mts  -r 29.97 -s 1440x1080 -sameq output.m2t
```OR......
```
ffmpeg -i INPUT.mts  -r 29.97 -s 1440x1080 -sameq output.mov
```ALSO be sure and set your preferences BEFORE you load the file into Openshot or whatever program you will use to edit. That will help stop crashes. Be sure you installed the program as directed according to your distro on the Openshot website

GOOD LUCK ! Im sure you will tackle this.. Please let us know what you finds that works

You can install VLC from the repositories or using synaptic package manager

---

### Post by WSparrow23 on 2010-05-10
You can use TsMuxer to demux your (m2)ts files then feed the raw streams into AviDemux and filter/edit/recode any number of ways.  Doesn't work with all codecs, but it's worth a shot.

btw I don't think you'll find TsMuxer in any repos but there's a linux version on their website that works for me with Lucid.

---

### Post by elias@unam on 2010-07-02
Openshot is a good editor.
The problem with AVCHD is a patent, with a monopolic strategy.
If you are in time to change your camera, do it, the canon hv40 uses other format HDV, also having good optics.
I also have other Canon model with the same video chip than yours. It is very limmited you can't choose other resolution like 720p, just 1920x1080 or 1440x1080, the bitrate is the only thing that changes choosing other quality.
I even tried to edit AVCHD in an Intel i7/(4 cores/8 threads) computer with an nvidia quadro card, but AVCHD videos don't look fluent under linux.
The problem is not the computer, nor linux, but the threat from pattent holers to linux distribution proyects.
They forbid to include free versions of patented codecs in distributions.

This is very unfair, because one has paid many times royalties for AVCHD, once in the camera, other time in the limited editing software included (not for free, just for windows or Mac OS) whith your camera, with the microcode in the videcard, Win7 (included with charge in your computer) also has codecs for AVCHD), you and I have paid that software that includes the royalties for that patent. 
But can't use AVCHD codecs in our favorite OS, Ubuntu or other Linux distributions. Due to legal, not technical reasons.

Still there are h264 codecs available in the internet (search h264 linux, freeware,..)
Also the medibuntu site has something.

Some of this software is distributed in source code, difficult to compile and install for non experts.

My advice, that is what I have done, buy a big hard disk, 500GB/7200RPM for a notebook, or that 1-2TB for desktop.
Then translate your videos with ffmpeg (compiled with h264 and other codecs) to an open or at least supported format.
I am in the process, to experiment with several formats, I can't tell you which is better at this time. 
But that seems a better option.

Anyway, if you want to encode to AVCHD (h264/ac3) you may find a program to do that, but it makes no sense, if you want to burn Blu-ray, the burners an the recordable disks are very expensive, cost almost the same as one with a movie. 
This format was created to make very difficult to make illegal copies of pictures, they did not take into account that some people, like us, want to do their own films, or backup large ammounts of information, and are not interested at all in doing copies of their stupid films.

In my experience, I can see fluently in a core2duo@2GHz, with Intel 945GM chipset, 1440x1080 videos. I think is the third quality option to select (see your manual).
In practice I have to convert videos to less definition.
It does not matter to much if you consider that not to many people is capable to see 1080p  videos in their computers.

If you make your pictures with your friends you can generate DVDs for them, so they can play it anywhere.
You can, if you want burn DVDs with AVCHD/Blu-ray format, but for just a little more that 8GB in a dual layer DVD-R.

Or you can use comercial software, mainly available for windows, and pay again a lot for the AVCHD royalty.

Here is a page with information about codecs:
[http://www.w3.org/2008/WebVideo/Fragments/wiki/State_of_the_Art/Codecs](http://www.w3.org/2008/WebVideo/Fragments/wiki/State_of_the_Art/Codecs)

Here a page about the blu-ray patent
[http://bluraysucks.com/](http://bluraysucks.com/)

More information about h264 codec in wikipedia
[http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC](http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC)

Here information about an open format
[http://en.wikipedia.org/wiki/Theora](http://en.wikipedia.org/wiki/Theora)

---

### Post by 2912pwil on 2010-07-08
Just bought a Panasonic FZ38 camera that also does video, test-shot a bit and then wondered how the h**l I'd convert/view it...

Then I tried my favourite editor, Handbrake (think it comes in MOC OS & Windoze versions also...) free software, opensauce, 

I'd previously used it to copy/convert stuff off DVDs & t'InterWeb Flash moves onto my ANDROID Nexus One:  

So, loaded it up, selected the source (blimey, Handbrake recognises it..) clicked on iPhone pre-sets ('cos that's what I'd used before ..) and off she runs, spittin' out an .m4v vid.. which runs nicely with Movie Player..

Then re-ran it also starting iPhone presets & wind up the Picture settings back to the format it was shout in 1280x720 

HTH

Lodger

---

### Post by bsmith1051 on 2010-07-08
Are you able to run Handbrake 'directly' under Wine?

---

### Post by TorreyKite on 2010-07-09
@Elias
Thanks for the detailed information and the tips on what to look up.  
 
In my case...   I've got a Sony HDR SR11.  We love the picture quality especially when plugged directly into our HTS. 
Our goal with that camera was to capture family video in HD so that years later we can use it  and it will not look as dated. 
I'm sure that as time goes on the disks, BD Burners, software and players will drop significantly in price. CD-Rs are dirt cheap now right?
 
As for Ubuntu... I started off on Karmic and migrated to Lucid once it was released.  Still trying to learn about what multimedia software is out there.

---

### Post by JohnAStebbins on 2010-07-10
> **bsmith1051 said:**
> Are you able to run Handbrake 'directly' under Wine?

You don't need to.  There's a native linux version.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by dmp2010 on 2010-07-24
s_ø

Thank you. I was able to import the files with your instructions and convert the clips to .mov files. One question I have is, what's best way and format to convert it to so that I can give it to my friends who don't use Linux or not too computer savvy?


Thanks.

---

### Post by IronArjen on 2010-08-29
I get an error message when I try to convert using ffmpeg:

Unsupported codec for output stream #0.1

I must lack something but what?

---

