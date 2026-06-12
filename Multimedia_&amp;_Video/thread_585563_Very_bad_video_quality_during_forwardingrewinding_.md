---
title: "Very bad video quality during forwarding/rewinding - Why?"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Palmyra on 2007-10-21
When I am forwarding/rewinding low quality videos (videos that are less than 100MB in size), I usually get very strange pictures.  This usually happens to .WMV files, but I am not sure if it is exclusively .WMV.  I already have all codecs.

I have attached screenshots (taken from VLC's snapshot feature).

I have an Intel 915GM video card, but I don't know if that has anything to do with this problem.  This ONLY happens when rewinding/forwarding videos, not during normal play.  

Please take a look at the screenshots, and tell me what's wrong, and how to fix the problem.

[[IMG]http://img81.imageshack.us/img81/438/vlcsnap1395614du5.th.png[/IMG]](http://img81.imageshack.us/my.php?image=vlcsnap1395614du5.png)
[[IMG]http://img81.imageshack.us/img81/2839/vlcsnap1397095sg7.th.png[/IMG]](http://img81.imageshack.us/my.php?image=vlcsnap1397095sg7.png)
[[IMG]http://img81.imageshack.us/img81/4574/vlcsnap1398708ne1.th.png[/IMG]](http://img81.imageshack.us/my.php?image=vlcsnap1398708ne1.png)
[[IMG]http://img88.imageshack.us/img88/6570/vlcsnap1398906qe6.th.png[/IMG]](http://img88.imageshack.us/my.php?image=vlcsnap1398906qe6.png)
[[IMG]http://img64.imageshack.us/img64/8256/vlcsnap1399671oq0.th.png[/IMG]](http://img64.imageshack.us/my.php?image=vlcsnap1399671oq0.png)
[[IMG]http://img64.imageshack.us/img64/1343/vlcsnap1400161os0.th.png[/IMG]](http://img64.imageshack.us/my.php?image=vlcsnap1400161os0.png)

---

### Post by Light- on 2007-10-21
This is due to the way video compression works

Generally, there is a keyframe, and then all the frames after the keyframe only record the changes from the previous frame until they get to the next keyframe

Judging by those pictures, your media player seeked a frame that wasnt a keyframe. Therefore, its only displaying the changes from the previous frame, which is that garbled mess you see. If you play for a bit after seeking, it fixes itself, right? This is because it gets to the next keyframe which contains the whole image.

Someone correct me if i'm wrong

---

### Post by Palmyra on 2007-10-21
You are absolutely right about that.  If I let it go for a couple of seconds, it plays just fine.  The problem is that it doesn't do this immediately.  With high quality videos (usually .AVI files), this problem does not exist.  I could forward and rewind as much as I would like with no problem, and it instaneously plays the video the way it should play.

Do you have a solution for this problem?  I don't recall experiencing this with Windows, which I haven't used in a long time.

---

### Post by Palmyra on 2007-10-22
I should add that this doesn't seem to be distro-version specific.  I am sure this has happened since Dapper.

---

### Post by Octagonal on 2007-10-22
Does this happen in mplayer as well as VLC?
From my experience mplayer handles wmvs better than any other linux media player I've tried including kaffeine, totem and vlc.

---

### Post by Palmyra on 2007-10-22
> **Octagonal said:**
> Does this happen in mplayer as well as VLC?
From my experience mplayer handles wmvs better than any other linux media player I've tried including kaffeine, totem and vlc.

No, I just tested MPLAYER, and all the files are playing just fine using MPLAYER, but I'd prefer not using MPLAYER.  I'd prefer using either Totem or VLC.  I just don't like MPLAYER's user-interface (to begin with, it has two separate windows).

---

### Post by Palmyra on 2007-10-24
I noticed the same problem with a large WMV file as well.  What could it be, if it's not the file size?

---

### Post by Palmyra on 2007-10-27
Is there some place I can read more about this?

---

### Post by Palmyra on 2007-11-01
Nothing at all?

---

### Post by disturbed1 on 2007-11-02
It's nothing more than an issue with the wmv codec. Even Windows will do this. The player needs to update the index. If you open the same file with Windows Media player, a text will appear at the bottom stating *buffering* or *updating index*.

A video stream contains 3 types of frames, I,P,and B frames. The distance between 2 I frames is called a GOP (group of pictures). I=intra frame (key frame) contains the most amount of data, least compressed frame. P = predicted frame, predicted motion from the previous I frame, contains less data, and is more compressed than an I frame.. B = bidirectional frame, these frames contain the least amount of data and the heaviest amount of compression. They are predicted from the previous and next P and/or I frame in the GOP. WMV encodes achieve great compression by using hideously long GOPs. Meaning there is a longer distance between I (key frames). When you skip forward in a video, if the section you happen to skip forward to is not an I (key) frame, it will not be decoded correctly until the player advances to the next I frame. Hence the washed out smeary playback.The player cannot properly display a predicted, nor bidirectional frame without first decoding the referencing Intra frame.

Mplayer uses a trick to over come the short coming of using an inferior compression codec, and amateur encoders that do not understand the fundamentals of video encoding. It (mplayer) most likely just advances to the close I (key) frame when you skip forward or back. 

Some other codecs do not experience these problems because of better encoding and decoding methods. Which includes, amount other things, a more robust indexing system, referred to as the avi header, which can be considered the TOC for the file.

---

### Post by NilsE on 2007-11-12
> **Palmyra said:**
> No, I just tested MPLAYER, and all the files are playing just fine using MPLAYER, but I'd prefer not using MPLAYER.  I'd prefer using either Totem or VLC.  I just don't like MPLAYER's user-interface (to begin with, it has two separate windows).

I don't like the mplayer interface either but the good news is smplayer is a front end to mplayer and gets over all the mplayer issues. Just install smplayer from the repository and wherever you call mplayer change it to smplayer and configure away to your hearts content.  It supports single window, single instance, and even themes.

---

