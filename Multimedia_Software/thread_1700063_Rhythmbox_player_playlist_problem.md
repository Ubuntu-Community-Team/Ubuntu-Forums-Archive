---
title: "Rhythmbox player playlist problem"
date: 2011-03-04
forum: Multimedia Software
---

### Post by kendi on 2011-03-04
Hello everyone!
Firstly to say that I am really new to Ubuntu/Linux thing. I am running Ubuntu 10.10 for about 2 weeks now and I am really happy with it. I enjoy working from it more then from Windows, and I want to learn more and more about it every day :)

Back to the problem.
I really enjoy this Rhythmbox music player version is 0.13.1, but I have a problem with playlist. I made a two of my playlists, now, when i boot up Ubuntu, run the player it takes AGES to load it. 
Now, I am really really sorry if there was a topic about it before, but would really appreciate the help with this matter.

Kind regards!
.kendi

---

### Post by kendi on 2011-03-04
Little update, I noticed something now that may be the cause.

Since my music was on D drive, maybe cause the music was not in home directory it was not loaded, so when I would load the D drive it would appear.
This seems pretty logic to me. Could be the cause :)

So question, Linux or Ubuntu after boot loads only home ? not other partitions ? (until you reach for them manually)

.kendi

---

### Post by fewjr on 2011-03-04
I'd like to jump in here too. I just installed 10.10 a couple days ago and look forward to learning more. I started back a few releases ago and gave it up for awhile. I do not have problems like you describe as of yet. My problem is with my folder full of .m4a files that I ripped a while ago. I ripped them with the default player in Hardy Heron, I think. They played fine in that version of Ubuntu and Ibex as well. On Meerkat they play, but they skip terribly. I would hate to have to rip all that music again!
 
I will say that I imported the folder of music from a different partition on the same drive that Ubuntu is installed on. I don't think that would matter though. Any thoughts???

fewjr

---

### Post by travissparks1307 on 2011-03-19
Okay, first off kendi, you're right. If your music is on a Windows partition (i.e. D: drive) then it would not load until that partition is MOUNTED. Until a drive is MOUNTED under Linux, its data is unavailable. I hope that helps.

fewjr, is this problem consistent with 10.10? Have you tried the files with another music player (besides Rhythmbox) or another OS such as Windows, Mac, or a different Linux?

---

### Post by fewjr on 2011-03-19
travissparks1307,
     I have played them in older versions of Ubuntu and Windows, but I haven't tried another player besides Rhythmbox yet. I also just got a new 11" netbook that I want to try the files on. I have a feeling I will have the same problem.
     I will download another player and let you know how it goes.

fewjr

---

### Post by kendi on 2011-03-19
> **travissparks1307 said:**
> Okay, first off kendi, you're right. If your music is on a Windows partition (i.e. D: drive) then it would not load until that partition is MOUNTED. Until a drive is MOUNTED under Linux, its data is unavailable. I hope that helps.


Yepp! Thanks :)

---

### Post by fewjr on 2011-03-23
travissparks1307,
     I finally have a day off and I installed Amarok and Alsaplayer and could not get the files to play in either. I said I would let you know. These music files are mp4 with the AAC extension, (Apple Lossless). If Linux can't play them I will rip to flac I guess or convert to flac I suppose. What do you think, can Rhythmbox play these files with some tweaking? Windoze does play them fine of course.

Thanks,
fewjr

---

### Post by fewjr on 2011-03-24
Another update on my problem. I installed Soundconverter and converted one folder of music (one album) to flac. They still will not play in Rhythmbox. They converted without any errors, so I do not know what the problem is. Oh and I miss spelled in the last post. The music folder I am having trouble with are .m4a with the AAC extention, not mp4. I'd like to add that if I rip a cd to flac, everything is fine in all the players I have tried. 

     So it has got to be a problem with the original rips. It has been a while since I ripped all those cd's, so maybe I was mistaken about how I ripped them originally. I must have used itunes to do it. I think I tried to use ubuntu for it, but had trouble and went back to itunes I guess. Would that be it you think, or should they still be able to play?

---

### Post by travissparks1307 on 2011-03-25
Hmm... I would say there is a problem with the original rips, yeah. If you are using SoundConverter, it would be best if, instead of converting from one encoded format to another, i.e. AAC to MP3 for example, first convert to MS WAV, then convert to the desired format. Going from one encoded format to the other produces a lot of "clipping" and "ticks" and "static" in the audio. The only drawback to this method (convert to WAV then convert to encoded format) is that you lose your tags. Transferring files between drives and devices (regardless of filesystem) usually does not impact sound quality. Also, (and I should have asked this sooner, I apologize) have you installed the ubuntu-restricted-extras package? These are the libraries and codecs needed to play proprietary formats such as MP3 and WMA. I have included a link to the official Ubuntu documentation that details the steps and explains what it does.
[URL="https://help.ubuntu.com/community/RestrictedFormats"]
https://help.ubuntu.com/community/RestrictedFormats[/URL]

If none of this helps you, then I would say you'll have to bite the bullet and re-rip. Good luck. Let me know what happens.

---

### Post by fewjr on 2011-03-25
I hadn't thought about converting from apple lossless to flac being a problem. That makes sense though. I will check on the restricted extras and give it another try. I'll let you know. I will re-rip otherwise. 

Thank you,
fewjr

---

### Post by fewjr on 2011-03-30
Ok bud...I tried to convert to wav first to see if it would play. The songs play now but there is still all the clicks and miscellaneous artifacts. So I have to believe it will either work with the restricted extras or I need to re-rip. I can't get restricted extras to download right now. Maybe the wireless connection. I'll post later.

fewjr

---

