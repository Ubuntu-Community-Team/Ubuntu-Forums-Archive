---
title: "simple audacity question"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by Ripfox on 2007-01-07
Why does audacity make a high pitched noise under edgy? It never did under Dapper...is this a kernel issue? I am not advanced to that level yet.

Thanks...

---

### Post by Mike'sHardLinux on 2007-01-07
What are you doing at the time when you hear a high pitched noise?

I am trying to recreate the same symptom. I opened an mp3 in Audacity, but I can't get it to make any high pitched noise. Mine seems to be working fine.

---

### Post by Ripfox on 2007-01-07
I am recording with a microphone. I tried both the "mic" and "line in" and both seem to give me a high pitched noise as well as background hiss.

---

### Post by meng on 2007-01-07
It's not feedback is it? Do you turn the speaker volume down to zero while you are recording?

---

### Post by Ripfox on 2007-01-07
I turned the speakers down...also, the recording sounds kind of like a robot.

---

### Post by Ripfox on 2007-01-07
where can i host an audio file so you can hear it?

---

### Post by meng on 2007-01-07
If it's not very long you can post a .tgz or .zip file as an attachment.

---

### Post by Ripfox on 2007-01-07
Ok here it is..btw, this never happened under Dapper, if that helps.

---

### Post by meng on 2007-01-07
Ha ha! Sounds like I'm at the supermarket or train station or something. I don't know the reason why you have that, perhaps you could try using the basic "sound recorder" for recording, and leave audacity for the editing (assuming the recording is satisfactory of course).

---

### Post by Ripfox on 2007-01-07
The only problem, is that I need a multitrack recording program to make my tunes. I lay down the guitar, then the vocals then the icing....also, for some reason my pc wont play wav files either...](*,)

---

### Post by Ripfox on 2007-01-07
[http://music.download.com/rippleeffect/3600-8731_32-100700678.html?tag=MDL_listing_song_artist](http://music.download.com/rippleeffect/3600-8731_32-100700678.html?tag=MDL_listing_song_artist)

the third song down, "Freedom Jam" was done with Audacity only. But that was back on Breezy...this sucks, cuz I don't want to have to set up a windows partition or downgrade Ubuntu...

---

### Post by Mike'sHardLinux on 2007-01-07
Hi Ripfox.

I just heard the clip and I hear what you mean. I assume you are using the onboard sound on your computer/motherboard? if not, what audio interface are you using?

The last time I heard something like that in a recording (a while ago), it was a problem with the driver. That was back when I had a soundblaster. It could also be caused by other things. Have you tried recording with a different program to see if it's only Audacity?

I am not an expert on sound in Ubuntu, but I know of one thing you can mess around with that may help. In System --> Preferences -->Sound, I noticed on my Ubuntu Edgy, it is using ALSA by default. Try switching to one of the other choices and see if it's better.

---

### Post by Ripfox on 2007-01-07
I will try that, and get back. Thanks!

---

### Post by Ripfox on 2007-01-07
Unfortunately...that made no difference. Hmmm...

---

### Post by Mike'sHardLinux on 2007-01-07
I don't have my Linux workstation set up to record. It only has onboard sound, and I don't have the right connectors to hook up a mike, but I will try installing my audio interface and see if I can recreate the problem.

I really believe it's something simple. There's all sorts of stuff to look at. Make sure the bit-depth in the software is set properly. If your audio interface is a 16-bit audio, you don't want your software to be set for 24-bit. Check the software mixer settings.

1 more question: If you unhook your mike, does the high-pitched sound still get recorded?

---

### Post by Ripfox on 2007-01-07
I assume that you mean if I hook up a guitar to the "line in" and yes I still  get the same background noise, whatever the input instrument is. I have set the depth to 16 in Audacity, per some research on google to no avail. All I have is onboard sound card, but it worked before....

---

### Post by Ripfox on 2007-01-08
I just recorded a "blank" segment, and there was a high pitched sound, but not nearly as loud, in fact it was quite miniscule.

---

### Post by Mike'sHardLinux on 2007-01-08
Wow, this must be really frustrating! 

Before I went through the trouble of hooking my other audio interface, I hooked up some earbuds to the microphone input and recorded a bit. It sounded like poo as expected, but I am not getting the high pitched whine you are getting. I am trying to brainstorm on all the possible differences that could cause the noise. I have to assume that it's a software/driver problem since you had no problems with a previous Ubuntu installation on the same hardware.

1) Did you upgrade from Dapper, or fresh install of Edgy?
2) If an upgrade, did you run into any issues that needed to be fixed?
3) Tell me anything you know about your hardware: 
           brand/model if it's oem, or if you built it yourself, what motherboard?

4) Did you ever try recording with another software, just to see if it's specific to Audacity, or system-wide?

---

### Post by Ripfox on 2007-01-08
Fresh install of Edgy.

It's an Athlon xp 3500 combo...I built it myself, it's in a cube. (not that that matters, they are just cool :)

The motherboard....hmmm, I forgot, but its the onboard sound that I am using. 

Is there a Ubuntu utility to identify it?

---

### Post by crane on 2007-01-27
I am having the same issues. I am using onboard sound which worked fine in breezy and dapper.
I also tried using a sound card (soundblaster) but could get no sound at all out of the mic.
Anyone found a fix for this?

---

### Post by xJake on 2007-03-18
In searching to resolve the same problem I found this thread. It worked for me :)

[http://ubuntuforums.org/showthread.php?t=279971](http://ubuntuforums.org/showthread.php?t=279971)

He installed the alsa-oss package, then ran audacity with OSS emulation with "aoss audacity".

---

### Post by Ripfox on 2007-03-18
Dude, you are a god...this has been a problem for like 3 months. Now i can get back to making music! It works!!

Peace

Ripfox

---

### Post by Ripfox on 2007-04-21
Crap...no longer works with Feisty...freezes the program. DANG!!

---

