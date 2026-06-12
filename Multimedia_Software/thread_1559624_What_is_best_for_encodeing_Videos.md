---
title: "What is best for encodeing Videos?"
date: 2010-08-23
forum: Multimedia Software
---

### Post by alberto2172 on 2010-08-23
i just want to know what is best to convert in linux ubuntu 10.04LTS to convert videos!?

---

### Post by andrew.46 on 2010-08-24
Hi alberto,

> **alberto2172 said:**
> i just want to know what is best to convert in linux ubuntu 10.04LTS to convert videos!?

IMHO this is the best:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

---

### Post by hsoulen on 2010-08-24
> **alberto2172 said:**
> i just want to know what is best to convert in linux ubuntu 10.04LTS to convert videos!?

Depends on what you would like as output and what you are using as input. Personally h/x264 mkv is my preference as they are pretty transportable. 

Handbrake lets me work with almost any input I currently use (DVD/MPEG2, divx/xvid avi etc.) so I vote Handbrake.

Cheers,

Hank

---

### Post by howefield on 2010-08-24
> **hsoulen said:**
> so I vote Handbrake.

Yep, handbrake is a great application.

Just to point out that if you want to use it with 10.04, you need use the handbrake repository to get the snapshot version as the release version at handbrake.fr won't work with 10.04.

Edit: just noticed the download page is updated.

---

### Post by hsoulen on 2010-08-24
> **howefield said:**
> Yep, handbrake is a great application.

Just to point out that if you want to use it with 10.04, you need use the handbrake repository to get the snapshot version as the release version at handbrake.fr won't work with 10.04.

Edit: just noticed the download page is updated.

Good point, fail on my part for not including any additional info. :sad:

I use John Stebbins PPA for my handbrake snapshots: [https://launchpad.net/~stebbins/+archive/handbrake-snapshots]("https://launchpad.net/%7Estebbins/+archive/handbrake-snapshots")

Hank

---

### Post by d3v1150m471c on 2010-08-24
ffmpeg. if you're planning on doing any serious encoding I recommend adding the medibuntu repositories.

[Medibuntu - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Ghost_Mazal on 2010-08-24
I using handbrake to convert with x264. How can I set the -vpre setting in handbrake ? I can't find an option for it.

---

### Post by slooksterpsv on 2010-08-24
I use WinFF - GUI for FFmpeg. It works great!

---

### Post by 0004tom on 2010-08-24
This could be compared to whats better kde or gnome.. lol there's so many options to choose from.

Myself hate ffmpeg.. I use mencoder, so I say Mencoder is best lol

---

### Post by Ghost_Mazal on 2010-08-24
> **slooksterpsv said:**
> I use WinFF - GUI for FFmpeg. It works great!

Thanx , works very good for single files. Now I just need to find an app that can do a whole dvd.

Tried avidemux , but same problem , can't set -vpre option

---

### Post by slooksterpsv on 2010-08-24
> **Ghost_Mazal said:**
> Thanx , works very good for single files. Now I just need to find an app that can do a whole dvd.

Tried avidemux , but same problem , can't set -vpre option

DVD::RIP

You will need to install some items like rar xvidconf and that. If you go to Debug -> Check Dependencies after it's installed, you can go to software center and search for that package or go to terminal and type in:
sudo apt-get install <package>
For example
sudo apt-get install rar

---

### Post by Ghost_Mazal on 2010-08-24
Tried dvd::rip but I couldn't see any -vpre setting so it won't work.
It must be an app that you can set that.
The default vpre runs the encode at a terrible 14fps which is way too slow. So I need an app that I can set that to a faster value

It also has no audio codec options. Just a standard mp2. Input codecs also can't be edited.

---

### Post by Linuxforall on 2010-08-24
WinFF, DeVeDe and Acidrip work quite good, they also work with compiled ffmpeg, x264 and mencoder as per FakeOutdoorsman and Andrew46's instructions.

---

### Post by Ghost_Mazal on 2010-08-24
Acid rip also don't work. Just hangs with a lot of cpu activity but nothing happens.

The search continues

---

### Post by Ghost_Mazal on 2010-08-25
Ah I found that Handbrake can read a dvd structure :D Just also no option for vpre setting. At least it runs slightly better at 20fps and can enque jobs. So will use that for now for my DVD encode needs and just enque them and start the que when I go to bed ;)
 
Really impressed with ffmpeg and x264 quality of the output file. Very nice :)

---

### Post by Linuxforall on 2010-08-25
> **Ghost_Mazal said:**
> Acid rip also don't work. Just hangs with a lot of cpu activity but nothing happens.

The search continues

Have you installed mplayer, Acidrip works fine here.

