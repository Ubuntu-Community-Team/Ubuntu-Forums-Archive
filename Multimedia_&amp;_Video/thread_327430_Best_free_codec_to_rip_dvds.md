---
title: "Best free codec to rip dvds?"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by viciouslime on 2006-12-29
I have a good number of DVDs I want to rip to my computer so I won't have to take the disks with me when I go to uni, I want to rip them using a free codec but I have a few issues.

Firstly, is xvid free, or not? There seems to be some controversy surrounding this, but I don't understand it. If it isn't completely free, does that mean ogg theora is the only totally free solution?

I am happy to use ogg theora, however, for some of the DVDs I want to rip two audio tracks and the subtitles. I know ogg theora supports this, but I can't find any ripping software that will do it...

I did find a very hackish way of getting the two audio tracks as can be seen in this thread: [http://ubuntuforums.org/showthread.php?t=318698]("http://ubuntuforums.org/showthread.php?t=318698")

However, I don't know how to do the subtitles...

So, has anyone got any recommendations as to how they would rip a dvd into a free format but keeping multiple audio tracks AND subtitles...?

Thanks in advance!!! :D

---

### Post by s6dalane on 2006-12-29
I have not tried it myself, but [this]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs") page recommends a program called **Thoggen**.

---

### Post by viciouslime on 2006-12-29
Thoggen is good, but, it doesn't support ripping subtitles, nor multiple audio tracks. While the post I link to shows how it is possible to do multiple audio tracks it still doesn't help with subtitles. Thanks anyway!

---

### Post by spnoe on 2006-12-29
Try DVD Rip. You will need to search for the URL.

---

### Post by viciouslime on 2006-12-29
I am playing with that now, it seems to do what I want, however, it seems that xvid isn't the way to go for me and dvdrip doesn't handle theora :(

---

### Post by viciouslime on 2006-12-29
I'm still not getting this xvid thing, some sites say it all totally open source and free in the same way that theora is, but others warn of it still being patent encumbered, but I don't understand why. One site claimed that Xvid is always illegal except for research purposes :confused: 

Can anyone clear this up for me?

---

### Post by pseudonym on 2006-12-29
I can't help you with xvid but I can recommend another ripping tool - [Acidrip]("http://untrepid.com/acidrip/") . It uses a different encoding backend to dvdrip and is a tad easier to use IMHO. It's in the Ubuntu repositories, too, btw.

---

### Post by drr422 on 2006-12-29
I would recommend [OGMrip]("http://ogmrip.sourceforge.net/index.html") its pretty simple and you can rip subtitles.  you have a variety of codecs to choose from, and it works. Everytime.

---

### Post by viciouslime on 2006-12-30
> **drr422 said:**
> I would recommend [OGMrip]("http://ogmrip.sourceforge.net/index.html") its pretty simple and you can rip subtitles.  you have a variety of codecs to choose from, and it works. Everytime.

Oh yeah! I was in the middle of trying that when I got sidetracked and I forgot about it totally. I will finish off installing it and let you know how it goes, looks great!

---

### Post by PriceChild on 2006-12-30
I may be wrong... but XviD flip reversed spells DivX ;)

afaik xvid is the free reversed engineered open version.... but haven't a clue...

---

### Post by viciouslime on 2006-12-30
> **PriceChild said:**
> I may be wrong... but XviD flip reversed spells DivX ;)

afaik xvid is the free reversed engineered open version.... but haven't a clue...

I believe it is too, but there seems to be something about it producing mpeg streams and therefore infringing patents?

OGMRip is running now, but it can't create ogg files much to my disappointment. I am trying matroska though, but that's not really what i wanted since ubuntu can't play matroska files without extra things being installed (i think).

---

### Post by tagra123 on 2006-12-30
> **viciouslime said:**
> I have a good number of DVDs I want to rip to my computer so I won't have to take the disks with me when I go to uni, I want to rip them using a free codec but I have a few issues.

