---
title: "Fesitval (text-to-speech) alternatives?"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by Peepsalot on 2006-06-05
I was looking into using festival to read ebooks to me, but the voice quality does not sound very good to my ears.  Is there any other similar program available, or different settings or voice files that might work better?

---

### Post by monchichi on 2006-06-05
use gnopernicus and the festival gnome-speech driver. there are tons of voices available.

---

### Post by Peepsalot on 2006-06-05
Ok, I checked and I have gnopernicus installed, along with "libgnome-speech3" which I assume is the gnome-speech you are talking about.  When I try to change voices in gnopernicus, there are only the two english voices that were installed for festival(one came with it, and the second was from me installing the only other english voice I saw in synaptic).  Where are the "tons"?

Also, I can't even figure out how to get this program to read a text file.  For festival it would just be ```
cat blah.txt | festival --tts
```  But I don't understand gnopernicus at all.  It's just reading button names to me and annoying the crap out of me.

---

### Post by monchichi on 2006-06-05
Oh, yeah, I guess gnopernicus could be pretty annoying. The only reason I suggested it is that I don't know how to change the festival voice at the command line.

You can add new festival voices in /usr/share/festival/voices/english/

you can download some voices from here: [http://festvox.org/packed/festival/1.95/]("http://festvox.org/packed/festival/1.95/")

and there's more available floating around the net. Google is your friend.

---

### Post by Zyphrexi on 2006-06-10
i can't get either festival or gnopernicus to work, when I do the command ```
cat Unsaved\ Document\ 1 | festival --tts
```

nothing happens.

how do I set it up?

---

### Post by Peepsalot on 2006-06-12
[QUOTE=Zyphrexi]i can't get either festival or gnopernicus to work, when I do the command ```
cat Unsaved\ Document\ 1 | festival --tts
```

nothing happens.

how do I set it up?[/QUOTE]
Does running that command from a terminal give any text output?

No special configuration was necessary on my system.  Are you sure your soundcard is otherwise functioning properly?  Can you play sound files like wav or mp3 from another media player?

---

### Post by iplayfast on 2006-06-15
on mine it shows
```

echo "Hello world" | festival --tts
Linux: can't open dev/dsp

```

Looking at /dev/dsp i
```

ls -l /dev/dsp
crw-rw---- 1 root audio 14, 3 2006-06-15 15:37 /dev/dsp

```

I am in group audio

I'm at a loss.

---

### Post by iplayfast on 2006-06-15
Running festival as root works though.

---

### Post by iplayfast on 2006-06-15
And now running as a normal user it starts working.

Any idea why it was broke and if it will stay fixed?

---

