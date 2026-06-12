---
title: "Mythbuntu playback"
date: 2010-12-24
forum: Mythbuntu
---

### Post by wildcard442 on 2010-12-24
Hi,

I am having choppy playback with mythbuntu.  It keeps stuttering and pixelating on most of my HD (720p) videos.  It isnt the videos because they play back fine on my laptop and desktop.  It used to run fine on my previous versions of MythDora and Mythbuntu, but now none of my 720p (or higher) movies are watchable.  Oh and during playback, top says my "mythfrondend" process is about 85% of the CPU

I am running 10.10 and my hardware specs are:

AMD Athlon X2 2.0GHz
Nvidia GeForce 7300 GT PCI-E x16
1GB Ram
500GB Sata HD
Asus A8N5X motherboard

Have I configured something wrong or do I just need to upgrade my video card? 

Please help me thanks!

---

### Post by thatguruguy on 2010-12-24
Are you running mythtv .23 or .24?
What settings are you using in your front end?

---

### Post by thatguruguy on 2010-12-24
Also, your video card doesn't support VDPAU. You can get an 8400 GS for ~$50, which would provide much better playback.

---

### Post by wildcard442 on 2010-12-28
I am running .23

I'm going to upgrade the video card and see if that fixes the issue.

---

### Post by sami8519 on 2010-12-28
Hi,

Sorry for posting here, but I want to know if upgrading to version .24 will improve playback? because I also have some stuttering. 

Also I think the frontend is not configured by default to use VDPAU, because when I went to tv settings>General I did it manually there. Anbody can confirm that?

Thanks.

---

### Post by newlinux on 2010-12-28
> **wildcard442 said:**
> Hi,

I am having choppy playback with mythbuntu.  It keeps stuttering and pixelating on most of my HD (720p) videos.  It isnt the videos because they play back fine on my laptop and desktop.  It used to run fine on my previous versions of MythDora and Mythbuntu, but now none of my 720p (or higher) movies are watchable.  Oh and during playback, top says my "mythfrondend" process is about 85% of the CPU

I am running 10.10 and my hardware specs are:

AMD Athlon X2 2.0GHz
Nvidia GeForce 7300 GT PCI-E x16
1GB Ram
500GB Sata HD
Asus A8N5X motherboard

Have I configured something wrong or do I just need to upgrade my video card? 

Please help me thanks!

What type of files and bitrate are your trying to play (mpeg-2, h.264, etc.)? 720p isn't enough information to tell us what the requirements for playing the video would be, but a VDPAU supported card would help greatly. What are the specs on the other machines where you can play the files? And on the machine where it studders in myth, if you play them with mplayer do they still studder? It could also be a playback configuration problem, you may not need another video card.

---

### Post by ian dobson on 2010-12-28
Hi,

With a vdpau capable graphic card almost any CPU will do. My frontend has a underclocked e5200@1.2GHz and a NVidia 9600 passive graphic card that plays back 1080p h264 video files (BBC HD) with only about 10-15% load.

Even mplayer playing mkv's isn't more than 20% load, when vdpau is enabled.

Regards
Ian Dobson

---

### Post by newlinux on 2010-12-28
> **ian dobson said:**
> Hi,

With a vdpau capable graphic card almost any CPU will do. My frontend has a underclocked e5200@1.2GHz and a NVidia 9600 passive graphic card that plays back 1080p h264 video files (BBC HD) with only about 10-15% load.

Even mplayer playing mkv's isn't more than 20% load, when vdpau is enabled.

Regards
Ian Dobson

Yes, this is true, but he may not have had to spend any money to get his system working if what he is experiencing is playback problems. Most any dual core would be able to handle 720p mpeg-2 and lower bitrate 720p h.264 without any accelerations, so if he is having studders it might be fixable via configuration without additional hardware.

My suggestion to use mplayer was to help diagnose if it the problem only happened in myth (i.e. playback configuration problem).

---

### Post by thatguruguy on 2010-12-28
> **newlinux said:**
> Yes, this is true, but he may not have had to spend any money to get his system working if what he is experiencing is playback problems. Most any dual core would be able to handle 720p mpeg-2 and lower bitrate 720p h.264 without any accelerations, so if he is having studders it might be fixable via configuration without additional hardware.

My suggestion to use mplayer was to help diagnose if it the problem only happened in myth (i.e. playback configuration problem).