Firstly, is xvid free, or not? There seems to be some controversy surrounding this, but I don't understand it. If it isn't completely free, does that mean ogg theora is the only totally free solution?

I am happy to use ogg theora, however, for some of the DVDs I want to rip two audio tracks and the subtitles. I know ogg theora supports this, but I can't find any ripping software that will do it...

I did find a very hackish way of getting the two audio tracks as can be seen in this thread: [http://ubuntuforums.org/showthread.php?t=318698]("http://ubuntuforums.org/showthread.php?t=318698")

However, I don't know how to do the subtitles...

So, has anyone got any recommendations as to how they would rip a dvd into a free format but keeping multiple audio tracks AND subtitles...?

Thanks in advance!!! :D


Why not make backup copies?

This how to help make backup copies of even the most difficult disks. I do this to keep the 3 year old from breaking the originals.

[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)


Another good page is here if you want to use the copy route.,

[http://gentoo-wiki.com/HOWTO_Backup_a_DVD](http://gentoo-wiki.com/HOWTO_Backup_a_DVD)

[http://www.debiantutorials.org/content/view/10/135/](http://www.debiantutorials.org/content/view/10/135/)

---

### Post by viciouslime on 2006-12-30
Well the whole idea is so that I don't have to take the discs with me. Lol that wasn't code for "I want to copy all my friends' DVDs" I really do just want to rip my own legal DVDs. Thanks anyway.

---

### Post by crispy_420 on 2006-12-30
> **PriceChild said:**
> I may be wrong... but XviD flip reversed spells DivX ;)

afaik xvid is the free reversed engineered open version.... but haven't a clue...

I may be wrong but it is not a reversed engineered of DivX. Sometime around DivX 4, the license was changed from open source to closed. Xvid is just the continuation of the original project before the project went closed source. I thinkl that is correct because I use to use it in the days of file sharing as a great compressor.If you worry about Xvid's license, just look it up.

According [Xvid.org]("http://www.xvid.org/"):

> Xvid is an open-source research project focusing on video compression and is a collaborative development effort. All code is released under the terms of the GNU GPL license.

The Xvid video codec implements MPEG-4 Simple Profile and Advanced Simple Profile standards. It permits compressing and decompressing digital video in order to reduce the required bandwidth of video data for transmission over computer networks or efficient storage on CDs or DVDs. Due to its unrivalled quality Xvid has gained great popularity and is used in many other GPLed applications, like e.g. Transcode, MEncoder, MPlayer, Xine and many more.

---

### Post by tagra123 on 2006-12-30
> **viciouslime said:**
> Well the whole idea is so that I don't have to take the discs with me. Lol that wasn't code for "I want to copy all my friends' DVDs" I really do just want to rip my own legal DVDs. Thanks anyway.

Would vob copy do the trick? -- See my earlier post.

---

### Post by viciouslime on 2006-12-31
I suppose it would but there are a lot of dvds, so some compression would be nice. As for the quote about the xvid licence, thanks, but that doesn't really help. I am aware that xvid is open source and released under the GPL, however, I am also aware that for some reason it isn't considered free, i think, from what i have read, that it infringes on certain mpeg patents? This is what I am trying to understand now...

---

### Post by pseudonym on 2006-12-31
Like all of this stuff, it depends on the country you live in. wikipedia mentions the US and Japan as candidates. But I seriously doubt that, as a simple user, there's much chance of being sued, even if you live in either of those 2 countries.

---

### Post by viciouslime on 2006-12-31
> **pseudonym said:**
> Like all of this stuff, it depends on the country you live in. wikipedia mentions the US and Japan as candidates. But I seriously doubt that, as a simple user, there's much chance of being sued, even if you live in either of those 2 countries.

So is it ONLY infringement of software patents? Because as far as I am aware, they're not valid here in the EU.

---

### Post by pseudonym on 2006-12-31
> **viciouslime said:**
> So is it ONLY infringement of software patents? Because as far as I am aware, they're not valid here in the EU.
Well, tbh, I don't know if the issue goes beyond software patents. But it's really not worth the time, effort, or anxiety trying to satisfy yourself one way or the other, if all you're concerned about is your use of the software. Because, as a simple private user, the point is that a) nobody is going to know, much less care, that you're using said software; and b) nobody is ever going to be bothered taking you to court over it, even if software patents were enforceable in the EU.

For such a situation to become even remotely likely, I think you would have to do something like print up a t-shirt and a placard with 'I use xvid, and I don't care!' emblazoned all over them, then go down to the offices of DivX's lawyers and make your presence felt in the most obtrusive way you can. And even then, the only thing you're likely to be charged with is some kind of public nuisance offence.

I don't mean to sound flippant about it but, seriously, I don't think you've got anything to worry about. Hell, if any of us did, we should all stop using Linux right now. Because, even as Torvalds himself admits (don't ask me for a link), the linux kernel probably violates dozens of patents.

