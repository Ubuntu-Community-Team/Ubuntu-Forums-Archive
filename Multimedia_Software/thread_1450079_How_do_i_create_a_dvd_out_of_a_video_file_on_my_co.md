---
title: "How do i create a dvd out of a video file on my computer?"
date: 2010-04-08
forum: Multimedia Software
---

### Post by BadName on 2010-04-08
What software will do this for me?

---

### Post by ron999 on 2010-04-08
Hi
Look in Ubuntu's repository for **devede**. It's point-and-click.

The program that I use is **tovid**. There's a GUI for it too, **tovidgui**

---

### Post by BadName on 2010-04-09
I have tried Devede before and it didn't work for me. After you recommending it i tried it again but the same problem. I have tried it on a few DVD players and the same thing happens. None of them recognise the disc. My burner is working 100%. I have used it to burn stuff recently with no problems whatsoever so i'm wondering what the problem could be. Also should it take Devede a few hours to burn one movie?

---

### Post by ron999 on 2010-04-09
> **BadName said:**
>  Also should it take Devede a few hours to burn one movie?
It does take quite a while to convert the video into the correct format for a DVD (that's MPEG-2). It's a very CPU-intensive process. So it depends how fast is your computer.
That's the longest part.
After that, when you burn it to disc, it will depend what speed you choose to burn it at, 8x or whatever.

I never had any success with devede, that's why I use tovid.

---

### Post by Andrew Golightly on 2010-04-09
Hey there,

I tried tovid last night. It seemed to all basically work.. except the audio and video are slightly out of sync. The original file is an avi and it's in perfect sync.

I used the command tovid -pal -in xx -out xy

Post that though, the menu, and burning the disc worked fine. Works fine on the DVD player too. Just need to sort out the syncing thing. Anyone have any ideas?

thanks.

---

### Post by ron999 on 2010-04-09
> **Andrew Golightly said:**
> 

I used the command tovid -pal -in xx -out xy



That's OK.
You can specify FFmpeg for conversion. It will be quicker to convert and might be less likely to lose sync.
Like this:-
```
tovid -pal -ffmpeg -in xx -out xy

```
:)

---

### Post by Mia1990 on 2010-04-09
+1 for tovid if your using tovidgui then go to the encoding tab then on that tab click the video button there should be a check box that says encode using ffmpeg put a check there and it should sync up.

---

### Post by Andrew Golightly on 2010-04-10
Thanks guys and girls :)

I tried encoding with ffmpeg using the command line and it all worked beautifully.

---

### Post by BadName on 2010-04-10
Anyone know any simple GUI programs for my purpose?

---

### Post by 2hot6ft2 on 2010-04-10
I would give QDVDAutor a shot. It's not in the ubuntu repos. though. It is in the Ubuntu Ultimate Edition repo. that's how I got it. I run UUE.
[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

But it may be more than what you want!!!

---

