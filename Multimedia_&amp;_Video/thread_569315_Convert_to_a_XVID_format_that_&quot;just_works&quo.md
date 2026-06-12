---
title: "Convert to a XVID format that &quot;just works&quot;"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by amitroy5 on 2007-10-06
Hello. I love my XVID movies. However, I use media players such as the Dlink DSM-520, which has problems because of the various codecs that XVID has. How can I convert all my XVID files into one uniform one which "just works," meaning that they all use the same video and audio codecs?

I noticed that Mpeg-1 Audio Layer 3 works very well. Is there any program that I can do this in batch?

---

### Post by MrFSL on 2007-10-06
You can script this out using ffmpeg or mencoder

---

### Post by amitroy5 on 2007-10-07
Is there any way to convert to DivX? I know its not an open format, but it seems to work on all media players.

---

### Post by MrFSL on 2007-10-07
Roughly Divx is just mpeg4 video and mp3 audio wrapped up in an avi container. The exact specifications in encoding bitrates and proportions are what define this as "Divx."

You can do this with both ffmpeg and mencoder.

Be warned - many devices claim to play divx but I have had mixed results. Even using DiVX proprietary encoder off the DiVX website I could not get it to play in certain players.

In short - yes Divx is a standard - but it is a loose standard and often not the same between devices in terms of compatibility.

---

### Post by amitroy5 on 2007-10-07
I never realized how difficult it is to encode. I thought all you had to do was drag in a file and click "Encode" and it will convert the file for you. At least I thought it should have been that easy to convert between formats.

---

### Post by JBAlaska on 2007-10-08
The Xvid codec is not the problem, It's the optional features such as GMC and Q-Pel and possibly packed bitstream that choke a standalone player.

There is a windoze program (mpeg4modifier) that will un-pack the  bitstream without re-encoding. As for the GMC (general motion compensation) and Q-Pel (quarter pixel) options, you WILL have to re-encode to remove those.

Unfortunately, The only thing I still use a windoze box for is encoding so I can't help in recommending a Linux GUI frontend for ffmpeg or mencoder.

---

### Post by amitroy5 on 2007-10-08
What program do you use for conversion?

---

### Post by JBAlaska on 2007-10-08
I use VirtualDubMod, I'm not sure if it runs under wine but I guess it's high time I found out.

If you want to convert your XviD's with VirtualDubMod (freeware), You can use a nice GUI frontend called AutoGK that makes it a painless point and click operation. Here's a good guide:
```
http://forum.videohelp.com/topic273901.html
```

---

