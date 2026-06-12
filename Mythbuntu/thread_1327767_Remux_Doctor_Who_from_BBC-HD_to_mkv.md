---
title: "Remux Doctor Who from BBC-HD to mkv"
date: 2009-11-15
forum: Mythbuntu
---

### Post by utar on 2009-11-15
Ok I had better start by saying this is not 100% on topic for this forum, other then the fact I watch the files on my myth box!  However I'm at a loss on this one and as I've had so helpful answers from here in the past thought I would make a post.

Basically I recorded Doctor Who off BBC-HD earlier today and want to remux this into to a mkv container with no recompression.

I used tsmuxer (on windows) to demux the streams and then tried mkvmerge (the windows version again but there is a build of this in the ubuntu repository as well) and other software including ffmpeg (via a front-end) but cannot get a mkv file that works on myth, vlc or anything else correctly.

What is confusing is that I managed to remux the last episode of Doctor Who shown earlier in the year, and I'm sure I used the same method.

Any help would be appreciated.



Utar

---

### Post by utar on 2009-11-16
Well in case anyone else has the same issue in future I thought I would post an update.

It seems that BBC-HD must have changed their transmission format as tsmuxer was not correctly demuxing the stream.  After a lot of experimentation I managed to get vlc to remux the stream into a new ts container (less the audio track I didn't want) which tsmuxer liked. I could then use tsmuxer to demux the ts file and cut the over-recording at the start.

Mkvmerge then worked, although I had to set the fps to 50, rather then 25.

The mkv files plays fine on myth and any other player.


Utar

---

### Post by SiHa on 2009-11-17
> It seems that BBC-HD must have changed their transmission format 
Well that explains why Myth is showing it as simply 'HD' rather than '1080' in the recordings list.

Any good? Haven't watched it yet.

---

### Post by utar on 2009-11-17
I liked it, well worth watching.

If you are interested there is a blog post on the BBC website re the change which happened in August:

[http://www.bbc.co.uk/blogs/bbcinternet/2009/11/points_of_view_and_hd_picture.html](http://www.bbc.co.uk/blogs/bbcinternet/2009/11/points_of_view_and_hd_picture.html)



Utar

---

### Post by SiHa on 2009-11-17
Yes, I stumbled across one of the BBC-HD / PQ blogs a while back. Things certainly do get quite heated. Personally, I think the PQ is pretty good, but then I've not got SKY or a Blu-Ray player yet.

---

