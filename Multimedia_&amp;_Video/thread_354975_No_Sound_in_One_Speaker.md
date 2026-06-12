---
title: "No Sound in One Speaker"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by firefly2442 on 2007-02-06
Hello.  My sound works fine by default except I can only hear audio from one speaker.  I searched around and someone suggested that my other channel in alsamixer is muted but it doesn't look like it is.  Are there any other options that I can look at?  Thanks. :)

---

### Post by firefly2442 on 2007-06-02
*Bump*

Anyone else having this issue?  I think it was resolved with the new Feisty release but after a kernel update, it's back again.

Thanks. :)

---

### Post by firefly2442 on 2007-06-03
Nevermind, I think this is a hardware issue...

---

### Post by vultaire on 2007-06-05
I'm not so sure.  I just bought a new laptop and I'm having the same issue.  In Windows Vista both speakers work fine, but in Feisty, only the left one works.  Earphones show the same issue.

Laptop is an Acer Aspire 3103WLMi, Gnome's volume control lists the audio device as a "Realtek ALC883" (OSS Mixer), and lspci mentions "00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)".

I haven't really spent any time messing with it yet.  Oh, one more thing: I only see OSS as handling the device; I'm unable to start alsamixer.  So that's another odd thing...

---

### Post by MSalzbrenner on 2007-06-11
I have an Acer 5100 with a similar problem. When I first install Ubuntu 7.04 it works fine, but once I upgrade the kernel to 2.6.20-16 I loose the left audio channel. The right channel works fine. If I reboot back into the 2.6.20-15 kernel everything works fine. I know there isn't anything wrong with the hardware as all is well with kernel 2.6.20-15 and WinXP. I've tried everything I know to get it up, but with no luck. I have gone back to the old kernel just to keep both sides of the audio. Any suggestions would be appreciated.

---

### Post by nduanetesh on 2007-06-15
I have the same problem (sound worked fine in fiesty before kernel upgrade, and now I've only got sound out of one speaker).  I've found (and this is really strange) that if I open up the sound mixer (double click on the volume control), slide the main volume all the way down and bring it back up again, I'll suddenly have sound in both speakers.  yeah, I know that sounds ridiculous, but it works every time.  

I have also noticed, as have others, that I no longer have ALSA as a sound mixer option.  (I did before the kernel upgrade.)  Now, I've only got OSS.  

I did have some success, though, but it wasn't permanent...
I also followed the "getting ALSA drivers from a fresh kernel" instructions in [this]("http://ubuntuforums.org/showthread.php?t=205449") thread, and I actually had ALSA running and working UNTIL I rebooted.  After the reboot, things were back to (non-working) normal, with only OSS as a sound mixer option.

Hopefully that's a clue that some more knowledgeable linux user can use to figure this out...in the meantime, I'll keep poking around...

---

### Post by leandrorepolho on 2007-07-01
I'm having the same problem, i have Feisty under 64 bits then upgraded my kernel and now only the right speaker works. I did what nduanetesh user said and the problem was solved, but every time i have to do that, isn't there any way to solve it?

---

### Post by joao82 on 2007-07-07
Yup. same here on an Acer 5101 with a realtek sound card and kubuntu 7.04. It happened after the kernel update from 2.6.20-15 to 2.6.20-16. no sound in one speaker after that but the problem is solved after moving around the sound balance button once every boot.
the exact same thing happened after I made a kernel update on Fedora.
although, when I started kubuntu yesterday with the old kernel that was kept in grub, i managed to have sound in both speakers. and today i started with the new kernel and both speakers still have sound. weird :D

---

### Post by ReapingWildOats on 2007-07-13
Yeah same exact thing here.  Acer 5102.  After the latest kernal upgrade the left channel went out.  I did notice that everyonce in a while both channel would work but I am guessing I used the fix mentioned by nduanetesh and didn't realize it.  What an annoying problem!  But atleast we have a temporary fix.  Wish I had known about that yesterday while watching casino!!

good luck all, I'll be checking this thread if anyone finds a more perma solution.

---

### Post by jdunn on 2007-07-21
Same problem with my Aspire 5100.  I found a temp solution.  I'm running Kubuntu 7.04.  For me, using kmix to MUTE and then UNMUTE solves the problem...until I reboot.

---

### Post by oblivious on 2007-08-14
Hi, 

 I found a solution (or a workaround) to the problem... I did what's described here under the Sound section:

[http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/]("http://nosrednaekim.wordpress.com/2007/05/28/linux-on-the-acer-aspire-5050/")

just gave it a shot and created /etc/modprobe.d/sound containing this:

```

alias snd-card-0 snd-hda-intel

options snd-hda-intel index=0 probe_mask=3 position_fix=3

```

 Upon rebooting, it solved the one-speaker-at-startup problem, and now alsa is working fine. My setup:
Acer Travelmate 5510 with AMD Turion 64 processor
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)


 Why this works is beyond my comprehension (intel????), maybe more experienced users can shed some light on the matter? :confused:

 Thing is... it worked for me.... hope it works for you.

---

### Post by asmiller-ke6seh on 2007-12-23
I had a similar problem, today (no sound from the left channel) - and it was resolved by simply going into the ALSA controls (double click on the speaker icon on the Panel) and mute the FRONT speakers, and then unmute them.

This is the first occurrence, for me. I will report if it re-occurs.

I have a System 76 Serval Performance SerP2 (Compal HEL80) with Realtek ALC 268 sound subsystem running Gutsy Gibbon with all current updates and the System 76 driver.

I am so happy it is not a hardware problem - that would have really suprised me because this seems to be a really well built laptop.

:)

---

### Post by chalewa on 2007-12-23
i have a similar problem in that my left channel is riddled with static.

---

### Post by darth_indy on 2008-02-06
I just got this same problem yesterday, and after going through the forums, I tried muing and unmuting the sound settings (double-clicking on volume manager). But before that, I noticed in ALSAmixer that the two channels were connected, but inversely - one would mute while the other had sound, and I could switch it but not turn both on (i.e. I started with left muted and right working fine, but I could switch it to left working and right muted). I don't know the shortcuts to use in ALSAmixer, but pushing 'm' while highlighting the front just inverted the muting, not turn it off. As I said, mute/unmute in volume manager fied it, at least for now. Does anyone have any ideas as to why this would happen in the first place?

---

### Post by robholmes on 2008-04-11
Hi, I've had exactly the same problem everyone else is having. Most of the time the sound comes from both speakers of my laptop, but sometimes when i boot i only get sound from the right speaker.

I used to just reboot and the problem would go away, but today I just discovered another way to fix my problem:

Just plug my headphones in the jack, then take them back out again. Voila... Stereo sound again!

This baffles me slightly, but I hope this helps someone else with the same problem, until a fix is released.

Cheers,

Rob

---

### Post by hammedhaaret on 2008-06-27
I had the same problem after installing the OSSv4 (open sound system) with this guide: [http://ubuntuforums.org/showthread.php?p=4874981#post4874981](http://ubuntuforums.org/showthread.php?p=4874981#post4874981)

able to solve it when going into the ossxmix (OSS' manager) and muting 'outmix-mute'.
I have not rebooted yet, so I do not know wether it is permanent or not.

Otherwise i can really recommend OSSv4 to those tired of having sound going through both ALSA and oss.

---