---

### Post by Ghost_Mazal on 2010-08-25
> **Linuxforall said:**
> Have you installed mplayer, Acidrip works fine here.
 
Yep I did. I probably have all major video apps installed now during my testing and searching.
 
Best overall one is Handbrake.
 
I do however think all might not be well with my install.
When I wanted to learn the ffmpeg way in terminal I got missing file errors. So I did a uninstall and re-install of ffmpeg and a lot of stuff was removed and most of my video apps like VLC and mplayer are acting strange.
I'm gonna do a new fresh install over the weekend from scratch , but I fail to see how any of the apps I already tested gonna beat Handbrake anyway.
 
Also , I am on a 32bit install but do have a 64bit cpu so the fresh install will be 64bit. That might also make a big difference.

---

### Post by prabath_fun on 2010-09-08
Hi,
   I tried DVD/VOB file conversion to MP4/MKV with Handbrake. Basically, VOB/DVD file which I want to convert got 2 audio tracks (AC3 and DTS). While converting, I want to keep second track -DTS track as is, without encoding. But, in audio tab, I can able to see only AC3 output and AC3-pass-through option. DTS pass through is disabled. 
  Kindly someone guide me how to get DTS pass through while converting the DVD file using Handbrake. 
   I can able to do with Avidemux, but, I am facing audio out-of-sync with video problem...
With advanced thanks,
Prabath

---

### Post by JohnAStebbins on 2010-09-08
First, DTS passthru is only going to work if you are using mkv.  mp4 doens't support DTS.  Second, make sure you have selected the DTS source track before trying to select the output type.  It won't let you select DTS output if your source track isn't DTS.

---

### Post by prabath_fun on 2010-09-08
Hi JohnAStebbins, Thanks for your reply...
I have selected mkv for DTS output which I came to know through Handbrake website guide.
But, I don't know where to select DTS sound track before selecting output type. I searched throughout the menus. I could not... 
Please guide me how to select Second sound (DTS) track for conversion....

---

### Post by JohnAStebbins on 2010-09-09
On the audio tab, there is a 'Track' option and a 'Codec' option. Before you can set the 'Codec' to DTS, you must select the DTS source 'Track'.

---

### Post by prabath_fun on 2010-09-09
Hi JohnAStebbins,
   Thanks...
   But, track shown is only "Unknown (AC3) (5.1ch)". nothing else.
   I am using Handbrake  svn3506 (i686) version. Is there any other version I need to use!!!!

---

### Post by JohnAStebbins on 2010-09-09
Well, it sounds like handbrake isn't finding a second DTS track.  You'll have to show me the activity log of the scan for me to tell for sure.

---

### Post by prabath_fun on 2010-09-12
Hi JohnAStebbins,
   Kindly let me know where can I find the log file.

---

### Post by prabath_fun on 2010-09-13
Hi,
  I got the below log from view -> activity window. 
libdvdread: Encrypted DVD support unavailable.
[19:53:17] hb_scan: path=/dev/sr0, title_index=0
[19:53:17] scan: trying to open with libdvdread
[19:53:17] dvd: Region mask 0xff
[19:53:17] dvd: Warning, DVD device has no region set
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[19:53:17] dvd: not a dvd - trying as a stream/file instead
[19:53:17] file is MPEG Program Stream
libdvdread: Encrypted DVD support unavailable.
[19:53:35] add_audio_to_title: added AC3 audio stream 0x89bd
[19:53:35] add_audio_to_title: added AC3 audio stream 0x80bd
[19:53:36] scan: decoding previews for title 1
[19:53:37] scan: audio 0x80bd: AC-3, rate=48000Hz, bitrate=448000 Unknown (AC3) (5.1 ch)
[19:53:52] scan: 10 previews, 720x480, 23.976 fps, autocrop = 58/56/2/0, aspect 1.78:1, PAR 32:27
[19:53:52] scan: removing audio 0x89bd because no bitrate found
[19:53:52] scan: title (0) job->width:720, job->height:304
[19:53:52] libhb: scan thread found 1 valid title(s)
libdvdread: Encrypted DVD support unavailable.


Kindly let me know why I could not able to select DTS audio (second) track.

---

### Post by andrew.46 on 2010-09-13
Hi prabath,

> **prabath_fun said:**
> 
```
libdvdread: Encrypted DVD support unavailable.
```


Loks like you are missing libdvdcss, have a look here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This will guide you through its installation...

Andrew

---

### Post by prabath_fun on 2010-09-13
Hi andrew,
 Thanks.. I did as mentioned in the link...
 But, still, no improvement... Handbrake is not showing second audio track. Still, it is showing AC3 track only.... Below is the log after restricted packages installed
