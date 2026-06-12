---
title: "Ubuntu Studio calls for RealTime kernel testing."
date: 2007-05-12
forum: Multimedia Production
---

### Post by MetalMusicAddict on 2007-05-12
**UPDATE:**

Testing should now be done from from the Gutsy repos. As of 9/22/07 the -rt kernel supports the repo nVidia/fglrx drivers.

There are 32 and 64bit -rt kernels. **sudo apt-get install linux-rt** should grab everything needed.

Old post.
> Hi all you crazy kids. We would like testing/feedback on a RT kernel we have. You can find the repo for it [HERE]("https://wiki.ubuntu.com/RealTime")

It is a full Ubuntu kernel with Ingo's patches and the restricted modules. So far, the team has had no issues but we want more testing before we put it in our repo.

ATM this is a 32bit kernel only.

All the needed info *should* be on the WIKI page but ask away here.

---

### Post by Penguin Power on 2007-05-12
How rude, you came into #ubuntuforums, posted your link, and didn't even say hello?! =;

---

### Post by MetalMusicAddict on 2007-05-12
> **Penguin Power said:**
> How rude, you came into #ubuntuforums, posted your link, and didn't even say hello?! =;

Please stay on topic.

---

### Post by jondecker76 on 2007-05-13
I have used this realtime kernel on 2 machines

The first machine was a completely stock Feisty install with the built-in restricted nvidia driver (glx-new) and i had no problems

The second machine was a Feisty install with the latest NVidia drivers installed with Envy, no problems with this one either

---

### Post by MetalMusicAddict on 2007-05-13
> **jondecker76 said:**
> I have used this realtime kernel on 2 machines

The first machine was a completely stock Feisty install with the built-in restricted nvidia driver (glx-new) and i had no problems

The second machine was a Feisty install with the latest NVidia drivers installed with Envy, no problems with this one either

Thank you for the report.

---

### Post by sebos69 on 2007-05-13
Hi,

I just tried the realtime kernel on a Toshiba laptop, with no problems until now. I was able to use Jack in realtime, with 5ms Latency.

I did experience xruns (one xrun every 5-10 minutes) using Ardour combined with Jammin, but maybe this is not a big problem.

Moreover, I have the feeling than the desktop is more responsive with this patch, but maybe it's only psychological....

finally, a big thanks to the developpers, ubuntustudio is great :)

---

### Post by MetalMusicAddict on 2007-05-13
> **sebos69 said:**
> Hi,

I just tried the realtime kernel on a Toshiba laptop, with no problems until now. I was able to use Jack in realtime, with 5ms Latency.

I did experience xruns (one xrun every 5-10 minutes) using Ardour combined with Jammin, but maybe this is not a big problem.
This could be a couple of things actually. Settings and hardware have alot to do with it. What soundcard are you using and can you post a screenshot of your qjackctl settings?
> Moreover, I have the feeling than the desktop is more responsive with this patch, but maybe it's only psychological....
Some have said things are snappier.
> finally, a big thanks to the developers, ubuntustudio is great :)

Thanx. We're trying.

---

### Post by pekko on 2007-05-14
No problems with realtime kernel here. No xruns with 3 ms latency. I tried it also with 1,5 ms latency, but then I got few xruns and triple cpu hit so I went back to 3 ms. I can totally live with that, it's better than in WinXP with same hardware (Echo Audio Miamidi).

Compared to lowlatency kernel I could half the latency with realtime kernel.

---

### Post by MetalMusicAddict on 2007-05-14
> **pekko said:**
> No problems with realtime kernel here. No xruns with 3 ms latency. I tried it also with 1,5 ms latency, but then I got few xruns and triple cpu hit so I went back to 3 ms. I can totally live with that, it's better than in WinXP with same hardware (Echo Audio Miamidi).

Compared to lowlatency kernel I could half the latency with realtime kernel.

Thanx for the report.

---

### Post by sebos69 on 2007-05-15
> **MetalMusicAddict said:**
> This could be a couple of things actually. Settings and hardware have alot to do with it. What soundcard are you using and can you post a screenshot of your qjackctl settings?.

I use an Edirol FA-101 for recording. My next music session is on Friday, so I will report afterwards.

On the other hand, I did encounter a small glitch : when trying to compile the omnibook kernel module (omnibook.sf.net, a kernel module enabling multimedia keys for some laptops),  I get a compilation error:

```
 
make -C /lib/modules/2.6.20-15-realtime/build SUBDIRS=/home/valette/prog/omnibook/trunk modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.20-15-realtime »
  CC [M]  /home/valette/prog/omnibook/trunk/init.o
Dans le fichier inclus à partir de include/asm/timex.h:10,
          à partir de include/linux/timex.h:187,
          à partir de include/linux/sched.h:50,
          à partir de include/linux/utsname.h:35,
          à partir de include/asm/elf.h:12,
          à partir de include/linux/elf.h:7,
          à partir de include/linux/module.h:15,
          à partir de /home/valette/prog/omnibook/trunk/omnibook.h:19,
          à partir de /home/valette/prog/omnibook/trunk/init.c:18:
include/asm/tsc.h:1:28: erreur: asm-x86_64/tsc.h : Aucun fichier ou répertoire de ce type

```

basically, the file tsc.h is missing in that directory, but is present in the directory asm-i386, so the fix is trivial, with just a symbolic link

But maybe this is not really your primary concern.

---

### Post by MetalMusicAddict on 2007-05-15
> **sebos69 said:**
> But maybe this is not really your primary concern.

Correct. We're more concerned with it working with existing Ubuntu packages. I will however pass this on. Is this also the case with the -generic kernels?

---

### Post by sebos69 on 2007-05-15
> **MetalMusicAddict said:**
> Correct. We're more concerned with it working with existing Ubuntu packages. I will however pass this on. Is this also the case with the -generic kernels?

no, the omnibook module compiles fine on generic and lowlatency kernels

---

### Post by MetalMusicAddict on 2007-05-15
> **sebos69 said:**
> no, the omnibook module compiles fine on generic and lowlatency kernels

Ok. Ill have this looked into.

---

### Post by foo Utu on 2007-05-16
barely any xruns to speak of which is good, but my 3D graphics performance has taken a big hit using :

barf@barfsbox:~/bin/secondlife$ uname -a
Linux barfsbox 2.6.20-15-realtime #2 SMP PREEMPT Tue Apr 24 01:53:29 UTC 2007 i686 GNU/Linux
barf@barfsbox:~/bin/secondlife$ cat /proc/version
Linux version 2.6.20-15-realtime (root@godzilla) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Tue Apr 24 01:53:29 UTC 2007

---

### Post by sengoku on 2007-05-18
it seems to work just fine on my setup. with a buffer size of 32 (1.33msec latency) it starts giving the odd xrun, but at 64 it seems stable (even with loading programs etc).

setup : 2.4Ghz dual core intel with a firewire presonus firebox (which runs fine on freebob).

excellent work on ubuntu studio, by the way. thanks!

---

### Post by tapazzz on 2007-05-20
Is there any support infrastructure for setting up  the interrupt handler priorities? Planet CCRMA e.g. provides the rtirq init script for setting up the irq handelr priorities.

---

### Post by sebos69 on 2007-05-20
Ok, you guys rock!

My last recording session using this kernel was flawless. The only times I had xruns was when launching applications and/or wiring them together with jack, but no problem during playback or record. Thumbs up! I used an edirol FA-101 (firewire interface), with freebob drivers.

A small note : hibernation works but sometimes, after resume, I get a message saying "HAL could not hibernate", which I don't understand as the hibernation/resume process went fine :)

---

