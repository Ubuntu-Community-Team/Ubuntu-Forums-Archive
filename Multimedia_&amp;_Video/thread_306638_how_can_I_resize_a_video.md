---
title: "how can I resize a video"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by LucasLinard on 2006-11-25
Hi folks,
Can't find the answer at the forum. I need to resize a 4:3 movie.avi to 16:9 movie2.avi
Can anyone help me?

---

### Post by cilynx on 2006-11-25
My best bet would be to look into "mencoder" and "transcode".  They're the big guns in movie file processing.

---

### Post by LucasLinard on 2006-11-25
> **cilynx said:**
> My best bet would be to look into "mencoder" and "transcode".  They're the big guns in movie file processing.

I thought so, BUT how can I do this? I have no idea on how to use mencoder or transcoder. What are the differences between them?

---

### Post by cilynx on 2006-11-25
Here's the appropriate section in the mencoder docs:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html#menc-feat-vcd-dvd-output-aspect](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html#menc-feat-vcd-dvd-output-aspect)

mencoder is attainable within a rerasonable amount of time.  transcode requires a lot more wizardry.

---

### Post by LucasLinard on 2006-11-25
> **cilynx said:**
> Here's the appropriate section in the mencoder docs:

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html#menc-feat-vcd-dvd-output-aspect](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html#menc-feat-vcd-dvd-output-aspect)

mencoder is attainable within a rerasonable amount of time.  transcode requires a lot more wizardry.

Thanks a lot!
I really searched the net, got a txt documentation for mplayer and mencoder but could'nt understand it very well. the link you posted is really self-explicative!

---

### Post by LucasLinard on 2006-11-25
just another question how can I convert multiple files? like movie1.avi, movie2.avi and movie3.avi to movie1conv.avi, movie2conv.avi and movie3conv.avi??

---

### Post by cilynx on 2007-07-29
8 months later...

```

for x in 1 2 3 ; do encoderCommand movie$x.avi movie$x\conv.avi ; done

```

Hopefully you figured that out a while ago =)

---

### Post by LucasLinard on 2007-07-30
Thanks a lot dude!
I already know how to use mencoder but thanks for your help! :)

> **cilynx said:**
> 8 months later...

```

for x in 1 2 3 ; do encoderCommand movie$x.avi movie$x\conv.avi ; done

```

Hopefully you figured that out a while ago =)

---

