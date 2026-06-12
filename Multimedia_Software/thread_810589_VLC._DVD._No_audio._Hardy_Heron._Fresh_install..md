---
title: "VLC. DVD. No audio. Hardy Heron. Fresh install."
date: 2008-05-28
forum: Multimedia Software
---

### Post by Roasted on 2008-05-28
I'm trying to play a concert I have on DVD. 

What happens is this... I open VLC, then go to "open disc". I end up hitting okay, since the default options are already set to the CD drive I have the DVD in. The DVD prompts me with its usual screen and I have to hit play.

It freezes for about 60 seconds here, causing VLC to go to that shade of dark gray where you know something is wrong. Then it comes back to life and plays the video fine, but I have no audio.

I installed the medi packages and all of that garbage. My system is fully up and running, except no DVD playback yet. What can I do?

---

### Post by hyperair on 2008-05-28
You need the pulseaudio plugin for VLC. Then change VLC's audio settings to use PulseAudio as the output module. The package is "vlc-plugin-pulse".

---

### Post by Roasted on 2008-05-29
Pulse is already installed. I went to preferences and hit advanced and went under the "output" section under audio. I selected the drop down list to pulseaudio.

Still nothing.

Is a reboot required to make this work? I'm heading out the door as we speak for work or else I'd try it now.

---

### Post by hyperair on 2008-05-29
No a reboot should not be needed. Could you run VLC in the terminal and post the output when you try to play a DVD?

---

### Post by Roasted on 2008-06-20
jason@jason-hardy:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: THE_PATRIOT
libdvdnav: DVD Serial Number: 29286F39
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jason/.dvdnav/THE_PATRIOT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000480
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002d20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000093c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00013be0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00013ca0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00013da0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00049098
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x00049098)!!
libdvdread: Elapsed time 29
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0030f700
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0030f720
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00331e60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00351380
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003742a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003742c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00377a40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0039bfa0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003a5920
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003a5980
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 29
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
[00000344] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000

edit - for the record, when I hit "play movie", VLC simply sucks. It constantly freezes and never gets the movie rolling.

I gotta admit, guys. This is making XP look a lot more attractive. I have been through hell and back trying to get movies to play on Ubuntu, yet every distro I've had, I've never gotten it to work.

---

### Post by mc4man on 2008-06-20
What's odd is to see these 2 lines on the same title
> libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
> libdvdnav: Suspected RCE Region Protection!!!

in any event the error cracking key for /VIDEO_TS/VTS_03_1.VOB is your problem (may be others)
I'd install regionset and then with a _dvd in the drive _run regionset from the terminal (if you have 2 drives you'll need path in command for 2nd drive - /dev/scd1  ect.)
ex. of set drive
```
doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET   [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n

```
ck. that out and post back , if it's not been set then set it to your region.

---

### Post by Roasted on 2008-06-21
Cool. Now I have no audio on VLC.

Why do I bother? With XP, I hit play. 

What else can I do to get this running? I've never had to run through so many hurdles in my life.

---

### Post by analoog on 2008-06-21
can you actually hear sound when you play a sound file (mp3 or wav) for example.

---

### Post by Roasted on 2008-06-21
I got Taylor Swift screaming at the top of her lungs right now on Audacious.

See why I'm frustrated yet? Maybe sticking with Totem was a better choice. The how-to seems much easier.

---

### Post by Roasted on 2008-06-21
Nevermind. Just switched the default program to Totem. Totem simply shuts off immediately after the DVD is inserted.

Ridiculous. 

I'm going to do a fresh install in the morning if I don't get anymore answers here this evening. Then I am going to follow that guide for the 3rd time and see if I get anywhere. If not? Hello XP.

---

### Post by mc4man on 2008-06-21
> Cool. Now I have no audio on VLC. Checking or setting a dvd region has no effect on whether you have audio or not.
90% of the time having no audio in vlc can be solved by going vlc -> settings -> preferences -> click adv. options -> audio -> highlight output modules and in drop down on right change from default  to alsa ....
> Just switched the default program to Totem
How did you set that up?, there's a couple of right ways, a couple of wrong ways
Setting up dvd playback should only take a min. or two (assuming a region has been set)
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)
a decent way to change vlc to default player
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

