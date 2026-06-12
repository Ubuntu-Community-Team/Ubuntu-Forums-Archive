---
title: "No sound from my headphone jack"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by adredwood on 2007-10-11
Hi there - my problem is pretty much what it says above, i can play all sounds, music etc, but only through the speakers on my laptop. When i plug in any sort of jack, ie for external speakers or headphones, sound stops from the laptop but doesnt play through the headphone jack.

Ive seen threads that are basically this problem in reverse, and they mention using alsamixer and unchecking boxes for 'Jack Sense' - but i cant for the life of me find these. When i open alsamixer (GUI or from command line) i get nothing but levels, no mention of Jack Sense and no boxes to untick.

There are also a couple of daunting (for me) threads featuring long lines of adjustments, but im not sure if they are soecific to my problem. [This]("http://ubuntuforums.org/showthread.php?t=455147") one seems to be about HP computers and [the other]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29") doesnt mention this specific problem. So m not sure what to do.

I should point out that i am a complete newbie to this - today i learnt how to start a program from the command line, im that new...

So any help here would be appreciated: ive put the output of aplay -l below in case its helpful - if i need to give some more info please let me know.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

Thanks!

Andy (:

---

### Post by adredwood on 2007-10-17
Please help, i feel like ive tried everywhere and no-one seems to know about this specific problem... Thanks in advance (:

Andy

---

### Post by digitally404 on 2007-10-17
Hi Andy,

Much like you, I've had a similar problem (the opposite one),  and I've also come across several useless threads out there that had no solution to my problem.

What I found is you need to play around with the sound settings in Ubuntu, and "unmute" the setting which is affecting your headphone output.  (Actually, there's a headphones checkbox)

Open your "Volume Control" for Alsa mixer.  (right click speaker icon, click 'open volume control')
Goto Edit -> Preferences, and check all the boxes.   Click 'Close'. One of those boxes is bound to be affecting your headphones output (also note the new tabs that are available). Under the "Switches" tab you may find a "headphones" checkbox. 

Anyways, for my 'no speakers, only headphones sound' problem, i found I needed to unmute my 'Surround' sound setting on my laptop, and everything worked fine after.

Hope this helps.

---

### Post by Rockman4140 on 2007-10-18
I'm having the same issue too, my only options to check though are Caller ID and Off Hook, neither which played music through the headphone jacks. I have downloaded PulseAudio and I have had no luck attempting to get it to work with that either.

---

### Post by GriZzm0 on 2007-10-19
> **digitally404 said:**
> Hi Andy,

Much like you, I've had a similar problem (the opposite one),  and I've also come across several useless threads out there that had no solution to my problem.

What I found is you need to play around with the sound settings in Ubuntu, and "unmute" the setting which is affecting your headphone output.  (Actually, there's a headphones checkbox)

Open your "Volume Control" for Alsa mixer.  (right click speaker icon, click 'open volume control')
Goto Edit -> Preferences, and check all the boxes.   Click 'Close'. One of those boxes is bound to be affecting your headphones output (also note the new tabs that are available). Under the "Switches" tab you may find a "headphones" checkbox. 

Anyways, for my 'no speakers, only headphones sound' problem, i found I needed to unmute my 'Surround' sound setting on my laptop, and everything worked fine after.

Hope this helps.

I had the exact same problem as the thread creator and enable "surround" worked. However, after this I wasn't able to use the volume gnome controller at first. I fixed that by right-clicking -> preference and changed from the current to surround. Works fine except it gets muted and you can't use the scroll to increase the sound once you decrease it to 0%. You have to right-click and hit the "mute" option.

---

### Post by mathgirl1990 on 2007-10-23
I'm having the same problem. When I enable Surround Sound, I get the white noise that says your speakers are on, but no music. 

Is there any way that you can get Ubuntu to treat your surround sound jack like a regular jack?

---

### Post by marcantonio on 2007-10-29
Hey all,

I followed this [post]("http://ubuntuforums.org/showthread.php?p=3501600#post3501600").  Interesting thing is that I didn't have to check off the missing option "headphone jack sense".

Marc

---

### Post by unfjoel on 2007-11-13
> **Rockman4140 said:**
> I'm having the same issue too, my only options to check though are Caller ID and Off Hook, neither which played music through the headphone jacks. I have downloaded PulseAudio and I have had no luck attempting to get it to work with that either.

I have this exact same problem - there is no option that I can enable in the volume control that has anything to do with Headphones...

---

