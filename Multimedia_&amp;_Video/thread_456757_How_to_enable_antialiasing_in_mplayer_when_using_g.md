---
title: "How to enable antialiasing in mplayer when using gl2 for video output"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by Starwindow on 2007-05-28
I was wondering if anyone could help me to get antialiasing to work when using gl2 video ouput in mplayer.  I can't seem to find any switches to do this and whenever I select gl2 I just get:

```
[gl2] antialiasing off
```

Anyone have any ideas on how I can turn it on?  I can't seem to find anything in any of the manuals for mplayer that cover how.

---

### Post by Spudgun on 2007-11-12
Bump..

---

### Post by jurp5 on 2007-12-10
if(key=='a'||key=='A')
	{
		gl_set_antialias(!gl_antialias);
		return 0;
	}

You have to press a :)

---

### Post by JanusDC on 2008-02-23
> **jurp5 said:**
> if(key=='a'||key=='A')
	{
		gl_set_antialias(!gl_antialias);
		return 0;
	}

You have to press a :)

And there isn't any way to start playing with antialiasing? (like an option to pass to mplayer command)

By the way, What is antialiasing for (in a movie)?

---