### Post by smackcode on 2007-05-20
works quite well on my s270 notebook, but i got compilation errors when I try to build fglrx with the realtime kernel.

---

### Post by mosteo on 2007-05-21
Everything seems ok here, feisty in a toshiba u200 laptop with x86 32bit processor. I still get some xruns from time to time, even after following the suggestions in 

[http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

but I'd attribute them to the low-quality integrated sound chipset (Intel HDA).

---

### Post by barbe-et-hache on 2007-05-22
Unbuntu studio is very long to start with this kernel.

The new kernel is very good. I have no more xruns problems. With the Ubuntu Studio kernel, jack crashes after a will complaining of xruns while there wasn't any during a few minutes. Now I can play for a long time without any problem.

I tested the kernel with JACK Raq, Hydrogen and Ardour together. 

I was able to use my card with a lower latency (configuring for 48000Hz, period = 64 frames, buffer = 4 periods) while with the other kernel I used 128 frames/period.
This config gives me error when the the cpu usage become higher than 30%.  I get the following messages but it doesn't cause any problem to my playing or recording.

delay of 673.000 usecs exceeds estimated spare time of 673.000; restart ...
delay of 673.000 usecs exceeds estimated spare time of 673.000; restart ...
delay of 677.000 usecs exceeds estimated spare time of 673.000; restart ...
16:33:21.490 XRUN callback (31 skipped).

When I use 128 frames/period, I have no error message.

note : ndiswrapper not working


hardware : 
- hp dv2310 with AMD64 and nvidia go6150
- m-audio fast track usb

---

### Post by alistair_j on 2007-05-24
Works well.
Solved the MIDI problems I had with the 2.6.20-15-lowlatency kernel shipped with Ubuntu Studio, where the computer would freeze

MIDI stable as under this kernel.

Audio Card: MAudio 1010lt, with a good stable 5.8ms latency

Exellent work by the Ubuntu Studio Team!!!!

---

### Post by Drophere on 2007-05-24
Works perfectly on my onboard via chipset.
Xruns on my RME Digi 96/8 Pro.
Xruns on my Novation Speedio.

---

### Post by zettberlin on 2007-05-24
apt-get claims that there is no package linux-realtime after addding the repo.

Could it be, that there is no package for amd64 yet?

---

### Post by Nycthbris on 2007-05-24
Worked pretty well for recording with JACK, Ardour, and Hydrogen. I had 5.6ms latency at 44.1kHz with my integrated sound card. I had bouts of xruns at ~7 minute intervals, but nothing to disrupting (they're probably from some background process I haven't bothered to look for yet). I can't seem to compile the VirtualBox kernel module because it can't find the sources directory. Could someone tell me how to install the sources for the realtime kernel? (I'm not to sure of the package name) Thanks!

HW setup: IBM Thinkpad G41, P4 3.33GHz, nVidia FX Go5200, 1GB RAM, Integrated Intel soundcard & Audigy 2ZS Notebook.

Also much thanks to MMA and all the contributors to UbuntuStudio, its freakin' awesome!

---

### Post by Sandsound on 2007-05-25
Besides from looking SO cool (I just love the theme), it runs real smooth with none or very few x-runs on a 10msec latency setup in Jack.
Only problem is Muse crashing when i load SimpleDrums, but it might be a Muse related problem, other than that I havent had a single crash.

Great work =D>

My specs. : Athlon64 / Nvidia chipset / G-force 7600 / 1Gb ram / Audigy2z

---

### Post by Techneon on 2007-06-04
Well, to some extent I've been testing it.

I noticed I'm having problems attempting to compile mad wifi on my macbook when using the realtime kernel (asm_x64 related file not found or some such, wouldn't necessarily blame it on the kernel however).

The only other issue I've had, I had similar with the lowlatency one, and that has been outlined in [this]("http://ubuntuforums.org/showthread.php?t=463766") forum post if you'd care to have a read :).

Again, someone in this thread indicated an issue w/ the Intel HDA onboard audio, and as with any onboard audio I only trust it so far, but if you can suggest anything I'm happy to give it a try.

---

### Post by sebos69 on 2007-06-06
> **Techneon said:**
> Well, to some extent I've been testing it.
I noticed I'm having problems attempting to compile mad wifi on my macbook when using the realtime kernel (asm_x64 related file not found or some such, wouldn't necessarily blame it on the kernel however).


I had a similar issue with 2.6.20-16 realtime when compiling the omnibook kernel module : 
```

include/asm/tsc.h:1:28: erreur: asm-x86_64/tsc.h : Aucun fichier ou répertoire de ce type

```

I think it is a kernel problem.
```

$ more /usr/src/linux-headers-2.6.20-16-realtime/include/asm-i386/tsc.h 
#include <asm-x86_64/tsc.h>

```

the file /usr/src/linux-headers-2.6.20-16-realtime/include/asm-i386/tsc.h points to an other header (asm-x86_64/tsc.h) which does not exist.

It does exist in the 2.6.20-15 version of the kernel.

Typing

sudo cp /usr/src/linux-headers-2.6.20-15-realtime/include/asm-x86_64/tsc.h /usr/src/linux-headers-2.6.20-16-realtime/include/asm-x86_64/

Solved my issue.

---

### Post by ElEdwards on 2007-06-08
A question....

I do commercial voice-overs and have been using WinXP and Adobe Audition for quite a while in my studio.  Being tired of Windows and wanting to experiment with Linux, I've installed Ubunto 7.04 on my laptop as a dual boot with WinXP.

My laptop is a Presario 2170US, 40 Meg ATA HDD, 512 Meg RAM.

I've played a bit with Audacity in Ubuntu.... and now I'm wondering if I'd see better performance installing Ubuntu Studio and using it for my audio/voice-over purposes, feeding it from either a mic directly plugged into my laptop or on my desktop, feeding my Sound Blaster Audigy 2 card from my Macky mixer.

Thanks for any advice :)

---

### Post by Siggimund on 2007-06-09
Hi MetalMusicAddict

I've got one of those dreaded hda-intel ICH7 cheapo build in soundcards, Its a Toshiba Tecra A6 (PTA60E-01D015ED). laptop. So I've struggled alot to get zero XRUNs and that only seems possible with acpi=off even with your realtime kernel.
Anyway back to the bug report:

