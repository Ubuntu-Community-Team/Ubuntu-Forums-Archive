---
title: "Rendering subtitles with DVD:Rip"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by kidux on 2008-03-03
First off, I jut want to say you guys rock! I've been lurking here for awhile, and it's taught me quite a bit. I came from RH7->RH9->FC3->Slack10-12->Kubuntu Feisty, and now am running Ubuntu Feisty on my laptop and Xubuntu Gusty on my desktop. 

I set my desktop up to be a media server, so I can share my movies and music though my LAN, and using the latest uShare I can even stream to my 360.:guitar:

So on to my problem. I am in the process of ripping my DVDs to my HDD, and started out with one that required subtitles because the audio is Japanese. So using DVD:rip, I attempted to rip it but it kept bombing out with an error that I couldn't understand. Reading thread after thread, I couldn't figure it out, so I tried Acidrip, K9Copy, and some others with the same result. 

Actually, let me correct myself. DVD:Rip did rip it into vob format (which was playable), it was the transcoding to avi format that gave me the problem. In K9Copy, it wouldn't work because I was selecting the subtitle track to encode as well. 

So I used K9Copy to make an ISO of the disk, then used VLC to watch it but even though it saw that there was a subtitle track, it wouldn't display it, so I determined I didn't have subtitle support, and after further review of the log from DVD:Rip, I was able to confirm this. I have since ripped 3 DVDs to avi with no problems, so what do I need to get DVD:Rip to render subtitles into the avi?

Also, what is the best, highest quality codec to use when encoding the movie as an avi? File size is not an issue.

Thanks!!

---

### Post by kidux on 2008-03-03
I also had another question. What is "deinterlacing", and how would I find out if a DVD is interlaced in the first place to require deinterlacing?

---

