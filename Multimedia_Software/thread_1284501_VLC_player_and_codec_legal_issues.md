---
title: "VLC player and codec legal issues"
date: 2009-10-06
forum: Multimedia Software
---

### Post by billdotson on 2009-10-06
So, I am assuming it is not possible to distribute, say Ubuntu, with VLC included right? If I got a computer (or built one) and sold it to someone would it have to be completely free of anything proprietary? Would it be possible to pay the licensing fees for the codecs in VLC player and then include it (or give them one click access to install it)?

If I were to do this on a relatively small scale how would I go about doing this? What codecs would I have to pay licensing fees for so that the users could use VLC legally? Would paying those licensing fees give them the full ability to use the paid-for codecs in any other program that needs them or would licensing fees need to be paid for each program that includes its own codecs? What about programs that use the gstreamer framework?

Does anyone know what codecs would require royalties to be paid? I am assuming I would need to fix encrypted dvd, mpeg 1+2, mpeg4, mp3, divx and windows media player. Are there any others that anyone can think of that I would have to cover? I heard that for  encrypted dvd and mpeg4 it is a one time fee of $2.50.

Thanks.

---

### Post by HappyFeet on 2009-10-06
Codecs are a grey area at best. If you were to pay for them, you would be one of the few people in this world that do.

If you've ever bought a pc with windows on it, you have already paid for some. I would not worry about it. If they were to crack down on it, (which they won't) they would have to go after 500 million people. I personally, would not worry about it, as it is not something they enforce.

---

### Post by HappyFeet on 2009-10-06
But if you feel you *must* pay for them, see [this]("http://shop.canonical.com/index.php?cPath=19"). Plus, ubuntu will make a little money too.

---

### Post by billdotson on 2009-10-09
I already know about the canonical store but I was wondering if there was a cheaper way. Isn't there some way to pay them directly and not have the software price bundled with stuff?

This question is assuming I am building a PC for someone and want to have it working for them when they get it.

---

### Post by mc4man on 2009-10-09
I'm actually kinda curious as to who do you think you're going to pay and for what licenses?

Taking as one example, commercial dvd playback. By itself vlc doesn't decrypt dvd's, it uses libdvdcss2. There's  no license to be had or paid for there.

If you're not going to include the couple (or 1)  licensed media player and or codec providers and have concerns about installing unlicensed and probably un-licensable codecs then just make and include a shell script or 2 that takes care of it.
Ubuntu does that for libdvdcss2, there's a shell script in libdvdread that will install it when run

---

### Post by billdotson on 2009-10-09
As I understand it you are supposed to be able to contact the MPAA and pay a one time $2.50 fee for mpeg4 and encrypted DVD playback. In practice it may be one of the most difficult things in the world to do...

---

