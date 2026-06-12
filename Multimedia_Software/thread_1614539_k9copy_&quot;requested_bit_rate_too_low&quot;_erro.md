---
title: "k9copy &quot;requested bit rate too low&quot; error on 2nd pass"
date: 2010-11-05
forum: Multimedia Software
---

### Post by Ragnar! on 2010-11-05
I am having a great time very quickly migrating from Windows through Ubuntu. 

One area that I am still having trouble in is transcoding VOB into DivX, XviD, AVI, etc. I have been succesful one time using k9copy and it made a great looking avi. Since that time I get a failure on the 2nd pass. It seems as if the problem is related to the line in the error log "requested bit rate too low". So I changed from filesize to bitrate selection in the wizard and set it at max (99999). This got it to start the 2nd pass but still ended up crashing about 3/4 of the way through with an unexpected error message. Undaunted i tried again with the same setup and options. This time I once again got the bitrate too low error on the 2nd pass.

I have tried other GUI apps like avidemux (sound out of sync with that one), WinFF (not merging the vob's together), and others without satisfactory results. It would be great if I could get k9copy to work as it did the first try as it did exactly what I am looking for.

I have mencoder and all the depedencies installed (I believe). I am running a quad core amd64 bit processor and ubuntu 10.04.

It is just puzzling to me that k9copy worked flawlessly the first time and now nothing but trouble.

These are VOB's that have been put together by IFOedit from files dmuxed by DVDdecryter (under wine) stripped of copy guard. I take the ac3 soundtrack and convert it into WAV so that i can add a commentary (rifftrax) in audacity, then convert that back into ac3 and combine it all together again. I have been doing this for some time in Windows, and can now do everything in Ubuntu except for the avi transcode (really bothersome to reboot into windows just to run DivX Pro converter).

I would appreciate any thoughts or suggestions and would love to provide any extra info you might need (I would more than likely need the command line for terminal work). It would really be great if I could just get past the problems on the 2nd pass in k9copy as it made a beautiful avi the first time.

Thank you for listening to me ramble....

---

### Post by Ragnar! on 2010-11-06
Still no love with k9copy. I must be missing something simple being new to Linux (again, I had it 10 years ago, Mandrake).

BUT, i discovered the problem with my audio sync issue in avidemux. It is reading the fps wrong and you need to enter in the fps manually. I ran mediainfo on the vob and found that it was at 24.976 fps. Avidemux had it set to 29 fps. I made the correction and the sync issue is fixed. While it did not make quite as good of a transfer as k9copy did the first time it worked, it is still very watchable and I am just being very picky here.

---

