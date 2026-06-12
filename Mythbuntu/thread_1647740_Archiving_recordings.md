---
title: "Archiving recordings"
date: 2010-12-17
forum: Mythbuntu
---

### Post by GuiGuy on 2010-12-17
Hi
It's taken nearly two weeks (it's linux afterall), but the crashed backend/ frontend has been rebuilt after a fried motherboard event. It's running on some pretty smart hardware, including a quad core processor, 4G RAM etc. EVerything is pretty much sorted.

Except the archiving of recordings;

nuvexport is no longer around AFAIK, mythexport just won't work for me and seems too complicated to configure, which leaves mythnuv2mkv, which works. Sort of. It is just too sslloowwwwww.......... despite the hardware, it processes files at about 1 frame a second, so to archive  an hour of video will probably take a month or so.

Are there any other options for archiving, or can the mythnuv2mkv script be coaxed to perform better? I mean, handbrake converts mpg to mkv at a rate of 80 to 100 fps on this box, so the hardware is certainly capable.

Thanks

---

### Post by ian dobson on 2010-12-19
Hi,

Why not just hack a script together using mythnuv2mkv as an example but using handbrake to transcode.

I know thats not a great deal of help but......


Regards
Ian Dobson

---

### Post by PhilWig on 2010-12-19
You don't say which version of Myth you are using.  These were the steps I took to get DVD writing working in Mythbuntu 9.04:

1.  needs a temporary work directory with bags of space.  Create one:
         cd /var/lib/mythtv
         sudo mkdir work
         sudo chmod 777 work

    Insert name of this directory /var/lib/mythtv/work in frontend setup, archive section.

