---
title: "Amarok: No suitable demux plugin"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by snakyjake on 2006-09-06
Trying to play mp3 files in Amarok (v1.4.2).  It plays ogg files fine.  Rhythmbox and Banshee play mp3 files.  I also use Xubuntu.

Error Message:
Error Loading Media
No suitable demux plugin. This often means that the file format is not supported.
file:///home/jake/Podcasts/NPR: On Point with Tom Ashbrook/WBUR_5692690.mp3

Thank you,

Jake

---

### Post by croak77 on 2006-09-07
Install libxine-extracodecs

---

### Post by snakyjake on 2006-09-07
That worked.  Thank you.

---

### Post by redvox on 2006-11-26
I ran across this error message too, and tried to follow the advice above, but it turns out I already have these installed.  If anyone can help me understand why I might still have these errors, I'd appreciate it.

---

### Post by ethos101 on 2006-12-10
I'm having the same problem when I click on a shoutcast stream.  I can play aac+ streams but not mp3 streams.  I have the extra codecs installed also.

---

### Post by destructchaos on 2006-12-30
i'm also having this problem.  i can play mp3 and aac files from either my hard drive or my ipod, but i can't seem to play streams.

---

### Post by RomanW on 2007-02-20
I had the same problem. Reinstalling the libxine-codecs (even though I already had them) fixed the problem for me.

---

### Post by st14n on 2007-03-27
I had a similar problem, only that local mp3s worked fine but radio streams did not. The fix that worked for me was to close Amarok, delete the ~./xine folder and restart Amarok.

---

### Post by mohnkern on 2007-04-07
In addition to removing .xine, I found removing .gxine solves the problem as well.

---

### Post by Gunner_Sr on 2007-10-22
I tried initially to install libxine-extracodecs on Feisty. It said that the following package can be installed to replace it, which was libxine1-ffmpeg. So installed that package and it worked like a charm.

Thanks. :guitar:

---

### Post by freetonik on 2007-10-25
nothing helps
and there is no libxine-extracodecs in repo

---

### Post by stryderjzw on 2007-10-28
> **freetonik said:**
> nothing helps
and there is no libxine-extracodecs in repo

As mentioned in the previous post, it's been replaced by libxine1-ffmpeg.  Try that.  Mine was already installed, but still not working.  I deleted both .gxine and .xine folders in my home directory and it works fine now.

Justin

---

### Post by go_beep_yourself on 2007-11-21
I have libxine1-ffmpeg installed, and I still get that error.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=50961&d=1195691014[/IMG]

---

### Post by RgnKjnVA on 2007-12-21
+1  re: lib installed, still see the problem

---

### Post by 3ntity on 2007-12-22
> **st14n said:**
> I had a similar problem, only that local mp3s worked fine but radio streams did not. The fix that worked for me was to close Amarok, delete the ~./xine folder and restart Amarok.Thanks, that did the trick.
Somehow i think this problem was caused because of installing AmaroK first, then the codecs... But that's just a hunch ;)

---

### Post by amanita on 2007-12-27
Hi, the same problem here. When Amarok starts it always creates new .xine folder in my home. libxine1-ffmpeg is installed ](*,)

---

### Post by Gummi on 2008-01-07
Bump

---

### Post by RedRat on 2008-01-10
Posted this same situation in another thread but get the same demux problem. Rythimbox will not play shoutcast streams either. This is a brand new installation of the 7.10 on a new Dell machine (virgin install). Funny thing is that Amarok on my old Dell Dimension 4100 plays the streams. Any comments???

---

### Post by tgrisier on 2008-01-11
> **st14n said:**
> I had a similar problem, only that local mp3s worked fine but radio streams did not. The fix that worked for me was to close Amarok, delete the ~./xine folder and restart Amarok.


+1 on this solution.  Worked like a charm.

---

### Post by dragon_788 on 2008-01-13
+1 as well, installing the libxine1-ffmpeg and quitting completely out of Amarok (in addition to deleting the .xine folder) fixed the streams for me.

---

### Post by Ateo on 2008-01-14
Annoying issue. If I click on a shoutcast stream enough times, the stream finally kicks in. So, this most definately a bug with either amarok or one of the plugins. Sometimes, I only have to click it once and it starts.

So, what's the real issue here? My bet is libxine1-ffmpeg is the culprit. Whether installed before or after amarok should be irrelevant.

This is a major show stopper.

---

### Post by 0micron on 2008-01-26
I had the same problem when trying to play a shoutcast station. However, removing the .xine folder in my home directory solved the issue.

---

### Post by jasex on 2008-03-02
I found to get my entire problem solved, which was inability to play mp4 songs and a few other files.... was to delete the ~/.xine folder and reinstall the ffmpeg for xine =) just pointing this out to help any others who stumble upon this same issue. 

hope this helps at least some people

oh yeah this isn't relevant... but amarok is like the greatest audio manager.... imo if you want to call it a 'manager' too bad exaile doesn't compare, because I am kind of addicted to GNOME now, but you can't ever steal my KDE shine


THUMBS UP on amarok for anyone thinking about installing it that stumbles on this thread

---

### Post by propan0 on 2008-06-14
Well, I've tryed all of the above, and stil get the error message on a random basis.

I went into the irc channel** #amarok in irc.freenode.net**, and asked about the issue in there, **here is what I was told:**

[LIST]
[*]It's a missunderstanding between xine and the streaming server (rather than a bug).
[*]It needs to be fixed in xine and the streaming server.
[*]Amarok can't do much about it.
[/LIST]


So it looks like we are out of luck for now... til xine figures out what's going on.. anyone what's the status on this?

---

### Post by lenu on 2008-07-08
> **tgrisier said:**
> +1 on this solution.  Worked like a charm.

+1 for me as well. i couldn't play mp3's but quitting amarok and deleting /.xine solved the problem.

propano0's problem still persists though.

---