[18:59:37] gtkgui: HandBrake svn3506 (2010090101) - Linux i686 - [http://handbrake.fr](http://handbrake.fr)
[18:59:37] hb_init: checking cpu count
[18:59:38] hb_init: starting libhb thread
[18:59:38] hb_init: checking cpu count
[18:59:38] hb_init: starting libhb thread
libdvdread: Encrypted DVD support unavailable.
libdvdread: Encrypted DVD support unavailable.
[18:59:42] hb_scan: path=/dev/sr0, title_index=0
[18:59:42] scan: trying to open with libdvdread
[18:59:42] dvd: Region mask 0xff
[18:59:42] dvd: Warning, DVD device has no region set
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[18:59:42] dvd: not a dvd - trying as a stream/file instead
[18:59:42] file is MPEG Program Stream
[18:59:53] add_audio_to_title: added AC3 audio stream 0x89bd
[18:59:53] add_audio_to_title: added AC3 audio stream 0x80bd
[18:59:54] scan: decoding previews for title 1
[18:59:54] scan: audio 0x80bd: AC-3, rate=48000Hz, bitrate=448000 Unknown (AC3) (5.1 ch)
[19:00:09] scan: 10 previews, 720x480, 23.976 fps, autocrop = 58/56/2/0, aspect 1.78:1, PAR 32:27
[19:00:09] scan: removing audio 0x89bd because no bitrate found
[19:00:09] scan: title (0) job->width:720, job->height:304
[19:00:09] libhb: scan thread found 1 valid title(s)
libdvdread: Encrypted DVD support unavailable

---

### Post by JohnAStebbins on 2010-09-14
There's a lot of problems here.
```

libdvdread: Encrypted DVD support unavailable.
libdvdnavVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnavVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[18:59:42] dvd: not a dvd - trying as a stream/file instead
[18:59:42] file is MPEG Program Stream

```
You still don't have libdvdcss installed properly.  But there are other problems to solve before this would be an issue.  It's not even recognizing the disc as a DVD.  Note the errors in trying to open VIDEO_TS/VIDEO_TS.IFO.  Can you mount the disc and show us a directory listing of what is present there?  It finds something that looks like a program stream by reading the raw data it sees on the disc.  But this is a definite path to failure.

---

### Post by prabath_fun on 2010-09-14
Hi JohnAStebbins,
   I have verified libdvdread and libdvdnav installation in synaptic package manager. It shows that, it is installed with green color. But, I am not seeing libdvdcss... I just checked in ubuntu packages website for same, I am not getting libdvdcss. Is it collection of above said to packages???
   I am not under standing "show us a directory listing of what is present there?". Is it do you mean directory structure / tree!! Or some sort of log file. If log file, Kindly let me know where can I find. 

If it is tree, after mounting, it will be /media/Madrasa..<Dvd name>
inside this I will be having one folder called video_ts and inside this folder will be having .vob files and supported files...

  Further, just I gave a try with windows version of Handbrake in XP, which runs inside virtualbox. There I found no problem. I can able to select second audio track (DTS track) or first audio track (AC3 track) with mkv setting.

---

### Post by slooksterpsv on 2010-09-15
> **prabath_fun said:**
> Hi JohnAStebbins,
   I have verified libdvdread and libdvdnav installation in synaptic package manager. It shows that, it is installed with green color. But, I am not seeing libdvdcss... I just checked in ubuntu packages website for same, I am not getting libdvdcss. Is it collection of above said to packages???
   I am not under standing "show us a directory listing of what is present there?". Is it do you mean directory structure / tree!! Or some sort of log file. If log file, Kindly let me know where can I find. 

If it is tree, after mounting, it will be /media/Madrasa..<Dvd name>
inside this I will be having one folder called video_ts and inside this folder will be having .vob files and supported files...

  Further, just I gave a try with windows version of Handbrake in XP, which runs inside virtualbox. There I found no problem. I can able to select second audio track (DTS track) or first audio track (AC3 track) with mkv setting.

To install libdvdcss do this.

Click Applications -> Accessories -> Terminal
And type in the following commands:
```

sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

```

That will install libdvdcss - [ Reference: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) ]

---

### Post by prabath_fun on 2010-09-15
Hi all,
   Thanks...
   I have done 
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.s
also...
No improvement...