True, but he mentioned running higher resolution videos as well. He can get a 8400GS for $30-$40, and it is probably worth the investment.

---

### Post by wildcard442 on 2010-12-28
> **newlinux said:**
> What type of files and bitrate are your trying to play (mpeg-2, h.264, etc.)? 720p isn't enough information to tell us what the requirements for playing the video would be, but a VDPAU supported card would help greatly. What are the specs on the other machines where you can play the files? And on the machine where it studders in myth, if you play them with mplayer do they still studder? It could also be a playback configuration problem, you may not need another video card.


Hi,

The files are h.264, and MKV container. 

It plays fine on my laptop which is a core duo (not a core 2 duo, but the first generation) T2400 1.83GHz, 3GB ram, Nvidia NVS 300M laptop graphics.

How do I play it on mplayer?  Let me know and I will try it.

---

### Post by newlinux on 2010-12-29
> **thatguruguy said:**
> True, but he mentioned running higher resolution videos as well. He can get a 8400GS for $30-$40, and it is probably worth the investment.

Better to know the problem before finding the solution. Those cards aren't going anywhere... Also you are better off with a GTX 200 series Nvidia card given the prices are about the same (you can get one for 30-40 as well) and they support acceleration of more codecs than the 8400 via VDPAU, if you are planning for the future.

> **wildcard442 said:**
> Hi,

The files are h.264, and MKV container. 

It plays fine on my laptop which is a core duo (not a core 2 duo, but the first generation) T2400 1.83GHz, 3GB ram, Nvidia NVS 300M laptop graphics.

How do I play it on mplayer?  Let me know and I will try it.

Find the file on your hard drive (or mount it if it's on a remote drive) and play it via commandline.

mplayer filename

Let us know if you need any help with that.

---

### Post by 4romany on 2011-01-04
This is what I use for mkv filetype:

mplayer -ac  hwdts,hwac3 -vo vdpau -vc ffh264vdpau -ao alsa:device=hw=0.1 -fs -quiet

I have a Nvidia 210 ...I also added this:

Section "Extensions"
    Option         "Composite" "Disable"
EndSection


at the bottom of my /etc/X11/xorg.conf file...

This is what I used in .22 and .23..worked perfectly....in .24 I'm setting a very slight - very quick - pause when playing...and my subtitles tend to stay on the screen sometimes....still looking into that...

---

### Post by Archmage on 2011-01-05
> **wildcard442 said:**
> How do I play it on mplayer?

If you are in Mythvideo on a file press "e" and go to the filed "external player" enter mplayer there and than you should be able to play the file with mplayer (if it is installed).

---

### Post by wildcard442 on 2011-01-17
Ok, just a quick update... I re-played one file that was giving me issues with the internal player. I used mplayer (# mplayer filename) and that seemed to resolve the issue; there werent any skips or jitter.

Does this mean I should use mplayer for all my videos or do I have some sort of configuration wrong?

---

### Post by BicyclerBoy on 2011-01-17
You could have the playback profiles in MythTV not optimized for CPU only.

Or it could be that the version of mplayer works better on your setup with weak video.

The mythtv internal player is so well integrated & mplayer is so ...... that it makes this a no-brainer..

I would get a new video card for viewing HD material GT220/240/430.
Don't get the GT210.
The only downside is losing component & S-video connectivity (no great loss).

The feature set C purevideo vdpau is a great step up from all the previous cards..
IMHO There are picture quality improvements that you can only just achieve with very powerful CPU & very good setup.

---

### Post by ill_switch on 2011-01-17
> **BicyclerBoy said:**
> I would get a new video card for viewing HD material GT220/240/430.
Don't get the GT210.
The only downside is losing component & S-video connectivity (no great loss).


I'm not a big graphics card person so maybe I am missing something obvious, but what's the difference between the 210 and the others that makes the others more worthwhile?

---

### Post by newlinux on 2011-01-17
> **wildcard442 said:**
> Ok, just a quick update... I re-played one file that was giving me issues with the internal player. I used mplayer (# mplayer filename) and that seemed to resolve the issue; there werent any skips or jitter.

Does this mean I should use mplayer for all my videos or do I have some sort of configuration wrong?

Chances are you just need to tweak your playback profile if mplayer works. What are you using now? Try normal, slim, CPU++, etc. and see which one seems to work the best. hopefully you won't have to do too much tweaking and one of the presets will work.

Also, take a look at your frontend logs from the times when you are having playback problems.

---