note; If or when you get playback on _this install_ i'd go home dir. (show hidden files) find .dvdcss and delete everything _inside_

---

### Post by Roasted on 2008-06-21
Thanks for the insight. I will look at it tomorrow. I'm on my laptop in bed, I gave up for the night. Thanks for the tip of the home dir, I forgot about that. I tried another guide or two for getting dvd playback to work, and I had the feeling that I had some garbage installed that I shouldn't have after I tried this last guide.


If you look at the sticky at the top, the comprehensive video audio one, in there somewhere is a gksu gedit file, and you just change everything from totem.desktop to vlc.desktop and it changes the default.

DVD playback takes a minute or two? Really? I've used Ubuntu for 2 years. I have yet to get it working. And I don't consider myself to be an idiot with computers... after all, I'm a pretty successful computer technician. But hot damn I must be doing something wrong. Perhaps a fresh install would yield better results? I'll try the home dir thing first, though...

Oh - and about the regionset audio thing... I changed nothing. Absolutely nothing. My audio was working fine on that DVD. I change regionset. No audio.

I don't know what to tell you. What happened, happened. :(

---

### Post by mc4man on 2008-06-21
> DVD playback takes a minute or two?
_if_ you do a fresh install and right after updating, getting your video driver stuff addressed (open source, resticted, whatever) you run through those 2 links in order you'll have everything you need as far as libs and codecs, with vlc as your default player. (in other words dvd playback will be enabled) If there are any audio, video issues then that's exactly what they are and should be addressed as such, no need to chase libs, codecs and players.
Because your on a laptop it would be good to know your dvd drive model. Matshita drives can present unique issues.
run ```
sudo lshw -C disk
``` to get model

edit: as far as the region setting - if it's set it's set, no reason to ever change (unless you go back to windows and the region where your getting your dvds changes)

---

### Post by Roasted on 2008-06-21
Is there anything I can do to revert my audio/video settings back, then start over the guide that you gave me? It'd be nice to avoid having to do a fresh install.

And no, you misunderstood about the laptop. I have an XP laptop and I run Ubuntu on my desktop. I gave up on the Ubuntu desktop for the night so I'm just here in bed on XP floating around on a couple web sites before I zonk out. No Ubuntu here. (no wireless support)

---

### Post by mc4man on 2008-06-21
> Is there anything I can do to revert my audio/video settings back
First to get something 100% out of the way - a region is set yes?, and when so there's no reason to ever change it in linux. and ...
You are switching your default choice for player in file management, not going back into defaults.list and reediting.(totem to vlc to totem ect.)

The thread goes back 3 wks. so there's no discounting what you've done.

