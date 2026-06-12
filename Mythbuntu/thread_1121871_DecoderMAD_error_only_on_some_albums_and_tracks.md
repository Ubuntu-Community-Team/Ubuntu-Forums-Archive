---
title: "DecoderMAD error only on some albums and tracks"
date: 2009-04-10
forum: Mythbuntu
---

### Post by SchneiderIS on 2009-04-10
I am experiencing an odd problem.  Add because all other posts I have found on the issue of "decoderMAD: failed to open input. Error 5." talks about not being able to listen to any of their music.  For me this isn't the case.  I can listen to the majority of the music in my library but the some albums produce this problem.  I have gone to the file browser in Ubuntu desktop and executed VNC without error.  With MPlayer I get a "ao: [pulse] failed to connect to server: connection refused" but it still plays the audio and the same error happens on files that will play in MythTV.

It is an irritating issue in that when I randomly play tracks it will occasionally hit one of these tracks that throws the DecoderMAD error.

Does anyone have any suggestions?

---

### Post by AlecJ on 2009-04-11
For DecoderMAD error read "File not found".

If you music is on a unmounted drive or you have not updated the data base recently the file will not be found and there for can not be decoded.
MAD I know..

or the file is present but is not in the right form, i.e mp3 ect or just unreadable.

---

### Post by SchneiderIS on 2009-05-31
Sorry for the delayed reply AlecJ,  I just found the post again and the notification didn't come through.

I have checked the files and they will work if I open them with MPlayer and other media players.  They are at the right location and permissions are all good.  The files were imported through Myth and many work but some do not.  Given that Myth imported the folders I would expect it to have the right path and it should only pick up files that it knows.  These files were ripped by the same software that ripped others that work and with the same setup so it is all very frustrating.

Thanks in advance for your help.

---

