---
title: "Totem crashes playing x264 .mkv files"
date: 2010-05-09
forum: Multimedia Software
---

### Post by Johnnys5 on 2010-05-09
Hi all,

My totem crashes after several seconds of playing x264 .mkv files. Plays everything else fine (and my HD content better than .vlc so I'm not interested in switching). In terminal, the only output I get is 'Aborted'.
Any ideas (including what to post to help?).

Thanks

---

### Post by mikeljnola on 2010-05-10
I have found this problem as well upon upgrading to 10.04.  

Using NVidia proprietary drivers 195.36.15 on Linux-x86_64.  

Any ideas would be appreciated because just about all of my movies are x264 mkv.  I didn't have any problems before upgrading.

---

### Post by vaiocomputer on 2010-05-11
One possibility is that Gstreamer has, so far, less capable decoders than the more mature media frameworks.  I've had problems where Totem wouldn't play a file or crash or have errors only to find that the file would play on SMPlayer or VLC or at least one of them.

You could try installing Xine (but not the GUI) and have Totem alternatively use Xine as its backend.

---

### Post by Johnnys5 on 2010-05-11
I also just upgraded to 10.04, but wasn't sure whether that played into it.
I'll try the Xine workaround idea

---

### Post by -Jeremy- on 2010-05-13
Hello everyone,

I'm having this problem as well after installing ubuntu 10.04 (fresh install, no upgrade). I was previously still using 8.04 where totem would play .mkv perfectly.

I tried installing totem-xine, but apparently development on totem-xine has been discontinued and is no longer available in ubuntu 10.04 other than in the form of a meta-package which basically contains gstreamer. 

New suggestions/tips/solutions are very welcome because nearly all my videos are .mkv format.

kind regards,
Jeremy

---

### Post by -Jeremy- on 2010-05-16
I still have not found a solution for this problem and to prevent this thread from getting buried I'm bumping it. 

*Bump*

Is there really no-one who knows of a solution to the problem of totem aborting while playing .mkv files in ubuntu 10.04? :(

---

### Post by Johnnys5 on 2010-05-21
*bump*

Any ideas to solve this still unsolved problem?

---

### Post by Agent.Logic_ on 2010-06-16
Just adding that I too have this problem playing .mkv files in totem and VLC. Until a solution is found, I gotta fall back to Vista. :(

---

### Post by Tejus on 2010-07-10
I'm having the same problem!

It crashes Totem.

In VLC the audio stops after a few seconds but the video continues

In XBMC for Ubuntu, everything plays perfectly.

Intel integrated graphics.

Creative sound blaster card as well as integrated Intel audio.

By the way, what's *Bump*?

---

### Post by TehWan on 2010-07-11
I do have this issue too, which is pretty annoying. Nothing but "Aborted" is printed to the console. Can't seem to get any other error log.

*bump* means that you are posting to "bump" the message back on the top of the list of threads. Sadly, a lot of people  overuse it, like bumping a thread that is already on top or visible in the first page.

---

### Post by snake_865 on 2010-08-02
on my old pc i m having the same problem!it just says aborted in the terminal=( my other pc plays mkv smoothly though.i ll change the video drivers on the unlucky one and see what happens,it s worth giving a try.any news from you guys?

---

### Post by zinigor on 2010-08-12
Same thing here, here's the end of my debug log:

```
(totem:6791): Totem-DEBUG: totem_playlist_add_one_mrl (): file.mkv (null) (null)

Aborted

```

Does anyone know where to submit a bug report?

---

### Post by dcstar on 2010-08-16
> **zinigor said:**
> 
.......
Does anyone know where to submit a bug report?

```
man ubuntu-bug
```

---

### Post by Yellow Pasque on 2010-08-16
I'd suggest trying latest stable gstreamer to make sure the issue isn't already resolved upstream: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by Jetro on 2010-09-26
I've got the same problem... :( 
Ubuntu 10.04, nVidia accelerated graphics driver (version current).

---

### Post by tempo_# on 2010-10-06
Hello everyone,

I've got the same problem. any advice or solutions from anyone by now??

btw. VLC works, but has these pixelization problems... strange.. but I like totem better so I'd like to fix this somehow

Thanks!

---

### Post by captaintrav on 2010-11-22
Updating from the ppa doesn't help here.  Nor does the latest version of gst-ffmpeg.  What puzzles me is totem just quitting, perhaps it is actually a totem problem?  I've had issues with gstreamer before, but it doesn't usually crash totem.

with GST_DEBUG set, I get this:

```
0:07:13.525556235  2015  0x8c936e0 INFO                  ffmpeg :0:: Internal error, picture buffer overflow
Aborted

```

If someone else wants to confirm the same problem, do
'export GST_DEBUG=3' then run totem from a terminal window, see what you get.  I've only had this issue since 10.04 as well.  Using a player that uses mplayer as the backend plays with no issues.

---

### Post by mixmadmen on 2010-12-05
Same issue here. I've noticed that it happens at the same exact times on particular files, so I wondered if the files themselves were to blame. Seeing that this is happening to others, I'd wager it's not the case. Also, I've tried in VLC but that's no good either. I really prefer Totem, so here's hoping someone finds a fix. 
```

0:01:04.219149371  2915  0xa95b300 INFO               GST_EVENT gstevent.c:597:gst_event_new_new_segment_full: creating newsegment update 1, rate 1.000000, format GST_FORMAT_TIME, start 0:00:59.958666662, stop 99:99:99.999999999, position 0:00:59.958666662
0:01:04.219193371  2915  0xa95b300 INFO               GST_EVENT gstevent.c:597:gst_event_new_new_segment_full: creating newsegment update 1, rate 1.000000, format GST_FORMAT_TIME, start 0:00:59.958666662, stop 99:99:99.999999999, position 0:00:59.958666662
0:01:04.220815924  2915  0xa95b300 INFO               GST_EVENT gstevent.c:597:gst_event_new_new_segment_full: creating newsegment update 1, rate 1.000000, format GST_FORMAT_TIME, start 0:00:59.958666662, stop 99:99:99.999999999, position 0:00:59.958666662
0:01:04.272845796  2915  0xa970840 ERROR                 ffmpeg :0:: Internal error, picture buffer overflow
Aborted
```

It plays fine for awhile, then the whole thing just vanishes from the screen when it hits a problematic patch. I also noticed on one particular file that the audio cut out completely and didn't come back. It was a dual-audio file, and swapping tracks didn't correct the issue. Unfortunately I only run Ubuntu, so I'm not able to test these files elsewhere just yet. Trying to get a working hackintosh, so I'll give it a test on that system once it's set up to eliminate the variable that it may be damage in the files themselves.

If any other info will be of help to anyone, please post your request. Thanks!

---

### Post by martonz on 2011-01-21
Check this bug report, it might help, [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/596737](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/596737)

---

### Post by stoian on 2011-01-22
it looks like there's no solution yet.
BUT, i used gxine to play the mkv files, and it works just fine, including srt subtitles...

Edit: I just tried mplayer - that one works well, too - so plenty of options :)

---

### Post by gp73 on 2012-01-07
here is my crash report:
(totem:2474): GLib-GIO-WARNING **: Missing callback called fullpath = /media/B0FF-1537/sitcom-comedy/King of the Hill/Season 02/210 - Bobby Slam.mkv


(totem:2474): GLib-GIO-WARNING **: Missing callback called fullpath = /media/B0FF-1537/sitcom-comedy/King of the Hill/Season 12/1202 - Bobby Rae.mkv

Aborted


gstreamer updates fixed problem

---

### Post by coffeecat on 2012-01-07
Old thread. Closed.

---

