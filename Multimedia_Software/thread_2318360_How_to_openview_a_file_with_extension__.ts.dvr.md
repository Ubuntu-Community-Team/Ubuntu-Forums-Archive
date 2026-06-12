---
title: "How to open/view a file with extension  .ts.dvr ?"
date: 2016-03-25
forum: Multimedia Software
---

### Post by Innernet on 2016-03-25
Hi.
My television receiver allows to record programs/movies on a flash drive plugged to its slot.  Waaaay smaller than a 'Betamax' or DVR  :D

The 720p/1020p audio and video high definition recorded file has an extension **.ts.dvr ** - Plays perfect on the TV.  How to view/play such in Ubuntu ?

---

### Post by deadflowr on 2016-03-25
Moved to **Multimedia Software**

What happens when you click on it in Ubuntu's file manager?

---

### Post by Geoffrey_Arndt on 2016-03-25
Did you try VLC Player . . . ?   It may play these files.

More info here:   [http://askubuntu.com/questions/716424/how-to-convert-ts-file-into-main-stream-file-losslessly](http://askubuntu.com/questions/716424/how-to-convert-ts-file-into-main-stream-file-losslessly) 

See ffmpeg program also:   [https://ffmpeg.org/](https://ffmpeg.org/)

---

### Post by ajgreeny on 2016-03-25
My TV also records programmes on a USB drive, but my recorded files are just .ts

If I look at one of those files with mediainfo it tells me the video is mpeg2
```
Video
ID                                       : 101 (0x65)
Menu ID                                  : 4171 (0x104B)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Custom
Format settings, GOP                     : Variable
Format settings, picture structure       : Frame
Codec ID                                 : 2
```
and the audio is also mpeg
```
Audio
ID                                       : 102 (0x66)
Menu ID                                  : 4171 (0x104B)
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 2
Codec ID                                 : 3
```

All those files play perfectly in VLC , gnome-mplayer,  and plain mplayer in terminal, but not in parole video player.

Incidentally, after copying those files to my HDD, I use Plexmediaserver to stream them direct from my HDD to smart TVs,  That also works faultlessly, so Plex is not baffled by the .ts files either.

---

### Post by Innernet on 2016-03-25
Thanks, gentlemen.
deadflowr , Geoffrey : In 'open with Files' ; it went to gedit.  Changed to open with VLC; hit play and nothing. Then I opened this thread.

After reading your responses, on VLC --->  Media ---> Open file ---> selected file and played like a charm.  Simple things but never done before.  Good guidance, thanks.

ajgreeny :  What TV brand/model do you have ?

---

### Post by ajgreeny on 2016-03-25
I said smart TV for simplicity in this thread.  It is actually a small digital/analogue TV about 4 years old but with an HDMI input port into which I have plugged a Now-TV box, which I don't really use much for Now-TV's subscribed programmes but more for the catch-up services in UK from the major channels, BBC, ITV, Channel-4 and Channel-5, plus the many things available on the Now-TV box when you side-load the plex application from, in my case, Rarflix.

I can record programmes on the USB hard disk, copy them to my HDD, and then play them via the Plexmediaserver through the Now-TV box.  I also have several ripped DVDs, all my photos and music available, and with a decent soundbar style speaker system plugged into the small TV I can get very good sound quality.

I have no idea if the Now-TV box is available in the USA, but if not the roku-box from which Now-TV is derived, is available everywhere, I believe, though for a higher cost.

---

