---
title: "AVCHD &amp; Cinelerra"
date: 2014-09-28
forum: Multimedia Software
---

### Post by Bhakti108 on 2014-09-28
I have googled for information relating to how to import or convert and load AVCHD (mts) HD files into cinelerra. Most of the threads are pre 2012 and being as its now nearly 2015, I am hoping things have improved. I have been using Final Cut Pro on a mac for some months and that can open and convert these files direct from the camera -- Cinelerra cannot which is a great pity.

Does anyone know what I need to do to be able to open and edit these files and render to mp4 H264?

Also are things like lower thirds plugins available for cinelerra?

Thanks in advance

---

### Post by Rob Sayer on 2014-09-28
I've never used cinelerra myself ... mostly avidemux and openshot ... but I've looked into it a bit.  From what I just looked at, which didn't yield any more than what you've apparently found, it doesn't look good.  The only mention of avchd with cinelerra said to convert from avchd to something else first.  Not promising.


There doesn't seem to be any dedicated user forum for cinelerra either.  Usually that's the first thing I look for.  For something that complex I don't find this encouraging at all.  The fact that there is not just one but two cinelerra open source projects wouldn't help the situation ... I couldn't even find an up to date manual.  Hopefully you had more luck there.


You can't expect open source project development to progress all the time.  You may be surprised to learn that many open source projects consist of one guy who wrote a GUI front end for a bunch of existing utilities.

AVCHD is a proprietary format AFAIK and that can be a problem in linux.  That's the reason, for example, that Gimp is not an acceptable substitute for Photoshop for professional use.

The only linux video editor I could find with AVCHD support is Kdenlive, and according to this:

 [http://www.kdenlive.org/about-kdenlive/audio-and-video-formats](http://www.kdenlive.org/about-kdenlive/audio-and-video-formats)

it's experimental and they make no guarantees.  Good luck.

---

### Post by Bhakti108 on 2014-10-01
Well I have found out that Cinelerra needs to have a converted file to work wit, so using Handbrake I converted my mts file to mkv ( a relatively new container) but Cinelerra doesn't like that either, and as you stated Rob there is little in the way of online help. KDEnlive doens't cut it for high level editing. This is frustrating as I do not want to rebuild a hackintosh again, and dual boot is not possible with a Mac OS running on PC hardware. Handbrake would.t give me any other output format other than mkv - what to do, what to do. 

maybe someone else will jump in and help. 

Thanks Rob

---

### Post by Bhakti108 on 2014-10-01
Solved --- did some more searching on why handbrake didn't give me any other options other than m4v and this thread explains a bug and the fix [http://askubuntu.com/questions/473308/only-mkv-format-available-in-handbrake](http://askubuntu.com/questions/473308/only-mkv-format-available-in-handbrake) So after following the instructions, very simple too, I re tried with the new install of handbrake and was able to convert to mpeg-4. Opened Cinelerra, loaded the file and away it went. 

Now able to edit and see what this program is capable of. 

So there you go. Use the updated handbrake, convert the file, edit in Cinelerra.

Done  :guitar:

---

### Post by FakeOutdoorsman on 2014-10-01
If file size is not much of an issue you could use a lossless intermediate file for editing. This avoids any generational quality loss due to converting it again with a lossy encoder. The other advantage is that they are usually easy to decode for the editor. I've never used Cinelerra, and I don't know what it supports, but you can try:

```
ffmpeg -i input -vcodec huffyuv -acodec pcm_s16le output.mkv
```

Other video encoders to try are:
[list]
[*]-vcodec ffv1
[*]-vcodec ffvhuff
[*]-vcodec utvideo
[*]-vcodec libx264 -qp 0 -preset veryslow (or "ultrafast" depending if compression efficiency or encoding speed are most important)
[/list]

Other stuff:
[list]
[*]If it doesn't like mkv you can try avi.
[*]Adding -g 0 (intra only) may help with the x264 example if it still has issues decoding, but it may double the output size.
[*]Since development is so active you can [download a build of ffmpeg](https://ffmpeg.org/download.html) to take advantage of new features and bug fixes.
[/list]

---

