---
title: "How do you get full functionality in Kino?"
date: 2008-05-18
forum: Multimedia Software
---

### Post by chunlong on 2008-05-18
Hi there. Is there any way to get full functionality in Kino?

I just installed hardy, and then installed kino. In the export > "Other" tab, I get no options. There used to be options to export to flv, avi, dvd etc..
Also, in the export > mpeg tab, everything is blanked when I tried to export a whole bunch of dv video. I get the status message "Failed to execute mpeg2enc. MPEG export requires a complete installation of mjpegtools.", even though I have installed mjpegtools (sudo apt-get install mjpegtools). This happens when I have a lot of dv video in the storyboard, I seem to be able to access this tab when I do only one dv video at a time. I also noticed there are less options in here as well, like, I can't export to k3b burning?

Is there some way to make sure I have a complete installation to access all these options? I reinstalled with hardy coz I thought something was wrong with my gutsy install, but I get less options than in gutsy now.


Thanks in advance :)

---

### Post by chunlong on 2008-05-20
Looks like, this is probably something beyond kino and ubuntu.
Just another question if this can be answered, why didn't ubuntu hardy come with kino 1.3.0?

I want to try 1.3.0, is there anything wrong with installing the deb file from the debian package website (as in generic debian and not ubuntu)?
I know there will be some other dependencies I need to upgrade as well, but will this be bad for my system?

Thanks.

---

### Post by chunlong on 2008-05-21
alright, so just in case this is useful for anyone (it wasn't obvious to me at first). I figured out why I wasn't getting k3b burning and the extra stuff in the "other" tab. Those appeared when I installed other programs (such as devede etc..)

but I am still having trouble with the creating of a dvd. exporting something in the "other" tab doesn't actually work anymore (no file is even created) and I'm still having the mpeg tab disabled when I try to export (with that mjpegtools error).

Any help?

Thanks

---

### Post by glymph on 2009-08-01
The simple way to get the mpeg export tab to function in kino is to apt-get install mjpegtools.

---

