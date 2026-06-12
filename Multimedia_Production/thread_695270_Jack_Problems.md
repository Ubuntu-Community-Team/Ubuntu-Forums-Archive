---
title: "Jack Problems"
date: 2008-02-12
forum: Multimedia Production
---

### Post by Croww on 2008-02-12
Hello all, I'm not real sure where to start. I am using Ubuntu Studio 7.10 64bit for a basic studio setup. I have been trying for weeks now just to get Jack to stay connected with my USB sound card (M-Audio Fast Track). I started on my laptop (AMD 64bit), and now I have moved to my desktop (AMD 64bit Dual-Core). I've had similar problems with both setups. I have read just about every piece of literature on the subject and have no idea what I could possibly be doing wrong. I've tried so many different options with varying results. Basically, I either get an avalanche of xruns after a while, which kills Jack, or Jack will just crash. This has literally been trial and error from hell. Sometimes it seems as though I've found a winning combination and then it fails. One interesting problem I've seen is that, no matter if I'm using Jack or not, whenever I play any audio through my USB sound card, it will usually flicker out and then stop seeing the device. I can replug in my sound card and it will work again (until I play audio). Sorry if this is such a lengthy post, but I desperately want to use Studio for my recording and this has been holding me back for quite some time. If ANYONE can shed some light on this subject, I would be a very happy person. Yes I'm somewhat of a newbie, but I feel I have exhausted all the resources I can find.

---

### Post by Stochastic on 2008-02-12
Okay well the first issue to look for is which driver you're using when these issues are arising.  I say this because it sounds like it's across setups and with that particular hardware device.  I've had some devices in the past that just have bad linux drivers written for them.  I'm assuming you're leaving the driver section of jack's settings at alsa?

The question is what errors?  If you're starting jack from qjackctl I'd make sure that in the settings panel you have checked the 'verbose' mode.  Then, when jack crashes go to the messages window, find where the end section of that jack run, and copy and paste that into the post.  Without an error message it's very difficult to pin down the issue.

The last thing to mention, would be to possibly attempt to get it working on a 32bit system.  I know, I'd prefer to use 64bit too, but sometimes there are more random bugs lying in the 64bit installs.  And from what I hear you need upwards of 4gig of ram before the step up to 64bit processing is really noticed in terms of speed.  If this option sounds good, you can easily clear out a portion of your drive, repartition and dual boot 32bit to test and see if your bug disappears.

Oh, and if you're able to find any way of reliably reproducing your bug, file a bug report! but be as detailed and specific as possible.

---

### Post by Croww on 2008-02-13
Yes I am using alsa. I usually get one of three errors: 1. After a minute or so, Jack will get a few xruns and then hundreds and shut down. 2. Jack will just shutdown. or 3. Jack shuts down when I connect to Ardour.

I will try the verbose setting and see if I can get a more detailed error report. I was also thinking of using the 32bit version to see if that corrects the problem for now.

Thanks for your help, and I will post my results soon

---

### Post by lapcat66 on 2008-02-13
Croww, did you install Ubuntu Studio from Synaptic, or from the dvd?  Your experience sounds like mine with a Gutsy install + Ubuntu Studio from Synaptic, but those problems went away when I installed from the dvd.

---

### Post by Croww on 2008-02-13
Funny you should mention that. I tried every way imaginable to install Studio. The dvd just wouldn't work. I ended up  installing Ubuntu Gutsy and upgrading through Synaptic to Studio. The real time kernel is installed with the other configurations listed on Ubuntu Studio's wiki. I could never get the dvd to boot, no matter what media or burner I used. It's been a grueling couple of weeks :|

---

### Post by Stochastic on 2008-02-13
I'd file a bug report about not getting the DVD to boot.  I know that doesn't directly help your issue, it may prevent the issue from arising in the future.

---

### Post by Croww on 2008-02-13
> **Stochastic said:**
> I'd file a bug report about not getting the DVD to boot.  I know that doesn't directly help your issue, it may prevent the issue from arising in the future.

Well, the dvd has worked on my laptop. And even on another PC using my dvd-rom, so it is just an issue on my PC.

---

### Post by lapcat66 on 2008-02-13
Yeah, I got the dvd to boot, and that gave me a working studio system.  But installing through synaptic, even with all of the ubuntu studio pieces including the rt kernel, had too many issues to be usable.  I was ready to roll back to feisty ubuntu studio when I decided to give the dvd a try.

