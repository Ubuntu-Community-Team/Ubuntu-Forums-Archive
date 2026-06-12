---
title: "Video frame buffering failed too many times - mythbuntu 9.10"
date: 2009-11-05
forum: Mythbuntu
---

### Post by DominicF on 2009-11-05
I'm running mythbuntu 9.10 from a fresh install.  Recently, I've been seeing the message pop up:

Video frame buffering failed too many times

While watching LiveTV the image would freeze followed by the message appearing.  I [ESC] out to the main menu and go back into Watch TV but now every channel to change to I don't get a signal Lock, it only says Partial Lock and nothing appears on screen.  To get around this I have to re-boot the PC and then it starts working again until the next time.

   
Any advise?

---

### Post by DominicF on 2009-11-06
Some more info:

I'm running both frontend and backend on the same machine.

Using the Nova-T 500 DVB dual tuner card plugged in a roof top antenna.

---

### Post by Boppy3125 on 2009-11-06
No real answers here, but some observations from my recent work.  The message was coming to me when I would try to go to a channel that couldn't lock.  What I noticed is that once the message came up, that tuner was crashed.  I could only fix it by stopping and restarting the backend.  Eventually I noticed that if I just tried a channel for about 5-8 seconds and if it wasn't coming up I would change to a known good one.  Then I could try another.

I know your situation is different, since you say you are watching Live TV and then it freezes.  Whatever is happening, I would guess that the message is indicating that your backend has crashed (at least its connection to that tuner.)

Good luck.  Maybe you can setup something to easily restart your backend when it happens while working through issues.

Is this OTA, Cable, other?  Are you splitting the signal?

---

### Post by newbie02 on 2009-12-06
I am seeing the same issue. My front end loses the signal on the tv of a recorded show, then this message appears. I hardly ever watch live tv.

I also did fresh installs of 9.10 for both front and back end. I never had this issue with 8.04 which was the version i came from with backend my front end used to be 9.04.
Newbie02

---

### Post by nickrout on 2009-12-06
how about the front end/back end log files and dmesg?

---

### Post by newbie02 on 2009-12-10
I figured out my new hard drive was/did crashed.

