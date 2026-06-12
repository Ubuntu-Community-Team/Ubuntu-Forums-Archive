---
title: "DVD: Copy or Transcode?"
date: 2009-01-24
forum: Multimedia Software
---

### Post by Brian96 on 2009-01-24
I am slowly but surely converting my PC into an HTPC (no TV tuner, just using it with the TV to stream internet video, etc.). I'd like to backup my DVD library to my harddrive to watch from the PC. For now the computer is hooked up to a 27" SDTV, but I'd like to think that eventually it will be hooked up to a larger HDTV. That is to say, I'm more interested in making sure that the video quality will be good than shrinking the video down to save HDD space. Oh, I'd also like to preserve the "extras" on the DVDs, and the menus if it's not too much trouble.

Here are my questions:

1. Would I be better off copying an ISO of each DVD (e.g., using K9Copy), or transcoding it to a file?

2. If transcoding is the best way to go, which codec format is the best (xvid seems to be popular) and does it matter what file type I use as the container (avi, mp4, etc)? Also, what audio codec?

I've played around with dvd::rip and K9Copy, and I'm a little more comfortable with K9Copy at this point.

Thanks in advance.

---

### Post by Twitch6000 on 2009-01-24
> **Brian96 said:**
> I am slowly but surely converting my PC into an HTPC (no TV tuner, just using it with the TV to stream internet video, etc.). I'd like to backup my DVD library to my harddrive to watch from the PC. For now the computer is hooked up to a 27" SDTV, but I'd like to think that eventually it will be hooked up to a larger HDTV. That is to say, I'm more interested in making sure that the video quality will be good than shrinking the video down to save HDD space.

Here are my questions:

1. Would I be better off copying an ISO of each DVD (e.g., using K9Copy), or transcoding it to a file?

2. If transcoding is the best way to go, which codec format is the best (xvid seems to be popular) and does it matter what file type I use as the container (avi, mp4, etc)? Also, what audio codec?

I've played around with dvd::rip and K9Copy, and I'm a little more comfortable with K9Copy at this point.

Thanks in advance.

To question 1. that is more of a personal preference. I like just transcoding and using the codec avi or divx. Ofcourse this can slow things down if you transcode and stream at the same time.

---

### Post by dorkdork777 on 2009-01-24
1. If you want extras and not too much quality loss, ISO **all the way**. Encoding will result in quality loss, though it might not be too visible. Also if you have it stored as one video file, you've just got the movie, while an ISO of the disc is a copy of the DVD itself, including menus, extras and *sigh...* adverts.

2. But if you're sure you want to encode to a format, I'd suggest using MKV for the best quality, but for the best quality/compatiblity combo, xvid is very good.

---

### Post by Brian96 on 2009-01-25
Thanks for the replies. Here's where I'm at:

1. I've used K9Copy to backup a DVD as an iso. This was incredibly painless, and certainly seems to be the easiest way to simply backup a DVD. On the other hand, I was disappointed with the playback, as I could not figure out how to get navigable menus in either VLC or Totem; both simply played all the tracks strung together.

2. I've tried transcoding to either mp4 or avi (couldn't figure out mkv with those apps) in different ways using both dvd::rip and K9Copy. Due to various problems, I never did end up with a usable output file.

3. Now I'm trying to transcode to mkv (x264 and ac3 streams) using a script I found on here somewhere. In the process I learned that I could dump the movie stream/track/title (not sure of the preferred term) to a single .vob file, and that this file is playable. In terms of ending up with a playable file that is the movie, the whole movie, and nothing but the movie (not entirely true, I know, as there will be subtitle tracks, etc), this seems to be the easiest method.

My new question, then, is what are the pros and cons to just dumping the movie to a single .vob file? Is there any loss (wouldn't think so, as there doesn't seem to be much--if any--compression going on)? The only con I can think of is that this would not give me a true backup of the DVD (unless I dumped all the menus, etc., also). Am I missing something?

---

### Post by justsomedude on 2009-01-25
> **Brian96 said:**
> 
My new question, then, is what are the pros and cons to just dumping the movie to a single .vob file?

PRO:
-lossless
-very fast

CON:
-large files (can cause problems with FAT32 file systems)

If hard drive space is not an issue, this is the way to go.

> **Brian96 said:**
> Is there any loss (wouldn't think so, as there doesn't seem to be much--if any--compression going on)? The only con I can think of is that this would not give me a true backup of the DVD (unless I dumped all the menus, etc., also). Am I missing something?

If you just dump it as a vob file, there is no loss (unless the programm you use is configured to compresss the files to fit on a 4.7 GB DVD).

If you want to preserve the menus, dump the whole content of a DVD to a folder. Vobcopy can do this for example (use it with the -m option). VLC should be able to open the .ifo file and display the menu.

---