2.  Error messages:
     failed while running mytharchivehelper to get stream information from <mpeg2 file> and various other failures.
     "failed while running ffmpeg to re-encode video" 
         
    NB logs are in work directory above.
    Problem caused by presence of file ~/.ICEauthority (why?).
    See  [http://ubuntuforums.org/showthread.php?t=610856&page=2](http://ubuntuforums.org/showthread.php?t=610856&page=2)
    Apply change as suggested by racmar, 16 Jun 09 on para 3
              sudo mv /usr/bin/mythtranscode /usr/bin/mythtranscode.real
              sudo gedit /usr/bin/mythtranscode
                 - insert code as suggested but change username and put in file existence checks.
              sudo chmod +x /usr/bin/mythtranscode

3.  Two types of errors, one with failing to close tray in growisof after writing, the other is transcode errors.
     Needs system updates.
   
   See:
   [http://ubuntuforums.org/showthread.php?t=986534](http://ubuntuforums.org/showthread.php?t=986534)   Confirmed in:
   [http://www.gossamer-threads.com/lists/mythtv/users/378092](http://www.gossamer-threads.com/lists/mythtv/users/378092)
         but more importantly:
   [http://ubuntuforums.org/showthread.php?t=1108565](http://ubuntuforums.org/showthread.php?t=1108565) which suggests:

          sudo apt-get purge ffmpeg
          sudo apt-get update
          sudo apt-get install libavcodec-unstripped-51 libavdevice-unstripped-52 libavformat-unstripped-52 libavutil-unstripped-49 libpostproc-unstripped-51 libswscale-unstripped-0 ffmpeg

          NOTE:  libavcodec-unstripped-51 is not found, so omitted it without any penalty.

4. Finally,

       Restore the archive menu (if missing) by ticking box in Myth control centre > applications and plugins.

HTH
Phil

---

### Post by laffinet on 2010-12-20
> **GuiGuy said:**
> mythnuv2mkv, which works. Sort of. It is just too sslloowwwwww.......... despite the hardware, it processes files at about 1 frame a second, so to archive  an hour of video will probably take a month or so.

I hope your exaggerating. I use mythnuv2mkv a lot. Probably transcode 1 recording per day, with 2 pass encoding.
yes, does take some time, but now what you're describing. This is on a pretty weak 2 core processor.

---

### Post by ZedThou on 2010-12-21
I've spent a bit of time trying to stream ATSC 1080i and 720p transcoded video from my Atom/ION combined front/backend to my phone.  I ended up with a custom mythexport profile which uses mencoder to do it in about 2/3 real-time, compared with 1/4 real-time using the default ffmpeg mythexport transcoding. Keep in mind, this is on an Atom, so your hardware is easily up to the task. If you find that you just cannot get mythexport working then this won't be of any use, but if you want details I'd be happy to share.

---

### Post by GuiGuy on 2010-12-21
> **laffinet said:**
> I hope your exaggerating. I use mythnuv2mkv a lot. Probably transcode 1 recording per day, with 2 pass encoding.
yes, does take some time, but now what you're describing. This is on a pretty weak 2 core processor.

No, I am not exaggerating. But the slow performance only occurs when mythnuv2mkv is handling the job. If I use mencoder or ffmpeg or handbrake directly performance is right up there for the hardware I have.

The other thing I notice is that the resulting files are huge; bigger than the originals. 

It has to be something the script's doing. But I have downloaded the latest, re-installed and still get the same output.

---

### Post by GuiGuy on 2010-12-21
arghhhh... 
I've downoaded and re-installed the script. Now I'm logging this

> 2010-12-21 16:58:57.868 Enabled verbose msgs: important
2010-12-21 16:58:59.867 New DB connection, total: 2
2010-12-21 16:59:00.008 Using protocol version 63
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
File not found: '/var/tmp/mythnuv2mkv8304/vidout'
Failed to open /var/tmp/mythnuv2mkv8304/vidout.
Cannot open file/device.

Exiting...
21/12,16:59 [8304] ERROR Skipping /var/lib/mythtv/recordings/1005_20101218203900.mpg. Problem with 1st video pass of 2.
------------------------------------------

 /var/tmp/mythnuv2mkv8304/vidout exists. It belongs to root. Permissions issue?

---

### Post by GuiGuy on 2010-12-21
> **PhilWig said:**
> You don't say which version of Myth you are using.  

Since it's new hardware the latest made sense; MythBuntu Maverick/ mythtv 0.24

---

### Post by laffinet on 2010-12-21
Can you post the line you are using to call the script?

And the top part of the script where all the general variables are set?

---

### Post by GuiGuy on 2010-12-22
> **laffinet said:**
> Can you post the line you are using to call the script?


See below. It is unchanged from what I used to use with good results prior to the rebuild. 

[I]/usr/bin/mythnuv2mkv.sh --jobid=%JOBID% --quality=480 --deinterlace=ON --copydir=/mnt/multimedia/archived --chanid=%CHANID% --starttime=%STARTTIME%
[/I]

*/mnt/multimedia/archived* is, of course, a valid secondary HDD storage device. NOte that it makes no difference what I set --quality to. The result is always the same; slow and a huge file., when it works.
> 
And the top part of the script where all the general variables are set?

I believe so:

> 
#!/bin/bash
# @(#)$Header: /home/mythtv/mythtvrep/scripts/mythnuv2mkv.sh,v 1.61 2010/10/09 21:06:19 mythtv Exp $
# Auric 2007/07/10 [http://web.aanet.com.au/auric/](http://web.aanet.com.au/auric/)
# Default aspect for Myth Recording mpg files. It will try to work it out but if it can't will use this.
readonly DEFAULTMPEG2ASPECT="16:9" # 4:3 or 16:9
# Log directory
readonly LOGBASEDIR="/var/tmp" # Don't use a directory with spaces in it's name
# Number of errors reported by mplayer allowed in the transcoded file
readonly MPLAYER_ERROR_COUNT="8"
# Path to your mysql.txt file
readonly MYSQLTXT="/home/myusername/.mythtv/mysql.txt"
# What to separate Title SeasonEpisode SubTitle with
readonly SEP=","
# Chapter marks every X minutes
CHAPTERDURATION=0
# Crop input
CROP="ON" # ON | OFF, can also change with --crop argument
CROPSIZE=8
# Delete recording after successful transcode. Only for transcode out of MythRecording. (Actually just sets to high priority autoexpire.)
DELETEREC="OFF" # ON | OFF, can also change with --deleterec argument
# Include denoise filter
DENOISE="OFF" # ON | OFF, can also change with --denoise argument
# Include deblock filter
DEBLOCK="OFF" # ON | OFF, can also change with --deblock argument
# Include deinterlace filter.
# SOURCENAME is ON for that source. Can have multiple. e.g. DEINTERLACE="Cabel,FTA1"
DEINTERLACE="ON" # ON | OFF | SOURCENAME,SOURCENAME can also change with --deinterlace argument.
# Include inverse Telecine filter (Experimental. Can someone from NTSC/ATSC land try this?).
# invtelecine filter is never added if deinterlace has been added.
INVTELECINE="OFF" # ON | OFF, can also change with --invtelecine argument.
# number passes
PASS="two" # one | two, can also change with --pass argument
# number of threads. Only used by lavc and xvid (x.264 auto calculates threads)
THREADS=1
# avi encoder lavc or xvid
AVIVID="lavc" # lavc | xvid, can also change with --contype=avi,xvid argument
# container
CONTYPE="mkv" # mkv | mp4 | avi, can also change with --contype argument or name of script.
# mkv audio encoder aac or ogg
MKVAUD="aac" # aac | ogg, can also change with --contype=mkv,ogg argument
# add your own filters if you want
POSTVIDFILTERS=""	#must include , at end
ENDVIDFILTERS=""	#must include , at end
# Disable some output checks. Can have multiple. e.g. OUTPUTCHECKS="NOSIZERATIO,NOSCAN"
OUTPUTCHECKS="" # NOSIZE,NOVIDINFO,NOSIZERATIO,NOFRAMECOUNT,NOSCAN can also change with --outputchecks argument.
# Boinc passwd, if you run boinc and want to disable it during transcode
readonly BOINCPASSWD=""
# Use mediainfo if available to identify video properties.
USEMEDIAINFO="TRUE" # TRUE or FALSE
#
PATH=~mythtv/bin:${HOME}/bin:$PATH:/usr/bin


Thanks for your interest.

Cheers

---

### Post by laffinet on 2010-12-23
Can't really see anything wrong there. Only difference is that you're not deleting the original recording.
Below is mine.

For reference, mine takes about half and hour to an hour to transcode a 30min recording. Resulting file is approx. 250MB with a quality setting of 480.

```
#!/bin/bash
# @(#)$Header: /home/mythtv/mythtvrep/scripts/mythnuv2mkv.sh,v 1.61 2010/10/09 21:06:19 mythtv Exp $
# Auric 2007/07/10 http://web.aanet.com.au/auric/
##########################################################################################################
#
# Convert MythRecording & MythVideo nuv or mpg files to mkv mp4 or avi.
#
######### Vars you may want to set for your environment ######################################################
# Default aspect for Myth Recording mpg files. It will try to work it out but if it can't will use this.
readonly DEFAULTMPEG2ASPECT="16:9" # 4:3 or 16:9
# Log directory
readonly LOGBASEDIR="/var/tmp" # Don't use a directory with spaces in it's name
# Number of errors reported by mplayer allowed in the transcoded file
readonly MPLAYER_ERROR_COUNT="30"
# Path to your mysql.txt file
readonly MYSQLTXT="/home/laffi/.mythtv/mysql.txt"
# What to separate Title SeasonEpisode SubTitle with
readonly SEP="-"
# Chapter marks every X minutes
CHAPTERDURATION=0
# Crop input
CROP="ON" # ON | OFF, can also change with --crop argument
CROPSIZE=8
# Delete recording after successful transcode. Only for transcode out of MythRecording. (Actually just sets to high priority autoexpire.)
DELETEREC="OFF" # ON | OFF, can also change with --deleterec argument
# Include denoise filter
DENOISE="OFF" # ON | OFF, can also change with --denoise argument
# Include deblock filter
DEBLOCK="OFF" # ON | OFF, can also change with --deblock argument
# Include deinterlace filter.
# SOURCENAME is ON for that source. Can have multiple. e.g. DEINTERLACE="Cabel,FTA1"
DEINTERLACE="ON" # ON | OFF | SOURCENAME,SOURCENAME can also change with --deinterlace argument.
# Include inverse Telecine filter (Experimental. Can someone from NTSC/ATSC land try this?).
# invtelecine filter is never added if deinterlace has been added.
INVTELECINE="OFF" # ON | OFF, can also change with --invtelecine argument.
# number passes
PASS="two" # one | two, can also change with --pass argument
# number of threads. Only used by lavc and xvid (x.264 auto calculates threads)
THREADS=1
# avi encoder lavc or xvid
AVIVID="lavc" # lavc | xvid, can also change with --contype=avi,xvid argument
# container
CONTYPE="mkv" # mkv | mp4 | avi, can also change with --contype argument or name of script.
# mkv audio encoder aac or ogg
MKVAUD="aac" # aac | ogg, can also change with --contype=mkv,ogg argument
# add your own filters if you want
POSTVIDFILTERS=""    #must include , at end
ENDVIDFILTERS=""    #must include , at end
# Disable some output checks. Can have multiple. e.g. OUTPUTCHECKS="NOSIZERATIO,NOSCAN"
OUTPUTCHECKS="" # NOSIZE,NOVIDINFO,NOSIZERATIO,NOFRAMECOUNT,NOSCAN can also change with --outputchecks argument.
# Boinc passwd, if you run boinc and want to disable it during transcode
readonly BOINCPASSWD=""
# Use mediainfo if available to identify video properties.
USEMEDIAINFO="TRUE" # TRUE or FALSE
#
PATH=~mythtv/bin:${HOME}/bin:$PATH:/usr/local/bin
```

---

### Post by GuiGuy on 2010-12-24
Ok, I am going crazy. 

I have a 2.2G mythtv (mpg) recording. I ran mythnuv2mkv afrom a command line. I've used ogg for audio processing here, but the results with faac are very similar.

Here's the output, which I have truncated in parts:

> ~/nuvexport$ mythnuv2mkv.sh --contype=mkv --quality=high --deleterec=OFF --copydir=/mnt/multimedia/archived --chanid=1002 --starttime=20101225085255 
25/12,09:26 [5223] INFO Changed to mkv,ogg.
25/12,09:26 [5223] INFO Changed to high quality.
25/12,09:26 [5223] INFO Delete Recording set to OFF.
25/12,09:26 [5223] INFO Video will be located in /mnt/multimedia/archived.
25/12,09:26 [5223] INFO 1002 20101225085255 matches rage	 (/var/lib/mythtv/livetv//1002_20101225085255.mpg)
25/12,09:26 [5223] INFO 576i or 576p 720x576 NA 16:9 (Found in Channel) 25.000 FPS Audio Rate 48000 Channels 2 ASamplingRate NA
25/12,09:26 [5223] INFO Crop to 704:560:8:8. Scale to 656x368.
25/12,09:26 [5223] INFO Deinterlace filter added.
25/12,09:26 [5223] INFO If progressive this is wrong use --deinterlace=NO.
25/12,09:26 [5223] INFO Audio Encoder: oggenc  --raw-chan=2 --raw-rate=48000 --quality=6 -o /var/lib/mythtv/livetv//1002_20101225085255_audio.ogg /var/tmp/mythnuv2mkv5223/audout.
25/12,09:26 [5223] START Starting ogg audio trans of /var/lib/mythtv/livetv//1002_20101225085255.mpg. quality 6.
2010-12-25 09:26:53.331 Using runtime prefix = /usr
2010-12-25 09:26:53.331 Using configuration directory = /home/pierre/.mythtv
2010-12-25 09:26:53.332 Empty LocalHostName.
2010-12-25 09:26:53.440 New DB connection, total: 1
2010-12-25 09:26:53.457 Closing DB connection named 'DBManager0'
2010-12-25 09:26:53.464 Enabled verbose msgs: important
2010-12-25 09:26:53.580 Using protocol version 63
2010-12-25 09:26:54.033 mythtranscode: 0% Completed @ 0 fps.
WARNING: Raw channel count specified for non-raw data. Assuming input is raw.
Encoding "/var/tmp/mythnuv2mkv5223/audout" to 
         "/var/lib/mythtv/livetv//1002_20101225085255_audio.ogg" 
at quality 6.00
	Encoding [ 0m10s so far] \ 2010-12-25 09:27:14.045 mythtranscode: 3% Completed @ 89.9146 fps.
	Encoding [ 0m30s so far] \ 2010-12-25 09:27:34.054 mythtranscode: 10% Completed @ 132.108 fps.
	Encoding [ 0m50s so far] - 2010-12-25 09:27:54.065 mythtranscode: 17% Completed @ 145.689 fps.
	Encoding [ 1m10s so far] \ 2010-12-25 09:28:14.070 mythtranscode: 23% Completed @ 150.705 fps.
	Encoding [ 1m30s so far] / 2010-12-25 09:28:34.075 mythtranscode: 30% Completed @ 153.315 fps.
	Encoding [ 1m50s so far] | 2010-12-25 09:28:54.078 mythtranscode: 36% Completed @ 155.324 fps.
	Encoding [ 2m10s so far] | 2010-12-25 09:29:14.084 mythtranscode: 44% Completed @ 160.626 fps.
	Encoding [ 2m15s so far] \ 2010-12-25 09:29:18.589 AFD Error: Unknown audio decoding error
	Encoding [ 2m30s so far] | 2010-12-25 09:29:34.097 mythtranscode: 51% Completed @ 165.227 fps.
	Encoding [ 2m50s so far] \ 2010-12-25 09:29:54.103 mythtranscode: 58% Completed @ 166.251 fps.
	Encoding [ 3m10s so far] / 2010-12-25 09:30:14.107 mythtranscode: 66% Completed @ 168.062 fps.
	Encoding [ 3m20s so far] \ 2010-12-25 09:30:24.185 AFD Error: Unknown audio decoding error
2010-12-25 09:30:24.188 AFD Error: Unknown audio decoding error
	Encoding [ 3m20s so far] | 2010-12-25 09:30:24.334 AFD Error: Unknown audio decoding error
	Encoding [ 3m21s so far] - 2010-12-25 09:30:24.531 AFD Error: Unknown audio decoding error
2010-12-25 09:30:24.539 AFD Error: Unknown audio decoding error
	Encoding [ 3m30s so far] | 2010-12-25 09:30:34.118 mythtranscode: 72% Completed @ 168.57 fps.
	Encoding [ 3m50s so far] \ 2010-12-25 09:30:54.133 mythtranscode: 79% Completed @ 168.558 fps.
	Encoding [ 4m10s so far] / 2010-12-25 09:31:14.140 mythtranscode: 86% Completed @ 169.068 fps.
	Encoding [ 4m30s so far] / 2010-12-25 09:31:34.146 mythtranscode: 94% Completed @ 170.959 fps.
	Encoding [ 4m50s so far] / 2010-12-25 09:31:54.150 mythtranscode: 100% Completed @ 170.776 fps.
	Encoding [ 5m10s so far] | 2010-12-25 09:32:14.152 mythtranscode: 107% Completed @ 170.602 fps.
	Encoding [ 5m30s so far] | 2010-12-25 09:32:34.159 mythtranscode: 114% Completed @ 171.233 fps.
	Encoding [ 5m50s so far] \ 2010-12-25 09:32:54.346 mythtranscode: 117% Completed @ 166.294 fps.
	Encoding [ 6m10s so far] | 2010-12-25 09:33:14.457 mythtranscode: 118% Completed @ 158.828 fps.
	Encoding [ 6m30s so far] - 2010-12-25 09:33:34.488 mythtranscode: 119% Completed @ 152.132 fps.
	Encoding [ 6m51s so far] \ 2010-12-25 09:33:54.509 mythtranscode: 120% Completed @ 146.08 fps.
	Encoding [ 7m11s so far] - 2010-12-25 09:34:14.568 mythtranscode: 121% Completed @ 140.572 fps.
	Encoding [ 7m30s so far] \ 2010-12-25 09:34:34.672 mythtranscode: 122% Completed @ 135.523 fps.
	Encoding [ 7m51s so far] - 2010-12-25 09:34:54.729 mythtranscode: 123% Completed @ 130.91 fps.
	Encoding [ 8m11s so far] \ 2010-12-25 09:35:14.775 mythtranscode: 124% Completed @ 126.676 fps.
	Encoding [ 8m31s so far] | 2010-12-25 09:35:34.778 mythtranscode: 125% Completed @ 122.769 fps.
	Encoding [ 8m50s so far] - 2010-12-25 09:35:54.827 mythtranscode: 126% Completed @ 119.144 fps.
	Encoding [ 9m11s so far] \ 2010-12-25 09:36:14.879 mythtranscode: 127% Completed @ 115.777 fps.
	Encoding [ 9m31s so far] \ 2010-12-25 09:36:34.882 mythtranscode: 128% Completed @ 112.654 fps.
	Encoding [ 9m51s so far] \ 2010-12-25 09:36:54.940 mythtranscode: 129% Completed @ 109.725 fps.
	Encoding [10m11s so far] - 2010-12-25 09:37:14.952 mythtranscode: 130% Completed @ 106.995 fps.
	Encoding [10m31s so far] - 2010-12-25 09:37:35.049 mythtranscode: 131% Completed @ 104.425 fps.
	Encoding [10m51s so far] \ 2010-12-25 09:37:55.097 mythtranscode: 132% Completed @ 102.015 fps.
	Encoding [11m11s so far] | 2010-12-25 09:38:15.263 mythtranscode: 133% Completed @ 99.7347 fps.
	Encoding [11m31s so far] | 2010-12-25 09:38:35.269 mythtranscode: 134% Completed @ 97.6038 fps.
	Encoding [11m51s so far] | 2010-12-25 09:38:55.391 mythtranscode: 135% Completed @ 95.5799 fps.
	Encoding [12m11s so far] / 2010-12-25 09:39:15.452 mythtranscode: 136% Completed @ 93.6681 fps.
	Encoding [12m31s so far] | 2010-12-25 09:39:35.458 mythtranscode: 137% Completed @ 91.8651 fps.
	Encoding [12m51s so far] \ 2010-12-25 09:39:55.491 mythtranscode: 138% Completed @ 90.1499 fps.
	Encoding [13m12s so far] / 2010-12-25 09:40:15.653 mythtranscode: 139% Completed @ 88.5112 fps.
	Encoding [13m32s so far] \ 2010-12-25 09:40:35.669 mythtranscode: 140% Completed @ 86.966 fps.
	Encoding [13m51s so far] - 2010-12-25 09:40:55.796 mythtranscode: 141% Completed @ 85.483 fps.
	Encoding [14m12s so far] / 2010-12-25 09:41:15.804 mythtranscode: 142% Completed @ 84.082 fps.
	Encoding [14m32s so far] | 2010-12-25 09:41:35.977 mythtranscode: 143% Completed @ 82.728 fps.
	Encoding [14m52s so far] / 2010-12-25 09:41:56.169 mythtranscode: 144% Completed @ 81.435 fps.
	Encoding [15m12s so far] / 2010-12-25 09:42:16.181 mythtranscode: 145% Completed @ 80.211 fps.
	Encoding [15m32s so far] | 2010-12-25 09:42:36.378 mythtranscode: 146% Completed @ 79.0257 fps.
	Encoding [15m52s so far] - 2010-12-25 09:42:56.387 mythtranscode: 147% Completed @ 77.9042 fps.
	Encoding [16m12s so far] / 2010-12-25 09:43:16.527 mythtranscode: 148% Completed @ 76.8193 fps.
	Encoding [16m32s so far] \ 2010-12-25 09:43:36.533 mythtranscode: 149% Completed @ 75.786 fps.
	Encoding [16m52s so far] / 2010-12-25 09:43:56.545 mythtranscode: 150% Completed @ 74.7908 fps.
	Encoding [17m12s so far] \ 2010-12-25 09:44:16.551 mythtranscode: 151% Completed @ 73.8371 fps.
	Encoding [17m32s so far] \ 2010-12-25 09:44:36.557 mythtranscode: 152% Completed @ 72.9193 fps.
	Encoding [17m53s so far] - 2010-12-25 09:44:56.579 mythtranscode: 153% Completed @ 72.0307 fps.
	Encoding [18m12s so far] - 2010-12-25 09:45:16.611 mythtranscode: 154% Completed @ 71.1755 fps.
	Encoding [18m33s so far] | 2010-12-25 09:45:36.768 mythtranscode: 155% Completed @ 70.3465 fps.
	Encoding [18m52s so far] - 2010-12-25 09:45:56.811 mythtranscode: 156% Completed @ 69.5503 fps.
	Encoding [19m13s so far] \ 2010-12-25 09:46:16.932 mythtranscode: 157% Completed @ 68.7803 fps.
	Encoding [19m33s so far] / 2010-12-25 09:46:37.098 mythtranscode: 158% Completed @ 68.0339 fps.
	Encoding [19m53s so far] - 2010-12-25 09:46:57.114 mythtranscode: 159% Completed @ 67.3184 fps.
	Encoding [20m13s so far] \ 2010-12-25 09:47:17.123 mythtranscode: 160% Completed @ 66.6276 fps.
	Encoding [20m33s so far] / 2010-12-25 09:47:37.250 mythtranscode: 160% Completed @ 65.9527 fps.
	Encoding [20m53s so far] - 2010-12-25 09:47:57.345 mythtranscode: 161% Completed @ 65.3002 fps.
	Encoding [21m13s so far] | 2010-12-25 09:48:17.466 mythtranscode: 162% Completed @ 64.6692 fps.
	Encoding [21m25s so far] / 2010-12-25 09:48:31.239 AFD Error: Unknown audio decoding error
83307+70583 records in
83307+70583 records out
51811176960 bytes (52 GB) copied, 1287.97 s, 40.2 MB/s
	Encoding [21m27s so far] - 

Done encoding file "/var/lib/mythtv/livetv//1002_20101225085255_audio.ogg"

	File length:  55m 31.0s
	Elapsed time: 21m 28.0s
	Rate:         2.5866
	Average bitrate: 173.9 kb/s

25/12,09:48 [5223] INFO Video Encoder: mencoder -idx 			/var/tmp/mythnuv2mkv5223/vidout -demuxer rawvideo -rawvideo w=720:h=576:fps=25.000 			-audiofile /var/tmp/mythnuv2mkv5223/audout -audio-demuxer rawaudio -rawaudio rate=48000:channels=2 			-ovc x264 -x264encopts level_idc=31:bframes=3:force_cfr:b_pyramid=normal:weight_b:threads=auto:direct_pred=auto:subq=6:frameref=5:partitions=all:8x8dct:mixed_refs:me=umh:trellis=1:bitrate=902:pass=1:turbo -passlogfile /var/tmp/mythnuv2mkv5223/2pass.log 			-oac copy 			-vf pp=fd,softskip,crop=704:560:8:8,scale=656:368,harddup -sws 7  			-of rawvideo -o /dev/null.
25/12,09:48 [5223] START Starting h264 1st video pass trans of /var/lib/mythtv/livetv//1002_20101225085255.mpg. vbr 902 abr .
2010-12-25 09:48:42.212 Using runtime prefix = /usr
2010-12-25 09:48:42.212 Using configuration directory = /home/<user>/.mythtv
2010-12-25 09:48:42.212 Empty LocalHostName.
2010-12-25 09:48:42.372 New DB connection, total: 1
2010-12-25 09:48:42.379 Closing DB connection named 'DBManager0'
2010-12-25 09:48:42.439 Enabled verbose msgs: important
2010-12-25 09:48:42.610 Using protocol version 63
2010-12-25 09:48:45.074 mythtranscode: 0% Completed @ 0 fps.
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
Option x264encopts: turbo option is deprecated; use slow_firstpass to disable turbo
success: format: 0  data: 0x0 - 0x0
rawvideo file format detected.
rawaudio file format detected.
[V] filefmt:65536  fourcc:0x30323449  size:720x576  fps:25.000  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=656 h=368]
Opening video filter: [crop w=704 h=560 x=8 y=8]
Crop: 704 x 560, 8 ; 8
Opening video filter: [softskip]
Opening video filter: [pp=fd]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
[PP] Using external postprocessing filter, max q = 6.
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x18951c0]Gaussian scaler, from yuv420p to yuv420p using MMX2
x264 [info]: using SAR=368/521
x264 [info]: using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
x264 [info]: profile Main, level 3.1
Selected video codec: [rawi420] vfm: raw (RAW I420)
==========================================================================
audiocodec: framecopy (format=1 chans=2 rate=48000 bits=16 B/s=192000 sample-4)
2010-12-25 09:49:05.079 mythtranscode: 0% Completed @ 37.6274 fps.8939:1536]
2010-12-25 09:49:25.336 mythtranscode: 2% Completed @ 44.1779 fps.9704:1536]
2010-12-25 09:49:45.587 mythtranscode: 3% Completed @ 47.9841 fps.8931:1536]
2010-12-25 09:50:05.595 mythtranscode: 4% Completed @ 48.6166 fps.9158:1536]
2010-12-25 09:50:25.597 mythtranscode: 5% Completed @ 49.7066 fps.8901:1536]
2010-12-25 09:50:45.604 mythtranscode: 7% Completed @ 50.1838 fps.8892:1536]
2010-12-25 09:51:05.767 mythtranscode: 8% Completed @ 50.4904 fps.8515:1536]
2010-12-25 09:51:25.975 mythtranscode: 9% Completed @ 49.5873 fps.8747:1536]
2010-12-25 09:51:46.144 mythtranscode: 10% Completed @ 49.1725 fps.911:1536]
2010-12-25 09:52:06.296 mythtranscode: 11% Completed @ 48.8448 fps.057:1536]
2010-12-25 09:52:26.303 mythtranscode: 12% Completed @ 48.8799 fps.090:1536]
2010-12-25 09:52:46.308 mythtranscode: 14% Completed @ 48.5324 fps.290:1536]
2010-12-25 09:53:06.720 mythtranscode: 15% Completed @ 48.7439 fps.244:1536]
2010-12-25 09:53:26.729 mythtranscode: 16% Completed @ 48.6257 fps.347:1536]
2010-12-25 09:53:47.047 mythtranscode: 17% Completed @ 48.1125 fps.547:1536]
2010-12-25 09:54:07.054 mythtranscode: 18% Completed @ 47.8963 fps.653:1536]
2010-12-25 09:54:27.078 mythtranscode: 19% Completed @ 47.671 fps.9816:1536]
2010-12-25 09:54:47.081 mythtranscode: 20% Completed @ 47.4982 fps.914:1536]
2010-12-25 09:55:07.087 mythtranscode: 21% Completed @ 47.2253 fps.0034:1536]
2010-12-25 09:55:27.344 mythtranscode: 22% Completed @ 47.1168 fps.0037:1536]
2010-12-25 09:55:47.600 mythtranscode: 23% Completed @ 47.1655 fps.999:1536]]
2010-12-25 09:56:07.679 mythtranscode: 25% Completed @ 47.85 fps.[9715:1536]]
2010-12-25 09:56:27.689 mythtranscode: 27% Completed @ 49.1287 fps.223:1536]
2010-12-25 09:56:37.228 AFD Error: Unknown audio decoding error0 [9033:1536]
2010-12-25 09:56:48.003 mythtranscode: 28% Completed @ 50.0149 fps.874:1536]
2010-12-25 09:57:08.039 mythtranscode: 30% Completed @ 50.8557 fps.560:1536]
2010-12-25 09:57:28.333 mythtranscode: 31% Completed @ 50.7944 fps.611:1536]
2010-12-25 09:57:48.992 mythtranscode: 33% Completed @ 50.6577 fps.594:1536]
2010-12-25 09:58:09.006 mythtranscode: 34% Completed @ 50.3671 fps.643:1536]
2010-12-25 09:58:29.305 mythtranscode: 35% Completed @ 50.3288 fps.638:1536]
2010-12-25 09:58:49.538 mythtranscode: 36% Completed @ 50.1331 fps.686:1536]
2010-12-25 09:59:09.870 mythtranscode: 37% Completed @ 50.0222 fps.690:1536]
2010-12-25 09:59:30.042 mythtranscode: 38% Completed @ 50.1244 fps.623:1536]
2010-12-25 09:59:50.057 mythtranscode: 40% Completed @ 50.3075 fps.485:1536]
2010-12-25 10:00:10.060 mythtranscode: 41% Completed @ 50.4414 fps.377:1536]
2010-12-25 10:00:27.136 AFD Error: Unknown audio decoding error0 [8294:1536]
2010-12-25 10:00:27.141 AFD Error: Unknown audio decoding error
2010-12-25 10:00:27.612 AFD Error: Unknown audio decoding error0 [8291:1536]
2010-12-25 10:00:28.117 AFD Error: Unknown audio decoding error0 [8288:1536]
2010-12-25 10:00:28.133 AFD Error: Unknown audio decoding error0 [8288:1536]
2010-12-25 10:00:30.294 mythtranscode: 42% Completed @ 50.4859 fps.278:1536]
2010-12-25 10:00:50.297 mythtranscode: 43% Completed @ 50.5247 fps.212:1536]
2010-12-25 10:01:10.623 mythtranscode: 45% Completed @ 50.5046 fps.162:1536]
2010-12-25 10:01:30.827 mythtranscode: 46% Completed @ 50.5759 fps.121:1536]
2010-12-25 10:01:51.103 mythtranscode: 47% Completed @ 50.5435 fps.091:1536]
2010-12-25 10:02:11.334 mythtranscode: 48% Completed @ 50.5155 fps.093:1536]
2010-12-25 10:02:31.341 mythtranscode: 50% Completed @ 50.5171 fps.082:1536]
2010-12-25 10:02:51.588 mythtranscode: 51% Completed @ 50.6237 fps.043:1536]
2010-12-25 10:03:11.824 mythtranscode: 52% Completed @ 50.8262 fps.969:1536]
2010-12-25 10:03:31.827 mythtranscode: 54% Completed @ 51.0668 fps.876:1536]
2010-12-25 10:03:51.878 mythtranscode: 55% Completed @ 51.3382 fps.781:1536]
2010-12-25 10:04:12.122 mythtranscode: 57% Completed @ 51.7272 fps.656:1536]
2010-12-25 10:04:32.202 mythtranscode: 58% Completed @ 51.8458 fps.612:1536]
2010-12-25 10:04:52.497 mythtranscode: 60% Completed @ 51.8425 fps.590:1536]
2010-12-25 10:05:12.708 mythtranscode: 61% Completed @ 51.8447 fps.576:1536]
2010-12-25 10:05:32.729 mythtranscode: 62% Completed @ 51.8319 fps.575:1536]
2010-12-25 10:05:53.149 mythtranscode: 63% Completed @ 51.7507 fps.630:1536]
2010-12-25 10:06:13.556 mythtranscode: 64% Completed @ 51.5303 fps.659:1536]
2010-12-25 10:06:33.766 mythtranscode: 65% Completed @ 51.3044 fps.651:1536]
2010-12-25 10:06:53.768 mythtranscode: 67% Completed @ 51.409 fps.7610:1536]
2010-12-25 10:07:13.772 mythtranscode: 68% Completed @ 51.4772 fps.573:1536]
2010-12-25 10:07:34.010 mythtranscode: 69% Completed @ 51.5119 fps.542:1536]
2010-12-25 10:07:54.088 mythtranscode: 71% Completed @ 51.5909 fps.502:1536]
2010-12-25 10:08:14.095 mythtranscode: 72% Completed @ 51.6686 fps.466:1536]
2010-12-25 10:08:34.292 mythtranscode: 73% Completed @ 51.7177 fps.422:1536]
2010-12-25 10:08:54.372 mythtranscode: 75% Completed @ 51.7686 fps.384:1536]
2010-12-25 10:09:14.383 mythtranscode: 76% Completed @ 51.8207 fps.345:1536]
2010-12-25 10:09:34.554 mythtranscode: 77% Completed @ 51.8645 fps.327:1536]
2010-12-25 10:09:54.681 mythtranscode: 79% Completed @ 51.889 fps.7330:1536]
2010-12-25 10:10:14.848 mythtranscode: 80% Completed @ 51.9119 fps.339:1536]
2010-12-25 10:10:35.024 mythtranscode: 81% Completed @ 51.9322 fps.354:1536]
2010-12-25 10:10:55.244 mythtranscode: 82% Completed @ 51.9322 fps.384:1536]
2010-12-25 10:11:15.390 mythtranscode: 84% Completed @ 51.9535 fps.365:1536]
2010-12-25 10:11:35.460 mythtranscode: 85% Completed @ 51.9588 fps.354:1536]
2010-12-25 10:11:55.472 mythtranscode: 86% Completed @ 51.9388 fps.357:1536]
2010-12-25 10:12:15.487 mythtranscode: 87% Completed @ 51.92 fps.[7359:1536]
2010-12-25 10:12:35.823 mythtranscode: 89% Completed @ 51.9159 fps.355:1536]
2010-12-25 10:12:56.110 mythtranscode: 90% Completed @ 51.862 fps.7368:1536]
2010-12-25 10:13:16.230 mythtranscode: 91% Completed @ 51.8331 fps.386:1536]
2010-12-25 10:13:36.232 mythtranscode: 92% Completed @ 51.8708 fps.386:1536]
2010-12-25 10:13:56.315 mythtranscode: 94% Completed @ 51.8638 fps.395:1536]
2010-12-25 10:14:16.580 mythtranscode: 95% Completed @ 51.8631 fps.407:1536]
2010-12-25 10:14:36.669 mythtranscode: 96% Completed @ 51.8683 fps.424:1536]
2010-12-25 10:14:56.778 mythtranscode: 97% Completed @ 51.8887 fps.433:1536]
2010-12-25 10:15:16.782 mythtranscode: 99% Completed @ 51.8774 fps.436:1536]
2010-12-25 10:15:34.105 AFD Error: Unknown audio decoding error0 [7451:1536]
Pos:3329.9s  83288f ( 0%) 51.99fps Trem:   0min   0mb  A-V:0.040 [7451:1536]
Flushing video frames.

