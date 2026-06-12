---
title: "Capturing .ram stream"
date: 2009-09-20
forum: Multimedia Software
---

### Post by MrNatewood on 2009-09-20
Does anyone know how to save a streaming .ram video to local disk?

Saving the .ram results in a small sort of link file to the stream being saved.

I tried fiddling with VLC to get it to output to file with no luck.

---

### Post by raboofje on 2009-09-20
Got an example URL? mplayer/mencoder are usually able to handle this.

---

### Post by MrNatewood on 2009-09-20
this for example:
[http://web.mit.edu/smcs/8.02/lecture1-220k.ram](http://web.mit.edu/smcs/8.02/lecture1-220k.ram)

EDIT: thanks, I managed to do it with mplayer, used this command :
```
mplayer -noframedrop -playlist http://web.mit.edu/smcs/8.02/lecture1-220k.ram -dumpstream -dumpfile file.rm
```

---

### Post by andrew.46 on 2009-09-20
Hi MrNatewood,

'I will show you, whether you like it or not, that physics is beautiful', I love that line!

```

mplayer -noframedrop \
       -playlist http://web.mit.edu/smcs/8.02/lecture1-220k.ram \
       -dumpstream -dumpfile file.rm

```

You could safeguard yourself a little against the vagaries of network streaming by perhaps adding a little cache:

```

mplayer -cache 2048 \
       -playlist [http://web.mit.edu/smcs/8.02/lecture1-220k.ram](http://web.mit.edu/smcs/8.02/lecture1-220k.ram) \
       -dumpstream -dumpfile file.rm

```

Does *-noframedrop* work when saving a stream in this way? I am not completely sure but I suspect not although I have been wrong many times before :).

Andrew

---

