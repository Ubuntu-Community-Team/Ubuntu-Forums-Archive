---
title: "sound problem (again)"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by insurin on 2008-03-12
kubuntu 7.10 gutsy

I have read all over this forum about how to get it to work but still had no luck. It's a fresh install and I have never had sound working.

admin@nibiru:~$ lspci -v

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Intel Corporation Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e400 [size=256]
        I/O ports at e080 [size=64]
        Memory at ffa7f800 (32-bit, non-prefetchable) [size=512]
        Memory at ffa7f400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

admin@nibiru:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
admin@nibiru:~$ 

in Aslamixer (I have attached a screenshot) 

I am getting no sound and do not know what to do from here. I have tried

admin@nibiru:~$ sudo modprobe snd-intel8x0m
[sudo] password for admin:
admin@nibiru:~$ sudo modprobe snd-intel8x0


help much appreicated

---

### Post by superprash2003 on 2008-03-12
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by insurin on 2008-03-12
advice please

---

### Post by insurin on 2008-03-12
> **superprash2003 said:**
> hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

I am using kubuntu so I think  the instructions are different.

I have tried 'system settings/hardware tab and changing 'select the audio device' to advanced linux sound architecture instead of autodetect

---

### Post by linux1time on 2008-03-12
there&#347; only one way to activate sound,at lest just one that i know

is this [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603)


good luck post here to see if it works:)

---

### Post by insurin on 2008-03-13
> **linux1time said:**
> there&#347; only one way to activate sound,at lest just one that i know

is this [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603)


good luck post here to see if it works:)

I have still had no luck. this is getting on my nerves now, I want to use this OS, I have often installed linux but only kept it on for a week or so but I can see me sticking with ubuntu because I like it.

Has anyone got a checklist that I can work with so I know that every setting is where it should be.

Also as a side note, I have changde a setting on my task bar that does not display my current applications that are open, I have to alt-tab to get back to them, anyone know how to get them back on my bar at the bottom

---

### Post by Pindulet on 2008-03-13
Hey Insurin
Just wanted to saythat I have the exact same problem (and the same soundcard). I tried the comprehensive sound solution guide and it didn't help me. But maybe you have better luck:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

but i will subscribe to this thread and write it here if I find a solution and I hope you will too if youfind one.. 
Has anyone else experienced this problem and solved it??? 

I too really want to use this OS but I also want to hear some sound:guitar:

Regards

---

### Post by insurin on 2008-03-13
hi, 

that link was the first thing I tried, but because I do see my card

admin@nibiru:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0

I am assuming success, so I stick on youtube and try a vid to test sound and also play the Amorak default tune, here I can see the equalizer bobbing around but no sound.

I don't even know which modprobe I should do, i.e. modprobe snd-intel8x0??

---

### Post by Pindulet on 2008-03-13
That'swhat I tried but as you know i didn't have much luck..

I'll get back to you if I find a solution to this annoying problem. If anyone has a clue what to do please say so.

regards

---

### Post by insurin on 2008-03-14
bumping this as its still an issue

---

### Post by davyboy04 on 2008-03-14
hey guys.  I have the same problem and same audio driver.  BUT i just read a crazy tip in another thread that said to disable your headphone jack sense.  

Here are my setting in alsamixer:   my sound started blasting and almost knocked me out of my chair :)


Master: 29
Master Mono : 100
Headphone: 100
Headphone Jack sense: MM  (press m to set this)
PCM: 100
EVERYTHING ELSE:  MM

be sure to keep scrolling to the right because there are several others that are not on the screen,  

I hope this helps you!! I just installed ubuntu today and it is my first linux installation and dont know too much about it.  So I have no idea why this works, just that it does!  Let me know if it worked for you!

---

### Post by insurin on 2008-03-14
> **davyboy04 said:**
> hey guys.  I have the same problem and same audio driver.  BUT i just read a crazy tip in another thread that said to disable your headphone jack sense.  

