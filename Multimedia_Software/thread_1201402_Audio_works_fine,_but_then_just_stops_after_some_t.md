---
title: "Audio works fine, but then just stops after some time"
date: 2009-07-01
forum: Multimedia Software
---

### Post by Nybb on 2009-07-01
So, my audio and video stuff all works fine for a while. But then after a certain point, audio just stops working. If I try to watch say a Youtube video, there is no audio and the video plays for a couple seconds and then just stops and won't work any more. If I try to use any multimedia programs like Rhythmbox or Totem movie player, they just start to freak out (which usually means they just become unresponsive as soon as they start up). The problem goes away after a reboot, but not after just logging out and then back in again.

I have never seen the problem happen before switching users, so I think it might have something to do with that. I am using Ubuntu 8.10. The only other specifications I could think to list is this from doing an lshw:

```
 *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel

```

Ideas are greatly appreciated.

---

### Post by mosteo on 2009-08-06
Have you had any success with this? I have a similar problem.

Everything works all right until at some random time is as if the card disappeared; no sound can be obtained and sound applications generally report a problem with the hardware (i.e. kaffeine says there's a problem with xine initialization, spotify (under wine) says that there's a hardware problem, etc).

This usually happens after several hours; most usually I leave the computer working all-right and when I come back after going out there's no sound.

Login out and in again cures the problem but is obviously a big hassle. It happens the same with kde4, gnome or xfce (this is ubuntu 9.04).

My hardware is (I see that it uses de same driver than you)

```
*-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

The only thing salient about this computer is that it is an atom fanless silent box from [http://www.tranquilpc.co.uk/](http://www.tranquilpc.co.uk/). However, the box temperature is stable, I couldn't see a correlation with high CPU and temperature loads.

---

### Post by sandwormblues on 2009-08-06
Darn it, same here!  Happened when i was on the radio, too.  fortunately this is a new hardy installation and i had a back up CD to play while i rebooted).


Tried it on a couple kernels.

*lspci|grep Audio*
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

running 2.6.24-24-generic.

---

### Post by KarenAK on 2009-08-06
I have the same problem ! This cannot be a coincidence !

Edit: Maybe I should specify this a bit:

When I play a video - any video - it'll stop after a little while and the flash box goes blank. If I reload the page, flash appears again, plays for a while then stops.

2. edit: Everything worked fine until about a week ago or so. All I did was do the regular Ubuntu updates

Somebody please help !

---

### Post by lavi17 on 2010-04-10
HI all, i'm not using ubuntu, i use it in office, at home i use debian, well i think if a thing works for ubuntu it'll work for debian too, i'm havin the same prb, if i open youtube on say any browser be it iceweasel, epiphany, opera, chrome. the youtube video works for sometime n after some x time, isnt' very long enuf, the video can be seen but sound cannot be heard, there's sound like it comes when some tape gets stuck, i've tried to dig out a solution so far no success, i've done a postin in debian forums too... 

[http://forums.debian.net/viewtopic.php?f=5&t=50774]("http://forums.debian.net/viewtopic.php?f=5&t=50774")

is there any way how to resolve this issue

PS when irestart the browser, it starts working normal....(that means can hear sound in youtube, or anyother flash video for sometime n after sometime have to redo it, i.e., restart the browser)

---

### Post by mosteo on 2010-04-11
In my case upgrading to 9.10 fixed the issue.

---

### Post by mikewhatever on 2010-04-11
> **lavi17 said:**
> HI all, i'm not using ubuntu, i use it in office, at home i use debian, well i think if a thing works for ubuntu it'll work for debian too, i'm havin the same prb, if i open youtube on say any browser be it iceweasel, epiphany, opera, chrome. the youtube video works for sometime n after some x time, isnt' very long enuf, the video can be seen but sound cannot be heard, there's sound like it comes when some tape gets stuck, i've tried to dig out a solution so far no success, i've done a postin in debian forums too... 

[http://forums.debian.net/viewtopic.php?f=5&t=50774]("http://forums.debian.net/viewtopic.php?f=5&t=50774")

is there any way how to resolve this issue

PS when irestart the browser, it starts working normal....(that means can hear sound in youtube, or anyother flash video for sometime n after sometime have to redo it, i.e., restart the browser)

'Works with Ubuntu, then it should in Debian and vice versa', is a wrong assumption, because package versions and configuration files are quite often different.
Anyway, you are better off opening a new thread, since this one is more then half a year old.

---

### Post by lavi17 on 2010-04-11
> **mikewhatever said:**
> 'Works with Ubuntu, then it should in Debian and vice versa', is a wrong assumption, because package versions and configuration files are quite often different.
Anyway, you are better off opening a new thread, since this one is more then half a year old.

Hello mike, well i've been tracin this issue for quite sometime now have a look at this thread there exists a thread, with so many users facing a similar prb,  [http://ubuntuforums.org/showthread.php?t=1356599]("http://ubuntuforums.org/showthread.php?t=1356599"), see this, is there any solution to this prb?

---

