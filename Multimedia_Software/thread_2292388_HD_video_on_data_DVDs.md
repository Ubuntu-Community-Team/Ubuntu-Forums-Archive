---
title: "HD video on data DVDs"
date: 2015-08-27
forum: Multimedia Software
---

### Post by VanillaMozilla on 2015-08-27
I sometimes make videos for myself and for a small group.  Until recently I have made video DVDs, but now I really need to move to high definition.

I surveyed my users, and many of them have no plans to get Blue Ray.  I also plan to leap-frog over that technology.  It's easy just to put video files on a data DVD.  My users can view them on a computer, and that would serve the purpose in a utilitarian way.

But I'm looking for a little more pizzazz.  I am able to make nice-looking video DVDs, which display an introductory photo with menus, etc.  I could release a combined video and data DVD, but what would really be nice is if I could display a the introductory photo with a menu that would provide links to activate the HD video files.  In other words, I'm looking for sort of a lightweight workaround or substitute for authoring a DVD, with high def. content.  Does anyone have an idea how to do that?  Of course, it needs to work on any computer, without installing software on the users' computers.

---

### Post by TheFu on 2015-08-27
I only know that you need to use h.264 for the video codec and some popular audio coded like AC3, AAC, mp3.  Each has downsides. Most players support AAC (yuck) - Chromecast only does h.264/AAC - nothing else without transcoding. That format is what most streaming services push.

Next is the video file container.  mp4 is popular, but mkv is 1000x more capable.  Windows7 won't play mkv natively. Don't know about later versions. On Linux, the top 10 video players handle mkv containers just fine.  Most streaming players do as well, so does android. 

As to the menuing ... I haven't a clue. Sorry.  Don't believe anything exists outside of the BluRay, DVD, XVCD, SVCD methods, but I haven't looked for it at all.  MKV did have the idea of a menu a few years ago. Guess it didn't get any love.

An idea ... may not good, but an idea ... 
Use chapters to control the video playback.  Chapter 1 would be the menu. Chapter 2 ... the intro, Chapter 3 ... 

Interesting problem. Thanks for posting.

---

### Post by VanillaMozilla on 2015-08-27
Here's something that sounds like it might work.  It does like an old, ugly hack that may not work, however.
[http://renomath.org/video/linux/hddvd/](http://renomath.org/video/linux/hddvd/)

---

### Post by Rob Sayer on 2015-08-28
> **VanillaMozilla said:**
> Here's something that sounds like it might work.  It does like an old, ugly hack that may not work, however.
[http://renomath.org/video/linux/hddvd/](http://renomath.org/video/linux/hddvd/)

That seems like a lot of effort for something only apparently tested on 2 DVD players and only one of them worked.  I wouldn't be optimistic.

Look up DVD compliance specs.  It does not use HD.  This is a question often asked by noobs on the videohelp  forum, and the answer by video geeks way more knowlegdeable than I is always the same.  Forget it.

---

### Post by SeijiSensei on 2015-08-28
Widescreen DVDs use "anamorphic" encoding with non-square pixels to create an effective image width greater than the DVD standard maximum of 720x480 (on NTSC players; PAL DVDs have slightly different dimensions).  

[Handbrake Anamorphic Guide](https://trac.handbrake.fr/wiki/AnamorphicGuide)

[DeVeDe]("http://www.rastersoft.com/programas/devede.html") has the ability to make menus and such.  I don't know whether it can create DVDs with the menu and links to video files in Matroska or MP4 format, though.  I tried this once long ago, with the now-deprecated older version of DeVeDe.  It converted the Matroska input files in 720p into MPEG2 video, the DVD standard, but preserved the widescreen aspect ratio.  The resulting disc image was playable on ordinary DVD players.

For a disk with the videos in data files, a simple menu solution could use an HTML index page with links to the individual files.  Something like:
```

<html>
<body style='background-image: url("background.jpg")'>
<h4><a href="file1.mkv">Jenny's First Birthday!</a></h4>
<h4><a href="file2.mkv">Jenny's Second Birthday!</a></h4>
...
</body>
</html>

```
I don't know whether you can get an index.html file to load automatically when the DVD is inserted though.  You could just name the file something obvious like MENU.html and tell your friends to click on that.  It will open in a browser, of course.  How the browser handles a file in .mkv depends on the file associations set up on the user's computer.

---

### Post by VanillaMozilla on 2015-08-28
Thanks for your replies so far.

Just to be sure, note that I'm only interested in high-definition content, and I want to display it at high def.  I'm not interested in converting high-def to low-def, and I don't need to support ordinary video DVD players.  I know that *video* DVDs (as opposed to *data* DVDs are not supposed to display high-def. content, unless there is some little-known hack or trick that I'm not aware of.  I'm open to almost any suggestion.

I had considered running it as a Web app., and that's probably the best idea I have heard yet.  I don't have any experience with that, but I can certainly find out how to do it.

---

### Post by VanillaMozilla on 2015-08-30
Another idea would be a program that displays a static image with the menu and links.  The links would use the system default media-viewing program.  There could be three program versions in the root directory:  "Linux--click here", etc.  It would not (or should not) autorun, but it might have an advantage in startup time.  It's possible that something like that has been written.

Other thoughts?

---

### Post by mc4man on 2015-08-30
While I know little to nothing of such things it feels like a local web page could be the menu.

---

### Post by VanillaMozilla on 2015-08-31
A Web page does work, but there's a problem.  Ideally, the media player should terminate after finishing and return focus to the menu page.  Unfortunately, that's a property of the media player, and I don't know of any way around this problem.  Unless, perhaps, there is a good cross-platform media player that can be started with this option from a command line?

---

### Post by SeijiSensei on 2015-08-31
I doubt that is soluble.  The web page just opens the linked content, but there is no further communication between the two processes.  Remember that the web protocols are designed to be "stateless," meaning each transaction is unique and knows nothing about events before or after the current one.

---

### Post by VanillaMozilla on 2015-09-01
Well, I'm trying to figure out how to do this by hook or crook.  Maybe this would work?:  [https://www.videolan.org/doc/vlc-user-guide/en/ch07.html#idp7188800](https://www.videolan.org/doc/vlc-user-guide/en/ch07.html#idp7188800) .

Of course, that would no longer be a guaranteed, default behavior for all computers, but perhaps it wouldn't be too odious a task to use this for enhanced behavior.  The html file could test for presence of the plugin.  As it is, I don't mind recommending the VLC player for all users because of its performance and slow-motion capability.  Perhaps the VLC plugin wouldn't be too much of a stretch, and in any case none of this would be be required to view the videos.

And then there is this:
vlc --play-and-exit <filename>

I tried it from a command line, and it works.  It should work in a shell called by a small, independent program--right?  The only system requirements (I think) would be the VLC Player and the ability to run a small program in userspace.  I don't know about security restrictions and zealous security software that might interfere--I don't have any experience with that.  But in theory it should work, right?  I assume the user would be asked for permission to run it--or chmod, etc.--and that's a downside.

I assume it's not workable from a Web browser, though, because executing a command line from an html file probably *would* be a security violation.

---