One difference I've noticed in the kern.log (though I haven't noticed any actually functionality loss) between lowlatency and realtime is this message just after I connect to a ntfs drive:
/var/log/kern.log
> 
...
Jun  8 00:05:20 tecrax kernel: [  457.118589] NTFS driver 2.1.28 [Flags: R/O MODULE].
Jun  8 00:05:20 tecrax kernel: [  457.118955] NTFS-fs warning (device sda2): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
Jun  8 00:05:20 tecrax kernel: [  457.208219] NTFS volume version 3.1.
Jun  8 00:05:27 tecrax kernel: [  463.293268] [color="red"]**BUG: at arch/i386/kernel/smp.c:557 smp_call_function()**[/color]
Jun  8 00:05:27 tecrax kernel: [  463.293289]  [smp_call_function+297/304] smp_call_function+0x129/0x130
Jun  8 00:05:27 tecrax kernel: [  463.293315]  [tick_handle_periodic+23/112] tick_handle_periodic+0x17/0x70
Jun  8 00:05:27 tecrax kernel: [  463.293329]  [trigger_softirqs+51/64] trigger_softirqs+0x33/0x40
Jun  8 00:05:27 tecrax kernel: [  463.293335]  [__set_page_address+85/192] __set_page_address+0x55/0xc0
Jun  8 00:05:27 tecrax kernel: [  463.293345]  [do_flush_tlb_all+0/80] do_flush_tlb_all+0x0/0x50
Jun  8 00:05:27 tecrax kernel: [  463.293358]  [on_each_cpu+44/128] on_each_cpu+0x2c/0x80
Jun  8 00:05:27 tecrax kernel: [  463.293376]  [flush_tlb_all+27/32] flush_tlb_all+0x1b/0x20
Jun  8 00:05:27 tecrax kernel: [  463.293384]  [kmap_high+376/896] kmap_high+0x178/0x380
Jun  8 00:05:27 tecrax kernel: [  463.293491]  [default_wake_function+0/32] default_wake_function+0x0/0x20
Jun  8 00:05:27 tecrax kernel: [  463.293512]  [<f8ea218c>] ntfs_end_buffer_async_read+0x18c/0x310 [ntfs]
Jun  8 00:05:27 tecrax kernel: [  463.293559]  [end_bio_bh_io_sync+0/64] end_bio_bh_io_sync+0x0/0x40
Jun  8 00:05:27 tecrax kernel: [  463.293564]  [mempool_free+58/128] mempool_free+0x3a/0x80
Jun  8 00:05:27 tecrax kernel: [  463.293576]  [end_bio_bh_io_sync+0/64] end_bio_bh_io_sync+0x0/0x40
Jun  8 00:05:27 tecrax kernel: [  463.293583]  [end_bio_bh_io_sync+35/64] end_bio_bh_io_sync+0x23/0x40
Jun  8 00:05:27 tecrax kernel: [  463.293591]  [bio_endio+74/144] bio_endio+0x4a/0x90
Jun  8 00:05:27 tecrax kernel: [  463.293595]  [__next_cpu+18/32] __next_cpu+0x12/0x20
Jun  8 00:05:27 tecrax kernel: [  463.293600]  [__add_entropy_words+94/448] __add_entropy_words+0x5e/0x1c0
Jun  8 00:05:27 tecrax kernel: [  463.293622]  [__end_that_request_first+385/1136] __end_that_request_first+0x181/0x470
Jun  8 00:05:27 tecrax kernel: [  463.293655]  [kmem_cache_free+103/128] kmem_cache_free+0x67/0x80
Jun  8 00:05:27 tecrax kernel: [  463.293673]  [<f8842485>] scsi_end_request+0x25/0xd0 [scsi_mod]
Jun  8 00:05:27 tecrax kernel: [  463.293706]  [<f8842626>] scsi_io_completion+0xa6/0x3e0 [scsi_mod]
Jun  8 00:05:27 tecrax kernel: [  463.293729]  [__schedule+825/3888] __sched_text_start+0x339/0xf30
Jun  8 00:05:27 tecrax kernel: [  463.293766]  [<f89699b5>] sd_rw_intr+0x75/0x2e0 [sd_mod]
Jun  8 00:05:27 tecrax kernel: [  463.293810]  [<f883d3e4>] scsi_finish_command+0x54/0xb0 [scsi_mod]
Jun  8 00:05:27 tecrax kernel: [  463.293845]  [blk_done_softirq+107/128] blk_done_softirq+0x6b/0x80
Jun  8 00:05:27 tecrax kernel: [  463.293858]  [ksoftirqd+272/576] ksoftirqd+0x110/0x240
Jun  8 00:05:27 tecrax kernel: [  463.293876]  [ksoftirqd+0/576] ksoftirqd+0x0/0x240
Jun  8 00:05:27 tecrax kernel: [  463.293879]  [kthread+186/240] kthread+0xba/0xf0
Jun  8 00:05:27 tecrax kernel: [  463.293888]  [kthread+0/240] kthread+0x0/0xf0
Jun  8 00:05:27 tecrax kernel: [  463.293899]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10
Jun  8 00:05:27 tecrax kernel: [  463.293916]  =======================
...


This only accurs with the realtime kernel but not with the low-latency from Ubuntu Studio

Anyway please tell me if you need more debugging info and how and what and I'll try and deliver.

and btw: many thx for working on this :D 

Siggimund

PS I haven't really tested minimum latencies yet course the hole acpi/hda-intel vs XRUNS has kind of kept me occupied.

---

### Post by Zaka on 2007-06-12
So,apparently I am the only one who gots problems with nvidia...
After installing the kernel realtime, i've reboot and I've got an xorg screen saying it was not possibile to load drivers, so i need to reset on 'nv' drivers.
I've tryied to reinstall the nvidia drivers and to resume my old xorg.conf .
It doesnt want to work .I can only use the 'nv' drivers. (I really want 3d acceleration ;)
It is also a mess working with jack in realtime with freebob (i need to hack some files for permissions) and after that, now it works but only the first time it runs, so if jack crashes theres no way to make it start again..only by rebooting..
If anyone knows how to fix this issues I'll really apreciate !!! (of course) :D

pc specs:
TOSHIBA Satellite laptop
nividia geforce 440 go
Pentium 4 intel - 2.2 GHz
edirol FA-101

---

### Post by rockyraccoon on 2007-06-13
i am using the 2.6.20-16-realtime kernel with a x2 2.8 ghz amd, 4 gig ram, and an m-audio delta 44. i've been recording bass and drums every day for the past week on ardour, leaving jack connected and recording audio for hours at a time with almost no xruns. 2.9ms latency, 44100 sampling rate,64 frames per period. it works wonderfully.

---

### Post by border on 2007-06-14
a while ago I found a kernel in (I think) your repositories:

linux-image-2.6.22-1-rt 

In combination with my Edirol UA-101 it work really well, it was the best kernel I had ever tested (self built and packages) for audio work. I felt like I could finally do some real audio work, but after I had to reinstall my sytem, that very kernel is not in the repositories no more, nor is a follow up to that kernel.

Where did it go?

