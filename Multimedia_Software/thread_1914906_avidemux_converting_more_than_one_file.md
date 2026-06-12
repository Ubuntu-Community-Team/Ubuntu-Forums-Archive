---
title: "avidemux converting more than one file"
date: 2012-01-25
forum: Multimedia Software
---

### Post by travisjkeyes on 2012-01-25
Hi. I am using Ubuntu 10.04 and avidemux to convert files in .avi to .mp4 with MPEG-4 AVC h.264 video codec and MP3(lame) audio codec. I need to convert about 50 files (TV episodes). I have been doing them one by one, but is there a way to convert them all and just let it run for a day or however long it takes?

BTW, I don't know how to do "scripts" or anything like that so if you suggest a non GUI or command-line solution can you tell me how to run it? Thanks!

---

### Post by satanselbow on 2012-01-25
I set a batch of iplayer downloads converting using **WinFF** (in the repos) If you have a set ffmpeg line you use then add it as a preset and away you go ;)

---

### Post by travisjkeyes on 2012-01-25
@Satanselbow Thanks for your suggestion. I tried to install WinFF and convert but the preset codes weren't working for me and it created a whole new set of problems. I searched the forums and it seems other people were having the same problems I was having with WinFF and the solutions were dling and installing a bunch of stuff... The interface was a lot simpler and it looked like a good program but I didn't feel like messing around with it.

Instead I kept poking around in avidemux and found my solution!

I simply had to open the file I wanted and select the codecs I wanted then go to File > Add job. Repeat for all the files I needed and then go to File > Job list > run all jobs. Works!

Now I can let those convert and use your line code "cd /fridge/beer/ | drink && fallover" HAHAHA I like that

---

