---
title: "AVI Playback issues"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by dwilson08 on 2007-12-17
Hey, I searched around a bit and I dont see anyone else that has this problem. When I try to open an avi file (from either my Windows partition or my windows network... actually it didnt work from Linux either) It tries to open the file then immediately closes the program. This happens in almost every media player, Caffeine is the only one that doesn't close, but I don't get any video output (Just sound) Please keep in mind I've been using Linux for like a day, and as far as I know I have got the codecs needed. (Mp3s play fine at least)

---

### Post by dwilson08 on 2007-12-17
I guess no one else has had this problem.

---

### Post by jken146 on 2007-12-17
Is it just a single file that gives you this problem?  If so have you been able to play this file somewhere else?

---

### Post by dwilson08 on 2007-12-17
Actually its all video files. Including DVDs, it just opens a media player then immediately closes.

---

### Post by shane2peru on 2007-12-17
I'm having this problem too!  I'm using Gutsy.  Here is what I just found out from running vlc from the command line:  

```

 vlc
VLC media player 0.8.6c Janus

** (.:20180): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000281] main playlist: stopping playback

```
I changed my theme back to the human theme instead of the clearlooks I had and here is the results:
```

vlc
VLC media player 0.8.6c Janus
[00000281] main playlist: stopping playback

``` 

This is the second issue I have had with attempting to use other themes and it gives me problems!  This is downright annoying.  It didn't play correctly the second time either, but it didn't give me the error either, I probably need to log out and back in and then try again.  This is really annoying since all my digital camera videos are in avi format!

Shane

**EDIT:**  When I logged out and back in I could play an AVI file!  You need to use Human theme, and possibly get rid of your compiz setup. Mine still doesn't work as my Intel card is blacklisted so I don't use it.  This is quite annoying to me.  I may downgrade my installation to Fiesty.

---

### Post by Lostincyberspace on 2007-12-18
I had that problem it turned out to be my nvidia 7300 LE graphics card driver. you might find it to be a similar problem.

---

### Post by dwilson08 on 2007-12-18
As much as I wish it wasn't true Shane, what you said is right. When I turned off compiz and changed my theme to human avi's played back fine. Thats makes me really sad my theme was looking just how I want.

Theres gotta be another way... right? Is it because I'm using a blacklisted videocard with that compiz workaround?

Edit: Looks like its just compiz really, I can use themes other than human.

---

### Post by dwilson08 on 2007-12-18
As a test, I was watching an avi, and I tured on compiz. The video crashed like I would expect and I got the following in the command line
```
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  10701
  Current serial number in output stream:  10702

```

Any ideas?

---

### Post by shane2peru on 2007-12-18
> **dwilson08 said:**
> As much as I wish it wasn't true Shane, what you said is right. When I turned off compiz and changed my theme to human avi's played back fine. Thats makes me really sad my theme was looking just how I want.

Theres gotta be another way... right? Is it because I'm using a blacklisted videocard with that compiz workaround?

Edit: Looks like its just compiz really, I can use themes other than human.

Glad you have an answer, sorry it isn't a good one!  I too have a blacklisted card Intel i910 I think or something like that.  I had a workaround for mine, but I just re-installed my system, something wasn't right because I had other problems besides this avi issue.  

Shane

---

### Post by Lord DarkPat on 2007-12-18
deleted cuz i posted s'thing wrong

---

