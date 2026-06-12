---
title: "Embedded Video in PDF files"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by zabyss on 2007-05-31
I'm not sure if this belongs under this category, but it's at least related...
I read an online magazine called Winding Road, which can be downloaded in PDF format.  There are usually several videos embedded in the file, which I could view in Windows under Adobe Reader.  The default File viewer in Ubuntu doesn't play these videos.  Is there another viewer that allows for this, or do pretty much all others do it?  Better yet, is there any way to configure the file viewer to do it?  I hate cluttering up my system with extra programs that do the same thing, but I know there are several other options that I can try out if I need to.  I just thought someone might know, and it appears it hasn't been discussed previously.

---

### Post by reckless2k2 on 2007-05-31
I've never heard of a PDF file with embedded video. Are you sure it was a PDF file? Maybe someone can chime in and correct me if I'm wrong.

---

### Post by zabyss on 2007-05-31
Yes, positive it was a pdf.  Here is a link to the latest issue, though I believe you've got to sign up for free to download it.
[http://www.windingroad.com/file-download?issue=22&pdf=true]("http://www.windingroad.com/file-download?issue=22&pdf=true")

---

### Post by HotShotDJ on 2007-05-31
Worked with Adobe Acrobat for Linux.  Acrobat doesn't actually play the file.  It links to whatever web browser you set up Acrobat to use.

---

### Post by reckless2k2 on 2007-05-31
Yeah i see that. You need to install flash player plugin and you'll be fine. The video is not embedded int he pdf. Only a link to.

---

### Post by zabyss on 2007-06-01
Oh man...  I feel ridiculous.  I guess it's been a while since I opened one of those videos.  I could have sworn it opened in Adobe Reader in Windows.  Regardless, the link didn't work in File Viewer either so it still was a problem.   :redface:  Thanks guys.

---

### Post by excelsior on 2007-08-09
Hi, sorry for resurrecting this thread, but I'm having trouble getting linked avi files to work.Is the flash player plugin mentioned for acrobat or firefox? If so, I can't find instructions on how to download plugins for acrobat

Thanks

---

### Post by reckless2k2 on 2007-08-10
i was talking about flashplayer plugin for firefox. view this site for falsh install and other nice instructions:

[http://easylinux.info/wiki/Ubuntu:Feisty](http://easylinux.info/wiki/Ubuntu:Feisty)

---

### Post by excelsior on 2007-08-10
OK, I have that already, and it's not what I need- thanks anyway.

Is there a way to play avi animations within the pdf file itself? I've seen it done on acroread on XP.

---

### Post by maxtreiber on 2008-03-09
1st of all: it is possible to include videos into pdfs. For example using:
[http://www.uoregon.edu/~noeckel/PDFmovie.html](http://www.uoregon.edu/~noeckel/PDFmovie.html)
But unfortunately it sais on the page:
"Also note that you cannot use Linux acroread to display multimedia embedded with the help of this package. In other words, Linux platforms can be used only to create the PDF movies, but not to present them."

Does anyone know if this is still true ? I could really use this for a presentation ...

---

### Post by rosencrantz on 2008-05-08
In practice, this is still mostly true, alas - The problem just split into several sub-classes.

Let's suppose you want to create a LaTeX/Beamer presentation with embedded video:
a) Adobe Reader 8 for linux is indeed capable of embedding a multimedia player, but apparently only the proprietary Real Player.
b) Real Player/Helix for Linux still refuses to play any .avi-contained movies.
c) Format and specification collisions are all over the place - see [this discussion]("http://www.adobeforums.com/webx?14@@.3bca21c1/4").

Possible solutions:
a) Get the [Real Producer]("http://www.realnetworks.com/products/producer/basic.html") for Linux and try encoding your stuff as Real Media.
I have no idea whether beamer/movie15 etc. will be able to embed this, whether the Producer works all right on Linux, or whether the Adobe Reader will actually display something instead of offering you to download a not-yet-existing plugin. And it sucks to have to convert your movies to an player-restricted closed-source format to embed them in *Linux* :-(
b) Wine. Gee, I don't even remotely want to try this. According to the [Wine AppDB]("http://appdb.winehq.org/"), Adobe Reader and e.g. Windows Media Player might work seperately - I haven't seen anything about embedding. Here at least you have some choices concerning format and player.

I'll try some options and post again.

---

### Post by troubleman on 2008-05-31
This is an annoying problem, no doubt. Good news is Adobe is actually working on it:

[http://www.adobeforums.com/webx/.3bca21c1/12](http://www.adobeforums.com/webx/.3bca21c1/12)
Sounds like if you can make your movie a .rm file it might work.

-tm

---

### Post by martux on 2008-06-26
> **troubleman said:**
> This is an annoying problem, no doubt. Good news is Adobe is actually working on it:

[http://www.adobeforums.com/webx/.3bca21c1/12](http://www.adobeforums.com/webx/.3bca21c1/12)
Sounds like if you can make your movie a .rm file it might work.

-tm

Has anyone ever succeeded in creating a pdf with an embedded (real or whatever) movie which acroread can play properly? I've tried but didn't manage to. For presentations this feature would certainly be very much appreciated by many people (in particular in academia, using e.g. beamer) and it is a shame there are still no linux pdf viewers around capable of doing this.
Choosing realplayer instead of a freely available media engine is an astounding decision though, to say the least...

---

### Post by rosencrantz on 2008-07-04
I tried to encode a movie with Real Producer, which is a real pain, if I remember right: only uncompressed input movies accepted, and in the end the movie consisted of an audio track only. I had some problems with finding a suitable test movie online, so I didn't check.

There seems to be some kind of workaround by externally linking to MPlayer:
\href{run:<some code>}, the code can be a shell script or a direct bash command (cf. [http://www.nabble.com/embedded-java-applet-td14231897.html]("http://www.nabble.com/embedded-java-applet-td14231897.html") for details). The geometry option in MPlayer should take care of the screen placement. In any case, you will still have window borders (maybe choose a borderless desktop style?)

---

### Post by martux on 2008-07-08
> **rosencrantz said:**
> I tried to encode a movie with Real Producer, which is a real pain, if I remember right: only uncompressed input movies accepted, and in the end the movie consisted of an audio track only. I had some problems with finding a suitable test movie online, so I didn't check.

There seems to be some kind of workaround by externally linking to MPlayer:
\href{run:<some code>}, the code can be a shell script or a direct bash command (cf. [http://www.nabble.com/embedded-java-applet-td14231897.html]("http://www.nabble.com/embedded-java-applet-td14231897.html") for details). The geometry option in MPlayer should take care of the screen placement. In any case, you will still have window borders (maybe choose a borderless desktop style?)

FACK! I had exactly the same experience with Real [Pain] Producer and in the end not finding any sample movies on the web.

Will try your suggestion to execute an external viewer. Cheers.

---

