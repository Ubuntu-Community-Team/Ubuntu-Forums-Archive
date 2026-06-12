---
title: "watch AND record tv at the same time?"
date: 2010-03-02
forum: Multimedia Software
---

### Post by horde on 2010-03-02
At the moment I have a script that uses mencoder to record a video stream from /dev/video0.  But when I try to watch /dev/video0 (using vlc or mplayer, for instance) while that script is running it says that /dev/video0 is in use by another program (obviously mencoder).

I was wondering if there was a way to both record and watch /dev/video0 at the same time.  Ideally I'd like not to have to stop using my script for recording.

Many thanks in advance.

---

### Post by Kubunteando on 2010-03-02
Have you tried kaffeine?

It is a good video player for KDE.
It allows you to schedule recordings, timeshifting...
And allows you to record the same show you are viewing or a different one if you have 2 tunners (or the second show is in the same band as the channel you are wathcing).
Pretty handy.

---

### Post by horde on 2010-03-02
Thanks for the reply.  Yes, I do use kaffeine on occasion but find that it's not nearly as configurable as mplayer/mencoder.  As such not being able to use mencoder would be a deal-breaker for me.

---

### Post by Kubunteando on 2010-03-03
I found this link:

[http://free-electrons.com/doc/embedded_linux_multimedia.odp](http://free-electrons.com/doc/embedded_linux_multimedia.odp)

Check the video part. Checks the slides 49 and 53.

So it seems that the driver should allow the concurrent access.
So you may need to check the driver your TV card is using and see if that driver supports concurrent open operations.

---

### Post by horde on 2010-03-04
Many thanks for the link...very elicidating.

I'm using the bttv driver with a Bt787 analogue video capture card to backup old VHS and Betamax (HA, that's dating myself!) tapes.  Some have degraded to the point of being unusable, hence my wanting to watch them while encoding them.  It doesn't look like the bttv driver allows for concurrent access.  I might have to get a card/driver that does for this to work.

Thanks for the help, and if anyone has any further ideas I'd love to hear them.

---

### Post by Kubunteando on 2010-03-04
It depends on what your script does.
But if you want to compress your VHS and see them at the same time usually the pipes and the command "tee" will help to split to sevaral outputs (usually a file and the standard output)

---

