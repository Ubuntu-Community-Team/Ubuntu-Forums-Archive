---
title: "Microphone? Updates?"
date: 2011-11-22
forum: Multimedia Software
---

### Post by Roasted on 2011-11-22
Is anybody else's microphone not working after a recent update? I'm not sure when exactly it was, but I distinctly recall using my headset to make a call via Google Voice on my computer about 2 weeks ago. I haven't used my desktop much since, but I tried to make another call last night and the microphone was non-responsive. Audacity and everything else failed. Sound settings proved to be right from what I can tell. My PCI sound card is selected in all tabs (not the onboard one) and nothing is muted.

Just at a loss for what it could be and curious if anybody else ran into this.

---

### Post by Lalaith on 2011-11-22
Hi Roasted, 

I'm an absolute newbie with ubuntu (and linux in general) and have some minor problems with it, one of them is the microphone. I read some threads but I don't understand much of what are they saying (like this one:  [http://ubuntuforums.org/showthread.php?t=766683&highlight=mic](http://ubuntuforums.org/showthread.php?t=766683&highlight=mic) ).

Apparently after an update of Ubuntu,  "Medibuntu" is disabled and you have to enable it again in order to get all things working properly again... I'm not sure if this is your or my problem or not, but check here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) while someone who knows what are we talking about help us ;-)

*btw, it sound a bit uncomfortable to enable the medibuntu every time anything related to linux/ubuntu updates, isn't it? :confused:

---

### Post by Lalaith on 2011-11-22
I'm sorry my problem was that the mic was muted... hope yours is fixed easily too! ;-)

---

### Post by gordintoronto on 2011-11-22
It might help if you told us what version of Ubuntu you are using, what type of computer you have, and what sound card. For example, I halfway expect sound issues running 10.04 on a laptop.

---

### Post by Roasted on 2011-11-22
> **gordintoronto said:**
> It might help if you told us what version of Ubuntu you are using, what type of computer you have, and what sound card. For example, I halfway expect sound issues running 10.04 on a laptop.

11.10 64 bit.
Custom built desktop.
Turtle Beach Montego 5.1 PCI sound card.

I'd like to believe I just goofed up a setting. But I'm not sure?

---

### Post by gordintoronto on 2011-11-22
Have you installed Alsamixer? I have found it useful for investigating sound settings, then I run sound recorder to test them. My laptop has a completely up to date 11.10, and the sound recording is OK, from headset or the built-in microphone.

---

### Post by Roasted on 2011-11-22
I thought alsamixer was installed by default? I ran alsamixer in terminal (I used to use this utility years ago for audio troubleshooting) but nothing struck me as "off".

Both of my laptops work fine with the microphone as well, which are both 11.10. I guess I'll just have to look a bit more.

Offhand in the input tab, which audio setting am I supposed to use? I have 4 of them there. Granted, I tried all 4 by switching through each one and talking at the same time, but I never saw any movement on the mic. I've also tried two mic's.

Hmm...

---

### Post by drewricciardi on 2011-11-22
> **Roasted said:**
> Is anybody else's microphone not working after a recent update? I'm not sure when exactly it was, but I distinctly recall using my headset to make a call via Google Voice on my computer about 2 weeks ago. I haven't used my desktop much since, but I tried to make another call last night and the microphone was non-responsive. Audacity and everything else failed. Sound settings proved to be right from what I can tell. My PCI sound card is selected in all tabs (not the onboard one) and nothing is muted.

Just at a loss for what it could be and curious if anybody else ran into this.
I have had the exact same problem! Updated my Asus eeepc 1015px netbook, HDA Intel sound card (this is how the sound card is described alsamixer). Cannot re-enable the mic, very annoying. Had originally fixed this problem thru alsamixer, but no success after the updates recommended in update manager.

If you have any suggestion's for my ubuntu noob self, i would very much appreciate it. thx
d

---

### Post by gordintoronto on 2011-11-23
> **Roasted said:**
> Offhand in the input tab, which audio setting am I supposed to use? I have 4 of them there...


Could you show us the choices?

---

### Post by Roasted on 2011-11-30
> **gordintoronto said:**
> Could you show us the choices?

Analog Input
Analog Line-In
Analog Microphone/No Boost
Analog Microphone/Boost


Just updated again, no change. It does it with both my internal sound card as well as my Turtle Beach 5.1 PCI sound card.

:confused::confused:

---

### Post by gordintoronto on 2011-11-30
Have you tried each of the choices? I assume your microphone is plugged directly into the sound card?

---

### Post by Roasted on 2011-11-30
> **gordintoronto said:**
> Have you tried each of the choices? I assume your microphone is plugged directly into the sound card?

Yup, and yup.

---

### Post by gordintoronto on 2011-12-01
All I can suggest is: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

With luck you can search within the thread and find useful information.

---

### Post by Roasted on 2011-12-02
> **gordintoronto said:**
> All I can suggest is: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

With luck you can search within the thread and find useful information.

:(

Most of that thread is getting sound to initially work. I'm trying to get it to work [again]. I'll take a look through it and hope for the best, though.

---

