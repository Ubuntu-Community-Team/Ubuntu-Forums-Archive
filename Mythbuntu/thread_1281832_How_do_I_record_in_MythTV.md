---
title: "How do I record in MythTV?"
date: 2009-10-03
forum: Mythbuntu
---

### Post by NinjaNumberNine on 2009-10-03
Is there a way that you can start recording quickly (with the commercial skipper activated) while watching LiveTV?

Thanks!

NinjaNumberNine

---

### Post by Lepy on 2009-10-03
If you have a properly configured remote, odds are you press the record button. 

If you are using a keyboard, R is the default button, but you can check this through mythweb or the frontend.

---

### Post by NinjaNumberNine on 2009-10-03
Thanks for the reply. Unfortunately, my remote isn't supported with linux yet... It's the one that comes with the KWorld ATSC 120.  I have pressed the R button already but I could not find where it stored the recordings. I set up the Groups in MythTV Backend and it should put it in my Videos folder, but it was not there. Wait a minute and let me try recording again, I haven't done it recently.

---

### Post by NinjaNumberNine on 2009-10-03
Ah, I see, my problem is that I don't know how to stop recording. I assumed you pressed R to start, which works, and that you press R again to stop, which doesn't work. Do you know the key to stop recording?

---

### Post by Lepy on 2009-10-03
I believe pressing R should stop the recording as well. 

I know that the record button on my remote starts the recording and will stop it too (because of the OSD), but to stop the recording it seems like there is a bit of lag as I must press the record button multiple times or wait for a while for the command to be recognized.

If you have your listings updated properly and intend to record a whole show (not just a section), I believe that the recording will stop once the show ends.

---

### Post by NinjaNumberNine on 2009-10-03
Problem is for me it says "Recording Canceled" and I think it deletes the file.

---

### Post by Lepy on 2009-10-03
If you cancel the recording instead of letting it complete by the listing schedule, I think that myth flags it as livetv. 

Make sure that you have marked the option to show livetv in the All Programs list found in Settings -> TV Settings -> Playback (or maybe General).

This is not the optimal method as you will also have to disable auto-expire and perhaps change the storage group if you want to keep the recording.

---

### Post by NinjaNumberNine on 2009-10-03
OK, I'm going to bed now but I did find the recordings in mythtv. Thanks for the help, more tomorrow!

---

