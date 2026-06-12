---
title: "continue recording after ota signal loss"
date: 2010-07-29
forum: Mythbuntu
---

### Post by iitywygms on 2010-07-29
Hi All:

I am running mythbuntu 10.04 trunk.
I get my tv ota.  Sometimes I lose signal.  If the signal is lost for only a few seconds, myth will continue recording the show I have scheduled to record.  If the signal loss is longer, maybe fifteen seconds? myth will stop recording, even if the signal re appears a minute later.
Is there anyway to get around this?  Some way to increase the "wait time"?   I assume this is directly related to the video buffer?
Thanks.

---

### Post by iitywygms on 2010-07-31
bttt

---

### Post by nickrout on 2010-08-01
Fix your signal path so you don't get dropouts!

---

### Post by iitywygms on 2010-08-01
> **nickrout said:**
> Fix your signal path so you don't get dropouts!

Um, yeah thanks.  If I could, I would.  Trust me.

---

### Post by LowSky on 2010-08-02
Sounds like you need a better antenna

Trying to do this from memory (I'm at work and teamviewer + Mythtv doesn't work so well)

in the backend there is a timeout options, I think its set to milliseconds so you'll need to set it very high.

I belive it can also be done through the frontend, but I'm drawing a blank. More than likely under TV settings.

---

### Post by iitywygms on 2010-08-02
Really?  That sounds like what I need to do.
Anyone know exactly where at?  I have been through the backend setup multiple times and do not recall ever seeing that option.

Concerning my incoming signal.  I have a cm4228, along with a 14 foot vhf antenna.  I am 60 miles from the source antenna, with mountains in between.  Yes I have an amplifier.
The cabling is all new.  My signal cannot get any better than what it is.

---

### Post by iitywygms on 2010-08-03
If anyone knows of this timeout option please let me know.  I can't find it.

---

### Post by nickrout on 2010-08-04
what sort of card is it? options depend on the type of card. (However I am not sure there is an option to do what you want).

---

### Post by LowSky on 2010-08-04
From the backend

choose Capture Cards> choose the tuner in question (I'm using a DVB DTV capture card)> look for **signal timeout**> adjust the time to much longer

---

### Post by nickrout on 2010-08-04
> **LowSky said:**
> From the backend

choose Capture Cards> choose the tuner in question (I'm using a DVB DTV capture card)> look for **signal timeout**> adjust the time to much longer

I don't think so, the comment for that setting says it relates to channel scanning, not to a situation of signal loss during recording.

---

### Post by LowSky on 2010-08-04
> **nickrout said:**
> I don't think so, the comment for that setting says it relates to channel scanning, not to a situation of signal loss during recording.

Just try it  ](*,)
What are you going to lose?

Otherwise its back to the signal strength:
Do you use a split the signal? If yes. buy a better splitter or a purchase a in-line amplifier.

---

### Post by iitywygms on 2010-08-05
I do know what you are talking about.  That is for channel scanning. I tried that in the past with no noticeable improvement.
Thank you for the suggestion thou.
And please.  I am not asking how to improve my signal strength.  I am asking how I can have mythtv wait longer before it fails recording a tv show due to signal loss. 
Yes I know.  Improved signal would help but the signal is as good as it is going to get.
Not trying to sound like a jerk and I apologize if I do.

---

### Post by iitywygms on 2010-08-05
> **nickrout said:**
> what sort of card is it? options depend on the type of card. (However I am not sure there is an option to do what you want).

hdhr and ati hdtv

---

