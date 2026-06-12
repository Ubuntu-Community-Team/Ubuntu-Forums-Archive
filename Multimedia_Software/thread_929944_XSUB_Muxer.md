---
title: "XSUB Muxer"
date: 2008-09-25
forum: Multimedia Software
---

### Post by l:x on 2008-09-25
Hello,

I'm wondering if anyone knows if it is possible to mux XSUBs into a Xvid file under Linux?

It's almost the only reason I still have a Winbox around :s

Cheers,
l:x

---

### Post by vipseixas on 2008-11-12
I am using AVIAddXSubs under Wine, it works perfectly.

[http://www.calcitapp.com/AVIAddXSubs.php](http://www.calcitapp.com/AVIAddXSubs.php)

Just download, unzip and run "wine AVIAddXSubs.exe".

---

### Post by lenooh on 2008-11-23
> **vipseixas said:**
> I am using AVIAddXSubs under Wine, it works perfectly.

[http://www.calcitapp.com/AVIAddXSubs.php](http://www.calcitapp.com/AVIAddXSubs.php)

Just download, unzip and run "wine AVIAddXSubs.exe".

Great! I can finally add subtitles to my xvid files and play them on my ps3!

:-)

---

### Post by vipseixas on 2008-11-29
Hi.

I am using AVIAddXSubs under wine too, but sometimes when I mux the avi under linux it generates a faulty divx file. For instance, today I muxed the last Heroes episode and when I played it the image became scrambled when any subtitled appeared on screen (turning off the subtitles restores immediately the image). I did the same process on windows and the file played perfectly. It is not the first time it occurred...

Anyone with similar problems? I am using wine 1.1.9 and AVIAddXSubs 8.2.

I am wondering too if there is an easy way to mux XSubs natively under linux... Googled for some tool and found nothing.

---

### Post by girishven on 2008-12-13
> **vipseixas said:**
> Hi.

I am using AVIAddXSubs under wine too, but sometimes when I mux the avi under linux it generates a faulty divx file. For instance, today I muxed the last Heroes episode and when I played it the image became scrambled when any subtitled appeared on screen (turning off the subtitles restores immediately the image). I did the same process on windows and the file played perfectly. It is not the first time it occurred...

Anyone with similar problems? I am using wine 1.1.9 and AVIAddXSubs 8.2.

I am wondering too if there is an easy way to mux XSubs natively under linux... Googled for some tool and found nothing.

Facing a diff kind of issue where the subtitles are scrambled when they are added using AVIAddXSubs under Wine. The subtitles are unreadable but the movie is OK. This happens almost all the time.  I use Wine 1.1.10. Have seen this in all versions prior to Wine 1.1.0 as well. No problems when used under Windows though.

Has anyone faced this / found a solution for this yet ?

---

### Post by ruelke on 2009-01-10
> **girishven said:**
> Facing a diff kind of issue where the subtitles are scrambled when they are added using AVIAddXSubs under Wine. The subtitles are unreadable but the movie is OK. This happens almost all the time.  I use Wine 1.1.10. Have seen this in all versions prior to Wine 1.1.0 as well. No problems when used under Windows though.

Has anyone faced this / found a solution for this yet ?

Mine solution to this problem is this:

In Configuration 1 turn off the "Break Long Lines" option
Check the font. I'm not sure what exactly is the problem but I found that I don't get scramble text with font "Liberation Sans"

This works for me. I hope it will work for you too :)

---

### Post by jlezama on 2009-02-21
Just to say that unchecking "break long lines" and using Liberation Sans as font worked for me too

[EDITED]

I'm sorry to inform that I am getting scrambled subtitles again, the solution worked for one movie but does not seems to work always.

---

### Post by joserpena on 2009-04-26
How to play XSUB subtitles in Ubuntu? Which player? Codecs?

Thanks.

---

### Post by inet.dysk on 2010-01-03
> **joserpena said:**
> How to play XSUB subtitles in Ubuntu? Which player? Codecs?

Thanks.
I have FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2xbmc1, from XBMC repository.
and playing avi with XSUB subtitles (0-first,1-second,etc.):

ffplay -sst 0 somemovie.avi

But when rewind subtitles disappears, and ffplay is very simple player.

---

### Post by Natty Dreed on 2010-02-07
> **inet.dysk said:**
> I have FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2xbmc1, from XBMC repository.
and playing avi with XSUB subtitles (0-first,1-second,etc.):

ffplay -sst 0 somemovie.avi

But when rewind subtitles disappears, and ffplay is very simple player.

it's worked for me

but i'm using arabic subtitle and it's not shown correctly

any way in winxp i didn't manage to play it any ;)

LINUX :) is better

---

