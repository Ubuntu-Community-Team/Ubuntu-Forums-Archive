---
title: "Finding Hidden Audio Video Stream URL's"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by Original Brownster on 2006-11-11
How many people would find a program useful to uncover the real url of a hidden or embedded audio/video stream?

What got me onto this idea was recently I was trying to record the electric proms shows from the bbc for listening to at a later date, I couldn't get the real audio / video stream address as the link is hidden. I use firefox and when you click on the link it plays it in an embedded player window, even looking at the source code of the window still didn't shed any light on the url of where the stream was coming from and in this case there was no option to 'open stream in stand alone player' as this link has the address you need normally.
Does anyone else have similar problems or is it just me???

In the end I used ethereal and captured the packets from my network and found the url within. I'm considering writing a program to automate this process in some way, it would go something like this:

feed the web link url to the program,
it follows the link, finds the stream url
starts up mplayer or maybe vsound and dumps the file to where you choose.

Any thoughts on whether a program like this would be useful to you?

---

### Post by Enjeru on 2006-11-22
Personally, I would love to have a program like this since I've tried to find the url of streams before, but with no luck.

---

### Post by mat_london on 2006-11-22
Do you also know how to select specific streams in multi stream mms:// sites using either VLC or Mplayer, see my thread here :

[http://ubuntuforums.org/showthread.php?t=304655]("http://ubuntuforums.org/showthread.php?t=304655")

Best

Mat

---

### Post by rylleman on 2007-04-26
I would find this extremely useful.
The reason I found this post is because I was trying to find a way to find out links to hidden real player streams. But as I'm starting to realise, and your post suggests, there are no easy way to do this...

---