Here are my setting in alsamixer:   my sound started blasting and almost knocked me out of my chair :)


Master: 29
Master Mono : 100
Headphone: 100
Headphone Jack sense: MM  (press m to set this)
PCM: 100
EVERYTHING ELSE:  MM

be sure to keep scrolling to the right because there are several others that are not on the screen,  

I hope this helps you!! I just installed ubuntu today and it is my first linux installation and dont know too much about it.  So I have no idea why this works, just that it does!  Let me know if it worked for you!

thats good news mate, my box is in work so I can only try it on Mon but be sure I will try those settings, i'll report back on mon

---

### Post by Programmer DO on 2008-03-14
I think your problem is in that you have the external amplifier turned on.

---

### Post by insurin on 2008-03-14
I have already tried loads of settings, i.e. external amp off as I have read that on here a few times. It has sorted a lot of users problems. I find in cases like this where no-one can resolve my issue, it must be something I am doing wrong, the fact that so many people seem to have got this working and the fix was something simple like unmuting leads me to believe that this should be a simple fix however I have tried a lot of things so far, which has been suggestions from this site, this I am grateful for else I would not know where to start.

---

### Post by Pindulet on 2008-03-14
hey thanks...but...
I have also tried muting the external amp..
my problem however by muting the headphone jack sense and line jack sense is that these options don't show up on my alsamixer. I have scrolled all the way to the right and tried muting/unmuting everything else :)

Does anyone know why I dont have these options in alsamixer?? and is there a way to fix it?

---

### Post by insurin on 2008-03-17
> **insurin said:**
> thats good news mate, my box is in work so I can only try it on Mon but be sure I will try those settings, i'll report back on mon

Just tried those settings and still had no luck, I have done a reinstall, well runing live at the moment and still cannot get sound.

---

### Post by Pindulet on 2008-03-17
Hey Insurin
I installed the Hardy Heron alpha 6 and sound works perfect for me now :)

I know its more unstable but it works with no problems for me and the final release will allready come in April. So thats good news for people with a card like ours.

maybe thats a solution for you??

---

### Post by insurin on 2008-03-17
Alright Pin

just going to give this a whirl [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)
  and Ill probably have a look at Hardy Heron too. Ill report back in a bit

---

### Post by Yellow Pasque on 2008-03-17
> **superprash2003 said:**
> hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)
Please stop posting this in every sound thread. It will not help 99% of the users. I think you're just spamming your blog link and that's not what Ubuntu is about.

insurin, please keep me updated on your progress with this. The OSS4 Intel AC97 driver hasn't been working for users that I've tried it with. I think the issue needs to be addressed on the 4front forums. PM me if you need to.

---

### Post by insurin on 2008-03-17
Temüjin : I followed the instructions but still did not get any sound, although I only tested settings for about 10 minutes, got a bit excited about installing hardy heron kubuntu after Pindulet told me it worked for him. Just finished installing few mins ago but had no sound so far

---

### Post by insurin on 2008-03-17
Pindulet

I still aint getting sound out of this PC, I am on the hunt for a soundcard at the moment to test. It's winding me up because I can see Amorak playing a CD and equaliser bobbing up and down

---

### Post by Pindulet on 2008-03-17
Hmmmm i don't really know where to point you then.. the sound worked out of the box for me with hardy. I didn't do anything special..

But the problem you describe is ecactly the same as I had with gutsy. Everything plays and no errormessages... but no sound!
I looks like there is some kind of bug that needs to be adressed.

I will keep my eyes open for anything that can help you..

---

### Post by insurin on 2008-03-17
cheers Pin,
 just for now though can you tell me exactly what you have muted an unmuted in alsamixer and also if you are using kubuntu (can't remember if you are) do you have it set to auto detect or not in sound system

---

### Post by insurin on 2008-03-18
update:

I have found a soundcard in an old dell xps dimension t550, slotted it in, now I have sound, just installed Firefox3 so fingers crossed

---