Cause the realtime kernel in the feisty repositories just isn't performing as well (a few leagues lower). 
My onboard soundcard is a real pain when trying out jack (it's on a macbook, so standard intel ICH7 stuff?), what kernel it is on seems to not matter much (I get thousands of xruns anyway in a few minutes).

But the main question remains: where can I find that kernel, or another one which performs as well?

---

### Post by fredj on 2007-06-15
I have installed the realtime kernel and my Intel HDA audio chipset is working perfectly so far.
Of course its not up to professional standards, the lowest latency I have been able to achieve 
running jackd in realtime mode is 8.71 msec , without xruns, not bad for a notebook chipset
and maybe good enough to record one or two audio tracks and combine them with a few midi
tracks. I will continue testing to see how much the latency needs to be increased under greater
load.

So far the kernel seems to be rock solid, but I will report any bugs I find. In the meantime I 
have a question for you. I can only run jackd in realtime mode if I start it in a root console.
I would like users to be able to run audio programs from the desktop but with root permissions.
This used to be possible under Debian by making users members of the audio group and
giving the audio group permission to to escalate programs to root privledges. Do you know how 
to do this under Ubuntu?

---

### Post by MetalMusicAddict on 2007-06-15
> **fredj said:**
> I have installed the realtime kernel and my Intel HDA audio chipset is working perfectly so far.
Of course its not up to professional standards, the lowest latency I have been able to achieve 
running jackd in realtime mode is 8.71 msec, not bad for a notebook chipset and maybe
good enough to record one or two audio tracks and combine them with a few midi tracks. I will
continue testing to see how much the latency needs to be increased under greater load.
You can do better. Play with the frames/periods in JACK Control.
> So far the kernel seems to be rock solid, but I will report any bugs I find. In the meantime I 
have a question for you. I can only run jackd in realtime mode if I start it in a root console.
I would like users to be able to run audio programs from the desktop but with root permissions.
This used to be possible under Debian by making users members of the audio group and
giving the audio group permission to to escalate programs to root privledges. Do you know how 
to do this under Ubuntu?

This is a common issue we take care of if you install Ubuntu Studio from disk.

Do this then logout/in:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'

```

---

### Post by fredj on 2007-06-15
Thanks for the swift reply that has solved the problem. I will keep experimenting with latency.

---

### Post by fredj on 2007-06-16
Ardour seems to be a bit unstable on my system, not sure why, so I went back to Rosegarden. 
I have experimented with playing back 9 stereo tracks and at the same time recording an audio track.
No Xruns and all this at a latency of 2.9 msec with 4.2% cpu usage. Kernel seems rock solid and who
could say after this that Intel's HDA audio is no good.

---

### Post by kayosiii on 2007-06-17
Just popped the realtime kernel into Kubuntu.... I have tried it in Ubuntu Studio too  but my highly customised Kubuntu is still my primary. The difference is night and day...

I am able to push a period size of 128 with a sample rate 96000 with my Presonus Firebox... I basically only get xruns when starting up or closing applications. ZynAddsubfx goes a little bit wacky with complex sounds and lots of polyphony -- Bringing it all back to 48000 basically seems to help that a lot.

With regards to ubuntu studio - default ownership of raw1394 really needs to be a group that the owner belongs too and the groups setup in the user manager was apsolutely useless.

Otherwise colour me impressed

---

### Post by fredj on 2007-06-28
Encouraged by the low latency I could get with the Intel HDA sound chipset on my notebook. I decided to
try connecting up my Edirol UA25 usb device. After some initial problems which were caused by the USB 
hardware on my Q35 notebook, it is now running with no problems and with half the latency I could get in
Sonar (with Asio drivers) under Windows XP. 

It now seems to me that Feisty with the realtime kernel is a far superior platform for audio than Windows ever
will be. The other people in this who also deserve praise are the programmers of Jackd and the Alsa sound
system programmers.

---

### Post by pirxthepilot on 2007-07-01
Hi all!

I've added the necessary repositories as specified on this wiki:

[https://wiki.ubuntu.com/RealTime/Feisty](https://wiki.ubuntu.com/RealTime/Feisty)

but thing is, I can't seem to get the **linux-patch-realtime-preempt-2.6.20** source package.  I will be needing this because I am currently using a customized kernel based on the latest Ubuntu kernel (added reiser4 support), so that means I can't use the original realtime patch from [http://people.redhat.com/mingo/realtime-preempt/](http://people.redhat.com/mingo/realtime-preempt/).

Could anyone point me to the location where I can get the Ubuntu-specific realtime preempt source?

Thanks a lot!

---

### Post by kwk on 2007-07-03
hallo,
it rocks!

toshiba tecra M1, 1.4GHz, 512RAM

$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XP4m32 (rev 91)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
05:00.0 Multimedia audio controller: Xilinx Corporation RME Hammerfall DSP (rev 0f)

the only startup problem: i had to change »priority« to 0 (it was 1 as default) in the Jack-settings to be able to run without xruns. (i also modified /etc/security/limits.conf as described above).

Running stable now with 128 frames/period, I'm having xruns when i start an application, but not always.

it works also with 64 frames (=2.x ms!), but that's pretending to much from this machine..

jack is not starting with 32 and 16 frames.

working sample rates is 44100 and 48000Hz, independently from frames/period, actually though, i'm not shure if this is a driver related issue (RME hammerfall dsp)?

thank you!
kwk

---

### Post by morgan_greywolf on 2007-07-05
I've been testing the realtime kernel and I've had random X server hangs. These seem to lock up the whole PCI bus sometimes, because the NIC becomes unresponsive. These do not occur with the low-latency or generic kernels. I've posted requests for help, but no one seems to know anything. Here's my setup:

AMD Athlon 1800+
1 GB DDR-266 RAM
MSI-brand VIA KT600 chipset motherboard
nVidia GeForce 5700 AGP 8X video card w/128 MB
300 GB SATA HDD
Onboard VIA VT823x audio
UbuntuStudio 7.04
Kernel 2.6.20-16-realtime

The good news:  no significant Xruns with 5-track recording.

---

### Post by fredj on 2007-07-07
How often do these hangups occur and how long do they last?

---

### Post by jd0739 on 2007-07-08
OK,

Have plugged in the Realtime kernel.

Platform - AMD Duron 1200, 512meg, OnBoard SIS Sound, Ubuntu Studio with 2.6.20-16-realtime Kernel

Prior to Ubuntu Studio I was using out of the box Fiesty............
When launching JACK I was getting numerous XRUN's.......
Any Syth's I used were stuttery at best.

I then heard about Ubuntu Studio which ships with a low latency Kernel????(Is this correct)
anyway......there was a small improvement with regards to XRUN's in JACK.

I then heard about Realtime............

Maybe its just me but JACK runs like a well oiled machine.
Any Synths have long clear notes........I havent had any crashes...........allllelujia......woop wooop.
Keep up the good work fella's

---

### Post by fredj on 2007-07-08
When you boot into the realtime kernel, wireless network drivers which are loaded through ndiswrapper
fail to load. So wireless networking is inoperable.

---

### Post by Cryophallion on 2007-07-18
> **Zaka said:**
> So,apparently I am the only one who gots problems with nvidia...
After installing the kernel realtime, i've reboot and I've got an xorg screen saying it was not possibile to load drivers, so i need to reset on 'nv' drivers.
I've tryied to reinstall the nvidia drivers and to resume my old xorg.conf .
It doesnt want to work .I can only use the 'nv' drivers. (I really want 3d acceleration ;)
It is also a mess working with jack in realtime with freebob (i need to hack some files for permissions) and after that, now it works but only the first time it runs, so if jack crashes theres no way to make it start again..only by rebooting..
If anyone knows how to fix this issues I'll really apreciate !!! (of course) :D

pc specs:
TOSHIBA Satellite laptop
nividia geforce 440 go
Pentium 4 intel - 2.2 GHz
edirol FA-101

Sorry to hop off topic, but I thought I'd answer this problem real quick, as it was driving me nuts too:

See this post - you need to install restricted modules:

[http://ubuntuforums.org/archive/index.php/t-468549.html](http://ubuntuforums.org/archive/index.php/t-468549.html)

Off to try real time now...

---

### Post by fredj on 2007-07-18
The solution to wireless drivers not loading under ndiswrapper in the real time kernel is simple.
Uninstall ndswrapper with modprobe -r. Then install the latest version of the Realtime Kernel headers
and rebuild ndiswrapper from source. Finally re-install your windows wireless driver and modprobe it.

---

### Post by znaut on 2007-07-20
So far so good for me...

What's interesting is that Ubuntu Studio wouldn't even boot for me with the low latency kernel.  The generic version works fine.  With the real time kernel installed on Studio it boots and everything runs great so far.  Ardour 2 and Jack are cruising along happily.

System is an Athlon 3000+ w/ 1G ram.  On board nvidia sound and PNY 7600 video card.  All kernel versions used are 2.6.20.16.

---

### Post by Sheik Yerbouti on 2007-07-26
I installed the realtime kernel everything went fine. Except I too experience random graphics subsystem lockups. X windows becomes totally unresponsive and you cannot get a virtual terminal or anything. A hard reboot is required to recover. I do not get this behavior at all on the low latency or generic kernels. It's ashame because while it was working the audio performance was stellar.  My setup. I may try tonight to pull my second video card (SLI)  to see if that fixes the crashing issue.

Dell XPS 600
Intel Pentium 4 3.8 ghz
2 GB Ram
500 GB SATA drive
2 Nvidia 7800 GTX in SLI (SLI off in X)
Soundblaster Audigy 2
Ubuntu Studio 7.04

---

### Post by Sheik Yerbouti on 2007-07-27
So I pulled one of the video cards out of the system. And so far I have had only one lockup and that was when I was doing a large multigigabyte copy from a an NTFS partition. I have seen that before I think without the realtime kernel. So I think it's good now.

Cheers

---

### Post by MetalMusicAddict on 2007-07-30
We have the kernel in the Gutsy repos now. We will be calling for testing as soon as the restricted modules drop. So for anyone wanting to test now (without restricted modules) go for it.

---

### Post by flowbot on 2007-07-31
The HDA Intel audio chip on my Inspiron 1420 is not working with the realtime kernel. It doesn't output any sound. It works with the generic kernel, but only with [this fix](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly). The card seems to be detected with realtime, and I can run jack (with almost no xruns), but nothing is output. I've checked all mixer settings.

I'm pretty keen to get the realtime kernel working, though, cos even with lowlatency kernel I get a stream of xruns when running jack. 

Is there any known issues with this chip and the current realtime kernel or alsa drivers?

---

### Post by fredj on 2007-08-01
Start by undoing all the changes you made to get your soundcard working.
Most of them don't apply to Ubuntu. Then assuming that you are running
Feisty edit the alsa-base file. Open a terminal and type 'cd /etc/modprobe.d'.
Then type 'sudo gedit alsa-base'.
Add to the bottom of this file the line
'option snd-hda-intel position_fix=1 model=3stack.
Open the Alsa mixer by double clicking on the speaker icon in the taskbar.
Then use the Edit->Preferences menu to add all the possible volume controls
(for both record and playback). Also add all the possible switches and ensure
that they are unmuted and that suitable volume levels are set.
If you stlll have problems then open a terminal and type
'sudo lshw -class sound' and post the output from that here.
This command should show the real name of your soundechip, Intel HDA is
a sound specification not a soundchip.

---

### Post by flowbot on 2007-08-01
> **fredj said:**
> Start by undoing all the changes you made to get your soundcard working.
Most of them don't apply to Ubuntu. Then assuming that you are running
Feisty edit the alsa-base file. Open a terminal and type 'cd /etc/modprobe.d'.
Then type 'sudo gedit alsa-base'.
Add to the bottom of this file the line
'option snd-hda-intel position_fix=1 model=3stack.

cool - that's a much simpler fix ... after getting rid of previous changes i'd made and implementing this, i've still got sound on generic kernel :)

still no good on the realtime kernel, though ...

> **fredj said:**
> 
If you stlll have problems then open a terminal and type
'sudo lshw -class sound' and post the output from that here.
This command should show the real name of your soundechip, Intel HDA is
a sound specification not a soundchip.

here's the output:

```

  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: iomemory:febfc000-febfffff irq:21
 
```

just can't figure out what would be the problem preventing this from running on realtime kernel ... just in case it's due to interrupts, here's output from "cat /proc/interrupts":

```

           CPU0       CPU1       
  0:    1375264          1   IO-APIC-edge      timer
  1:       1158          5   IO-APIC-edge      i8042
  8:         50          1   IO-APIC-edge      rtc
  9:         34         34   IO-APIC-fasteoi   acpi
 12:      26310          3   IO-APIC-edge      i8042
 14:      11749          0   IO-APIC-edge      ide0
 16:      79347          1   IO-APIC-fasteoi   nvidia
 17:      36349          1   IO-APIC-fasteoi   libata, ipw3945
 18:          1          1   IO-APIC-fasteoi   ohci1394
 19:          1          1   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7
 20:     131189          1   IO-APIC-fasteoi   uhci_hcd:usb2, ehci_hcd:usb4, uhci_hcd:usb5
 21:        824          1   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb6, HDA Intel
 22:          0          0   IO-APIC-fasteoi   sdhci:slot0
NMI:          0          0 
LOC:     116209    1350432 
ERR:          0
MIS:          0

```

let me know if there's any other info that would help.

[EDIT] 

Here's some more info anyways:

```

shayne@laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 21
shayne@laptop:~$ cat /proc/asound/pcm
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2
shayne@laptop:~$ cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer
shayne@laptop:~$ cat /proc/asound/modules 
 0 snd_hda_intel

```

---

### Post by flowbot on 2007-08-07
Ok, so realtime and lowlatency aren't working for me, but ever since using the fix suggested by fredj, i'm able to get some pretty low latency with no xruns using the generic kernel :D

I've filed a bug about no sound with lowlatency and realtime kernel [here](https://bugs.launchpad.net/redfish/+bug/130798), cos it would be good to be able to get even lower latency with this chip.

---

### Post by MetalMusicAddict on 2007-08-07
> **flowbot said:**
> Ok, so realtime and lowlatency aren't working for me, but ever since using the fix suggested by fredj, i'm able to get some pretty low latency with no xruns using the generic kernel :D

I've filed a bug about no sound with lowlatency and realtime kernel [here](https://bugs.launchpad.net/redfish/+bug/130798), cos it would be good to be able to get even lower latency with this chip.

I'm sorry to say that a bug in -lowlatency and not in -generic wont be fixed. Thats the official word.

Also a -rt kernel is available in Gutsy now. This is where our attention will go. The nVidia drivers dont work with the kernel but will be fixed soon. So when I tell you guys please start to test the -rt kernel in Gutsy. Info from this thread has gone into developing that kernel.

---

### Post by flowbot on 2007-08-11
> **MetalMusicAddict said:**
> I'm sorry to say that a bug in -lowlatency and not in -generic wont be fixed. Thats the official word.

Well, that sucks to be quite frank. I've installed Gutsy and the generic kernel is crap compared to the Feisty one. While I get next to no xruns with the the Feisty generic kernel, the Gutsy one spews them everywhere. So it looks like I'll have to move to a distro that supports realtime kernels if I want to keep making music.

> **MetalMusicAddict said:**
> Also a -rt kernel is available in Gutsy now. This is where our attention will go. The nVidia drivers dont work with the kernel but will be fixed soon. 

nVidia drivers worked for me on the Gutsy rt kernel (using envy).

> **MetalMusicAddict said:**
> So when I tell you guys please start to test the -rt kernel in Gutsy. Info from this thread has gone into developing that kernel.
 

I got sound from the rt kernel when i first booted into it. was beautiful, too - no xruns with frames/period set to 512. No sound on reboot, though - and I've done so about 5 times.

What i don't understand is - what's the point in testing a kernel when bugs won't be fixed? I mean, the whole point in testing RT kernel in this thread seems to be for audio production - i get no audio, which seems to be a pretty fundamental bug ... but it's not going to be fixed!? what's the point?

EDIT

woops ... i'd forgotten to add the "position_fix=1" part to alsa-base. adding that, and i've got next to no xruns on gutsy ... out of interest - why does that simple option fix up the xruns?

---

### Post by MetalMusicAddict on 2007-08-12
> **MetalMusicAddict said:**
> I'm sorry to say that a bug in -lowlatency and not in -generic wont be fixed. Thats the official word.
> **flowbot said:**
> Well, that sucks to be quite frank. I've installed Gutsy and the generic kernel is crap compared to the Feisty one. While I get next to no xruns with the the Feisty generic kernel, the Gutsy one spews them everywhere.
You may think it sux but any bug that doesn't present in -generic and only in -lowlatency wont get fixed. Thats the breaks. If you find issue with the gutsy-generic kernel file a bug.


> **flowbot said:**
> So it looks like I'll have to move to a distro that supports realtime kernels if I want to keep making music.
lol! Why do people always feel the need to post things like this? Does it really get you what you want? Is it supposed to be threatening? :)


> **MetalMusicAddict]Also a -rt kernel is available in Gutsy now. This is where our attention will go. The nVidia drivers don't work with the kernel but will be fixed soon.[/QUOTE]
[QUOTE=flowbot]nVidia drivers worked for me on the Gutsy rt kernel (using envy).[/QUOTE]
Thats because you compiled your own drivers. You'll have to recompile every update.


[QUOTE=MetalMusicAddict]So when I tell you guys please start to test the -rt kernel in Gutsy. Info from this thread has gone into developing that kernel.[/QUOTE]
[QUOTE=flowbot]I got sound from the rt kernel when i first booted into it. was beautiful, too - no xruns with frames/period set to 512. No sound on reboot, though - and I've done so about 5 times.[/QUOTE]
This is odd. I need more info. Quite often it comes down to a user setting.


[QUOTE=flowbot said:**
> What i don't understand is - what's the point in testing a kernel when bugs won't be fixed? I mean, the whole point in testing RT kernel in this thread seems to be for audio production - i get no audio, which seems to be a pretty fundamental bug ... but it's not going to be fixed!? what's the point?
This thread is about testing a RT kernel. Not -generic or -lowlatency. -lowlatency is the kernel I said wouldn't get fixed. So you're getting worked up here for nothing. ;)


> **flowbot said:**
> EDIT
woops ... i'd forgotten to add the "position_fix=1" part to alsa-base. adding that, and i've got next to no xruns on gutsy ... out of interest - why does that simple option fix up the xruns?
Ill look into this.

People need to remember that lots of things play into getting xruns. One big thing is hardware. If you're serious about recording, a onboard soundcard isn't gonna cut it in the long-run. No matter the kernel/settings.

---

### Post by flowbot on 2007-08-12
> **MetalMusicAddict said:**
> You may think it sux but any bug that doesn't present in -generic and only in -lowlatency wont get fixed. Thats the breaks. If you find issue with the gutsy-generic kernel file a bug.


Will do.

> **MetalMusicAddict said:**
> 
lol! Why do people always feel the need to post things like this? Does it really get you what you want? Is it supposed to be threatening? :)


No, it's not. It's supposed to be factual ... I came over to Ubuntu from CCRMA, which supports realtime/lowlatency kernels. If I can't get sound to work on an Ubuntu realtime kernel when I am willing to help bug-test it, then I'd prefer to use a distro that does support it. Quite simple and obvious, actually. It's not like I'm saying "Screw this - Linux sux, I'm going back to Windows if you don't help me". Anyway, if you find what I said threatening, you need to get out more, lol.

> **MetalMusicAddict said:**
> 
Thats because you compiled your own drivers. You'll have to recompile every update.


Absolutely fine by me. I don't mind getting my hands dirty.

> **MetalMusicAddict said:**
> 
This is odd. I need more info. Quite often it comes down to a user setting.


It is odd. I don't think it had anything to do with user settings, though. One thing that i've never seen before, was when I first booted into the RT kernel it paused during boot saying something like "no modules have been built for this kernel ... building them now". Once it had finished, and desktop came up, everyting ran fine as described. I can only think that it working the once only has something to do with the way the modules were built and loaded during that first boot. I dunno, though ... could be due to anything, really.

> **MetalMusicAddict said:**
> 
This thread is about testing a RT kernel. Not -generic or -lowlatency. -lowlatency is the kernel I said wouldn't get fixed. So you're getting worked up here for nothing. ;)


Well, RT don't work for me. Let me know what I need to do to get it working for my card, and I'll do what I can. As you can see from my edit, it doesn't really matter to me if I get the RT kernel working or not anymore, as the generic kernel seems to be doing fine. I would, however, like to help fix what is obviously a bug with the RT kernel. That's what the Linux community is about, isn't it? As I've said in my previous posts - I *am* testing the RT kernel. It doesn't work. And neither does the lowlatency one ... fixing this bug in one will most likely fix the same bug in the other.

I'm glad to hear that RT kernel will be worked on, though. 

> **MetalMusicAddict said:**
> 
People need to remember that lots of things play into getting xruns. One big thing is hardware. If you're serious about recording, a onboard soundcard isn't gonna cut it in the long-run. No matter the kernel/settings.

Sorry, I think that's a silly thing to say. Of course I'm not going to open a recording studio with the onboard soundcard on my laptop, but I sure can make music with it. It might not be up to your standards, but it's still music to my ears. I've got a desktop with a semi-decent soundcard that I use for more important recordings, but it works fine with all kernels, so that's not the issue here.

The problem here isn't that my hardware isn't capable of running jack at low latency, it's that the kernel being used has a bug. And as I said - It doesn't really matter to me if it doesn't work with RT anymore, cos I can get results that are satisfying to me with the generic kernel now (thanx to your fix, btw) ... I thought, though, that you were saying only bugs in generic kernel would be fixed - but as you say ... I was getting worked up for nothing. 

Let me know if you want me to do anything to find out the cause of this problem ... if not, I'll be off to make some music and bug-test Gutsy.

---

### Post by Thelonius on 2007-08-13
I followed the instructions for installing the RT kernel, but I got the message  "couldn't find package linux-realtime." Am I forgetting something?

---

### Post by flowbot on 2007-08-13
> **Thelonius said:**
> I followed the instructions for installing the RT kernel, but I got the message  "couldn't find package linux-realtime." Am I forgetting something?

Are you using Gutsy? If so, you want to do 'sudo apt-get install linux-rt'. If not, don't know :(

---

### Post by MetalMusicAddict on 2007-08-13
> **Thelonius said:**
> I followed the instructions for installing the RT kernel, but I got the message  "couldn't find package linux-realtime." Am I forgetting something?

That repo could be down as development has shifted to gutsy. Ill look in a bit and talk to Alessio.

I will also note the shift in the 1st post.

---

### Post by sovereign_soul on 2007-08-14
I have installed the realtime kernel for feisty fawn and am currently using it. However, I still get quite a few xruns....

I am using the following

$ jackd -d alsa 
I get too many xruns ..

moreover, realtime option -R isn't working ...should I use sudo ..even that isn't working .


pardon me for my ignorance ..but I'm a newbie at such things.

---

### Post by invalidentry on 2007-08-16
Hello, I followed the instructions for installing the Fiesty RT Kernel - which worked fine and I now see pid for my IRQs.

BUT, I can't get the latest driver for one of my soundcards to modprobe from Alsa 1.0.14.  It says fatal, module not found.  I can modprobe snd-layla20 and snd-usb-audio fine, but not snd-usb-caiaq which is new in the last Alsa release.

I have rebuilt alsa a number of times and can't determine what to tell its configure for --with-kernel=<kernel> and also the build directory since these patches don't seem to come with any source.

Anyhow, is anyone else having problems modprobing non-vanilla drivers after following the RT wiki steps?

Thanks,

Jonathan

---

### Post by invalidentry on 2007-08-16
An update:  I used the modprobe option --set-version to specify the original lowlatency kernel, so modprobe knows where to load the module from.  However, now I get a different modprobe error:

FATAL:  Error inserting <module>...: Invalid module format

Reading on the web this could be due to different versions of gcc used to compile the kernel and the module.

Is this system toast now?  Can anyone that has installed the RT Kernel following the wiki above use the new alsa drivers?

Whats the fix?

Thanks,

Jonathan

---

### Post by Steve H on 2007-08-16
I have just followed the instructions on the [wiki]("https://wiki.ubuntu.com/RealTime/Feisty") and it worked beautifully. I´m running Feisty and it is all running fine at the mo, fingers crossed.

Is there any reason i shouldn´t run the realtime kernel as my full time kernel??

Many Thanks

:)

---

### Post by MetalMusicAddict on 2007-08-17
> **Steve H said:**
> I have just followed the instructions on the [wiki]("https://wiki.ubuntu.com/RealTime/Feisty") and it worked beautifully. I´m running Feisty and it is all running fine at the mo, fingers crossed.

**Is there any reason i shouldn´t run the realtime kernel as my full time kernel??**

Many Thanks

:)

Yes. If your using a laptop on battery power. Because the timer is set to 1000mhz instead of the normal 250 it drains batteries that much faster.

---

### Post by MetalMusicAddict on 2007-08-17
> **sovereign_soul said:**
> I have installed the realtime kernel for feisty fawn and am currently using it. However, I still get quite a few xruns....

I am using the following

$ jackd -d alsa 
I get too many xruns ..

moreover, realtime option -R isn't working ...should I use sudo ..even that isn't working .


pardon me for my ignorance ..but I'm a newbie at such things.

Use JACK Control (qjackctl) to run JACK and have a look at [THIS]("https://help.ubuntu.com/community/UbuntuStudio/DapperPreparation") info.

---

### Post by pressman57 on 2007-08-18
The new kernel helped alot. It even makes my cheap-*** Chinese USB soundcard usable. Many thanks and kudos.

---

### Post by nalmeth on 2007-08-19
When I try to update after adding the repo, I get:
```
$ sudo apt-get update
E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
```
Anyone know the reason for this? I am absolutely certain it is the repo in question:
```
deb http://www.texware.it/ubuntu feisty
```

---

### Post by invalidentry on 2007-08-21
Well still no luck with the caiaq driver - guess I'll have to wait on that one.  

With the layla20 however, I have found much better performance than before with this newer kernel.

I can reliably play virtual instruments at 64 frames, 2 periods for 2.9 ms latency.  I was getting some artifacts at first, but changing the jack priority to 70 cleared those up.  Prior to using this new kernel I went to the trouble of dedicating a high priority IRQ, number 10 to the soundcard which, along with some changes to the pci timer latency values made the original ubuntu studio perform much better.  Now I am finding I might not need to change the latency timers.

Any possibility there will be a newer patch that will let me modprobe a new alsa driver?

Thanks!

-jonathan

---

### Post by kayosiii on 2007-08-24
Any progress on nvidia drivers for the gutsy rt kernel

---

### Post by MetalMusicAddict on 2007-08-24
> **kayosiii said:**
> Any progress on nvidia drivers for the gutsy rt kernel
There should be a update soon to enable them.

---

### Post by nalmeth on 2007-08-24
Problem with sources.list solved, the line should look like this:

```
deb [http://www.texware.it/ubuntu](http://www.texware.it/ubuntu) feisty\
```

The extra back-slash at the end was missing. No one picked up on this?

Anyway, kernel seems to be performing really well, only xrun experienced came from closing rosegarden. 3D performance is great, for some reason even better than with the generic kernel. 

I will have to do some more testing, but so far I am giving this a big thumbs up!

---

### Post by vivichrist on 2007-08-26
once you set "chrt -f -p 75 2904" bla bla
does it stick, can you reboot and this stays set?

do you do the same for the gutsy rt kernel as the feisty lowlatency kernel:
i.e. '@audio - rtprio 99' .... >> /etc/secuity/limits.conf ... etc.
?

I'm a bit confused.

I managed to compile the latest nvidia module for 2.6.22-10-rt kernel ala an edited envy.
just ... isn't this different to setup? or just slitely?

---

### Post by sebos69 on 2007-08-27
Hi!

I'm currently testing Gutsy. The -rt kernel fails to correctly hibernate (the screen gets black as usuall, but the computer seems to hang). Any idea?

hibernation works fine with the -generic kernel and a self-compilet 2.6.22.1-rt5 kernel

---

### Post by muzicman0 on 2007-08-29
OK, so it installed fine, boots fine, but I can't seem to start Jack (with QJackctl) with realtime enabled it says:

jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210860672, from thread -1210860672] (1: Operation not permitted)
cannot create engine
17:33:28.870 JACK was stopped successfully.
17:33:28.871 Post-shutdown script...

Any help here would be appreciated! 
Thanks,
mm0

P.S.  not sure if it matters, but I'm actually running KDE (Kubuntu), not Gnome.

---

### Post by blueboy4 on 2007-08-30
Hi. Ubuntu Studio crashes for me after I do a full installation. I boot it up and it says something like "X-Server Desktop not configured properly" then it crashes for some reason. Can someone tell me why it does this? Thanks.

---

### Post by MetalMusicAddict on 2007-08-30
> **blueboy4 said:**
> Hi. Ubuntu Studio crashes for me after I do a full installation. I boot it up and it says something like "X-Server Desktop not configured properly" then it crashes for some reason. Can someone tell me why it does this? Thanks.

Please search the forum or start a separate thread as this is about -rt kernel testing.

---

### Post by stravor on 2007-09-01
Hi! I've installed the realtime kernel plus jack deamon on feisty and everything went smooth. The only problem so far and I'm not quite shure it's related since it appears randomly is that sometimes after boot, sound is disabled. The only way I can get it back (tried restarting alsa-utils, X, booting again, changing sound systems, etc) is to reinstall every alsa related libs and progs then reboot.

As said, I cannot confirm it's related to the realtime kernel though.

Thanks for any support on that!

---

### Post by Scheater5 on 2007-09-02
I can't get 2.6.22-10-rt installed on Feisty using the Gusty repo.  While I easily installed 2.6.22-10-generic (and am happy to verify my sound card is finally supported) I get 
> The following packages have unmet dependencies:
  linux-ubuntu-modules-2.6.22-10-rt: Depends: linux-image-2.6.22-10-rt which is a virtual package.

when I try to install 2.6.22-10-rt.  I know this thread isn't for seeking help, so I've got another post where I'm asking for help, but I still thought you would like to know of this difficulty.

---

### Post by vivichrist on 2007-09-03
> I'm currently testing Gutsy. The -rt kernel fails to correctly hibernate

yep both suspend and hibernate.

> 
OK, so it installed fine, boots fine, but I can't seem to start Jack (with QJackctl) with realtime enabled

have you altered your limits.conf and used chrt to change the soundcards IRQ priority?

---

### Post by malrost on 2007-09-04
I've been using the realtime kernel on Ubuntu 7.04 for a few months now.

I'm getting 3ms latency using a RME Hammerfall HDSP 9632 on an embarrassingly old P4 (it has RDRAM and a vestigal tail.)

I haven't been able to get hibernation to work properly, but am not sure if that's a rt kernel issue.

---

### Post by fiddler59 on 2007-09-06
Is it ok to use the Gutsy RT kernel with Ubuntustudio ?? If so, Where are th repo's and how do I put them in my sources list ...

TIA,
David

---

### Post by Scheater5 on 2007-09-06
fiddler59 - in theory, you just add the main gusty repo for ubuntu and install the kernel via apt-get or your favorite gui package manager. 
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

 I have done this with the 2.6.22-10-generic, but I can't get the real time to install.  I would greatly appreciate it if you would let me know how it goes for you.

---

### Post by leoave on 2007-09-07
Hi !
got  the realtime kernel installed using the guide in [https://wiki.ubuntu.com/RealTime/Feisty](https://wiki.ubuntu.com/RealTime/Feisty)

Boot using the realtime kernel my notebook freezes, no key respond, have to turn off using the button of this Dell Inspiron 1501

there are 2 errors on top of the screen:

(24.016097) MP-BIOS bug:8254 TIMER NOT CONNECTED TO IO-APIC
(24.272047) PCI: BIOS BUG #81 [49435000] FOUND

Using the generic kernel no problem
2.6.20-16-generic 

Thanks
Leo

---

### Post by Toma- on 2007-09-10
Im happy to report no problems with Gutsy 32bit. Pretty standard desktop machine, was able to do a few things but didnt really hammer it, due to a lack of creativity. :confused:

Getting tribe6 now to try it in 64bit... Woohoo! :-\"

---

### Post by border on 2007-09-10
I tried the gutsy 2.6.22-11-rt kernel and performance is among the best I've ever encountered.
I tried zynaddsubfx on my internal intel-hda soundcard, and even at 64samples latency, I don't hear any crackles or pops or whatever you call it.
Zynaddsubfx is like a real reference for me since I've never found a kernel in which I was able to play it without audible cracks (even on better soundcards, with higher latency) on my laptop. Maybe it is because of not tuning the preferences correctly, or anything like that (plz tell me if you know any tips), but it still counts as a good reference.

Even when encountering a few xruns, it still isn't audible.

keep up the good work!!!

Edit:
the only thing I encountered is that the madwifi drivers delivered with that kernel don't work for me. I had to compile them myself...

---

### Post by motscousus on 2007-09-11
performance is really ok :)  

- **wireless not working** :  eventhough the madwifi kernel module seems to be installed in /lib/modules/2.6.22-11-rt/madwifi
here is the log :
```

dmesg | grep ath
[   30.372171] ath_pci: Unknown symbol _ath_hal_attach
[   30.372395] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   30.373178] ath_pci: Unknown symbol ath_hal_computetxtime
[   30.373833] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   30.374089] ath_pci: Unknown symbol ath_hal_detach
[   30.375220] ath_pci: Unknown symbol ath_hal_probe
[   30.376666] ath_pci: Unknown symbol ath_hal_init_channels
[   30.377216] ath_pci: Unknown symbol ath_hal_getwirelessmodes
```
compiling madwifi from source works (but i have to delete madwifi modules coming from the restricted modules package 1st)

**hibernate/suspend does not work**. (acpi messed up ?)

i am also concerned about how RT application would react with a changing CPU freq (frequency scaling). Under windows XP (yeah while doing audio i am always puting the CPU to its maximun freqency to avoid dropouts. i noticed the same behaviour on linux with qjackcontrol. i get dropouts if i leave my cpu (centrino 1.4ghz) in "conservative mode" (then having auto adaptive frequency from 600mhz to 1.4ghz depending on the cpu load). maybe put the cpu in fullspeed mode by default ?

---

### Post by vivichrist on 2007-09-17
amd64 gutsy I still have to compile nvidia drivers with envy so ...
but ya I can get latency's that halve that of the previous low-latency kernel in feisty just with cpu utilisation a bit high at times even at idle with no jack running.

---

### Post by jjalocha on 2007-09-23
Hi, I just installed Xubuntu Gutsy Tribe 5. I want to install/test the latest Ubuntustudio realtime kernel, but I am quite confused about the repositories/packages. It would be nice, if someone could help me with the following questions before I install/uninstall/modify anything:

[LIST=1]
[*] There's a 'linux-rt' package in the multiverse repo. Is this the same package as Ubuntustudio Gutsy?

[*] Does an Ubuntustudio Gutsy release exist?

[*] I tried to add the following repository:
```

