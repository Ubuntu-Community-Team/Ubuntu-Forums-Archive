---
title: "how do I convert a MKV file to avi?"
date: 2009-10-28
forum: Multimedia Software
---

### Post by Gatorade on 2009-10-28
anyone know how to do this?

---

### Post by SuperSonic4 on 2009-10-28
Both are container formats so a simple conversion should do

```
ffmpeg -i input.mkv -vcodec copy -acodec copy output.avi
```

Why would you want to do this? VLC plays mkv with no problems

---

### Post by Gatorade on 2009-10-28
hi , thanks for the info.

I would like to play it on a dvd player at my friends house.

I'm still kind of a newbie at this code stuff, so just to clarify,

I open up a terminal and just paste that code into it ?
how do I tell it which file to convert?

sorry if these are dumb questions.

---

### Post by SuperSonic4 on 2009-10-28
If you're using Devede you may be able to import the mkv file directly to make the video ISO although I do not have a test video to try it on

---

### Post by Gatorade on 2009-10-28
never even heard of devede before , so no I'm not using it, lol.

ok, I got that installed , now where do I go from there to convert the file?

---

### Post by vinutux on 2009-10-28
> **Gatorade said:**
> never even heard of devede before , so no I'm not using it, lol.

ok, I got that installed , now where do I go from there to convert the file?

Here | **[http://www.getdeb.net/app/DeVeDe]("http://www.getdeb.net/app/DeVeDe")**

[IMG]http://www.getdeb.net/media.php?id=44&type=screens&w=425&h=350[/IMG]

---

### Post by Gatorade on 2009-10-29
> **Topkingtips said:**
> I think you just need google with this keywords " mkv to avi"or "mkv converter", you will find your want:)

Good luck

I did that. but I got a lot of stuff that was windows based, and many of the programs required buying a program to convert the whole file.




thanks for the link vinutux.

---

### Post by vinutux on 2009-10-29
> **Gatorade said:**
> I did that. but I got a lot of stuff that was windows based, and many of the programs required buying a program to convert the whole file.




thanks for the link vinutux.

use mkv+avi+ubuntu or mkv+avi+linux as key words
or use google linux serch here **[http://www.google.co.in/linux]("http://www.google.co.in/linux")**

---

### Post by Gatorade on 2011-08-03
I was just trying to do this again and I found that it was making my computer run really hot. My CPU temp monitor was hovering around 97-100 degrees so I cancelled it. As soon as I stopped , the temps went right back down to normal.

anyone else experience this type of temperature spike while converting a video?

does this conversion really take that much processing power to overheat my computer like that?

---

