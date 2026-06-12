---
title: "Problems w/ multimedia on Israeli sites"
date: 2008-06-06
forum: Multimedia Software
---

### Post by lodp on 2008-06-06
OK, re-posting because the original title was considered offensive (which of course it was, but what is this -- a funeral?)

Moving on..

I've got disproportionatly more problems viewing multimedia stuff on Israeli sites than elsewhere. It seems the holy land is firmly in M$'s hand, everywhere it says "install Media Player Plugin".

For example, try viewing videos on [http://www.haaretz.com](http://www.haaretz.com), [http://www.ynet.co.il](http://www.ynet.co.il), or this one here: [http://www.keshet-tv.com/nehederet/](http://www.keshet-tv.com/nehederet/)

I use Firefox with the Media Player connectivity plugin, which usually works quite well for opening all kinds of media in kmplayer. But on the haaretz site, as well as on the ynet one, mplayer gets stuck in a choppy pre-content commercial loop, and the third example above doesn't play at all..


any pointers?

> Allow this goy to help you out. First do this:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Afterwards, this:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

Now you'll probably have more mazzel and your computer won't make you nebbish any more.

Shalom,
Pjotr.

Thank you, but nah, no mazel with that one

i've been around for a while, and i've had w32codecs, sun-java, and most of the other things you name there installed since the beginnings. and as i said -- i'm really not having problems playing wmv, rm, and other proprietary formats in general. It's just those few sites.

Since I'm using the media player connectivity plugin in FF, I can't try the mozilla-mplayer one. But I doubt the plugin would do better than the standalone mplayer (which media player connectivity launches to play the stream). I've also tried letting the plugin launch VLC, but to no avail.

Can you view videos properly on the sites I've named above? Haaretz.com is English, so there's no need for knowledge of the funny letters..

---

### Post by nucleuskore on 2008-06-06
I tried a video in Haretz.com and faced the same problem. I think they are using wmv8 or something new. In any case I do not understand why in cli mode I get an http error

VLC media player 0.8.6f Janus
[00000297] access_http access error: error: HTTP/1.1 500 Internal Server Error
[00000297] access_http access error: error: HTTP/1.1 500 Internal Server Error
[00000297] access_mms access error: error: HTTP/1.1 500 Internal Server Error

ditto with kaffeine.

---

### Post by lodp on 2008-06-07
I managed to extract the stream URI from one of the haaretz.com videos, and it seems it's WMV9. I don't think wmv9 is a problem per se, but the video gets stuck after playing the commercial that precedes the actual content.

---

