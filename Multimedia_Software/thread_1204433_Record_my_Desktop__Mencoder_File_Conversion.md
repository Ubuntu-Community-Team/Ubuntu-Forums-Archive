---
title: "Record my Desktop | Mencoder File Conversion"
date: 2009-07-04
forum: Multimedia Software
---

### Post by nu2rage on 2009-07-04
Guys,

I'm sorry I have to be a noob on this one.  I have gtk-recordmydesktop, which I like, to record my desktop sessions.  Works great get my ogg files then I use mencoder crank out an avi.  Both files play flawlessly on my Ubuntu machine.

Problem is I want to bring them in to Sony Vegas on a Windows box.  The Windows box can't play the ogg or the avi and even though Vegas should accept both, it takes neither.  I'm sure this hurdle can be overcome.  I feel if I had a file windows could play that Vegas would take it too.

Thanks for any input!
R.Smith
[www.netrage.org]("http://www.netrage.org")
[www.ubuntu-rage.blogspot.com]("http://www.ubuntu-rage.blogspot.com")

---

### Post by Boondoklife on 2009-07-04
This sounds like a codec issue, what are you using for the mencoder convert command?

---

### Post by nu2rage on 2009-07-04
mencoder out.ogg -O out.avi -ovc lavc

---

### Post by andrew.46 on 2009-07-04
Hi nu2rage,

> **nu2rage said:**
> mencoder out.ogg -O out.avi -ovc lavc

You could try:

```
mencoder out.ogg -o out.avi -ovc lavc -ffourcc XVID
```

I will admit that I am not sure what 'Sony Vegas' is though :-).

Andrew

---

### Post by nu2rage on 2009-07-04
Thanks!

Sony Vegas is a competitor to Final Cut Pro.  A very expensive media editor.

Unfortunately, looks like it's still a no go.  Won't play in windows or import to Vegas.  Thanks for trying to help, any other suggestions?

---

### Post by Boondoklife on 2009-07-04
Really the best recommendation is to find out what codecs vega supports, it is is not opening the xvid then I think it is pretty limited in the realm of codec to things you would download. Once you find out what it supports then pic one and chances are mencoder can conver to it.

And no avi is not a codec it is just a container, xvid, divx, etc are codecs

---