Perhaps the situation might be different if you are some major media distributor, selling boatloads of content encoded with xvid. Then the expense and hassle of a lengthy court case might be worth it for DivX. If indeed this is who you've been all along, then I sincerely apologise for leading you astray. :)

---

### Post by viciouslime on 2006-12-31
Thanks for your reply. I'm not bothered about "being caught" using it, I know that nothing would come of that, it's just knowing that it's not TOTALLY free... ubuntu has instilled a strange desire in me to have everything as free as possible...

---

### Post by pseudonym on 2006-12-31
Oh well, in that case, consider my face well and truly slapped for insulting your intelligence :) It's late, I'm drunk, and in less than 2 hours' time it will be 2007! yippeee! :D

---

### Post by viciouslime on 2006-12-31
> **pseudonym said:**
> Oh well, in that case, consider my face well and truly slapped for insulting your intelligence :) It's late, I'm drunk, and in less than 2 hours' time it will be 2007! yippeee! :D

:p You must be way ahead of me, it's only 11am here in England.

---

### Post by pseudonym on 2006-12-31
> **viciouslime said:**
> :p You must be way ahead of me, it's only 11am here in England.
I'm in the same time zone as Magadan (it's either that or Vladivostok, i can never remember which) :D

---

### Post by tagra123 on 2006-12-31
Heres a link suggesting acidrip or dvd:rip

[http://www.linuxforums.org/forum/linux-applications/38032-program-rip-dvds.html](http://www.linuxforums.org/forum/linux-applications/38032-program-rip-dvds.html)

Also on that link is a command line using mencoder to rip directly.

```
mencoder  dvd://1  -vf  scale=640:480 -o title1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4 alang=en
```

also from that page:

the dvd://1 to the real movie title (it normaly is 1 but somtimes that can be the copyright notice and the real movie may be 2 or 3

For two pass encoding:
Firstpass
```
mencoder dvd://2 -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -oac copy -o /dev/null
```
SecondPass

```
mencoder dvd://2 -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:vpass=2 -oac copy -o output.avi
```

You can also select the language using slang option

If you do it according to this method it looks like you will end up with a few avi's.

You can easily join them together using this command


```
avimerge -o foo.avi -i foo1.avi foo2.avi
```

mencoder can also join
```

cat 1.avi 2.avi | mencoder -noidx -ovc copy -oac copy -o output.avi -
```

an eassier way using mencoder is
```

mencoder -oac copy -ovc copy -idx -o whole.avi part1.avi part2.avi
```

I believe I've also used ffmpeg to do this to.

Here is a link on file format and codecs.

[http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/formats.html](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/formats.html)

---

### Post by tagra123 on 2006-12-31
Forgot to mention --  vlc is also capable of converting formats.

uses vlc's file - wizard menu.  Very easy.

I normally use mencoder, ffmpeg, or tovid for actual video processing (previous post)

---

### Post by handy on 2007-01-01
DVDshrink compresses by 50% or better.  I expect that you need better than that... incredibly reliable & easy to use though :)

---

