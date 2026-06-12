---
title: "DVDs not playing"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by w00tfest99 on 2007-10-18
I can't play any DVDs in any media player on Mythbuntu.  I've tried using the internal MythDVD player, mplayer, and xine.  Some DVDs play through the FBI warning message but then quit, some open a black screen then quit, and some just hang whatever media player I'm using.  Any ideas on what might be causing this?

---

### Post by deadgobby on 2007-10-18
If you installed the restricted CODECS it should play. Have you installed Ogle and see if the DVD would play. All so are you using Blue Ray CD's? 
Gobby

---

### Post by w00tfest99 on 2007-10-18
How can I make sure I have all the codecs?  I assumed that mythbuntu would come with all the proper codecs.  No, I'm not trying to play any blu-ray or HD-DVD discs.  Just plain ol' DVDs.

---

### Post by mybunche on 2007-10-18
I've just installed mythtv on the weekend, tv works fine but haven't tried DVD's. I'll try it tomorrow and let you know. If I forget send me a message.

---

### Post by w00tfest99 on 2007-10-18
Hmm, I just found this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I'll try this when I get home today unless someone has something better.

---

### Post by Dr Small on 2007-10-18
> **w00tfest99 said:**
> I can't play any DVDs in any media player on Mythbuntu.  I've tried using the internal MythDVD player, mplayer, and xine.  Some DVDs play through the FBI warning message but then quit, some open a black screen then quit, and some just hang whatever media player I'm using.  Any ideas on what might be causing this?
Did you try VLC ? It can play DVDs out of the box :D

---

### Post by w00tfest99 on 2007-10-18
Got it working, I just needed libdvdcss2 installed.

---