deb http://archive.ubuntustudio.org/ubuntustudio gutsy main

```
But this doesn't exist. In Feisty, you had to install both Ubuntu and Ubuntustudio repositories. Is this no longer necessary?

[*] In general, are the Ubuntu packages the same or different from the Ubuntustudio versions?
[/LIST]

---

### Post by MetalMusicAddict on 2007-09-23
> **jjalocha said:**
> Hi, I just installed Xubuntu Gutsy Tribe 5. I want to install/test the latest Ubuntustudio realtime kernel, but I am quite confused about the repositories/packages. It would be nice, if someone could help me with the following questions before I install/uninstall/modify anything:

[LIST=1]
[*] There's a 'linux-rt' package in the multiverse repo. Is this the same package as Ubuntustudio Gutsy?

[*] Does an Ubuntustudio Gutsy release exist?

[*] I tried to add the following repository:
```

deb http://archive.ubuntustudio.org/ubuntustudio gutsy main

```
But this doesn't exist. In Feisty, you had to install both Ubuntu and Ubuntustudio repositories. Is this no longer necessary?

[*] In general, are the Ubuntu packages the same or different from the Ubuntustudio versions?
[/LIST]

1.) Thats part of it. Just grabbing that is fine.
2.) Yes. Dailies are built. (but expect major hickups)
3.) That repo doesnt exist.
4.) They are the same as we use the same repos for Gutsy and also explains #3 more.

---

### Post by jjalocha on 2007-09-23
Thank you MetalMusicAddict, that makes it clear. I will install the new realtime kernel, then!

---

### Post by geekcliff on 2007-09-24
I've just tested the real time kernel on a clean install of xubuntu, and it runs great, I too  have the feeling that the desktop is more responsive with this patch, i thought it might fix the sound problem with vlc, but it didn't so i still use gxine without a glitch.

---

### Post by motscousus on 2007-09-25
using the new version of the kernel + restricted modules 2.6.22-12: on an IBM X31

-wireless atheros now works. 
-suspend button now work but pc crashes before putting it self to complete standby mode. (it remains on)

---

### Post by dragon76 on 2007-10-01
Testing Gutsy Beta amd64 - hibernate hangs at a black screen with a blinking cursor when running realtime kernel.

Generic kernel works fine.

System is an x2-3800+ desktop.

---

### Post by ubuntissimo on 2007-10-07
Running Gutsy on my HP dv2000 laptop (amd64, nvidia 6150). Generic kernel works fine, but rt kernel gives curious effects at boot - eg. hangs that can be unfrozen by touching power button, or sometimes space bar. 
Same happened with 64Studio, and with all my attempts at rolling my own vanilla+Ingo's patch kernels. Something to do with SATA HDD perhaps? Stock Etch,generic and lowlatency Feisty and generic Gutsy all ok. 
If I can persuade the RT kernel to boot fully I will post the dmesg.
UPDATE: got it to boot in recovery mode - dmesg attached with notes to show where it hung. Performance once up was poor - hundreds of xruns per min with 2x128 jack buffers and no other load. 
Also tried booting with noapic and pci=routeirg options; different hang points, but basically the same problem. Any other kernel options I should try?

---

### Post by oskar2000 on 2007-10-09
I run Gutsy with the latest rt kernel. The system freezes after about 10 minutes of playing 3d games like Nexuiz or Warcraft3. No freezes or hangs otherwise. I would file a bug report, but I have no idea how to trace whats going wrong.

(I use rosegarden and ardour, so yes, I need some kind of low latency kernel)

---

### Post by knyar on 2007-10-12
I can confirm the hibernation problem - I've got gutsy on my Thinkpad R52 and hibernation does not work with linux-image-2.6.22-14-rt while on generic kernel it works quite well.

---

### Post by MetalMusicAddict on 2007-10-16
From what Im being told, the -generic kernel is having the suspend/hibernation problem as well. We're looking at it. We dont recommend this kernel for general use. It is a very purpose built kernel and can have weird behavior outside of multimedia production.

Ok. With that we're closing this thread. Development is over and bugs should go to: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22)

---

