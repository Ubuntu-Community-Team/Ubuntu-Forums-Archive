---
title: "How to record a divx stream?"
date: 2011-07-25
forum: Multimedia Software
---

### Post by bennypr0fane on 2011-07-25
Hello,
 Divx webplayer in Windows can download and save a divx video file while streaming, so the stream is recorded to the hdd or sth.
 How can I do this in Ubuntu?
 In addition to Ubuntu Videoplayer I have installed Gnome Mplayer and VLC Player. Will any of this do the trick? If yes, how exaytly would I proceed?
 Thanks Ben

---

### Post by andrew.46 on 2011-07-26
MPLayer should be able to do the job. Can you give an example of a stream that you would like to capture?

---

### Post by bennypr0fane on 2011-07-31
Ok, [here]("http://vidxden.com/qlzboja86tb9/Fu_S03E06.avi.html")'s an example. As far as I know, with Video Player I can stream it, but I can't keep the file.
How would I do that in MPlayer?
Thanks, BEn

---

### Post by andrew.46 on 2011-08-06
Ooops sorry about the delay :(. Unfortunately now I have had a good look at the stream it looks like I can only reproduce your problem, the stream plays well enough with the gecko plugin but still manages to hide its actual location...

---

### Post by bennypr0fane on 2011-08-07
So is that the same problem for all divx streams? :confused:
Is there no application that will allow me to keep the file after streaming it?
It's so simple in Windows, especially since the divx codec, I believe, was created with this feature enabled right from the start, yes? (this may actually be not true at at all, but at least ever since I've first encountered divx on the web)
How can it be there is no way of doing this in Ubuntu?
:(

---

### Post by andrew.46 on 2011-08-09
The problem is more that I cannot find the *actual* address of the stream :(. With a direct url the stream can then be saved...

---

### Post by SeijiSensei on 2011-08-09
Firefox with gecko-mediaplayer and the DownloadHelper plugin found and saved it for me.  I gave smplayer the URL that DownloadHelper reported, but it choked for some reason.  Downloading with DownloadHelper created an AVI file that smplayer could play.

---

### Post by bennypr0fane on 2011-08-10
> **SeijiSensei said:**
> Firefox with gecko-mediaplayer and the DownloadHelper plugin found and saved it for me.  I gave smplayer the URL that DownloadHelper reported, but it choked for some reason.  Downloading with DownloadHelper created an AVI file that smplayer could play.


Dude, I didn't even know Downloadhelper could download .avi or .divx! I thought it worked just for flash video! This is awesome,thanks!
Streaming with Mplayer seems unreliable though, and also it doesn't store the file, does it?

---

### Post by beew on 2011-08-11
> **bennypr0fane said:**
> Dude, I didn't even know Downloadhelper could download .avi or .divx! I thought it worked just for flash video! This is awesome,thanks!
Streaming with Mplayer seems unreliable though, and also it doesn't store the file, does it?


Mplayer is very reliable in streaming DIVX  my experience. It doesn't store the file as far as I know but I wouldn't want to anyway. If you want to watch TV shows like futurerama (from your link) and store the file you may want to check out Miro.

---

