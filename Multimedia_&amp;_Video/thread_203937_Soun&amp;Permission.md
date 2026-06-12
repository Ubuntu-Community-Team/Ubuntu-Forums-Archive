---
title: "Soun&amp;Permission?"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by kalmi on 2006-06-26
My sound card stopped working(maybe after the last kernel update).
I figured out that root(I'm using ubuntu so I mean "sudo vlc") can use it. So it must be a permission problem.
Using "sudo chmod a+rw /dev/dsp /dev/mixer" I can get my card and my mixer to work. But after a restart it stops again. And I have to run this command again. Any idea?

Also I'm using this module:snd-intel8x0

---

### Post by res_overlord on 2006-06-26
I know this doesn't help, but I have the same exact problem.  I'm going to try to add the CHMOD command to a startup script somewhere. A coworker also suggested taking a look at stickybits, whatever those are.

---

### Post by res_overlord on 2006-06-26
Try adding yourself to the audio group:

sudo usermod -G audio [your_user_name]

This worked for me.

---

