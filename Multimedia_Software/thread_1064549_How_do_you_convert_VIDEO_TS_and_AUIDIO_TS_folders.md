---
title: "How do you convert VIDEO_TS and AUIDIO_TS folders?"
date: 2009-02-08
forum: Multimedia Software
---

### Post by andrewstevens on 2009-02-08
Hey I've been looking around the forums for a while trying to find out how to get my videos which are in the format that has a VIDEO_TS folder and an AUDIO_TS folder converted to a format to do some simple video editing with(just cutting some stuff out).  The best program I've found so far is Handbrake which installed and started up great.  However when I'm converting the files or the VIDEO_TS folder to mp4 or avi formats it will just convert 14 seconds of video and not do anything else.  If anyone has any suggestions of other programs or how to fix this problem please help me.
Thanks in advance,
Andrew

---

### Post by ohgodnotanother1 on 2009-02-09
VIDEO_TS and AUDIO_TS folders are the contents of a regular video DVD.
Check this link for more information: [http://www.doom9.org/index.html?/dvd-structure.htm](http://www.doom9.org/index.html?/dvd-structure.htm)

The video on a DVD is in MPEG-2 format, so you will need a tool that supports this. I don't know about Handbrake or other editing tools as I haven't used such thing under Linux yet.

---

### Post by punx45 on 2009-02-09
handbrake says it can handle VIDEO_TS.   i would suggest double checking the title selection in handbrake, it is possible that you have some sort of filler video segment selected rather than the feature.

also, how did you get the video_ts? did you just copy it off a DVD?   handbrake needs to have libdvdcss installed, as it no longer supports decryption itself.

---

### Post by wolfen69 on 2009-02-09
you could try winff which is the gui frontend for ffmpeg.

---

### Post by diegogranziol@gmail.com on 2009-02-09
run adept or syaptic and find some kind of dvd ripping application, such as dvd::rip or acidrip, that should do the trick. If you need any help setting that kind of thing up, PM me.

---

### Post by andrewstevens on 2009-02-09
Thank you everyone for your help, I went with  [email]diegogranziol@gmail.com[/email]'s advice and tried acidrip and it's working great. As for your questions punx45 it wasn't just a filler it was the actual video it would just stop at 1.62 % complete and it's from a dvd that my dad made. When he puts video from his video camera on his laptop(vista) it automatically burns it to a dvd rather than to the harddrive.

---