Video stream: 7452.350 kbit/s  (931543 B/s)  size: 3103419224 bytes  3331.480 secs  83288 frames

Audio stream: 1536.000 kbit/s  (192000 B/s)  size: 639456000 bytes  3330.500 secs
x264 [info]: frame I:1223  Avg QP:10.38  size: 53621
x264 [info]: frame P:46760 Avg QP:10.45  size: 43011
x264 [info]: frame B:35304 Avg QP:11.13  size: 29081
x264 [info]: consecutive B-frames: 24.0% 51.9% 12.0% 12.1%
x264 [info]: mb I  I16..4: 22.5%  0.0% 77.5%
x264 [info]: mb P  I16..4: 37.4%  0.0%  0.0%  P16..4: 56.8%  0.0%  0.0%  0.0%  0.0%    skip: 5.7%
x264 [info]: mb B  I16..4:  9.4%  0.0%  0.0%  B16..8: 49.8%  0.0%  0.0%  direct:29.6%  skip:11.2%  L0:18.0% L1:22.8% BI:59.2%
x264 [info]: final ratefactor: -4.98
x264 [info]: direct mvs  spatial:83.9% temporal:16.1%
x264 [info]: coded y,uvDC,uvAC intra: 88.3% 88.9% 86.8% inter: 83.4% 76.2% 57.1%
x264 [info]: i16 v,h,dc,p: 32% 17% 33% 18%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 22% 20% 14%  3% 10%  7%  7%  7% 10%
x264 [info]: i8c dc,h,v,p: 52% 20% 20%  8%
x264 [info]: Weighted P-Frames: Y:7.9%
x264 [info]: kb/s:298.09
25/12,10:15 [5223] INFO Video Encoder: mencoder -idx -noskip 			/var/tmp/mythnuv2mkv5223/vidout -demuxer rawvideo -rawvideo w=720:h=576:fps=25.000 			-audiofile /var/tmp/mythnuv2mkv5223/audout -audio-demuxer rawaudio -rawaudio rate=48000:channels=2 			-ovc x264 -x264encopts level_idc=31:bframes=3:force_cfr:b_pyramid=normal:weight_b:threads=auto:direct_pred=auto:subq=6:frameref=5:partitions=all:8x8dct:mixed_refs:me=umh:trellis=1:bitrate=902:pass=2 -passlogfile /var/tmp/mythnuv2mkv5223/2pass.log 			-oac copy 			-vf pp=fd,softskip,crop=704:560:8:8,scale=656:368,harddup -sws 7  			-of rawvideo -o /var/lib/mythtv/livetv//1002_20101225085255_video.h264.
25/12,10:15 [5223] START Starting h264 2nd video pass trans of /var/lib/mythtv/livetv//1002_20101225085255.mpg. vbr 902 abr .
2010-12-25 10:15:44.886 Using runtime prefix = /usr
2010-12-25 10:15:44.886 Using configuration directory = /home/<user>/.mythtv
2010-12-25 10:15:44.887 Empty LocalHostName.
2010-12-25 10:15:45.000 New DB connection, total: 1
2010-12-25 10:15:45.008 Closing DB connection named 'DBManager0'
2010-12-25 10:15:45.017 Enabled verbose msgs: important
2010-12-25 10:15:45.193 Using protocol version 63
2010-12-25 10:15:45.215 mythtranscode: 0% Completed @ 0 fps.
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x0
rawvideo file format detected.
rawaudio file format detected.
[V] filefmt:65536  fourcc:0x30323449  size:720x576  fps:25.000  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=656 h=368]
Opening video filter: [crop w=704 h=560 x=8 y=8]
Crop: 704 x 560, 8 ; 8
Opening video filter: [softskip]
Opening video filter: [pp=fd]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
[PP] Using external postprocessing filter, max q = 6.
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0x1cbc220]Gaussian scaler, from yuv420p to yuv420p using MMX2
x264 [info]: using SAR=368/521
x264 [info]: using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
x264 [warning]: Error: 2pass curve failed to converge
x264 [warning]: target: 902.00 kbit/s, expected: 298.08 kbit/s, avg QP: 10.0005
x264 [warning]: try reducing target bitrate or reducing qp_min (currently 10)
x264 [info]: profile High, level 3.1
Selected video codec: [rawi420] vfm: raw (RAW I420)
==========================================================================
audiocodec: framecopy (format=1 chans=2 rate=48000 bits=16 B/s=192000 sample-4)
2010-12-25 10:16:05.241 mythtranscode: 0% Completed @ 5.0916 fps.[10021:1536]
2010-12-25 10:16:25.454 mythtranscode: 0% Completed @ 7.55355 fps.8771:1536]]
2010-12-25 10:16:46.716 mythtranscode: 0% Completed @ 8.19406 fps.8953:1536]
2010-12-25 10:17:06.808 mythtranscode: 0% Completed @ 8.55392 fps.8939:1536]
2010-12-25 10:17:27.488 mythtranscode: 1% Completed @ 8.34963 fps.9616:1536]
2010-12-25 10:17:47.893 mythtranscode: 1% Completed @ 8.38733 fps.9927:1536]]
2010-12-25 10:18:08.737 mythtranscode: 1% Completed @ 8.38855 fps.9946:1536]]
2010-12-25 10:18:29.034 mythtranscode: 1% Completed @ 8.41747 fps.10019:1536]
2010-12-25 10:18:49.039 mythtranscode: 1% Completed @ 8.55133 fps.9803:1536]]
^Cx264 [info]: frame I:23    Avg QP:10.46  size: 64644 A-V:0.040 [9782:1536]
 

