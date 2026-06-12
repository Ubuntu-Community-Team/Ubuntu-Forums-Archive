---
title: "[SOLVED] configuring midi - again!"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by tonymoloney on 2008-03-26
I've just managed to nuke my Kubuntu setup that has been running happily for 12 months, so now I've installed Ubuntu Gutsy and I'm having trouble getting midi to work. It took me ages in Kubuntu and I've obviously missed something somewhere.

So far I've followed [URL="http://http://www.funnestra.org/ubuntu/gutsy/#timidity"] but when I get to the line that says 

timidity -iA -B2,8 -Os1l -s 44100

I get this output

Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 7524, period size 3760 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 129:0 129:1 129:2 129:3

The cursor the drops down to the next line and nothing else happens - no prompt - no timeout -it just sits there and of course midi still doesn't work.

Any help?

Edit. Just found my problem. I hadf to set preferences in Kmid when it started.

---

