---
title: "amarok 24bit 96khz flac problems"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by monkman on 2007-12-02
ubuntu 7.10
maudio revolution 5.1
c2d e6400
2gb ram

hi.

in my collection i got some 24bit 96khz flac musicfiles, which amarok doesn't play clean(alot of interruptions). rhythmbox does but it doesn't play musepack files, so i'm forced to use amarok. is there anything i can do about it? i think the problem is xine. are there any other amatok engines? i don't see any in synaptic.

thanks!

---

### Post by samwisgg on 2007-12-06
Monkman,

exact same problem here. Have a test 24bit 96 kHz file that plays like a charm under rhythmbox (using gStreamer) but sounds awful under Amarok (choppy sound). I found the location where xine holds it parameters : ~/.kde/share/apps/amarok/xine-config. Messed around with some of them but no result :(. For flac files I have another issue : I can't fast forward them while for mp3's there is no problem.

Your remark about using another sound server then xine (such as gStreamer) is very understandable but after some research I found out that the current version of Amarok (1.4.7) ony supports xine : a package amarok-gstreamer does not exist for Ubuntu ....

Can somebody out there help us out ?

---

### Post by razorwire on 2008-02-07
24-bit FLAC files encoded with 1.2.x take advantage of some obscure feature that it didn't use before.  Nice for the size, but it breaks compatibility.  If I remember right, GStreamer depends on and uses the official libraries, so it will play standard FLACs perfectly.  I don't know how xine decodes FLACs, but if it is anything like most other programs out there, it probably uses its own decoding method.  Anyway, GStreamer development for Amarok has pretty much been left behind: the only engine for Amarok 1.4.8 is the xine engine, and older engines depend on an older version of Amarok.  We're pretty much stuck with broken 24-bit FLAC playback, unless the Amarok developers stop doing things like everyone else and depend on the real libraries.

Oh, also, the format of MP3 has been frozen a while back.  That's why it's easier to support and that's also why broken playback is so uncommon, whereas FLAC is continually being developed and changed.

---

### Post by zeltak on 2008-03-16
Hi

Ive just encoded my whole library (400 Cd's...) with sound juicer and i have exactly the same problems (chopy playback no seek...). Has anyone made any progress on finding whats causing this in Amarok?

thx

Zeltak

---

### Post by zeltak on 2008-03-28
any solution?

its getting to get quite annoying.....90% of my songs are flac...

zeltak

---

### Post by zeltak on 2008-03-29
Hi again

just found out it has to be a xine issue. the same flac stutter happens in xine player and kaffeine (both use the xine engine)...

hope it helps us towards a solution

Zeltak

---

### Post by AJLobo on 2008-03-31
I downloaded some FLAC 24/192 files, but they don't play at all in Amarok. They also don't play in VLC. I rebooted into windows to make sure, and they do play fine in Winamp. The rest of my FLAC files also play perfectly in Amarok, it's just these hifi FLACs :-/

---

### Post by misterspider on 2008-06-27
> **samwisgg said:**
> Monkman,

For flac files I have another issue : I can't fast forward them while for mp3's there is no problem.



I've got this problem too and its really annoying. Anything that uses xine as an engine has this problem for me.

Also, is there an easy way to find out if a music file is 24 or 16 bit?

---

### Post by kioftes on 2008-07-16
Hi all! Is there anything new on the subject? Same problem here...has anybody filed a bug already??

---

