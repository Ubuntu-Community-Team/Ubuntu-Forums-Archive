---
title: "Strange MythTV Problem"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by silverbolt027 on 2007-02-21
Hey All,

So I am attempting to setup MythTV with my K-World 7131 TV-Tuner.  I sucessfully got Ubuntu Edgy to detect the card, installed MySQL server, installed MythTV, configured it all...

The problem is, when I try to watch live tv, I get a black screen.  mythbackend reports the following error when I attempt to watch live tv:

MPEGRec(/dev/video0) Error: Could not set MPEG controls 0 through 1.
                        eno: Invalid argument (22)

Any ideas or help diagnosing the problem?  I will post any other logs peeople see fit.

Thanks in advance! :)

---

### Post by silverbolt027 on 2007-02-21
solved my own problem again, by changing my card to analog, rather than MPEG2 recorder....

but I still have no sound! :(  Any ideas?

---

### Post by silverbolt027 on 2007-02-21
mythbackend reports this:

2007-02-21 19:25:45.154 NVR: Error, unknown audio codec
2007-02-21 19:25:45.263 DPMS Deactivated 
2007-02-21 19:25:46.427 Opening OSS audio device '/dev/dsp'.

Any ideas on how to get it to use ALSA?

---

### Post by NT4usB on 2007-02-21
Set the Audio Output Device and mixer to:
ALSA:default

instead of /dev/dsp

---

### Post by silverbolt027 on 2007-02-21
That brings me closer...

mythfrontend reports:
2007-02-21 23:00:34.589 Opening ALSA audio device 'default'.
2007-02-21 23:00:34.666 mixer unable to find control Master 1

mythbackend still reports:
2007-02-21 23:00:33.203 NVR: Error, unknown audio codec

Any other ideas?

---

### Post by NT4usB on 2007-02-21
lots of posts on this here... just can't remember where to find them all.
Try a google search and put in the google search window:

site:ubuntuforums.org <then all your searchwords...>
without the brackets...
you can use boolean searches that way.

For instance: site:ubuntuforums.org unknown audio codec mythtv
finds these:
[http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+unknown+audio+codec+mythtv&btnG=Search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+unknown+audio+codec+mythtv&btnG=Search)

I did fine this:
[http://www.ubuntuforums.org/showpost.php?p=1785800&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1785800&postcount=7)

---

### Post by silverbolt027 on 2007-02-21
thanks, yea I tried that fix, no avail.

I have searched all over the place...most people suggest what you have said, but it just doesn't work for me.  I assume the problem lies in the fact that the sound is coming from the TV-tuner card, and not from the system itself....I dunno

any further ideas?? I will continue to look, but for now I am stumped.

---

