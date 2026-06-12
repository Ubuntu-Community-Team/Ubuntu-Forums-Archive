---
title: "VLC segmentation fault"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by anemon on 2006-12-28
Hi there!

Just ripped my first DVD with dvd::rip, and it worked like a breeze. The file (in .avi format, encoded to xvid4) plays just fine in Totem, but the subtitles are in a separate .sub file, and I can't seem to make Totem play it. Solution: fire up the ol' favorite media player, VLC.

The problem is that VLC won't accept the .avi file! The program opens briefly, and then crashes without warning. Running it from terminal just gives me:

```
VLC media player 0.8.6 Janus
Segmentation fault (core dumped)

```

... and nothing more. Is there something wrong with the rip -- and, in that case, why would it work in Totem? I've never had any problems with VLC before, so I'm a bit confounded. What to do? I've seen other threads reporting similar problems, but none with a good solution.

Best / A.

---

### Post by anemon on 2006-12-28
PS. Tried with another .avi file, just to make sure (not xvid4, though), and that one is still working just fine...

---

### Post by paziek on 2006-12-28
DivX4 (theres no XviD4 codec so far) is and obsolete codec. Perhaps its not supported in VLC anymore.
I would suggest using older version of VLC or MPlayer (I know, that new one dropped DivX4 support).
Or you could compile ffdshow with DivX4 support and then try to play with.. totem for example.. I guess.



Or.. convert that file to different codec.

---

### Post by anemon on 2006-12-28
Aha. That would explain it! The howto I read must have been a bit passé. :???: So, what codec is the one to use? (I could easily just rip the film again with a different one.)

Oh, and -- thanks for the ever so rapid answer! Never seizes to amaze me, really...

---

### Post by paziek on 2006-12-28
Well, it seems, like you wont be watching it on DVD player, so XviD1.1 or XviD1.2 should be just fine.
But if you want to see it on DVD player, then I would suggest using DivX5, since old DVD players might dont have support for XviD.

---

### Post by anemon on 2006-12-29
Thanks! :)

---

### Post by anemon on 2006-12-29
Or, wait a sec ... I've taken a closer look on the dvd::rip docs, and it turns out the four in "xvid4" is not a version number, but something else entirely:

> transcode support different versions of the XviD codec. If you don't care about the details, just select xvid, which uses the default XviD codec if your transcode installation, which usually is xvid4 and refers to XviD 1.1.

So, the mystery remains! :cool: Why on earth won't VLC take an .avi encoded to xvid 1.1?

---

### Post by paziek on 2006-12-29
Huh.. try playback it with MPlayer.
If it wont start, it means file is corrupt?

---

### Post by anemon on 2006-12-29
Well, I tried to play it in MPlayer (Totem) first thing I did, and it seemed to work just fine ... So it's not really a problem with the file, but with VLC. (Which would probably make their forum a better place to raise this issue, but anyway... :-) )

Oh well. Perhaps I should just get over the whole thing? Or make a clean install of VLC and see if that works better...

---

### Post by damacus on 2007-05-05
> **anemon said:**
> Hi there!

Just ripped my first DVD with dvd::rip, and it worked like a breeze. The file (in .avi format, encoded to xvid4) plays just fine in Totem, but the subtitles are in a separate .sub file, and I can't seem to make Totem play it. Solution: fire up the ol' favorite media player, VLC.

The problem is that VLC won't accept the .avi file! The program opens briefly, and then crashes without warning. Running it from terminal just gives me:

```
VLC media player 0.8.6 Janus
Segmentation fault (core dumped)

```

... and nothing more. Is there something wrong with the rip -- and, in that case, why would it work in Totem? I've never had any problems with VLC before, so I'm a bit confounded. What to do? I've seen other threads reporting similar problems, but none with a good solution.

Best / A.

Actually, I am having the same problem -- divx rip with dvd::rip and external subs -- can't get the subs to work in any player, and VLC core dumps on start.   

Well, I think the problem isn't a codec.. its the sub file.   If you move the *.sub and *.idx files out of the same directory as the avi file, VLC plays the avi file without any problems at all....

---

### Post by vdawg on 2008-05-16
Yup, I was having the same problem, MPlayer actually plays the subs just fine. VLC was jus bein such a bitch!

---

### Post by pkkid on 2008-06-19
I was just having the same issue and found this thread.  So, thanks for explaining the issue to me.

Can you convert your subtitles to *.srt format.  That will probably fix your issue.  I never liked the way sub files rendered on the movie anyways.  I haven't tried this on my movie yet, but I don't see any reason it wouldn't work as expected. :)

---

