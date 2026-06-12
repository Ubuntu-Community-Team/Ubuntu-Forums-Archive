---
title: "mythstream audio/video synch problem"
date: 2008-06-27
forum: Mythbuntu
---

### Post by sr_guy on 2008-06-27
Does anyone have the issue of audio/video being out of synch when playing youtube vids with mythstream with mythbuntu? Is there a solution to this problem?

---

### Post by sr_guy on 2008-06-28
I'm sure others have had this issue? Anyone with a solution?

---

### Post by simonlesorcier on 2008-06-28
do you have it running to the point your only problem is audio sync?
what steps did you take?

cheers

Eduardo

---

### Post by ctpaterson on 2008-06-29
> **simonlesorcier said:**
> do you have it running to the point your only problem is audio sync?
what steps did you take?

cheers

Eduardo

The audio/video sync can be dealt with during play by using the + and - keys to adjust the sync.

Eduardo, you may still be dealing with a previous problem.  See this thread to see if it helps (check out the guy's bug report): [http://ubuntuforums.org/showthread.php?p=5254558](http://ubuntuforums.org/showthread.php?p=5254558)

---

### Post by sr_guy on 2008-06-29
Yes, everything is working fine with the parser, and I can get a list and play the youtube vids. The vid/audio synch issue seems to be on the lower bitrate vids on youtube. Other higher bitrate vids are fine with no synch problems most of the time.

I don't have any + or - keys on my hauppauge remote. I have the standard remote for the PVR-150. Any further suggestions would be apprectiated.

---

### Post by ctpaterson on 2008-07-05
> **sr_guy said:**
> Does anyone have the issue of audio/video being out of synch when playing youtube vids with mythstream with mythbuntu? Is there a solution to this problem?

Ultimately, I haven't found anything that will prevent the issue from
occurring - but when it does, I've found a means to deal with it.

Mythstream is using mplayer to play the videos, and the A-V sync can
be controlled with the "+" and "-" keys.  In my case, my mythbox is
solely controlled with an Hauppauge remote, so I've had to remap some
buttons to do the trick.

The CH/PG up and down buttons don't do anything in mplayer, and they
seemed suitable options, so I remapped those.

In the front end, select Setup -> Edit Keys -> Stream, and bind the
CH/PG up and down buttons to AVDEC and AVINC.

Now, when I play a stream that's out of sync, I can just hit the
buttons on my remote until it all lines up again.

---