Edit:
Considering you did the default thing in a proper manner  I'd not do anything with defaults.list as in link 2 with the exception of _after vlc is re installed checking/setting that the launcher command is %m _ (in edit menus)
I'd try first going into synaptic and doing a complete removal of vlc followed by libdvdcss2, libdvdnav4 and libdvdread3 (or do it from cli)
Then ck. in home dir. , if .dvdcss is there delete it or it's contents.
Then just for the heck of it run   sudo apt-get autoremove
Then run the commands in link 1.
If you know medibuntu is set as a repo (admin, software sources, third party) then don't run first 2 commands. In that case run ```
sudo apt-get update
``` followed by the remaining 3. (if anything is redundant no harm)
Then I'd ck. the vlc launcher comm. 
To take pulse out of the mix for now go system -> preferences -> sound and move the settings for music and movies from autodetect to alsa.
Change the audio setting in vlc as in prior post.
At this point playback is enabled (with issues noted below and edits in links) so then try vlc (run from terminal) with a couple of dvds and see. Or use totem-xine and see what shakes out 
A/V quality issues are a separate story, usually centered around the a/v output and or drivers
As far as commercial dvds try something in addition to the patriot, I find it surprising that title was released as all region. (as far as I know there's no conflict between all region coding and RCE Region Protection, maybe they did release an all region? )

---

### Post by Roasted on 2008-06-21
I took all of your advice. I get the exact same thing still.

I'm going to do a fresh install. I was wondering, instead of formatting my home directory, which contains about 2 hours worth of music/pictures to transfer back over from my backup drive, perhaps I can just delete all of the hidden folders and simulate a fresh format from that directory?

---

### Post by Roasted on 2008-06-21
Okay, after more thought about this, I'm convinced a fresh install won't help. I look around and found a few issues.

For one, my idiot rear end had gutsy medibuntu in the repo's and not hardy medibuntu. I changed it, and now I have video back. For a while I lost video.

When I put a DVD in, Totem opens, then closes. Okay, fine, Totem sucks anyway. So I open VLC and go to open disc... it plays the intro to the movie, but when I go to play movie, afterwards it just closes the big screen and I'm left with nothing. It doesn't flow to the next chapter, which would be scene 1. Why? 

Also, under system - preferences - preferred applications, what's the command to run VLC as main? I'm trying to set it to my default yet all it lets me do is Totem or custom, and I don't know the custom command.

---

### Post by mc4man on 2008-06-21
i would do a fresh install and get this squared away first thing, either follow my few commands or follow nathan's sticky.
honestly I've done maybe 50 installs from edgy to hardy for myself and others and never had an issue with dvd playback. It's the first thing i do after the basic setup, it serves as a good test of A/V settings, drivers, ect.
What's somewhat perplexing is you seem to have everything fine, the disk is detected, parsed, ect. Based on the 1 terminal output you posted your only problem (excluding any quality issues) is your not getting all the keys decrypted. Maybe try this, with a dvd in your drive
```
export DVDCSS_METHOD=title && vlc dvd://
``` you can also substitute totem for vlc

---

### Post by Roasted on 2008-06-21
I did a fresh format.
I installed the medibuntu package as described on that one page you linked me to, which from what I can tell is the exact directions on the ubuntu wiki.

The Patriot - It opens with VLC as my default. However, like before, after the main title screen plays and I hit "play movie" VLC simply closes. The little player stays up, with play/stop/pause, etc... but the big screen disappears. I do however, have sound and video.

Pearl Jam Live Concert DVD - Thinking maybe the DVD for The Patriot was messed up, seeing as though it had a couple scratches on it, I figured I'd try a DVD that I take great care of, such as Pearl Jam Live Concert DVD from Madison Square Garden. (Great stuff btw :P) So I put it in, I get the main screen. I hit Play DVD on the menu. It begins to play the DVD... however... The audio sounds like it has a hiccup every 4-5 seconds. Think about Eddie Vedder singing with a hiccup every 4-5 seconds. That's what it sounds like.

I'm relatively certain I have to change my audio preferences, but I forget how. But for the time being, I figured I'd post back here to share my findings as I set up the rest of my system.

---

### Post by mc4man on 2008-06-21
That sounds good (to some extent). As far as the libs ect. you should be good. I guess I've been fortunate as far as sound, other than it not working occasionally once it was the quality was fine (mostly various audigy, soundblaster cards or built in intel) maybe look thru the sound sticky or search your model of sound device. 
As far as 'the patriot' that disk seems suspect, if you wanted to test something install vobcopy and with dvd in drive run ```
vobcopy -v -m -F 16 /media/cdrom0 
```(adjust path if needed) That will copy it to a video_ts folder in home dir. if it fails there is definitely a prob. with disk though it may be able to get by read errors (better than player)

---

### Post by Roasted on 2008-06-21
What good does that do me, though? I have problems with a 2nd DVD as well... (concert DVD)

---

### Post by Roasted on 2008-06-21
Okay, the same stands true with the Pearl Jam Concert DVD. The Patriot DVD had some kind of a haze on it that I didn't notice until I turned it on an angle to see the glare on the DVD. I cleaned it off with a microfiber cloth and now it works fine. Instead of shutting off after the main screen, it follows through to the first scene.

However, I tested Gone in 60 Seconds + my Pearl Jam Concert DVD again, and I still have the choppy audio every 4-5 seconds... it's particularly noticable with the concert DVD when you have it cranked and the guitar solo is chopping out.

Thoughts?

Edit - VLC has the audio chop. Totem does not.

Edit again - Audio chop fixed with Alsa. Tried to go back to Pulse just to test and I got this error. 

audiotestsrc wave=sin freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused.

---

### Post by Roasted on 2008-06-22
Hey - me again. I just came home from work, popped in the same Pearl Jam DVD I played last night... audio is choppy! Sweet! Love it! Absolutely love it.

Any help, folks?

Mind you - I set it back to ALSA and it seemed to have been better last night. Zero chopping. Today, it's BETTER than before, but still choppy. :(

---

### Post by Roasted on 2008-06-23
bumpity <3

---

### Post by Roasted on 2008-06-28
This makes me want to load XP.
Don't make me do it.
I don't want to relive that. 
Please...

---

### Post by mc4man on 2008-06-28
Why don't you first find out what your sound device is. Any of these commands should tell you.  aplay -l  ;  sudo lshw  :  sudo lspci -v
Then try searching based on that device. If you search these forums use advanced search and limit each search to a particular forum, you'll get better results that way. Try multimedia, hardware (both the current forums and archives), scroll down to development archives and try Development hardy heron, ect.

---

### Post by Roasted on 2008-06-29
This help?

jason@jason-hardy:~$ sudo lspci -v
[sudo] password for jason: 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: 66MHz, fast devsel, IRQ 12
	I/O ports at ff00 [size=32]
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: [44] Power Management version 2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at febff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7585
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	I/O ports at ea00 [size=256]
	I/O ports at ee00 [size=256]
	Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f462:7125
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at fb00 [size=16]
	Capabilities: [44] Power Management version 2

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at f600 [size=16]
	Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at f100 [size=16]
	Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe900000-fe9fffff
	Prefetchable memory behind bridge: fea00000-feafffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7125
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f000 [size=8]
	Capabilities: [44] Power Management version 2

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fe800000-fe8fffff
	Prefetchable memory behind bridge: 00000000fe700000-00000000fe7fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fe600000-fe6fffff
	Prefetchable memory behind bridge: 00000000fe500000-00000000fe5fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fe400000-fe4fffff
	Prefetchable memory behind bridge: 00000000fe300000-00000000fe3fffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f4000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel

05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Unknown device 2112
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at f8000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

jason@jason-hardy:~$ 



I'm just kind of frustrated. Things are just easier when they just work and I don't have to spend weeks configuring it.

And, let's face it. I put the DVD in my laptop with XP, I hit play, it plays. I play the DVD here, I get nothing. Hence my frustration... I hope what I pasted above will somehow spark an idea. :)

---

### Post by Roasted on 2008-07-05
Me again. Not stopping till I figure this out.

I forget where we left off, and what all I did, but let's start with this...

I have Ubuntu Hardy Heron 8.04.
I would like DVD playback to be enabled.
I will be using VLC Media Player.
What plugins are required?
What codecs are required?

Currently - I have zero audio. None. Nadda. Of the above 5 questions, what do I need?

---

### Post by Roasted on 2008-07-05
Okay, screw pulse. It's just, no... Not dealing with it.

Put all the settings back in for Alsa, suddenly everything works great. Go alsa!

New problem... my video feed from the CD, every few seconds there's a slight ripple that travels up the screen on the picture. It's not a big deal, after all, I have sound now and all... but still. I know this is exclusive to linux because I tried playing it on my XP Pro laptop through VLC and I didn't get any of it, and I compared specific parts of the DVD that it would happen at.

I even wiped down the CD with a microfiber cloth before putting it back in my Ubuntu desktop, and even then it did the ripple every 10 seconds or so.

What is this?

Update - I've tried several different players.

MPlayer Movie Player - It seems as if there are ripples at each third of the screen that stay stationary. Kind of a pain. This happens with DVDs as well as local music videos playing off of my hard drive.

Movie Player (Totem) - Works nice, however, it seems as if it has an unusually hard time fast forwarding ahead when playing a DVD. It seems to require an unusually high amount of buffer time to handle this task. But, the video feed seems decent.

VLC - Fast forwards great, however, it has that rotating ripple that slowly draws up the screen, then repeats every 10 seconds or so.

Is there such thing as Quicktime for Ubuntu? Or some kind of a high def player?

---

### Post by hyperair on 2008-07-06
With MPlayer, try configuring it to use the GL or GL2 video output driver instead of XV. With the command line one, it's -vo gl or -vo gl2.

With Totem, you can just drag the slider, or middle click on the place you want to jump to. I think middle clicking on the place to jump to will be yield much better performance.

Depending on what GPU you have, there may be some setting you can tweak on VLC. Please post the output of ```
xvinfo
```

---

### Post by Roasted on 2008-07-06
For what it's worth, I have a PCIE Nvidia 6600 256mb graphics card. I'm not at home to run that command, but I figured I'd post that anyway just to see if it can stir any ideas up.

But yeah, in reality, it's not a BIG deal... I mean, after all, the audio is completely synced with the video and that's what's important, but it's noticable if you happen to look for it. :(

---

### Post by Roasted on 2008-07-06
So I just opened up a music video with VLC, and it has really scratchy audio. However, running DVDs seems fine. Yet, I get the video feed ripple every 10 seconds.

Come on...

---

### Post by aBitLater on 2008-07-06
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by Roasted on 2008-07-06
Been there, done that.

I'm thinking maybe a fresh install is due. I have no idea what settings were messed with. Maybe it'd be a good idea.

Unless somebody can tell me specific plugins I would have to have installed, and maybe the names of specific plugins that are known to interfere? Anybody know that information?

---

### Post by Prefix100 on 2008-07-06
I know you've had this problem for awhile, but reading through the thread I find your situation quite confusing.

Maybe a current status report would do good.

---

### Post by Lawrence Talbot on 2008-07-06
I switched to using Kaffeine and DVD's play fine.  I had the same problem.

---

### Post by Roasted on 2008-07-06
> **Lawrence Talbot said:**
> I switched to using Kaffeine and DVD's play fine.  I had the same problem.

I'm currently downloading 64 bit Ubuntu and going to install that. If I run into the same problems, I will take up that suggestion. Thanks!

---

### Post by Roasted on 2008-07-06
> **Prefix100 said:**
> I know you've had this problem for awhile, but reading through the thread I find your situation quite confusing.

Maybe a current status report would do good.

Surely.

MPG music video that I have downloaded...
MPlayer Movie Player - scratchy audio.
Movie Player Totem - scratchy audio.
VLC Media Player - scratchy audio.

System - preferences - sounds = "Alsa" for everything. Each of the sound options in Mplayer, Movie Player, and VLC are all set to Alsa, so everything should be fine.

Audacious - set to Alsa as well. Sounds perfect. Crisp and loud. No scratching that the other 3 media players have yielded.

Any ideas? I'm gonna give this another day or two...

---

### Post by Roasted on 2008-07-11
Hey! I'm back!

K so, I've changed a couple things since I posted back here.

For one, I formatted, installed Hardy 64 bit, and started over. I installed restricted extras, gstreamer plugins, medibuntu, libdvdcss2 blah blah blah... works great!

Ran into a couple more issues...

Hoping I can get some help on these...

I'm running an MSI K8N Neo4 Platinum Motherboard. It has onboard audio which I use in auxillary with my stereo system. Makes for some good tunes.

I noticed if I set VLC's audio up really high, I get static at high volume. Yet, if I keep VLC at 50%, and crank my system volume, it's perfectly fine. I tested this same theory in XP with VLC... same mp3... turns out VLC in XP is perfect at 100%. Is VLC in Ubuntu? Nope. Anything above 60% gets awful clarity. Same with Amarok.

Why is this?

Also - I noticed if I set my PCM level to like 75% or so, and then crank VLC's volume, it doesn't have "as bad" of a static sound. With PCM + VLC cranked, it's awful. jdklfajsdlkfjadafsdf asdfasdfasd!!

---

### Post by hyperair on 2008-07-11
> **Roasted said:**
> Hey! I'm back!

K so, I've changed a couple things since I posted back here.

For one, I formatted, installed Hardy 64 bit, and started over. I installed restricted extras, gstreamer plugins, medibuntu, libdvdcss2 blah blah blah... works great!

Ran into a couple more issues...

Hoping I can get some help on these...

I'm running an MSI K8N Neo4 Platinum Motherboard. It has onboard audio which I use in auxillary with my stereo system. Makes for some good tunes.

I noticed if I set VLC's audio up really high, I get static at high volume. Yet, if I keep VLC at 50%, and crank my system volume, it's perfectly fine. I tested this same theory in XP with VLC... same mp3... turns out VLC in XP is perfect at 100%. Is VLC in Ubuntu? Nope. Anything above 60% gets awful clarity. Same with Amarok.

Why is this?

Also - I noticed if I set my PCM level to like 75% or so, and then crank VLC's volume, it doesn't have "as bad" of a static sound. With PCM + VLC cranked, it's awful. jdklfajsdlkfjadafsdf asdfasdfasd!!

Lower your PCM value. At PCM=100%, on some sound cards, sound will have static because some values go out of range of the speaker. There will be a certain PCM value where there is no more static. Try playing the MP3 in Totem and see if you have the same problem.

---

### Post by Roasted on 2008-07-11
Would a new sound card, even like a 30 dollar PCI one on newegg, prove to be better than my onboard sound card?

Would the same be true if I were using OSS or Pulse?

What's PCM, exactly? Does XP have the same thing?

---

### Post by hyperair on 2008-07-11
I cannot say. I've only ever used an onboard sound card. And honestly? I think onboard sound cards can support 5.1 surround sound, and I'm probably never going above 2.1 anyway, so I have no intention to get a non-integrated sound card. 

OSSv4 has software mixing, but not lower versions. Software mixing is essential for sound cards that don't support hardware mixing, in other words, the majority (if not all) onboard sound cards. I need software mixing, and have never used OSS (except once when I was still beginning to use Ubuntu and having no idea about whatever anything was).

PulseAudio is a high level sound server that does sound pre-processing using the CPU (not the sound card) before it passes it to the backend. The back-end is generally ALSA, but you can possibly use OSS as the backend, but it's complicated to set up and I have no intention on trying and hence do not know how. Anyway PulseAudio comes with a cool set of feature (which you may never find use for) such as networked sound (imagine using your laptop to simulate another pair of speakers and achieving 4.1 sound with it, or routing all the computers in your house to use one set of speakers) Anyway Ubuntu Hardy uses PulseAudio by default if I am not mistaken.

---

### Post by imjustsomeguy72 on 2008-07-12
I had a similar problem, nothing would work, even changing all the sound settings to ALSA.

However, I got around this by installing the package vlc-plugin-alsa. Then, I changed as many of the audio settings in VLC as I could to an ALSA device, restarted VLC, and hey pretso! It (finally) worked! I'm not sure if you'd tried this already, but if you haven't, definitely give it a shot.

(I also use onboard sound, btw)

---

### Post by Roasted on 2008-07-12
I just installed that plugin as you suggested and made sure all of the settings were Alsa, blah blah...

didn't change a darn thing.

I'm willing to bet it's just hardware limitation. I was into car audio for a long time, so I understand distortion, clipped signals, signal to noise ratios, etc... and I noticed when I change PCM, it lists "db gain=1.00" or whatever, and changes the number accordingly.

"db gain" is often referred to as the gain knob on an amplifier... and around the time I left the car audio scene, which was an easy 3-4 years ago, gain would easily distort over 75-80%... a lot of people would put their amplifiers on bench tests and see what kind of power the amps would push. They said after the 75/80 percentage mark, the power turns to "dirty power" which results in a clipped signal to the speakers... clipped signal = static... like what I'm seeing.

That's why people would always have headroom on amps. They'd get a sub that can handle 1,000 watts, and an amplifier that pushes 1,500 watts, and just keep the gain low. That way they had more power, yet, it was clean power. You just had to be careful and logical of how you set the amp up so the sub doesn't go boom. :P 

So, taking that into consideration with this, it seems to be unusually similar... and considering I'm using a stereo system with two built in powered subwoofers (one in each speaker) I'm willing to bet that my onboard card just may not either A: have the best driver, or B: may be hardware limited to going any further.

Granted, in XP, I can push it a little harder and it's fine, so the driver in XP may be better... but it also sounds like pure *** when I crank it to those levels... to the point where the subs sound like shamoo's fart. So even though in XP it can hold its ground better as far as volume level, it still gets distorted to the point where I doubt a better driver in Linux would make a difference, IF the driver is even a restriction at all now... it's simply speculation and an assumed guess that it is. But I really have no clue. :P 

I'm curious and looking around at some sound cards on newegg... I'm wondering if I spend like 30 bucks if it would be a significant enough difference to justify the dollars spent on it. Some people swear that I'll notice a change, others are like, ehh, not for 30 bucks. *shrug*

---

### Post by Roasted on 2008-07-12
All right, I got to do some thinking and do some research on PulseAudio more...

Reminder - I'm running Hardy 64 bit.

My question is this... I was thinking it was a hardware limitation as to why I was having these issues at high volume. At the same time, I'm wondering if it's the fact that Hardy is designed for Pulse.

What would the wiser thing be to do? Try installing Pulse? Or, eff it, and try a new card with Alsa?

---

### Post by wesswei on 2008-07-23
> **Roasted said:**
> All right, I got to do some thinking and do some research on PulseAudio more...

Reminder - I'm running Hardy 64 bit.

My question is this... I was thinking it was a hardware limitation as to why I was having these issues at high volume. At the same time, I'm wondering if it's the fact that Hardy is designed for Pulse.

What would the wiser thing be to do? Try installing Pulse? Or, eff it, and try a new card with Alsa? 

Any more luck? I was having some issues long ago. I simply downloaded medibuntu packages and everything was fine. I'm using onboard sound and an ati graphics card (not best supported in linux but making some way). Anyway, just don't give up. It seemed frustrating to me at first, but once I finally got everything working, I was excited, AND I knew my computer a lot better! 

DVD encryption is a bad thing, and Ubuntu tiptoes around the issue by not installing the proper software to unlock such features which should be available by default.

---

### Post by Roasted on 2008-07-24
Yeah, I'm pretty much good now. I forget what I was doing wrong... 

Question, though, while you're checking in...

Running Hardy 64. Alsa. Amarok. 

If sys-sound-pref = "alsa"
and
Amarok = "auto detect"
YouTube is happy when I play Amarok at the same time.
---------------------------------------------------------------------------
If sys-sound-pref = "alsa"
and
Amarok = "alsa"
YouTube gets pissed off. K, all good. Shut off Amarok. No big deal.

Question is... what audio pipeline is Amarok using when in "auto detect" to still sound the same, and yet... work?

---

### Post by hinsons on 2008-12-03
The issue is apparently VLC ( or more likely a shared library ).
I had exactly the same issue. With the following behavior:

1. Playing DVDs just fine through ogle or Totem ( Ubuntu Movie Player )

2. Installed VLC through synaptic.

3. watched a DVD.

4. restarted.

5. All access to /dev/dsp would fail ( this is what ogle reported, I can only imagine it was the same issue with Movie Player although I didn't go look to verify it )

6. Completely removed vlc and restarted.

7. Issue resolved. 

8. Why ? I have no idea. 

Hope this might help for future questions.

---

### Post by lukeiscool on 2008-12-03
totem is annoying me. keeps shutting down when i start to use it.

---

