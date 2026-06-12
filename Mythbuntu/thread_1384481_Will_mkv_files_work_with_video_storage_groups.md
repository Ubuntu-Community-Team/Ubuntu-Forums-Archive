---
title: "Will mkv files work with video storage groups?"
date: 2010-01-18
forum: Mythbuntu
---

### Post by williammanda on 2010-01-18
After reading alittle about mkv files. The question came up if mkv could be streamed and work with stroage groups? The biggest headache seems to be the conversion of the existing vob & iso files to mkv format. Also does anyone current use a linux mkv program and if so...what is the program?

---

### Post by williammanda on 2010-01-18
I found this program:

[http://www.makemkv.com/]("http://www.makemkv.com/")

I tried it out on a windows unit and it seems to work fairly well except it doesn't see vob files. I would like to see if anyone here has used it on ubuntu and what comments you have?

---

### Post by nickrout on 2010-01-18
> **williammanda said:**
> I found this program:

[http://www.makemkv.com/]("http://www.makemkv.com/")

I tried it out on a windows unit and it seems to work fairly well except it doesn't see vob files. I would like to see if anyone here has used it on ubuntu and what comments you have?

I have installed it on linux but not yet used it. It worked fine on windows, although I'd rather transcode to something smaller - the program does no transcoding so you end up with huge files (but no worse than the vobs of course). Its advantage is you get the works as far as the original title is concerned - multiple audio tracks, subtitles, chapters etc (just not the dvd menu).

mkv files play in the Internal player, but there is some problem with subtitles. Take a look at the mailing list archives - there was a recent thread on this.

However they do play brilliantly in xbmc, but then again so should your vobs!

---

### Post by williammanda on 2010-01-18
> **nickrout said:**
> I have installed it on linux but not yet used it. It worked fine on windows, although I'd rather transcode to something smaller - the program does no transcoding so you end up with huge files (but no worse than the vobs of course). Its advantage is you get the works as far as the original title is concerned - multiple audio tracks, subtitles, chapters etc (just not the dvd menu).

mkv files play in the Internal player, but there is some problem with subtitles. Take a look at the mailing list archives - there was a recent thread on this.

However they do play brilliantly in xbmc, but then again so should your vobs!

I tried it today on ubuntu and it works the same as on windows. The main reason for looking at this avenue is to be able to use storage groups. I chatted with a couple of people on mythtv-users today and mkv will work with SG. So I'm going to change the format of all my iso & vob files to mkv. I should know something tomorrow. Also I tried a couple of dvd's that wouldn't copy in mythtv and they worked in this program.

---

### Post by nickrout on 2010-01-18
> **williammanda said:**
> I tried it today on ubuntu and it works the same as on windows. The main reason for looking at this avenue is to be able to use storage groups. I chatted with a couple of people on mythtv-users today and mkv will work with SG. So I'm going to change the format of all my iso & vob files to mkv. I should know something tomorrow. Also I tried a couple of dvd's that wouldn't copy in mythtv and they worked in this program.

mkv's do have their problems on myth, even at 0.22. Do a couple and try them before you go to the trouble of converting all of them!

---

### Post by williammanda on 2010-01-19
> **nickrout said:**
> mkv's do have their problems on myth, even at 0.22. Do a couple and try them before you go to the trouble of converting all of them!

The only problem I'm aware of is the subtitle issue where it doesn't work sometimes but I don't use them.

---

### Post by williammanda on 2010-01-19
I copied two dvd's an watched them fully without any issues. So..so far so good. I also found another program called mkvmerge that will allow for conversion of vob video files (ones recorded using mythvideo) to mkv files. All but three vob files converted ok. I remember that I did have a small hand full of vob files that wouldn't copy in mythvideo so I used a windows program to copy them. This could be the issue, I'm not sure. As of today SG seems to be working along with the artwork has remained intact. I only have one issue, I can't seem to delete a video file inside mythvideo, as I could before not using SG. It replies "failed to delete".

---

### Post by nickrout on 2010-01-19
don't know of any problems?

Try this thread:

[http://www.gossamer-threads.com/lists/mythtv/users/414461#414461](http://www.gossamer-threads.com/lists/mythtv/users/414461#414461)

I suspect the delete issue relates to permissions. what does the frontend log tell you?

---

### Post by williammanda on 2010-01-19
I got the file deletion worked out. It was a permissions issue. Also the post your supplied...I'm not having any seek issues as they talked about.
Thanks

---

### Post by nickrout on 2010-01-19
> **williammanda said:**
> I got the file deletion worked out. It was a permissions issue. Also the post your supplied...I'm not having any seek issues as they talked about.
Thanks

That's excellent. May I ask what version you are running? (I don't just mean 0.22, I mean what version of fixes are you on?)

---

### Post by williammanda on 2010-01-19
version 22 fixes 23193

---

