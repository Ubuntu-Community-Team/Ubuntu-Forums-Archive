---
title: "Some Speakers On Laptop Not Working, Sound Card Not There, ALSA Not Behaving... HELP."
date: 2010-10-13
forum: Multimedia Software
---

### Post by Pathologik on 2010-10-13
Gooooood time period, everyone.

Alright, relatively new to Linux, but catching on fast. I like learning as I go along.

But, my problem here is sound. You see, I have a laptop with really nice sound - a Lenovo Ideapad Y530. Got a nice sub built into it and everything. I got fed up with Windows, so I followed my brother's advice and installed Ubuntu 10.10. Loved it until I realized that my music sounded tinny, and realized that my woofer wasn't working. Front two speakers were fine, but not the bass. Looked up some tutorials, tried to compile ALSA drivers, libraries, and utilities (though I seem to already have the utilities), and none of it worked. Kept getting errors after I tried 'make install'.

I was working off of guides like this.

[http://iheartlinux.wordpress.com/2008/12/31/dolby-surround-sound/](http://iheartlinux.wordpress.com/2008/12/31/dolby-surround-sound/)

So, I'm not sure what could be up. Followed the Comprehensive Multimedia Guide here, and it seems that Ubuntu does not detect my sound card [Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03), it says with a shiny lspci -v command - kernel module snd-hda-intel]. And sound is no longer working. Sooo, kind of a step back. Any help will, well, help. Goal is to get my sound working, then get all of my speakers working properly.

tl;dr - Sound borked, HALP.

---

### Post by Benalene on 2010-10-13
Hi! I am the author of the blog you linked to! Wow, I wrote that almost two years ago! My surround sound had been working fine (on Ubuntu, and now Arch) up until a couple of months ago. I did an update, and then surround stopped working. Actually, all sound stopped working, and what I had to do was change the model from lenovo-sky to something else. And I still don't have surround working, just stereo. I keep hoping that an update will fix it, because unfortunately, I haven't had the time recently to research this problem, sound has not been high on my priority list :(.

---

### Post by Pathologik on 2010-10-13
Well, how's that for crazy happenstance!

Gahh, yeah, most of the fixes are at least a few years old. Not looking too good for me, I suppose I'm probably just going to have to live off of speakers as best I can in the meantime. I can probably get it working again just by setting alsa-base.conf back to default. Hoping that somebody else might have an idea though, it'd be a boon to both of us. It is a pretty nice little laptop.

One thing that concerned me was the errors I kept getting while trying to install the configured ALSA packages. Is that just the new version, are they already included? Or were my commands wrong? I think I tried
```
./configure --with-card-options=hda-codec-intel && make
sudo make install
```at least for the driver. Kept getting errors regarding the compiling process, which was odd, because it seemed to run smoothly enough.

What did you end up changing the model to? How did you figure out what to change it to?

---

### Post by shawnlauzon on 2010-10-14
I'm having the same problem since moving to 10.10.

Originally I had followed the info at [http://www.linlap.com/wiki/lenovo+ideapad+y530](http://www.linlap.com/wiki/lenovo+ideapad+y530) which simply said to add this to modprobe.d/alsa-base.conf

options snd_hda_intel model=lenovo-sky

I heard some talk about PulseAudio in 10.10; could that be causing this problem?

---

### Post by Pathologik on 2010-10-14
Hmm, maybe. I highly doubt it's a problem with the sound card if it worked in a previous version. Has to be something new or that was changed in a recent version. I highly doubt that my sound card is all that different from the other Y530 sound cards, I'd be willing to bet they're all similar.

Perhaps we should report the error and hope that it gets fixed, so that the fix works again? It's probably a pretty minor detail, but I'd imagine it could cause similar problems in any laptop with multiple internal speakers.

---

### Post by shawnlauzon on 2010-10-14
No, I didn't mean to imply it's a sound card problem. I started having problems exactly after the upgrade to 10.10, so I'm sure that's it.

My point was that I had heard there was a change from ALSA to PulseAudio, or something like that, but since I don't really understand how all of this works, it's not clear to me if that's at all related.

I think the problem is fairly major. It's not just a change from stereo to surround sound: if all the speakers aren't on, the sound is extremely tinny, and any music at all sounds absolutely UNBEARABLE. Major bummer.

So sure, a bug report makes sense to me. Are you going to open one?

---

### Post by michaelzap on 2010-10-16
Indeed. I've got this regression on my Y530 running 10.10 x64 also. Adding "options snd_hda_intel model=lenovo-sky" (or "6stack-dell", which worked for me in 10.04) just causes it to lose sound altogether.

---

### Post by lidex on 2010-10-16
Anyone care to post more detailed info?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by shawnlauzon on 2010-10-16
My pleasure. Information is at [http://www.alsa-project.org/db/?f=f946d6585ad115f6d3910bcc6ae5f9d7c3fc839b](http://www.alsa-project.org/db/?f=f946d6585ad115f6d3910bcc6ae5f9d7c3fc839b)

shawn.

---

### Post by shawnlauzon on 2010-10-16
BTW, this is without the options flag set, which as michaelzap notes, causes all sound to be disabled. I'll send info on that in just a sec.

---

### Post by shawnlauzon on 2010-10-16
Link to information with "options snd_hda_intel model=lenovo-sky" added to /etc/modprobe.d/alsa-base.conf which results in no sound, but before 10.10 worked great for Lenovo Y530: [http://www.alsa-project.org/db/?f=f6c2558bdda008b84d126a7bda9e5afd8f785119](http://www.alsa-project.org/db/?f=f6c2558bdda008b84d126a7bda9e5afd8f785119)

---

### Post by michaelzap on 2010-10-16
I just tried something else that didn't work. I added the PPA found here:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)
and installed linux-alsa-driver-modules-2.6.35-generic.

No change in the behavior (with the option I get no sound, without it only weak stereo sound).

---

### Post by lidex on 2010-10-17
> **shawnlauzon said:**
> Link to information with "options snd_hda_intel model=lenovo-sky" added to /etc/modprobe.d/alsa-base.conf which results in no sound, but before 10.10 worked great for Lenovo Y530: [http://www.alsa-project.org/db/?f=f6c2558bdda008b84d126a7bda9e5afd8f785119](http://www.alsa-project.org/db/?f=f6c2558bdda008b84d126a7bda9e5afd8f785119)

ALC888. You are not alone. I believe this is a regression and needs to be submitted in a bug report. 
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by shawnlauzon on 2010-10-17
Opened bug report [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662009](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662009)

---

### Post by lidex on 2010-10-17
> **shawnlauzon said:**
> Opened bug report [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662009](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662009)
Good job. Did you see Daniel Chens' reply - have you tried the 'auto' model?

EDIT: One curious thing in your dmesg:
> [   22.101417] asus_laptop: BSTS called, 0xff7f returned
[   22.101877] asus_laptop: Backlight controlled by ACPI video driver
[   22.101951] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input5

Strange to see that in a Lenovo.

---

### Post by shawnlauzon on 2010-10-17
Yep, I just replied. Ultra-tinny audio.

---

### Post by giadroom on 2010-10-17
I'm having the same problem on my lenovo y530 ubuntu 10.10. Ultra-tiny sound (but on headphones seems ok). After adding option  *options snd-hda-intel model=lenovo-sky* in alsa-base.conf no sound at all.

---

### Post by shawnlauzon on 2010-10-17
I found a workaround if you use the 2.6.32 kernel and keep the model=lenovo-sky line in alsa-base.conf, the sound works great. Don't know why that is, though.

---

### Post by lidex on 2010-10-17
> **giadroom said:**
> I'm having the same problem on my lenovo y530 ubuntu 10.10. Ultra-tiny sound (but on headphones seems ok). After adding option  *options snd-hda-intel model=lenovo-sky* in alsa-base.conf no sound at all.
Please add yourself to the bug report:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662009](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/662009)

---

### Post by Pathologik on 2010-11-12
Ohwow, forgot about this thread. Surprised at the helpful response. Well, excellent - have added myself to the bug report, let's hope for a fix. Don't think I have much more to add, everybody's pretty much nailed the problems I've been having on the head. I've sort of resigned myself to using external speakers, but here's hoping for a fix. Thank you all very much, I really do appreciate your time and effort.

---