Now log is 
[19:20:50] gtkgui: HandBrake svn3506 (2010090101) - Linux i686 - [http://handbrake.fr](http://handbrake.fr)
[19:20:51] hb_init: checking cpu count
[19:20:51] hb_init: starting libhb thread
[19:20:51] hb_init: checking cpu count
[19:20:51] hb_init: starting libhb thread
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Using libdvdcss version 1.2.10 for DVD access
[19:20:55] hb_scan: path=/dev/sr0, title_index=0
[19:20:55] scan: trying to open with libdvdread
[19:20:55] dvd: Region mask 0xff
[19:20:55] dvd: Warning, DVD device has no region set
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[19:20:55] dvd: not a dvd - trying as a stream/file instead
[19:20:55] file is MPEG Program Stream
[19:21:00] add_audio_to_title: added AC3 audio stream 0x89bd
[19:21:00] add_audio_to_title: added AC3 audio stream 0x80bd
[19:21:00] scan: decoding previews for title 1
[19:21:00] scan: audio 0x80bd: AC-3, rate=48000Hz, bitrate=448000 Unknown (AC3) (5.1 ch)
[19:21:04] scan: 10 previews, 720x480, 29.970 fps, autocrop = 54/52/0/0, aspect 1.78:1, PAR 32:27
[19:21:04] scan: removing audio 0x89bd because no bitrate found
[19:21:04] scan: title (0) job->width:720, job->height:320
[19:21:04] libhb: scan thread found 1 valid title(s)
libdvdread: Using libdvdcss version 1.2.10 for DVD access


Please guide me....

---

### Post by JohnAStebbins on 2010-09-15
> **prabath_fun said:**
> 
If it is tree, after mounting, it will be /media/Madrasa..<Dvd name>
inside this I will be having one folder called video_ts and inside this folder will be having .vob files and supported files...

Yes, I want to see the complete contents of the VIDEO_TS folder because it is failing to open a key file in that folder.
```

libdvdnavVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed

```

---

### Post by prabath_fun on 2010-09-16
Hi JohnAStebbins,
  Below is the complete content of DVD...

.Mad...../
.|-- AUDIO_TS
.`-- VIDEO_TS
.....|-- VIDEO_TS.BUP
.....|-- VIDEO_TS.IFO
.....|-- VTS_01_0.BUP
.....|-- VTS_01_0.IFO
.....|-- VTS_01_0.VOB
.....|-- VTS_01_1.VOB
.....|-- VTS_02_0.BUP
.....|-- VTS_02_0.IFO
.....|-- VTS_02_0.VOB
.....|-- VTS_02_1.VOB
.....|-- VTS_03_0.BUP
.....|-- VTS_03_0.IFO
.....|-- VTS_03_0.VOB
.....|-- VTS_03_1.VOB
.....|-- VTS_04_0.BUP
.....|-- VTS_04_0.IFO
.....|-- VTS_04_0.VOB
.....|-- VTS_04_1.VOB
.....|-- VTS_04_2.VOB
.....|-- VTS_04_3.VOB
.....|-- VTS_04_4.VOB
.....`-- VTS_04_5.VOB


Hope there is no problem with this. Because, Windows version of Handbrake does conversion without any error. Also, I tried another DVD in Ubuntu as well, same problem faced...

Further, I tried another DVD in windows, I got audio sync problem that video leading the audio. 
 

Since, I got similar problem in Avidemux, I jumped to Handbrake... But, while comparing with Avidemux, one of the DVD conversion was happened without any problem....

---

### Post by JohnAStebbins on 2010-09-17
Is the windows encode being done on the same machine as linux.  i.e. Are you dual booting?  I'm beginning to think there is something wrong with your dvd drive.  The files are all there. But it is failing to read some of them.

---

### Post by serverfarm on 2010-09-17
I'm trying to remember, I believe VLC lets you open a folder of files to transcode.  Also, they include all their own codecs!

---

### Post by prabath_fun on 2010-09-19
Hi JohnAStebbins,
  No, I am not dual booting. I use virtual PC in Ubuntu to boot windows and I can able to encode without any problem. 
   Hope there will be no problem with my DVD drive. Because, I use to write DVD with same writer without any problem and play the movies. 
   Is it possible guide me how to upgrade the firmware of DVD write in Ubuntu? I will give a try....

Further, serverfarm, My main aim is to convert my DVD with second sound track (basically DTS audio) to MP4 or mkv file to share to my friends and to save the movies in my external harddisk..... I could not able to do with VLC....

---

### Post by prabath_fun on 2010-09-19
Hi JohnAStebbins,
  I have dual booted my PC and tried to encode the movie using Handbrake. It end up with audio sync problem. That is, audio was played ahead of video.
  Further, I tried by copying DVD file to HDD and tried to encode from there. In this case, Handbrake was not detecting / showing different tracks..

  If I get out from audio sync problem, I will be happier. Else, I need to copy DVD files to my external HDD as is.... But, sharing to my friend is difficult....

---

