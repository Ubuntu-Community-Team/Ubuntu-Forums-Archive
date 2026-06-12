---
title: "sound only on .rm to .avi conversion with mencoder"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by Rafael, Jr. on 2007-05-29
On Feisty 7.04 with MPlayer installed through synaptic and codecs from the medibuntu repos, I successfully saved an .rm file using the -dumpstream option on MPlayer.  I wanted to convert the file to an avi format and then to a mpg.  Could not find a way to do it.  Only audio is converted over to the new avi container:

[COLOR="Red"]Video stream:    0.000 kbit/s  (0 B/s)  size: 0 bytes  224.200 secs  2244 frames

Audio stream:  127.327 kbit/s  (15915 B/s)  size: 3576492 bytes  224.712 secs[/COLOR]

the command I am using to convert rm to avi is:

[COLOR="Red"]mencoder file.rm -ovc lavc -oac mp3lame -o file.avi[/COLOR]

Other combinations seem to do the same thing.  Any advice?

---

### Post by Judo on 2007-05-29
You didn't specify any parameters for lavc.  You would do that with -lavcopts vcodec=whatever.  The documentation is [here]("http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html").

Why are you doing two conversions?  If you convert to AVI then MPG you will lose more quality than you need to.  I'm also a little confused on what you did with dumpstream.

---

### Post by Rafael, Jr. on 2007-05-30
Thank you for your response.
I used dumpstream to save the rm file from rtsp to my harddrive.  I'll mess around with the lavc options and post my results.  As far as the avi to mpg operation, I don't mind losing quality in the conversion because I'm doing it just to learn how.
Thanks again.

---

### Post by Rafael, Jr. on 2007-05-30
no luck, here's some output:

```
1 duplicate frame(s)!
Writing header...
ODML: vprp aspect is 4:3.
[rv20 @ 0x887fcb8]concealing 300 DC, 300 AC, 300 MV errors:0.062 [0:127]
[rv20 @ 0x887fcb8]I cbpc damaged at 0 0
[rv20 @ 0x887fcb8]ERROR at MB 0 0

2 duplicate frame(s)!
Writing header...
ODML: vprp aspect is 4:3.
Writing header...
ODML: vprp aspect is 4:3.
Pos: 224.2s   2244f (99%) 89.69fps Trem:   0min   3mb  A-V:0.066 [0:127]
Flushing video frames
Writing index...
Writing header...
ODML: vprp aspect is 4:3.

Video stream:    0.000 kbit/s  (0 B/s)  size: 0 bytes  224.200 secs  2244 frames

Audio stream:  127.327 kbit/s  (15915 B/s)  size: 3576492 bytes  224.712 secs
```

The command I used was

```
mencoder file.rm -o file.avi -ovc lavc -lavcopts vcodec=ffv1:aspect=4/3 -oac mp3lame
```

I tried different -libavcopts but returned the same result.

---

### Post by Rafael, Jr. on 2007-05-30
I replied to myself in the thread.  Sorry.  Could you please look at it?

---

### Post by Rafael, Jr. on 2007-05-30
Here's a screenshot of the rm file's properties

---

