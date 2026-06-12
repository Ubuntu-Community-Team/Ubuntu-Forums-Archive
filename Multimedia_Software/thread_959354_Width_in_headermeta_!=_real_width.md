---
title: "Width in header/meta != real width"
date: 2008-10-26
forum: Multimedia Software
---

### Post by Paretje on 2008-10-26
On Friday, I've got my TV-card, and everything works fine. I get a MPEG/MPEG-2 file, and I want to make it a bit smaller using Avidemux.

Testing a bit with the different systems, I saw a problem: the circle of "één" wasn't round when it was reencoded. And, I found the problem:
The frames are 768*576, but in the header, it says 720*576, and indeed, taking a screenshot in totem of the original and one of the Xvid/Divx version gives that result.

With some filter combinations, you can fix this, but I want to do this without loss of quality. So, just change the header information.

By the way: the films I get are interlaced, but I want to deinterlace them, because the quality is better then, but just like with the previous question, I want to do this without loss of quality, since I want to hold quality files on my new HDD of 250GB, and encoded with Xvid on a DVD to play on my DVD-player.

---

### Post by xc3RnbFO8P on 2008-10-26
> but just like with the previous question
What is the previous question????

---

### Post by Paretje on 2008-10-26
A command which can do this:
> **Paretje said:**
> With some filter combinations, you can fix this, but I want to do this without loss of quality. So, just change the header information.

---

### Post by Paretje on 2008-10-26
OK, to make clear what I want to know:
 - How can I change the header/meta information of the AVI file about the width, without changing something else (the film), since that has that value like I want to give to the header/meta.
 - How can I deinterlace without losing quality, since I have to encode de movie when I want to deinterlace with Avidemux, I have to use a filter, and then have to encode, which mostly gives a result with a lower quality.

This is to make clear what I want, and I hope to get an answer as soon as possible, since I'm very curious to see the first result which is ready to burn.

Thanks in advance ;)

---

### Post by xc3RnbFO8P on 2008-10-27
> How can I change the header/meta information of the AVI file about the width, without changing something else (the film), since that has that value like I want to give to the header/meta.
You cant.
> How can I deinterlace without losing quality, since I have to encode de movie when I want to deinterlace with Avidemux, I have to use a filter, and then have to encode, which mostly gives a result with a lower quality.
Here is example  
If you choose Mpeg4 ASP (Xvid4) then configure
**Main**> Encode Type> Two Pass> Video Size (1 cd 700mb ca 100 min)
**Motion & Misc**> Motion search precision> 6  VHQ mode 4 
then add Deiterlace filter.

---

### Post by Paretje on 2008-10-27
So it's really impossible? :(

But, thanks. I'll try to search to make it with the less loss of quality.

---

