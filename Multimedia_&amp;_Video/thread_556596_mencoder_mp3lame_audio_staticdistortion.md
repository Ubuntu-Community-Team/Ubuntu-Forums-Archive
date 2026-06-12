---
title: "mencoder mp3lame audio static/distortion"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by ca1vin on 2007-09-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/141314](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/141314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This one's a bit strange.  Using fully updated Feisty.

I've been using mencoder to shrink mp2 video I record from my Hauppage tv tuner card.  Video is transcoded into xvid, audio to mp3.

Recently the audio broke.  The source mp2 is fine, but the mp3 audio in the transcoded video is massively overmodulated and distorted.  

I just ran a bunch of tests.  This would be a typical encoding command:

mencoder -oac mp3lame -lameopts cbr:br=128 -ovc lavc -lavcopts codec=mpeg4:vbitrate=300:vhq:autoaspect -ffourcc DX50 -o test.avi test.mpg

Here's what I've eliminated

with -oac copy, audio is fine (224kbs mp2). 
with -oac pcm the problem is present as well, so the problem may be in decoding the input stream, or somewhere before the encoder.
I tried with various lameopts (and with none for the default).  No joy.
I tried calling mp3lame through lavc.  No joy.
I tried reinstalling liblame0 (apt-get install --reinstall liblame0)  No joy.



Could be the same bug as reported here:
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/141314](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/141314)

Any hints for a fix?

Thanks

Jim

---

### Post by we_r_disturbed on 2007-09-24
Look at this bug post:
[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751)

I did as they suggested by downloading and replacing mplayer and mencoder from the DeVeDe website and it worked for me.

---