I posted the logs here ...
[http://ubuntuforums.org/showthread.php?p=8474402#post8474402](http://ubuntuforums.org/showthread.php?p=8474402#post8474402)



Newbie02

---

### Post by GuiGuy on 2010-02-05
> **newbie02 said:**
> I figured out my new hard drive was/did crashed.
I posted the logs here ...
[http://ubuntuforums.org/showthread.php?p=8474402#post8474402](http://ubuntuforums.org/showthread.php?p=8474402#post8474402)
Newbie02

I had the same issue. Noted that I had to always fsck /dev/sda1 on a reboot so suspected the HDD was on its way out. 

I replaced the HDD (new) about two weeks ago and did a fresh install. All was well until a few days ago. Same "Video frame buffering failed too many times". Logs suggested something was very sick on the HDD. had to do the fsck /dev/sda1 again. 

Another HDD, another week, same problem started again tonight. 

Is there something in MythTV (.022) that could be trashing the file system?

---

### Post by 4dognight on 2010-02-05
Is it always on the same channel that the problem happens?

---

### Post by GuiGuy on 2010-02-05
> **4dognight said:**
> Is it always on the same channel that the problem happens?

I can't be sure, but given our habits I think it's likely to be the same channel.

---

### Post by 4dognight on 2010-02-05
I had a problem similiar to yours. It failed on the same channel.
I found a posting that recommended to set the 'quick tune' to 'always', in 'input connections' setting from the backend config. Dont know what it does , but my problem went away after that.

---

### Post by GuiGuy on 2010-02-05
> **4dognight said:**
> I had a problem similiar to yours. It failed on the same channel.
I found a posting that recommended to set the 'quick tune' to 'always', in 'input connections' setting from the backend config. Dont know what it does , but my problem went away after that.

Thank you. I'll try that. My settings were for live tv only.

---

### Post by GuiGuy on 2010-02-06
> **GuiGuy said:**
> Thank you. I'll try that. My settings were for live tv only.

well, that wasn't it. Just crashed again. Log is only telling me that the file system is read-only!!??

---

### Post by 4dognight on 2010-02-06
can you post the error from the log

---

### Post by GuiGuy on 2010-02-06
> **4dognight said:**
> can you post the error from the log


OK, going through some backups I managed to establish that just before a crash the backend log writes a bunch of stuff like this

> 
2010-02-01 13:30:55.282 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 43 8
2010-02-01 13:30:55.314 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 11 21
2010-02-01 13:30:55.331 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 44 35
2010-02-01 13:30:55.346 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 4
2010-02-01 13:30:55.363 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 5
2010-02-01 13:30:55.380 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 6
2010-02-01 13:30:55.397 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 7
2010-02-01 13:30:55.414 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 8
2010-02-01 13:30:55.431 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 9
2010-02-01 13:30:55.448 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 10
2010-02-01 13:30:55.465 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 11
2010-02-01 13:30:55.482 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 12
2010-02-01 13:30:55.499 [mpeg2video @ 0x7fdf72f97820]invalid mb type in I Frame at 0 13
2010-02-01 13:30:55.516 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 14
2010-02-01 13:30:55.533 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 15
2010-02-01 13:30:55.550 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 16
2010-02-01 13:30:55.567 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 1 17
2010-02-01 13:30:55.584 [mpeg2video @ 0x7fdf72f97820]ac-tex damaged at 0 18
2010-02-01 13:30:55.601 [mpeg2video @ 0x7fdf72f97820]invalid mb type in I Frame at 0 19


At some point within the sequence the log is no longer written because the file system becomes read only.

My reading of it is that a poor signal may be contributing. This would make sense. The weather has been unseasonal and there has been picture breakup when viewing or recording. 

But I reckon a program shouldn't trash the file system just because its input expectations aren't being met(?).


:(

---

### Post by nickrout on 2010-02-06
is the log file filling up your filesystem?

---

### Post by GuiGuy on 2010-02-06
> **nickrout said:**
> is the log file filling up your filesystem?

No. It's on a 1T drive with heaps of free space. The backend log file is typically ~3M to ~6M

However, I've now checked all the hardware, cleaned out the dust, reseated the CPU heatsink, checked all fans are working and changed the PS. 

Let's see what happens. I'll report back...

---

### Post by movieman on 2010-02-06
> **GuiGuy said:**
> But I reckon a program shouldn't trash the file system just because its input expectations aren't being met(?)

That sounds more like a hardware fault or driver bug: a normal user-mode program which isn't running as root should never be able to corrupt the disk in that way.

---

### Post by GuiGuy on 2010-02-07
> **movieman said:**
> That sounds more like a hardware fault or driver bug: a normal user-mode program which isn't running as root should never be able to corrupt the disk in that way.

I'm not disagreeing. I've tidied up the hardware side as good as I can make it now and will see what happens. 

Thanks

---

### Post by damien.morrissey on 2010-03-02
I too get this message from time to time, however it is only on one channel and only when it goes between programs (for recorded programs- I wouldn't know about live tv as I don't bother with it anymore). By theory is that there is a bitrate change between the programs. The thing is that it is a HD channel with (what I believe is) a mix of SD and HD content. It happens on no other channel- even the SD version of this same channel.

```
2010-03-02 16:52:08.349 WriteAudio: buffer underrun
2010-03-02 16:52:08.641 WriteAudio: buffer underrun
2010-03-02 16:52:08.929 WriteAudio: buffer underrun
2010-03-02 16:52:09.182 WriteAudio: buffer underrun
2010-03-02 16:52:10.233 NVP(4): prebuffering pause
2010-03-02 16:52:10.248 WriteAudio: buffer underrun
2010-03-02 16:52:10.315 NVP(4): Prebuffer wait timed out 10 times.
2010-03-02 16:52:10.395 AFD: Opened codec 0x11422a80, id(MPEG2VIDEO) type(Video)
2010-03-02 16:52:10.395 AFD: codec MP3 has 0 channels
2010-03-02 16:52:10.395 AFD: Opened codec 0x10f63910, id(MP3) type(Audio)
2010-03-02 16:52:10.396 AFD: Setting channels to 2
2010-03-02 16:52:10.396 [mp3 @ 0x7f3afb6f3820]Header missing
2010-03-02 16:52:10.396 NVP(4): Disabling Audio, params(16,2,0)
2010-03-02 16:52:10.407 NVP(4): Prebuffer wait timed out 20 times.
2010-03-02 16:52:10.507 NVP(4): Prebuffer wait timed out 30 times.
2010-03-02 16:52:10.575 NVP(4): Prebuffer wait timed out 40 times.
2010-03-02 16:52:10.596 NVP(4): Prebuffer wait timed out 50 times.
2010-03-02 16:52:10.618 NVP(4): Prebuffer wait timed out 60 times.
2010-03-02 16:52:10.639 NVP(4): Prebuffer wait timed out 70 times.
2010-03-02 16:52:10.660 NVP(4): Prebuffer wait timed out 80 times.
2010-03-02 16:52:10.690 NVP(4): Prebuffer wait timed out 90 times.
2010-03-02 16:52:10.727 NVP(4): Prebuffer wait timed out 100 times.
2010-03-02 16:52:10.727 NVP(4), Error: Timed out waiting for prebuffering too long. Exiting..
2010-03-02 16:52:10.945 TV: Attempting to change from Watching WatchingPreRecorded to None
2010-03-02 16:52:10.962 TV: Changing from Watching WatchingPreRecorded to None
2010-03-02 16:52:10.983 ScreenSaverX11Private: DPMS Reactivated 1
2010-03-02 16:52:10.983 TV: Attempting to change from None to None
2010-03-02 16:52:11.012 TV: Attempting to change from None to Watching WatchingPreRecorded
2010-03-02 16:52:11.083 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2010-03-02 16:52:11.083 playCtx, Error: Attempting to setup a player, but it already exists.
2010-03-02 16:52:11.083 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end error
2010-03-02 16:52:11.104 ScreenSaverX11Private: DPMS Deactivated 1

```

I should mention that I was fast forwarding through the program when it happened. If I skip (what I think is) the boundary between programs it seems to work just fine.

Very strange- any ideas?

---

### Post by NeoTrantor on 2010-05-31
Hi,

I ran into the same problem. Got that "Video frame buffering failed too many times" message and my /var filesystem became read-only. After a reboot everything is fine again. It happens after a while when I record a specific HD channel and watch it in Live-TV mode at the same time. I also can reproduce it this way. Never had any problems like that in other situations so I think faulty hardware is rather unlikely.
Watching that channel in Live-TV without recording it seems to be no problem. I can live with that issue since watching live tv implies recording it temporarily in mythtv but things like that shouldn't happen at all. ;)

---

### Post by petatkinson on 2010-05-31
I thought I was the only one suffering this problem.I am running MythTV under 10.04 and experiencing this problem too.I am trying to eliminate as much as possible but I haven't had one single reply to my post.By any chance do you have more than one pata/sata drive installed on your system.This is the next area I am checking.Also, are you using a wired internet connection or a wireless connection.

---

### Post by NeoTrantor on 2010-05-31
I am running 10.04 too. My HTPC has only one HDD and I'm using wired network. Here's my system:
 - Athlon X2 4850e (2x 2500 MHz)
 - Abit AN78HD (GeForce 8200)
 - 2 GB DDR2-800
 - Western Digital WD5000AACS 500 GB
 - Hauppauge WinTV Nova S2

---

### Post by petatkinson on 2010-05-31
Well you have managed to blow my theory out.I am running a Core 2Duo with a pata and sata drive and wireless connection through a router.I thought from the error messages issued from MythTV someone could lead us in the right direction.I have searched through the forum extensively and have not really seen any solutions to this problem.

I have noticed if a thread builds up a little it goes completely off topic and gets hijacked.I will keep experimenting to see if I can find a solution but you know when you change too much its time for the dreaded reinstall.

I understand that all the input here is voluntary and am very greatful for it but when you bring the friends around to see your new HTPC running under Linux and MythTV and it crashes for no apparent reason comments like "lets go to mine and see a real system working" doesn't do the cause for MythTV much good.

---

### Post by nickrout on 2010-05-31
> **petatkinson said:**
> Well you have managed to blow my theory out.I am running a Core 2Duo with a pata and sata drive and wireless connection through a router.I thought from the error messages issued from MythTV someone could lead us in the right direction.I have searched through the forum extensively and have not really seen any solutions to this problem.

If you are trying to view over a wireless connection, I would try a cable and see if that's any better.

> I have noticed if a thread builds up a little it goes completely off topic and gets hijacked.I will keep experimenting to see if I can find a solution but you know when you change too much its time for the dreaded reinstall.

I understand that all the input here is voluntary and am very greatful for it but when you bring the friends around to see your new HTPC running under Linux and MythTV and it crashes for no apparent reason comments like "lets go to mine and see a real system working" doesn't do the cause for MythTV much good.

Try asking on the mailing list. Try posting your frontend logs.

---

### Post by NeoTrantor on 2010-06-01
Here's what my Frontend logs reported before everything is going down:

```
...
00:26:30.594 NVP(1): prebuffering pause
00:26:31.574 NVP(1): Prebuffer wait timed out 10 times.
00:26:32.056 RingBuf(/daten/Video/mythtv/live/12100_20100530001509.mpg): Waited 2.0 seconds for data to become available...
00:26:32.056 Checking to see if there's a new livetv program to switch to..
00:26:32.574 NVP(1): Prebuffer wait timed out 20 times.
00:26:33.574 NVP(1): Prebuffer wait timed out 30 times.
00:26:34.574 NVP(1): Prebuffer wait timed out 40 times.
00:26:35.178 NVP(1): prebuffering pause
...
```The last line was repeated many times, then no more log data could be written since the filesystem was set to read-only.

What I noticed yesterday is that my syslogs gets flooded repeatedly by the following lines:
```
00:31:12 HTPC kernel: [ 1914.658686] ata3.00: exception Emask 0x10 SAct 0x7d SErr 0x400000 action 0x6 frozen
00:31:12 HTPC kernel: [ 1914.658698] ata3.00: irq_stat 0x08000000, interface fatal error
00:31:12 HTPC kernel: [ 1914.658703] ata3: SError: { Handshk }
00:31:12 HTPC kernel: [ 1914.658709] ata3.00: failed command: READ FPDMA QUEUED
00:31:12 HTPC kernel: [ 1914.658716] ata3.00: cmd 60/08:00:2a:73:99/00:00:02:00:00/40 tag 0 ncq 4096 in
00:31:12 HTPC kernel: [ 1914.658718]          res 40/00:34:b2:4a:41/00:00:26:00:00/40 Emask 0x10 (ATA bus error)
00:31:12 HTPC kernel: [ 1914.658720] ata3.00: status: { DRDY }
00:31:12 HTPC kernel: [ 1914.658723] ata3.00: failed command: WRITE FPDMA QUEUED
00:31:12 HTPC kernel: [ 1914.658727] ata3.00: cmd 61/00:10:aa:3e:41/04:00:26:00:00/40 tag 2 ncq 524288 out
00:31:12 HTPC kernel: [ 1914.658729]          res 40/00:34:b2:4a:41/00:00:26:00:00/40 Emask 0x10 (ATA bus error)
00:31:12 HTPC kernel: [ 1914.658731] ata3.00: status: { DRDY }
00:31:12 HTPC kernel: [ 1914.658733] ata3.00: failed command: WRITE FPDMA QUEUED
00:31:12 HTPC kernel: [ 1914.658738] ata3.00: cmd 61/00:18:aa:42:41/04:00:26:00:00/40 tag 3 ncq 524288 out
00:31:12 HTPC kernel: [ 1914.658739]          res 40/00:34:b2:4a:41/00:00:26:00:00/40 Emask 0x10 (ATA bus error)
00:31:12 HTPC kernel: [ 1914.658741] ata3.00: status: { DRDY }
00:31:12 HTPC kernel: [ 1914.658744] ata3.00: failed command: WRITE FPDMA QUEUED
00:31:12 HTPC kernel: [ 1914.658748] ata3.00: cmd 61/00:20:aa:46:41/04:00:26:00:00/40 tag 4 ncq 524288 out
00:31:12 HTPC kernel: [ 1914.658749]          res 40/00:34:b2:4a:41/00:00:26:00:00/40 Emask 0x10 (ATA bus error)
00:31:12 HTPC kernel: [ 1914.658752] ata3.00: status: { DRDY }
00:31:12 HTPC kernel: [ 1914.658754] ata3.00: failed command: WRITE FPDMA QUEUED
00:31:12 HTPC kernel: [ 1914.658758] ata3.00: cmd 61/08:28:aa:4a:41/00:00:26:00:00/40 tag 5 ncq 4096 out
00:31:12 HTPC kernel: [ 1914.658759]          res 40/00:34:b2:4a:41/00:00:26:00:00/40 Emask 0x10 (ATA bus error)
00:31:12 HTPC kernel: [ 1914.658762] ata3.00: status: { DRDY }
00:31:12 HTPC kernel: [ 1914.658764] ata3.00: failed command: WRITE FPDMA QUEUED
00:31:12 HTPC kernel: [ 1914.658768] ata3.00: cmd 61/f8:30:b2:4a:41/03:00:26:00:00/40 tag 6 ncq 520192 out
00:31:12 HTPC kernel: [ 1914.658769]          res 40/00:34:b2:4a:41/00:00:26:00:00/40 Emask 0x10 (ATA bus error)
00:31:12 HTPC kernel: [ 1914.658772] ata3.00: status: { DRDY }
00:31:12 HTPC kernel: [ 1914.658782] ata3: hard resetting link
00:31:13 HTPC kernel: [ 1915.480037] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
00:31:13 HTPC kernel: [ 1915.481637] ata3.00: configured for UDMA/33
00:31:13 HTPC kernel: [ 1915.481656] ata3: EH complete
```This looks very bad to me! There seems to be something wrong with the HDD, the controller, the link or the drivers. I should fix that first and see if mythtv works then. Maybe more or less intense asynchronous disk access which occurs while watching and recording HD channels brought out that crash. On the other hand, as I said, watching live tv without recording anything at the same time works without any problems even though that messages appear in the logs very frequent!

---

### Post by nickrout on 2010-06-01
If you google those kernel errors you will find some ideas.

---

### Post by petatkinson on 2010-06-01
Disconnected wireless link.Replaced with wired.Seems a little more stable.Think we are on our own on this one.I'd rather get on with watching TV rather than sifting through logs all night though.

---

### Post by Woodwa on 2010-06-25
> **NeoTrantor said:**
> I am running 10.04 too. My HTPC has only one HDD and I'm using wired network. Here's my system:
 - Athlon X2 4850e (2x 2500 MHz)
 - Abit AN78HD (GeForce 8200)
 - 2 GB DDR2-800
 - Western Digital WD5000AACS 500 GB
 - Hauppauge WinTV Nova S2

I'm running allmost exactly the same system... and having the same issues..

the wife is quiet upset about this..
my system is:
 - Athlon X2 4850e (2x 2500 MHz)
 - **Asus ** ??(GeForce 8200 based)
 - 2 GB DDR2-800
 - 2 seperate Sata HDDs
 - leadtek dtv1000s

I do remember in 9.1/9.04/8 taht the nvidia 180 drivers had no issues..

I'd try the 2xx.xx drivers by nvidia but apparently they are still quiet slow. and the 8200 only just copes with HD right now..

---

### Post by Woodwa on 2010-06-25
I just installed 256.35 drivers.

OMG its like im back to the quality of the 180 drivers..

I think the wife will recomend I don't change a thing for ever@!@!:popcorn:

I've nver had HD and the 8200 running as well as now

FYI I'm also running kernal 2.6.34 from mainline

I can do a dance now for my Advanced 1x and world cup finals.. Finals in HD.

---

### Post by thewoose on 2010-07-10
[SIZE=2]Hi,

I have had this same problem with the "buffering failed" error in Mythbuntu 9.10 and now again in 10.04.  It happens with me watching Live TV while changing channels from HD to SD, or from ATSC to SCTE or MPEG (lots of acronyms, but you get the idea!)  I'm using a Pinnacle PCTV HD PCI tuner card, and I'm actually tuning a Cable feed directly with card using QAM-256.  Anyway, there are several channels that don't work, and when trying to tune them I'll get this error and a crash, and as long as I stay off those it's fine.  Also, when I'm on an SD channel and then flip to an HD channel I get the Error, so it really seems to be caused by bitrate and/or stream type being changed.  If I exit Live TV and then re-enter it before going to an HD channel it's fine, and then tuning other HD channels is fine, but Myth has to be "stroked" to switch between changing stream types.  

Anyway, just wanted to sound off my experience with this goofy error. :D

-Steve
[/SIZE]

---

### Post by nickrout on 2010-07-10
You'll find Live TV is not as well supported as recording what you want and watching it at your leisure :) MythTV is not designed for channel surfing.

---

### Post by morias on 2010-08-27
This is how I fixed my video frame buffer failed too many times problem.

I have a mythbuntu setup on an acer revo for my tv which works great.  Flushed with my success from that installation I was trying to set up mythtv on my 10.04 ubuntu box but ran into the difficulty everyone else is facing here.  That is the tv would only run from 10 seconds to 15 minutes before failing with the above message.  It would also lose lock and cause me to need to shut down the backend and restart it in order to continue.

At first I thought it was a video audio syncing problem as I would get a lot of audio buffering messages in the frontend log.  Later I tried fiddling with the video drivers.

After fiddling with every option in the backend and frontend several times, I had a moment of inspiration and wondered if it would crash if I changed to my second tuner in my usb dual tuner (Kworld U399 with the AF9015 firmware).  I changed the input manually in the frontend and the result was stable operation with no annoying frame buffer messages kicking me back to the home screen.

To make it the default option, I switched the order of the tuners in the backend setup and now all is good. 

Hope this helps someone with this problem, as I could not find a solution anywhere despite people posting about it for some years.

---

### Post by petatkinson on 2010-08-30
I just revisited this problem and dare I say it I may have found a solution.In the MythBackend in Video Sources adjust the Timeout for channel change and signal detection.They are in milliseconds so double both values.One from 10000 to 20000 and the other from 7000 to 14000.Experiment a bit with those values.I have a feeling that the problem lies with the way pictures change briefly showing a blank screen during a program and the channel change which causes a black screen too.Also I wonder what effect EIT has on Myth as it is constantly seeking an over-the-air update.Just a thought.I really wish that verbose error message "video frame buffer overrun" was a bit more informative and didn't cause me to have to reboot my system.

---

