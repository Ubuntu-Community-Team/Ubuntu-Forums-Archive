---
title: "Looking for a DVD Video Burner Program"
date: 2014-01-06
forum: Multimedia Software
---

### Post by gregoryshock on 2014-01-06
As an old Windows User who is gradually moving into the world of Linux I've been looking for tools to replace the things I've always done in Windows.  The other day I happened to be running Ubuntu/Zorin and I had some video files from youtube I wanted to convert/burn to a DVD to play on my TV DVD Player.  I found Brasero on my Distro so I decided to try it.  It seemed to read the file formats I'm using (AVI and Mp4)  But when I clicked on burn it ejected my disc and said I have a disc error.  I know for a fact that there is nothing wrong with my RW DVD because I've been using it with Windows DVD Maker, and after I gave up on Brasero I went back to windows to burn the DVD.  Windows DVD Maker did it just fine.  I also have Ubuntu installed, so I booted up with Ubuntu and found Brasero.  This time when I tried it, it wanted me to install some extra things for reading my files.  I downloaded them and installed them.  Next I tried to burn, but after letting it run for an hour the progress bar never moved!  I don't know what's wrong but my Brasero seems to be junk on two operating systems!  I'm looking for something that I can take my Videos files and make normal DVDs for my TV DVD player.  What are my options?

---

### Post by SeijiSensei on 2014-01-06
Try [DeVeDe]("http://www.rastersoft.com/programas/devede.html").  It's in the Ubuntu repositories.

---

### Post by speartip on 2014-01-07
As mentioned above, you need to convert the files first, to an iso file using devede then burn the iso to disc so it can be played in any dvd player.
You may also need to make sure you have all the relevant multimedia codecs installed.
```
sudo apt-get install lubuntu-restricted-extras ffmpeg cdrdao transcode sox
```
That should be enough, but make sure you have canonical partners repos enabled first.

---

### Post by speartip on 2014-01-08
saraguo1123,
All the apps you have listed are Windows apps.
If I have read the post correctly the Op is looking for Linux equivalents. Unless of course you have all these apps working in Wine, in which case I apologize.

---

