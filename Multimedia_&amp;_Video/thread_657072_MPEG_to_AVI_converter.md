---
title: "MPEG to AVI converter"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Locutux on 2008-01-03
Can anyone recommend me a program which converts from MPEG to AVI? It's urgent. :S
Thank you.

---

### Post by charly4711 on 2008-01-03
Try ffmpeg (or mencoder of transcode, but ffmpeg should do well and work with sensible defaults).

---

### Post by Locutux on 2008-01-03
Thank you very much. I installed it, but how does this works? I'm a new to Ubuntu, and I'm a bit confused.

---

### Post by MONODA on 2008-01-03
try iriverter its pretty good.

---

### Post by Locutux on 2008-01-03
Thanks MONODA. I installed it, but here's a problem. There's the Iriverter icon in the menu, when I click it, it does nothing.

I tried running the program via the Konsole, look what I got:

Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/s
wt/events/SelectionListener (Unsupported major.minor version 49.0)

Can you tell me what's the problem and how to fix it? Thanks.

---

### Post by charly4711 on 2008-01-03
for ffmpeg the basic command line goes:

ffmpeg -i file.mpeg file.avi

Then there are tons of parameters if you're not satisfied with the result. If you want best possible video quality, do:

ffmpeg -i file.mpeg -sameq file.avi

If you need ms media player compatibility try:

ffmpeg -i file.mpeg -vcodec msmpeg4 file.avi

(For other options ... do I need to say "man ffmpeg" ?)

---

### Post by Locutux on 2008-01-03
Thanks. It's a bit confusing because all of this is done in a shell. :) 
I'll experiment and see what will come up.

Thanks again.

---

### Post by dannyboy79 on 2008-01-03
i believe avidemux can turn mpeg's into avi files. if not, check out this wiki for using ffmpeg [http://ffmpeg.mplayerhq.hu/documentation.html](http://ffmpeg.mplayerhq.hu/documentation.html) to use in the terminal. otherwise there's plenty of scripts within this forum for doing it.

[http://ubuntuforums.org/showthread.php?t=193754](http://ubuntuforums.org/showthread.php?t=193754)

---

### Post by yabbies on 2008-01-03
If you find that using a gui is easier for you
dvd::rip is a gui that will transcode mpg to avi.

---

### Post by Locutux on 2008-01-03
I saw the scrips, they seem to be nice, but for a newbie like me, I don't think are much useful. I'm eager to learn, so I'll see what I can do.

What I asked for, was a simple converter. :)

---

### Post by charly4711 on 2008-01-03
my 2 cents:
The whole video business is not simple.

If you want to do smth. simple, you may find a GUI which you find simple to use. (But I don't think it will be any simpler than "ffmpeg -i test.mpeg -sameq -vcodec msmpeg4 test.avi"). The GUIs I have seen had more than a few switches, too, and it always also took me time to understand what each was for.

The difficulties really start when you find what you were trying to do is not simple and you try to understand the subtleties of digital video.

You are not telling us what exactly it is you're trying to do, like:
Why do you need to convert?
What variant of mpeg format is the source video / where does it come from?
What is it you want to achieve by converting to avi?

---

### Post by Locutux on 2008-01-03
Alright...

There's a mpeg file, I want to convert it to .avi so my Panasonic DivX player can read it. I reads only .avi files.

---

### Post by yabbies on 2008-01-03
or if you do not want to use the gui. There are some very simple command lines. 
You will need mencoder for this
you can find it in synaptic if you don't already have it

put your mpg in a folder called transcode on your Desktop

open a terminal and 

```
cd Desktop
```

```
cd transcode
```

type

```
ls
```

to make sure your mpg is in the folder.

now to transcode the mpg to avi all you have to do is copy this code.

```
mencoder FOO.mpg -o FOO1.avi -ovc copy -oac copy
```

where FOO is the name of your original mpg and FOO1 is the name of your new avi file

---

### Post by Locutux on 2008-01-03
Thanks yabbies. I'll try this tonight.

EDIT: The original .mpg file will stay after is encoded to .avi, right?

---

### Post by yabbies on 2008-01-03
Sure will

---

