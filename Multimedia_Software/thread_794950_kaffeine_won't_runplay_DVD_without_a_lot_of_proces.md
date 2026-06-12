---
title: "kaffeine won't run/play DVD without a lot of process-killing"
date: 2008-05-15
forum: Multimedia Software
---

### Post by mrowth on 2008-05-15
As I wrote in the delirious ragged edge of this hopeless thread [http://ubuntuforums.org/showthread.php?t=794434](http://ubuntuforums.org/showthread.php?t=794434) -- 

I often (or: usually) have to "kill" Kaffeine before I can get it to run again. Even then it won't necessarily start playing DVDs it played fine just fifteen seconds ago.

It's not I have to kill it only after it crashes (which it does, at times, even after playing fine) - when it starts and works, I can *usually* quit it the usual way. Even so it may leave its two processes behind. 


Right now i've connected: 
IDE Secondary Master: Toshiba DVD-ROM 
IDE Secondary Slave: Sony DVD writer 

Both run relatively smoothly - when they run. 

Strangely enough BIOS has very recently begun offering only the Slave drive as a boot device, regardless which drive it is (I've been swapping three of them around, and also found a fresh cable...) (the BIOS setup screen does show it as the slave and the jumpers look right too)


edit: well, there's really not much info to go by here, is there? Kaffeine doesn't give any error messages, it just doesn't start, leaving two processes behind for me to mop up.

When I run it from the console, and I get as far as being able to actually attempt to play a DVD with it, it outputs this:
```

libdvdnav: Using dvdnav version 1.1.7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: TITLE_OF_DVD
libdvdnav: DVD Serial Number: 12345678
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/username/.dvdnav/TITLE_OF_DVD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00ed0000. Regions: 2 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000025b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0003345c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000565f4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0039d31e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0039d3d1
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0

```
When it works, this is followed by: 
```

AFD changed from -2 to -1
```

When it doesn't work, that was it. (When it works, it takes no time at all with the same DVD.)

---

### Post by mrowth on 2008-05-15
First and only *bump* 
[COLOR="Silver"]
[SIZE="1"](I've come to search my posts by looking for the ones without replies...)[/SIZE][/COLOR]

---

### Post by mrowth on 2008-05-15
I have a worse problem, though:

Namely --

DVD playback freezes every few minutes (2-6, roughly) for up to half a minute (guesstimate). 

Then it continues, at first by fast-forwarding crazily for a few seconds, then normally. The fast-forwarding can be aborted by seeking manually.

It's making the whole DVD watching thing quite the chore.

There're no error messages that I can see. 

This happens with all three DVD drives I have lying around, one of them brand new... with DVDs old and freshly unwrapped new... with different mediaplayers, like MPlayer and Kaffeine...

It's not happened any previous (that is, pre-Gutsy) Ubuntu release, Linux distribution, or Windows. 

Well, blah blah blah... I don't know what to check or do about this... :confused:^3

---

### Post by mrowth on 2008-05-16
Playback only freezes when I've got two drives connected - with just the master or just the slave it's fine. It doesn't matter which drive it is - as long as it's the only one. That's never been the case before. *sigh*

---

### Post by AlanR8 on 2008-05-16
I use VLC for DVD and video playback and have no problems. Give it a go and see if there's an improvement.

---

### Post by mc4man on 2008-05-16
Can you describe the ide cable your using, are the connectors different colors, can you see the individual wires or is it relatively smooth ect
What are your jumper settings and positions of drives on cable

---

### Post by mrowth on 2008-05-16
> **mc4man said:**
> Can you describe the ide cable your using, are the connectors different colors, can you see the individual wires or is it relatively smooth ect
What are your jumper settings and positions of drives on cable
I can see the individual wires.

The connector that I've plugged into the mainboard is black and blue. The others are black and grey. 

The jumper on the drive on the end connector is in the MA position. The drive is listed as Secondary Master in BIOS, and its device node in Ubuntu is /dev/hdc.

The jumper on the drive on the middle connector is in the SL position. The drive is listed as Secondary Slave in BIOS, and its device node in Ubuntu is /dev/hdd.

I've had my drives (both optical and harddisk) in this configuration from day one on this PC... never gave me a problem.

Another weirdness - I can no longer convince BIOS to let me boot off the secondary master drive - now the only option (as far as CD/DVD drives go) is the secondary slave. Unless there's no secondary slave because I unplugged it - then it'll let me have my secondary master boot drive. You'd think I've got them confused but... hm... something seems different now.

I've swapped it all around a dozen times, even found an unused-looking cable and replaced the old one, but it didn't help.

---

### Post by mrowth on 2008-05-16
> **AlanR8 said:**
> I use VLC for DVD and video playback and have no problems. Give it a go and see if there's an improvement.
Hmmm. I'm currently fighting with VLC. At first, it kept exiting and coredumping and whatnot. Now it's somehow stable. I haven't got both drives plugged in, though, so I can't test if playback halts with VLC, too. It does with Totem and two or so MPlayer frontends. So I'm not getting my hopes up.

VLC... which video output should I use? I never know. X11 eats some 29-50% CPU per core, XVideo 4-9%, and OpenGL doesn't work - but why not? Nvidia driver is running, Compiz would be running if I wanted it to, etc.

I still think Kaffeine ought to work... it *should* be my favourite media player...

---

### Post by mc4man on 2008-05-16
something seems borked with your hardware, and or install. The AFD error is puzzling. I believe refers to the generic ATA/ATAPI disk con- troller driver, though i'm not sure. FD would seem to indicate floppy drive.(?)
You've got nothing else to lose at this point, maybe try setting the jumpers on both drives to cs.

edit; not knowing what's available in your bios, if there is an option to set to default setting do that

---

### Post by mrowth on 2008-05-16
I set both drives to cable select. It seems to have rehabilitated the secondary master as a possible boot drive. Thanks for the idea. No change in DVD behaviour though (it just froze again, 8 min into a movie. Then again at 8:33. And 12:05. Fun! Maybe if I used the *third* IDE connector for one of the drives, it's a whole different controller... but I hate resorting to workarounds.

During the freezes, the drive goes silent... can't be mounted, either. It just ...stops for a while.

---

### Post by mrowth on 2008-05-17
I discovered and installed Linux Mint 4.0. At first, everything was working suspiciously great. I didn't have to "killall kaffeine" even once, playback never froze, no DVDs were chewed up, and so on. Watched for a long time, was satisfied. My hardware is ok after all... (as it usually is, in Windows...)

Then I continued setting things up. Tentatively installed linux-rt, rezound, ubuntustudio-audio (metapackage for tons of audio apps) and bang, it started freezing again! Wtf? Could that have anything to do with it at all? What of that could possibly interfere with the DVD-reading? I'm not even *running* any of it right now.

Removed rt kernel (which, as I said, I wasn't running)... now can play DVDs again? 

I'm so very confused

---

