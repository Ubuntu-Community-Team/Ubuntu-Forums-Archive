---
title: "Jaunty fast then slow out of sync video with stuttering sound"
date: 2009-05-02
forum: Multimedia Software
---

### Post by adam_kimber on 2009-05-02
I have looked around for solutions to this problem and am not really sure what the cause of this problem is. 

The symptoms. This happens in mplayer and totem-xine and totem-gstreamer. I cannot get VLC to work the sound is all garbled.

1) The video plays slowly with the sound out-of-sync with the picture
2) The video then plays REALLY fast to catch up with the sound
3) The sound stutters for a couple of seconds and then everything is in sync again for a few minutes 
4) repeat from 1

This happens on most videos. Can someone help!!! Thanks 

***UPDATE***

TWO POSSIBLE SOLUTIONS: 

> **aYs-Halo said:**
> Thanks for the hint! Combining these two suggestions here: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13)

actually appears to work for me :)

*update*
sometimes i have to do "killall pulseaudio" to get it to work after a reboot..

> **psyke83 said:**
> [https://bugs.launchpad.net/bugs/345627](https://bugs.launchpad.net/bugs/345627)

From what I have read, it seems that virtually *everyone* in this thread is suffering from this bug (which hasn't been resolved for everyone yet).

-------

Some things that might be helpful in diagnosing problem! 

```
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  23.976 fps  902.6 kbps (110.2 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.82:1 - prescaling to correct movie aspect.
VO: [xv] 640x352 => 640x352 Planar YV12 
No bind found for key 'MOUSE_BTN0'.                         0.3% 0 0 
A:  57.6 V:  57.5 A-V:  0.126 ct:  0.005 1379/1379  2%  0%  0.3% 63 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

```

-------------
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---------------- 
```

lshw
WARNING: you should run this program as super-user.
esteban                   
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2047MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2997MHz
          capacity: 2997MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority cpufreq


```

---

### Post by Mangus on 2009-05-02
same problem here, with every video or audio source: flash videos, divx, mp3 played with amarok etc...

---

### Post by Cresho on 2009-05-02
FLASH, GAMES, its bad.

---

### Post by adam_kimber on 2009-05-03
Hey I am glad its not just me!

---

### Post by Mangus on 2009-05-03
Well, any ideas?
This is a huge problem, and searching around i've found a lot of people with the same problem....but no solution yet

---

### Post by inspired on 2009-05-04
I found this thread whilst looking for threads on Ubuntu 9.04 being slow.
My system has become very slow in general since upgrading from 8.10 to 9.04. I shall raise that issue in another thread.

Another issue I experience, however, is that I can't play video on this machine any more. Since the up to 9.04 the playback is very poor. It can be okay if I keep the video in a tiny little window, but if I go to a larger window or fullscreen it looks like the machine can't render the video quick enough... making go slow, stopping, jumping to catch up, and so on. Perhaps this is related to what other people on this thread are experiencing.

I have only tried VLC.

Jonathan

---

### Post by adam_kimber on 2009-05-04
> **inspired said:**
> Since the up to 9.04 the playback is very poor. It can be okay if I keep the video in a tiny little window, but if I go to a larger window or fullscreen it looks like the machine can't render the video quick enough... making go slow, stopping, jumping to catch up, and so on. 

This is EXACTLY what I am experiencing. Its soooo annoying. :( Currently contemplating a downgrade or a distro swap.

---

### Post by amor0fati on 2009-05-05
I have this problem as well.  Thinking it might be a driver issue, I tackled that and ran into a number of new problems.  During these issues, I lost the use of my drivers for a time, and the problem persisted.  Now I've got all of my drivers and x server problems handled, and I still have the same issue.

---

### Post by DuncanR on 2009-05-06
I'm getting *exactly* the same problem. When watching videos on my local machine in Totem or on YouTube through Firefox/Flash, it plays ok for a while, then seems to go in slow motion for a while, then plays extra fast to catch up to where it 'should be'. The audio actually plays at the right speed but its the video speed that has mind of its own.

At first I thought that perhaps it was my due to me choosing to use nVidia's restricted driver, but then I switched back to the open source 'nv' driver and the problem is still there. I've even tried using the nouveau driver but it doesn't fix the problem so now I'm not convinced that its the video driver at all. I also have the 'desktop effects' turned off so thats not the cause either.

My machine isn't *that* slow (P4-3Ghz, 1Gb RAM, GeForce 7600) and I never had any video playing problems in 8.10 so I'm a bit disappointed to be honest.

I'm not really sure what to try next. Could it be something to do with PulseAudio? But if so, then why is the sound playing correctly?

We've just installed 9.04 on an old Dell laptop here at work and the window drawing/dragging performance is terrible compared to the same laptop running 8.10. Is there some regression with window drawing or desktop drawing that could also be affecting multimedia performance as well?

---

### Post by FritzOttoW on 2009-05-06
Hi,
I've the same Problem with all Videos avi, mov, Youtube....

As a possible solution I tryed the see the dma-disc mode:

hdparm  /dev/sda6

/dev/sda6:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 7296/255/63, sectors = 18988767, start = 98221473


And I was surprised to see nothing about DMS, so 
I wanted to set the DMA-mode of my disk, but I got only the message 

 hdparm  -d /dev/sda6

/dev/sda6:
 HDIO_GET_DMA failed: Inappropriate ioctl for device


Has somebody a solution about that Problem?

---

### Post by jefftickle on 2009-05-06
> **DuncanR said:**
> I'm getting *exactly* the same problem. When watching videos on my local machine in Totem or on YouTube through Firefox/Flash, it plays ok for a while, then seems to go in slow motion for a while, then plays extra fast to catch up to where it 'should be'. The audio actually plays at the right speed but its the video speed that has mind of its own.

I hate to drop a useless "me too" on ya, but this is also my problem.

We've ruled out codecs, because it affects them all the same and it also affects Flash, which also rules out individual frameworks (I've tried mplayer and vlc, too).  Anything showing "video" does this.  Now, I haven't had a problem with actual drawing on the screen (moving windows and such), so it's strictly video playback.

Sounds like you ruled out the nVidia drivers, and I doubt all of our hardware has gone bad at the same time (sawdust in the engine?)

I've also tried different -vo options in mplayer (xv, x11, gl, gl2) and all had the same problem.

I'm running Jaunty on x86-64, upgraded from a fresh Intrepid install, nVidia GeForce 9500 GT, Conexant CX23880/1/2/3 capture (probably irrelevant but you never know), Intel Core 2 Duo 3GHz.

Worth mentioning that I never had a single problem with videos in 8.10.  Only started happening the day I upgraded.

So, I guess it's the command line and 'mplayer -vo aa' for me :-)  Seriously though, any X hackers want to try and find out what changed?

---

### Post by adam_kimber on 2009-05-06
Ah we are slowly getting somewhere! Not drivers, not slow machines, happens in 9.04 only.

So we need to see if its a x86 or 64bit problem. I have 64bit and so does jefftickle? Anyone with 32bit? 

Could it be X itself? I will see if a newer vresion is floating around somewhere and see if i can break my system. I mean...... 

We also need to try and confirm whether its hardware. DMA on drives.

---

### Post by jonatanschroeder on 2009-05-06
I'm on 32bit and the same is happening to me on mplayer, xine, totem, skype, videos on flash like youtube, and even some radios that show info like the disk cover. I'm guessing it's something related to sound (I have the impression that CPU usage increases when the music being played has a lower volume), but it's just a guess.

---

### Post by jonatanschroeder on 2009-05-06
Did anyone create a bug report on this problem on launchpad? If so, could you provide the bug number? I don't like to repeat bugs that were already posted, but I cannot find an appropriate bug on this subject.

---

### Post by skiffler on 2009-05-06
I have a problem when playing streaming media (from BBC site) using either Firefox or Epiphany. Runs for a few seconds and then closes the browser. No problems with 8.04. Upgraded to 9.04 over the weekend. Thought initially that it was a Firefox 3.0.10 issue but with Epiphany acting the same way, it seems to be something more basic. Not a Linux expert.

---

### Post by jasidog on 2009-05-06
Another useless me too.

---

### Post by viduliya on 2009-05-06
I have the same issue with mplayer.  I think this is due to pulseaudio.  Please try this from a termial:

```
pulseaudio -k; mplayer -ao alsa myvideofile.avi
```

If your sound sync with video at this point then this is another problem with a program not working correctly with pulseaudio :(

When you run the above command from the terminal make sure you have no other sound apps running.  I had to make sure I turn off skype.  Without pulseaudio we can not use multiple sound applications simultaneously.

I think the pulseaudio server re-starts by itself at some point when you require it and when nothing is holding on to the sound hardware exclusively.  If you want to make sure you can logout and login again after running the above command to get things back to default behavior.

Unfortunately I have no good solution for this either :(

**UPDATE:**  I installed "ubuntu-restricted-extras" package and the problem seem to have disappeared.  I think it removed some old codecs and installed newer ones.  I am using janty defaults for all sound related packages.  No ppa or custom packages are installed.  I followed the guide for sound setup described here: [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+woes]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+woes")  Now mplayer is working nicely. :)

---

### Post by adam_kimber on 2009-05-07
Its not DMA, tested that last night. If you have SATA drives hdparm does not work. YOu will need to use sdparm. However Jaunty appears to automagically enable DMA on my drives. Type dmesg | grep ata and you should see that UDMA is enabled for your drives. 

Bug report will be submitted later on today. Its been a busy week! 

What versions of pulseaudio are you guys using? Standard Jaunty?

---

### Post by jasidog on 2009-05-07
Not in Ubuntu at the moment (Was doing my head in as there's also a big skype issue with pulse and I need it shortly.) to check exact pulsaudio version but whatever is standard jaunty 32bit yes.

Only thing i did odd was to use ext4 for the file system. However I just reinstalled with ext3 and the skype issue was still there. Not had a chance to try out video with that change as yet.

Thinking of downgrading to intrepid until it's sorted.

---

### Post by adam_kimber on 2009-05-07
Had problems with Pulse and Skype in Intrepid. Here is a workaround that worked fine. 

>  Firstly, add these lines:

default-fragments = 8
default-fragment-size-msec = 5

at the end of "/etc/pulse/daemon.conf"

Then, edit "~/.asoundrc" and add the following lines if they do not exist:

pcm.pulse { type pulse }
ctl.pulse { type pulse }

Install the libasound2-plugins package (on ubuntu, at least). (I also rebooted at this point, to restart the pulseaudio daemon - not sure if that was neccessary)

Finally, open Skype. Set the "Ringing" and "Sound Out" devices to "pulse", then set the "Sound In" to the plughw device of your microphone. 

From the [PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup") (why can't Ubuntu implement this entire guide? Then there would be NO problems (apart from the one mentioned in this thread.......)

---

### Post by jasidog on 2009-05-07
Cheers for the advice. :) I'd already tried that though and still 100% cpu. :( Sounds works allways did. Just hammers the cpu. 

Never had any skype issue at all on intrepid or the previous release also with pulse. Only current solution I've found is to set skype not to use pulse then it hogs the sound card. 

Still it's off topic for this thread.

---

### Post by usingruby on 2009-05-07
ugh, me too :( Has anyone filled a bug report so far, so that we can put the information there.

The system was working perfectly in Ubuntu 8.04, 8.10 and before the slow videos started with the upgrade

By the way: AMD64 bit system, dual core, 4GB, NVidia onboard graphic ship

---

### Post by usingruby on 2009-05-07
for flash checkout the solution mentioned here:
[http://ubuntuforums.org/showthread.php?t=1139243](http://ubuntuforums.org/showthread.php?t=1139243)

referencing this:
[http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/](http://bugfixbug.wordpress.com/2009/04/25/ubuntu-flash-does-not-work/)

=> sudo apt-get remove swfdec-mozilla

then reinstall flash for me it was flashplugin-installer and flashplugin-nonfree and not the mentioned adobe-flashplugin

---

### Post by nawitus on 2009-05-07
Try different players. I have this problem for totem, but totem-xine works perfectly.

Also, try VDPAU if you have 9.04 and NVIDIA binary drivers of 180+, using mplayer.

```

These are the different video codecs (-vc's).
vdpau at the end enables the hardware acceleration.
ffmpeg12vdpau -> ffmpeg12
ffh264vdpau -> ffh264
ffwmv3vdpau -> ffwmv3
ffvc1vdpau -> ffvc1

# HW accelerated:
./mplayer -vo vdpau -vc ffmpeg12vdpau file.mpg

# SW decoding:
./mplayer -vo vdpau -vc ffmpeg12 file.mpg

```
Replace mplayer with gmplayer to get gui.
Using VDPAU you can view HD films without using much CPU at all (it's being decoded in the GPU mostly!).

---

### Post by cowbellemoo on 2009-05-07
I have the same sort of problem.  I changed my sound output (System > Prefs. > Sound > Music & Movies) from PulseAudio to ALSA and playback is nice and smoothe again.

---

### Post by amor0fati on 2009-05-11
The last update seemed to fix my problems.

---

### Post by adam_kimber on 2009-05-12
I thought it did but its back :(

---

### Post by adam_kimber on 2009-05-12
Hmmm downgraded from the Muso repo and eveything seems to be fine now!

---

### Post by jasidog on 2009-05-12
Muso? Pretty sure i'm not using any such repo and still have problems.

---

### Post by suzumeuta on 2009-05-12
I offer a temporary solution.

Chances are you have ffplay installed if you installed medibuntu or other media packages.
"ffplay <video file>" will open a window with it. It's pretty much barebones, and I admit it's a bit uncomfortable to have around, but desyncs much less and does the work until a mainstream solution comes by. Your mileage may vary, but at least I can watch FLVs without everything sounding like a bad DJ in da house.
To control ffplay, you can click on a "percentage" of the video window to jump to the equivalent percentage of the video. Also you can, like in mplayer, skip with the arrow keys. 

Don't complain so much though ;) Real story here! (with some solutions too)
I am developing a game and right after the update I had to work on the sound system. Sound effects play more than one second after spawning, and tend to saturate the audio buffer resulting in clicking or the sound not playing. Decreasing the audio buffer size works (you'll find it also works in some players and console emulators!) but skyrocketed the CPU. However, I remembered a windows build worked OK, so I figured out something was wrong with my system audio. That's how I managed to find out the culprit, Pulseaudio!

To allow the sounds to come out with less lag, I started my SDL game engine from the console, like "SDL_AUDIODRIVER="esd" <program>". This will decrease the lag in SDL applications to a much more acceptable level. It is safe to use "esd", since it doesn't fail even if you don't have any ESD related package installed (which is probably the case with most of you :) Pulseaudio is supposed to be its "replacement").
To do this you need to install a different SDL package, libsdl1.2debian-all. Synaptic will automagically remove your conflicting library to replace it with the full one, so don't be afraid of breaking things if it asks you to remove your old libsdl1.2debian-??.

I hope it could help at least a bit :)

---

### Post by Neville Grech on 2009-05-13
Another useless me too. CPU isn't bogged down at all and it's quite funny to see videos on youtube speeding/slowing/speeding... you get it. I strongly suspect it's one of the codecs I have installed (but which one?). I shall try to purge and re-install some of them. I had upgraded from 8.10 (64-bit). I'm oddly surprised why this problem hasn't been fixed till now.

---

### Post by jonatanschroeder on 2009-05-13
My mplayer problem was solved by using xv as the video output.

mplayer -vo xv <file>

Anyone knows how to do the same thing (change the video driver) on flash?

---

### Post by Filipek on 2009-05-14
xv should be the default output probably I guess. Trying GL as output helped also a bit but this is not a solution:

```
mplayer <file> -vo gl
```

Disabling PulseAudio did the trick for me but it is obvious CPU does much more than it should be.

The problem becomes crucial when you try to play HD movies. For 720p it is so and so but you cannot skip any part - it does not synchronize together again.

1080p movies are not playable at all. This is a HUGE problem for Ubuntu being used as full home desktop computer system I guess. If anyone finds a viable solution, please make it sticky then...

thank you

---

### Post by psyke83 on 2009-05-14
Everybody,

See [bug #345627]("https://launchpad.net/bugs/345627"). In a nutshell, these issues are because of bugs in the intel-hda and intel8x0 kernel drivers (which are exposed by PulseAudio), and a fix is in the proposed kernel. Enable the proposed repository and upgrade to kernel 2.6.28-12-generic.

---

### Post by adam_kimber on 2009-05-14
> **psyke83 said:**
>  bugs in the intel-hda and intel8x0 kernel drivers (which are exposed by PulseAudio), and a fix is in the proposed kernel. Enable the proposed repository and upgrade to kernel 2.6.28-12-generic.

```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
```

```
lsmod | grep hda
snd_hda_intel         557620  3 

```

```
uname -a
Linux esteban 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:31:32 UTC 2009 x86_64 GNU/Linux
```

Still have the lag issues! :(

---

### Post by jasidog on 2009-05-14
Yeah I updated to the proposed kernel a couple of days back and it does seem to have improved performance a good deal. I hadn't posted back here about it because I was still trying to gauge that. There still seems to be problems for me. Flash playback has improved but it's still on occasion problematic. 

I had thought avi files and like were fixed but I came across some of the same old sync/stutter issues last night.

It does seem to have helped some though.

---

### Post by Filipek on 2009-05-17
> **psyke83 said:**
> Everybody,

See [bug #345627]("https://launchpad.net/bugs/345627"). In a nutshell, these issues are because of bugs in the intel-hda and intel8x0 kernel drivers (which are exposed by PulseAudio), and a fix is in the proposed kernel. Enable the proposed repository and upgrade to kernel 2.6.28-12-generic.

Thanks a lot for you tip but the problem is I don't have the integrated Intel graphic card, I have ATI 3850 with ATI's own drivers. I will install the above mentioned anyway in case there are more bugfixes hidden in it.

---

### Post by adam_kimber on 2009-05-19
> **Filipek said:**
>  I don't have the integrated Intel graphic card,.

As far as I know its to do with intel-hda (integrated sound card) / alsa / pulseaudio. I don't think that ATI graphics cards are part of the problem. Bizzarely it is the common consent that this problem of video lag is caused by buggy sound drivers!

---

### Post by BrowneR on 2009-05-19
I see this or similar behaviour in Amarok when playing music but not in Rhythmbox (xine vs gstreamer?).

Every so often the music speeds up and races ahead at say 1.5x speed then the audio pauses for a second (like some buffer has runs out) and the audio catches up to where it should be. Then it happens again. Sometimes it seems stable for minutes other times it happens all the time. CPU usage is generally normal for music playback.

Sometimes this is a problem with video too but it seems to depend on the file/player combination I use (totem/vlc/mplayer etc).

I have all latest updates from jaunty-proposed on a fresh 32bit install.

$ lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

$ uname -r
2.6.28-12-generic


Sometimes simply killing pulseaudio and restarting it seems to fix the problem temporarily. I will try unloading the snd_intel8x0 driver and using my USB DAC alone.

---

### Post by rdewit on 2009-05-20
Hi, since I experience the same problems as mentioned here, I created a bug entry: [1], which might be a duplicate of [2].
If you want to track progress, you can subscribe yourself to that bug and leave your comments there.

[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378606](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378606)
[2] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429)

---

### Post by psyke83 on 2009-05-20
> **rdewit said:**
> Hi, since I experience the same problems as mentioned here, I created a bug entry: [1], which might be a duplicate of [2].
If you want to track progress, you can subscribe yourself to that bug and leave your comments there.

[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378606](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378606)
[2] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337429)

They were both duplicates of [#345627]("https://bugs.launchpad.net/bugs/345627"), and I have marked them as such. Read the updated and original description of this bug and you'll see that it applies to you.

---

### Post by l-x-l on 2009-05-20
> **cowbellemoo said:**
> I have the same sort of problem.  I changed my sound output (System > Prefs. > Sound > Music & Movies) from PulseAudio to ALSA and playback is nice and smoothe again.

This worked for me. Thanks. [rant]As a side note... Pulseaudio and/or the intergration of it in Ubuntu sucks. [/end rant]

---

### Post by x20mar on 2009-05-22
Adding myself to the list here:

Jaunty 64-bit with nvidia G72M [Quadro NVS 110M/GeForce Go 7300] and Intel 82801G (ICH7 Family) High Definition Audio Controller

Any previously suggested idea did not work for me

---

### Post by adam_kimber on 2009-05-23
> **cowbellemoo said:**
> I have the same sort of problem.  I changed my sound output (System > Prefs. > Sound > Music & Movies) from PulseAudio to ALSA and playback is nice and smoothe again.

Hmmm. This combined with a previous post and a little research gave me a temporary solution. 

Last night I could not get an avi file to play. It kept slowing down stuttering catching up etc. It was unwatchable. Usually a few restarts of the file gets it playing smoothly, but this one wouldn't play ball. I then looked at this thread again and also how pulseaudio in later Intrepid and Jaunty releases is on autospawn, only if sound is played.

I discovered that if pulseaudio is not running when the movie file starts, I used Totem, then it plays fine. Pulseaudio autospawns back when sound is played again but seems to play nice! 

So if you have the problem. Stop the movie. Close the player. Open a terminal and type ```
pulseaudio -k
``` and restart movie. Should work fine! 

Can anyone confirm this?

---

### Post by adam_kimber on 2009-05-23
> **x20mar said:**
> (ICH7 Family) High Definition Audio Controller

There is something screwy going on with the HD Audio on Intel motherboards and Pulseaudio. That is far as I have got at the moment. :(

---

### Post by BrowneR on 2009-05-23
> I discovered that if pulseaudio is not running when the movie file starts, I used Totem, then it plays fine. Pulseaudio autospawns back when sound is played again but seems to play nice! 

So if you have the problem. Stop the movie. Close the player. Open a terminal and type ```
pulseaudio -k
``` and restart movie. Should work fine! 

Can anyone confirm this?

The problems I have with sound in Amarok seem to often be fixed by killing and restarting pulseaudio too. I cant confirm that this works every time because to be honest I've not tested it that much but it has worked a couple of times. I've just been issuing ```
 killall pulseaudio && pulseaudio -D 
``` but if it respawns itself i guess i dont need to do that.

I wonder if this is this something that occurs only after a suspend/resume cycle?

---

### Post by adam_kimber on 2009-05-23
> **BrowneR said:**
> I wonder if this is this something that occurs only after a suspend/resume cycle?

Quite possibly. I seem to have no problems if i keep pulseaudio "alive" after a restart. If I keep playing music then swap to a movie back to music etc and the audio is pretty much constant the error does not seem to come back. 

However if i leave the machine on for a while with no sound and try to play a movie there is much more of a chance that I will get the fast slow bug. 

We might be getting somewhere??!?!

---

### Post by Trist on 2009-05-24
Hi,
I have the same problem of video playback stuttering, speeding up and slowing down. But it only happens when I use Simultaneous Sound in Pulseaudio Device Chooser. What I did to fix this was using audacity I created a 1 Min long empty (no sound in the file at all) mp3 file and put it on a continuous loop in mplayer and added it to my startup apps. Now my Simultaneous Sound works perfectly and it doesn't add much to the CPU.

---

### Post by 11010110 on 2009-06-01
Hi everyone,

I am having a similar problem although mine only involves flash. all other video filetypes are just fine and in my case all audio works flawlessly. When a flash video is played it works unless it is set to fullscreen. this causes stutter slowdown and catchup of the video while the audio rolls on unhindered. flash games are also slow and glitchy. I dont mean to hijack the post or anything i was just wondering if anyone is having any similar problems. I have done extensive research and tried everything and no fix has been found.

Thanks everyone.

---

### Post by x20mar on 2009-06-01
No I think that your post is revelent and I get this same issue on some flash streaming sites (ie I'll get when I'm using 720p on Crunchyroll but not at all on youtube) I'll look into to seeing if there is a way to force flash to use ASLA (switching everything to ASLA and rebooting worked for me)

---

### Post by 11010110 on 2009-06-01
Well I tried setting everything to use alsa and rebooting and the stuttering of the video actually got worse. I also tried 
```
aoss firefox
```
after installing aoss and still no results. Its hard to believe that it is an audio problem in my case because the problem is seen in the video's actions. and for the mostpart only when fullscreen is used. Also when using the internet with Opera fullscreen flash seems to be more cooperative (although I ahte opera so I would like to find a firefox solution lol)

Thanks for the ideas I hope someone can figure this out! it seems to be holding back a lot of jaunty users.

---

### Post by adam_kimber on 2009-06-01
I believe junk flash is a seperate issue or possibly linked to the stuttering sound issue. I get both! Oh yeah. Most people I talk to who use Jaunty say flash sucks especially in full screen. 

PS Flash through wine in Firefox (for windows) is much smoother! Just don't go fullscreen it might crash FF (windows version). If anyone wants to know how to do this just shout, but there is plenty around to help!

---

### Post by dalem on 2009-06-02
I'm having the same problem... This is the first upgrade in Ubuntu that I have seriously regretted  making.

---

### Post by adam_kimber on 2009-06-02
I am contemplating flattening and installing Debian...... Been using Ubuntu since Breezy too. :(

---

### Post by BornOle on 2009-06-02
Pitching in with yet another "me too". I used Heron on this laptop for a long while and it was working perfectly. No more :(

---

### Post by yonyz on 2009-06-02
YAMT - Yet Another Me Too. Using 32bit and it happens on all media players. 9.04, of course.

---

### Post by 11010110 on 2009-06-02
If there was a simple way to downgrade to Intrepid id do it lol. I dont know if this bit of info will help anyone but compiz comes with a zoom feature and i tried to substitute fullscreen with just zooming in on a flash video until it reached a fullscreen size but again the video became laggy. the audio kept working perfectly as always though. it still works ok when not in fullscreen/zoom though... I dont know how they could release Jaunty knowing that this was such a serious problem for all of the normal desktop users out there. im very surprised they havent fixed it yet.

---

### Post by moody_mark on 2009-06-02
Installed 9.04 onto this old Satellite L20 here, from reboot sound works fine, when I try to play an AVI file in Totem or VLC the video goes slow after a while and then the sound starts to stutter consantly

---

### Post by moody_mark on 2009-06-02
Installed 8.04 instead, the machine is running just fine now and will play video and sound just fine, no problems. Shame as Im converting someone from Windows XP to Ubuntu and couldnt leave them with any excuse :-)

---

### Post by psyke83 on 2009-06-03
adam_kimber,

Perhaps you could edit post #1 with a reference to the bug report: [https://bugs.launchpad.net/bugs/345627](https://bugs.launchpad.net/bugs/345627)

From what I have read, it seems that virtually *everyone* in this thread is suffering from this bug (which hasn't been resolved for everyone yet).

---

### Post by aYs-Halo on 2009-06-03
Thanks for the hint! Combining these two suggestions here: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13)

actually appears to work for me :)

*update*
sometimes i have to do "killall pulseaudio" to get it to work after a reboot..

---

### Post by dalem on 2009-06-03
> **aYs-Halo said:**
> Thanks for the hint! Combining these two suggestions here: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13)

actually appears to work for me :)
Ditto... Appears to work for me, too.

---

### Post by heldal on 2009-06-07
> **psyke83 said:**
> adam_kimber,

Perhaps you could edit post #1 with a reference to the bug report: [https://bugs.launchpad.net/bugs/345627](https://bugs.launchpad.net/bugs/345627)

From what I have read, it seems that virtually *everyone* in this thread is suffering from this bug (which hasn't been resolved for everyone yet).

The description of that bug points to crackling noise with some specific audio-adapters. Most people in this thread are complaining about audio/video sync and stuttering which seems a complete different issue. 

Furthermore, the sync-issue is usually resolved by switching audio-output to anything other than pulseaudio. Video-players which support pulseaudio, alsa, oss and/or jack only have this problem with pulseaudio. I've been testing on a system set up for audio-recording with a number of studio-grade audio-adapters and they all have the same problem when used as a desktop with pulseaudio. The same system set up for recording with jack handles any number of audio sources and outputs in combination with video just fine. 

Increasing the timer frequency in the kernel (CONFIG_HZ_1000=y) may help, but then you'd have to build a custom kernel. This is an alternative to using a realtime-kernel when using a kernel release for which there is no realtime-patch available. It doesn't completely eliminate problems with pulse though.

The old pulseaudio-server in 8.10 didn't have this issue. Packages of the 9.04 version of pulseaudio for 8.10 had exactly the same problem when I tested them a few months ago. The latest version of pulseaudio (0.9.15) is if possible even worse than the one in ubunty 9.04 (0.9.14), while reverting to pulseaudio 0.9.10 from ubuntu 8.10 solves this problem (but requires a lot of recompiles of soundserver and apps to use it in 9.04).

A decent solution would be to make gstreamer use jack instead of pulse, but that currently requires manual editing of gconf objects, and even then it requires manual patching from application to output in jack as the gstreamer module for jack are missing an option to automatically attach applications to audio output devices when applications are starting.

---

### Post by adam_kimber on 2009-06-07
> **aYs-Halo said:**
> Thanks for the hint! Combining these two suggestions here: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/72)
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/344057/comments/13)

actually appears to work for me :)

*update*
sometimes i have to do "killall pulseaudio" to get it to work after a reboot..

This seems to work but I am not really sure! :(

---

### Post by adam_kimber on 2009-06-07
> **heldal said:**
> The description of that bug points to crackling noise with some specific audio-adapters. Most people in this thread are complaining about audio/video sync and stuttering which seems a complete different issue..

I will edit the first post to indicate that the quote might be a possible solution.

---

### Post by Squishy on 2009-06-08
I have this problem as well and tried al the suggested solutions.

:-?

---

### Post by psyke83 on 2009-06-08
> **heldal said:**
> The description of that bug points to crackling noise with some specific audio-adapters. Most people in this thread are complaining about audio/video sync and stuttering which seems a complete different issue. 

Furthermore, the sync-issue is usually resolved by switching audio-output to anything other than pulseaudio. Video-players which support pulseaudio, alsa, oss and/or jack only have this problem with pulseaudio. I've been testing on a system set up for audio-recording with a number of studio-grade audio-adapters and they all have the same problem when used as a desktop with pulseaudio. The same system set up for recording with jack handles any number of audio sources and outputs in combination with video just fine. 

Increasing the timer frequency in the kernel (CONFIG_HZ_1000=y) may help, but then you'd have to build a custom kernel. This is an alternative to using a realtime-kernel when using a kernel release for which there is no realtime-patch available. It doesn't completely eliminate problems with pulse though.

The old pulseaudio-server in 8.10 didn't have this issue. Packages of the 9.04 version of pulseaudio for 8.10 had exactly the same problem when I tested them a few months ago. The latest version of pulseaudio (0.9.15) is if possible even worse than the one in ubunty 9.04 (0.9.14), while reverting to pulseaudio 0.9.10 from ubuntu 8.10 solves this problem (but requires a lot of recompiles of soundserver and apps to use it in 9.04).

A decent solution would be to make gstreamer use jack instead of pulse, but that currently requires manual editing of gconf objects, and even then it requires manual patching from application to output in jack as the gstreamer module for jack are missing an option to automatically attach applications to audio output devices when applications are starting.

The bug I referenced deals with precisely the issue we're talking about - it's a bug in the ALSA kernel drivers, but it's only exposed by PulseAudio. If you read the entire report (both the updated and original description), you'll see that the buffering issues also cause audio and video to skip ahead and play at an irregular speed.

There was a potential fix for the HDA and AC'97 codecs in the -proposed kernel, but it was later reverted - perhaps it didn't help in all cases, or caused regressions elsewhere. I suggest everyone takes the time to read the bug thoroughly and subscribe (I've gone from a 99% certainty that everybody is experiencing that bug to 100% ;)).

P.S. Making GStreamer use JACK by default is not a solution at all. Leaving aside the fact that JACK isn't included by default, it's still ignoring the root cause of the bug.

---

### Post by psyke83 on 2009-06-08
By the way, be sure to take a note of the type of audio track (using Totem's Properties pane, for example) in a video file that plays irregularly.

I've noticed that only videos with audio content at a rate of 48000Hz causes the irregular playback/stuttering. Content which has audio at 44100Hz (the same rate as the PulseAudio server is running at) does not exhibit any unusual symptoms on my system (Jaunty and also Karmic on a separate partition).

---

### Post by heldal on 2009-06-10
> **psyke83 said:**
> P.S. Making GStreamer use JACK by default is not a solution at all. Leaving aside the fact that JACK isn't included by default, it's still ignoring the root cause of the bug.

Wasn't ment that way. It's just that JACK is fairly useful for audio-centric work, and it would be nice if desktop audio would play along a little nicer. Patches that make pulseaudio autoload jack sink/source when jackd is announcing it's presence on DBUS have been submitted to pulseaudio.org.

I read through all bugs related to audio problems and tried different versions of pulseaudio, alsa-drivers and kernel (up to and including 2.6.30-rc7) with no success with either of the soundscards I've got (HDA, Xonar DX, Roland Edirol USB, M-Audio Firewire). I also tried alsa drivers and libraries from git.alsaproject.org with no improvement. This made me doubt the claims that it would be a kernel and/or alsa issue.

It does however look like kernel 2.6.30 and the alsa-drivers included with it is close to solving the problem. I'm not yet sure if it is the kernel alone or a combination of updates that does the trick. The combination of things that look promising is:

[LIST]
[*]Alsa (1.0.19) and pulseaudio (0.9.15) updated from [http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu)
[*]Homebrew kernel 2.6.30 compiled with a 1000Hz interrupt frequency and stripped down to a bare minimum of drivers to support the actual hardware installed in the machine.
[/LIST]

---

### Post by cleatus99 on 2009-06-17
I am having same problem after upgrading FROM 8.10 Intrepid to 9.04 Jaunty. MP3s have static or don't play, video play back stutters or doesn't play. 

HP DV9200 CTO Laptop, AMD 64 Turion(tm) 64 X2 TL-64, 2 Gig RAM, Dual 500gig HDD, MCP51 HD Audio, Nvidia G70 [GeForce GO 7600], 2.6.27-11-generic

---

### Post by gilli4 on 2009-07-26
On my Jaunty (Ubuntu Studio) the modifications to /etc/pulse/daemon.conf did not help.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

Though it states that a fix was released, I didn't see any improvements on my ALC268 chip and I do keep my system updated.

It's actually an unfortunate situation for me since I'm using my PC for audio stuff 90% of the time.

Any new information on this?

---

### Post by martinbaselier on 2009-07-26
@fritzottow
hdparm is for ide devices, not for sata. Same goes for dma. 
If pulseaudio is the problem, don't just kill it, but uninstall it. 
I personally switched to  oss. It replaces both alsa and pulse functionality for me.

Edit: I only read the first page and did not see there were about 8 pages about this problem. I did not read them, so you can probably forget my comment.

---

### Post by gilli4 on 2009-08-01
Made the Ubuntu updates from two days ago for Jaunty which didn't seem to have any related updates at first sight. The updates required a restart.

Watched a 90min movie with totem today and any other video is totally in sync, no gaps in the sound. Even VLC, which had greater problems with this issue (tried to fix the sync by stopping/accelerating/slowing down the sound), is doing fine now.

Edit: Taking everything back. The problem still remains. It just happens randomly through the day.

---

### Post by EmEyKeYwAy on 2009-08-15
I can'  believe they didn't fix this yet. It's ******* annoying!

---

### Post by adam_kimber on 2009-08-16
Apparantly a lot of hte problem is with the HD Intel sound drivers. Which I think a lot of people have so I agree with EmEyKeywAy, I do not understand why it has not been fixed.

---

### Post by Filipek on 2009-09-18
Anybody knows whether this behaviour has been fixed in Karmic? I tried everything, normal videos are working but no chance for HD.

---

