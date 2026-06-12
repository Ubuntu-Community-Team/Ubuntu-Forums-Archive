---
title: "My Gpodder program has died, anyone else?"
date: 2011-03-20
forum: Multimedia Software
---

### Post by fynen on 2011-03-20
I have been using Gpodder as a podcast client. It had worked very well, but now has stopped working. Tried several things, including  deleting and re-installing the software, but it still won't function. Has anyone else a problem lately with Gpodder?

As a replacement I installed Amarok, but haven't a clue on how to make it work. There doesn't seem to be any help pages, only a link to an Amarok forum which doesn't provide instructions. 

Guess I'm getting too old to intuitively figure out technical things. 
Is the problem because of a new update to Gpodder? Is there another, easy to use, podcast client to use with Ubuntu?

---

### Post by dustrho on 2011-03-24
Oddly enough my gPodder has stopped working as well. I'm getting the following when trying to download YouTube videos:

[B][I]Downloads failed
HTTP Error 400: Bad Request[/I][/B]

Did something change on YouTube's end recently?

---

### Post by tgalati4 on 2011-03-24
It's working for me under Jaunty with mp3 podcasts.

---

### Post by dustrho on 2011-03-24
Can anyone test this by subscribing to any YouTube channel by doing the following?

1) CTRL + L
2) yt:YOUTUBECHANNEL

I just need to verify if it's a YouTube issue or if there's something wrong with my gpodder configuration.

Thanks.

---

### Post by Another Monkey on 2011-03-25
Down for me as well (Sneekylinux).  Have seen lots of problems with YouTube feeds in that past as they seem to make random changes.  All other feeds are fine.

I wish the Sneekster had a different feed.

edit: the relevant YouTube file is "/usr/share/pyshared/gpodder/youtube.py".  If I can figure out what the correct request should be I can try to hack this to work (although my knowledge about "Python" extends to being able to spell it).
A lunchtime project I think.

---

### Post by dustrho on 2011-03-28
> **Another Monkey said:**
> Down for me as well (Sneekylinux).  Have seen lots of problems with YouTube feeds in that past as they seem to make random changes.  All other feeds are fine.

I wish the Sneekster had a different feed.

edit: the relevant YouTube file is "/usr/share/pyshared/gpodder/youtube.py".  If I can figure out what the correct request should be I can try to hack this to work (although my knowledge about "Python" extends to being able to spell it).
A lunchtime project I think.

Any luck with it? I haven't been able to download new YouTube videos for over a week now. Hope you can figure it out. Thanks.

---

### Post by dustrho on 2011-03-28
Found a temporary fix for it provided by the gpodder support team. You'll need to do the following:

> To fix youtube downloads, in /usr/share/pyshared/gpodder/youtube.py:

fmt_url = fmt_url.replace('\\/', '/')

needs to change to:

fmt_url = fmt_url.replace('\\/', '/').replace("\u0026", "&")

I can confirm this change did in fact fix it for me.

---

### Post by Another Monkey on 2011-03-29
Thanks, that seems to have sorted it.

---