There must be some configuration issues that are too subtle for me to find (i.e., not just jack settings).

---

### Post by Croww on 2008-02-13
Here is the output of Jack when it shuts down.

(There are a ton of xruns before here)
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.020 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.022 msecs
**** alsa_pcm: xrun of at least 0.023 msecs
**** alsa_pcm: xrun of at least 0.020 msecs
**** alsa_pcm: xrun of at least 0.024 msecs
jackd watchdog: timeout - killing jackd
17:30:12.484 MIDI connection graph change.
zombified - calling shutdown handler
17:30:12.630 Shutdown notification.
17:30:12.631 Client deactivated.
17:30:12.633 JACK was stopped successfully.
17:30:12.634 Post-shutdown script...
17:30:12.634 killall jackd
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
cannot send request type 7 to server
cannot read result for request type 7 from server (Broken pipe)
jackd: no process killed
17:30:12.858 Post-shutdown script terminated with exit status=256.

---

### Post by Stochastic on 2008-02-13
> **Croww said:**
> Well, the dvd has worked on my laptop. And even on another PC using my dvd-rom, so it is just an issue on my PC.

I know this is a side issue from the thread, but really, there's a hardware reason why your PC isn't able to boot the DVD and if you're having that trouble then I'm sure there are many others who have the same hardware issue.  A bug should probably be filed if you can explain your PC's setup.


But back to your main issue, can you post your jack settings?

---

### Post by Croww on 2008-02-14
> **Stochastic said:**
> But back to your main issue, can you post your jack settings?

Well, I'm at work right now, but I'll do my best to recall my settings.

Priority = 0
Frames/Period = 128
Sample Rate = 44100Hz
Period/Buffer = 2
Real Time is checked

These are usually the most stable settings, however I have tried every combination I can think of.

Also, I wanted to mention that I installed Studio 32bit on a completely different setup last night (Intel Pentium 4) with more or less the same results. It will begin to work for a while, then start shutting down. I'm beginning to think my audio interface just isn't going to cut it.

And thanks again for everyone's help.

---

### Post by Stochastic on 2008-02-14
when I was running a Tascam US-122 I was told that USB devices should usually have their peroid/buffer at 3 rather than 2.

---

### Post by Croww on 2008-02-14
Yeah, I've read that usb should be set to 3 periods/buffer as well. However,this has little effect on my setup. If I could get consistent failures using this card, it would much easier to troubleshoot. It sort of does what it wants when it wants. I've literally, (usually on a fresh install) had it up and running beautifully for a very long time. Then maybe after a reboot, or after adding more tracks in Ardour, Jack will freak out. Then it seems the problems escalate from there. Three different PC's, 64 and 32 bit distros, all produce similar problems. Should I just be looking for a new audio interface? 

I just want to freakin' record :)

---

### Post by Croww on 2008-02-14
I was just looking on [http://www.alsa-project.org/]("http://www.alsa-project.org") for supported sound cards, and my M-audio usb fast track isn't listed. Purhaps this has been the problem?

---

### Post by Stochastic on 2008-02-14
> **Croww said:**
> I was just looking on [http://www.alsa-project.org/]("http://www.alsa-project.org") for supported sound cards, and my M-audio usb fast track isn't listed. Purhaps this has been the problem?

This is a little more interesting and fruitful: [http://www.m-audio.ca/index.php?do=support.faq&ID=cf6f53946a5d2cfa3792487b2af97e61](http://www.m-audio.ca/index.php?do=support.faq&ID=cf6f53946a5d2cfa3792487b2af97e61)
but the link they provide didn't lead me very far.

Also you should keep in mind that the alsa listing isn't always comprehensive.

---

### Post by nesabishii on 2008-02-15
I was able to get Jack working with my M-Audio FastTrack Pro (although I'm still having MIDI output issues with RoseGarden). I'm fairly sure the OSS drivers mentioned above were the solution that ultimately worked for me. I'm running Ubuntu 7.10 with linux-rt, Jack, and ALSA.

---

### Post by Croww on 2008-02-15
I'm not using the Fast Track Pro, mine is the lesser version. Not sure if there is a big difference between the two as far as Linux compatibility.

> **nesabishii said:**
> I'm fairly sure the OSS drivers mentioned above were the solution that ultimately worked for me.

Also, what OSS drivers where you referring?

---

### Post by Stochastic on 2008-02-15
I'm guessing he means the Open Sound System drivers that the m-audio link I gave leads to.

---

