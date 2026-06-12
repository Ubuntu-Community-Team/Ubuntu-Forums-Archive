---
title: "Sorta HOW-TO: recording with mic in Gutsy 7.10"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by dansan on 2008-03-02
I am a non-technical newbie with Linux and Ubuntu and have recently been asking for help in setting up Gutsy 7.10 to record voice with a microphone.  In fact, no one answered my posts, but this was not surprising because there are dozens of such questions and a lot of pointers on how to go about doing this. I think I have read through most of these, but after getting no results I posted my query.

Last night, I solved my problem, and in the Ubuntu spirit, I am posting this "Sorta HOW-TO". I chose this title because it is more about methodology than technical detail.

1. The first step was shifting my search from the forums to Google. Ironically, Google turned up items on the Ubuntu forums that the identical keywords I had used there had not produced. Here are the magic keywords: "how record with mic on ubuntu" and "hda intel mic". My chipset is from the Intel ICH8 family: AD1983

2. Several of the "new" items suggested that adding linux-backports-modules might help. I did this, but I still could not record my voice using a microphone.

3. I also found several suggestions to add the following line to your /etc/modprobe.d/alsa-base or (if that one does not exist or is empty) /etc/modprobe.conf: 

options snd-hda-intel model=[ref], where [ref] is the name of your sound card or onboard chipset. Read [_here_]("http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+mic") for the details.

4. I followed this recommendation, but in the course of doing so found out that my chipset AD1983 does not have a reference in ALSA Configuration.txt, so, based on a comment in another item, I changed the line to

options snd-hda-intel model=auto

but was still unable to record my voice with a mic.

5. Finally, something else from all of that reading popped into mind: it may be necessary to plug the mic into the record jack on the motherboard. My brain did a Homer Simpson DOHNG! I think the last time I even thought about this jack was five years ago. I always plug mics into USB sockets. So I shifted the connection, and that cracked the problem. I can now record my voice clearly and loudly in, for example, Sound Recorder.

6. The screenshot shows my settings in Sound Preferences under System.

I may have unintentionally left out something important - just ask. The reason for posting this is to underscore the power of shifting a search to a new platform and also to thank all of those contributing the bits and pieces that eventually helped me solve this recording problem.

Dansan

---

### Post by telemetry on 2008-03-25
Something that really helped me in the end after many hours of trying to get my microphone to record in gutsy:  If you are well and truly stuck you can try changing some sliders in alsamixer.  Just type in: alsamixer      in the console and you can change settings but make sure you remember your default settings.

Once you've altered anything - go to your volume control and then the top menu bar and the Edit option - then choose preferences.  Select and tick the boxes you want to be able to control and make sure you select microphone or anything else you think you may need.  Once you've done this you can go back into volume control and the HDA (alsa mixer) and make the sure the now selected microphone settings (and others) are enabled and don't have the red disabled thingy at the bottom.  Once I changed this I was able to record.  Hope this helps someone.

---