At 1% the file output file is already 80M, meaning the final one will be in the order of 8G to 10G, for to five times the original. And the frame processing rate is awful for the given hardware.

Ready to give up...

---

### Post by laffinet on 2010-12-24
Sorry, I am by no means an expert on this. Have you posted any of this on [auric's]("http://web.aanet.com.au/~auric/?q=node/6") website ?

He can be a bit slow to respond but usually comes through with the goods !

You should give it a try.

---

### Post by GuiGuy on 2010-12-24
> **laffinet said:**
> Sorry, I am by no means an expert on this. Have you posted any of this on [auric's]("http://web.aanet.com.au/~auric/?q=node/6") website ?

He can be a bit slow to respond but usually comes through with the goods !

You should give it a try.

Thanks
I just sorted out the speed/performance issue; the backend has a CPU setting which was on medium. I put it on HIGH and processing jumped to~24fps. Much better. Still not up there where it should be, but certainly an improvement.

Now just the huge files mencoder is putting out :(

Cheers

---

### Post by GuiGuy on 2010-12-25
I think I may have solved it; it seems to have been mencoder after all. 

I purged the the system of mencoder and then enabled the medibuntu repository and installed mencoder from there. Small tests were successful with single pass video processing to mkv @ 480p happening at ~40fps.  If it holds I'm good with that.

Cheers

---

### Post by GuiGuy on 2010-12-26
Looks like I didn't solve it. Restarted the box this morning and archiving speed to mkv is back to something like less than 0.6 fps. If I do avi it's marginally better at about 5 frames a second. 

Time to give up and find a new hobby, I think. :(

And it was such a great system for over twelve months. Until the motherboard fried.

---

