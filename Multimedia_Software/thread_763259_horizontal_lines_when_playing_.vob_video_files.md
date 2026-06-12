---
title: "horizontal lines when playing .vob video files"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Fernando Negro on 2008-04-22
No matter which player I use, whenever I play .vob (MPEG-2) video files (small ones I have on my computer, not from a DVD) I get some strange horizontal lines.

(a sample image follows as an attachment)

This is a problem I've always had in Linux for this type of files.

At first I thought it could be caused by the fact that the ATI card I had was not well supported in terms of drivers, but then someone in the #mplayer IRC channel, I think, told me I just needed to put a code in the configuration file and it solved the problem in mplayer (the player I decided to use for this kind of files).

Now I have a NVIDIA card and the same thing happens. I've put a code again ("vf=lavcdeint") and it solved the problem. Until recently that is, when I started getting an error message when opening this type of videos: "Cannot prepare subtitle font".

If I disable the code I've put, the error message goes away but the lines come back.

I tried opening this kind of files with Totem and gxine and realized that the horizontal lines also appear if I use these players. So it's a problem with Linux reading this kind of files and not a problem specific to mplayer.

Does anyone know what can I do to solve it for all players?

Thank you in advance.

---

### Post by cor2y on 2008-04-23
have you tried the deinterlace filter thats in totem, vlc etc?

---

### Post by Fernando Negro on 2008-04-23
I've just tried it in Totem and in gxine it was already enabled by default. The problem remains.

---

### Post by mc4man on 2008-04-23
> vf=lavcdeint
That's calling a deinterlacer - the one in totem/ xine is blend, there are much better ones in mplayer. Try using smplayer to call mplayer, theres 5 choices for deinterlace. Check and see if you have mplayer-fonts installed
in repo or latest [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

---

### Post by Fernando Negro on 2008-04-23
I've tried installing mplayer-fonts and it stopped giving me the error about the font. But now the video plays slowly and desynchronized (audio not matching the video) and after a few seconds it crashes. (It was already playing slowly before when it gave me the error about the font, but I thought it was because of the repetitive error message(s))


[I]"Fatal error!"
"MPlayer interrupted by signal 6 in module: vo_check_events"

"Fatal error!"
"- Mplayer crashed. (...)"

[/I]
If i disable the "vf=lavcdeint" code the lines come back again.


I installed smplayer, chose the first deinterlace filter and it worked. :)

I'm now happily watching the video I wanted without the horizontal lines.


I remember reading something about a front-end for mplayer a long time ago, but wasn't aware of how advanced it was. And being able to see my .vob video files in smplayer is already good enough for me.


Thanks for your help cor2y.

Thank you very much for your help mc4man and for your explanation. :)


Take care you all.

---

### Post by rykel on 2008-07-04
I am interested in removing these lines too, as it is a PITA when I see those lines in a DVD movie.

---

