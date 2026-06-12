---
title: "Recording Audio Results in Feezing"
date: 2011-07-21
forum: Multimedia Software
---

### Post by rizlmilk on 2011-07-21
I am trying to record audio, but the default Sound Recorder program in Ubuntu always freezes. Sometimes it will freeze when I press the record button, other times it freezes a few minutes into the recording. This is very frustrating as I need to record for an average of 10 minutes at a time. Is there any widely-known problem with Sound Recorder not working? Usually my entire computer freezes after Sound Recorder stops working. (I can move the mouse but can't interact with anything)

Also, I've tried Audacity. It usually only loads once I have closed all programs, and even then it still may take a couple of minutes to load. (which is odd because my computer is otherwise very fast) Even then, it will still freeze.

I assumed I must have messed something up, but I just installed Ubuntu on a separate drive and it gives the same freezing problem on the brand new installation.

I'm using 10.04 if that matters.

---

### Post by lkjoel on 2011-07-21
> **rizlmilk said:**
> I am trying to record audio, but the default Sound Recorder program in Ubuntu always freezes. Sometimes it will freeze when I press the record button, other times it freezes a few minutes into the recording. This is very frustrating as I need to record for an average of 10 minutes at a time. Is there any widely-known problem with Sound Recorder not working? Usually my entire computer freezes after Sound Recorder stops working. (I can move the mouse but can't interact with anything)

Also, I've tried Audacity. It usually only loads once I have closed all programs, and even then it still may take a couple of minutes to load. (which is odd because my computer is otherwise very fast) Even then, it will still freeze.

I assumed I must have messed something up, but I just installed Ubuntu on a separate drive and it gives the same freezing problem on the brand new installation.

I'm using 10.04 if that matters.
Could you give me the output of this Terminal (Applications->Accessories->Terminal) command?
```
free
```

---

### Post by shantiq on 2011-07-22
i have two command-line ways here which are solid 
For me audacity has always been a great tool for audio manipulation on ubuntu but for recording often can be a nightmare or at best a hit and miss affair


**[grab desktop sound]("http://ubuntuforums.org/showthread.php?t=1805550")**   and **[here]("http://ubuntuforums.org/showpost.php?p=11053351&postcount=9")**

[and if it is **voice** you want]("http://ubuntuforums.org/showthread.php?t=1704350")

---

### Post by rizlmilk on 2011-07-22
Thanks to everybody who has responded. I have since installed 11.04 and that fixed all of my problems. I suppose it was just a 10.04-specific problem because brand new installs were having difficulty in recording sound with any application and 11.04 magically works.

---

