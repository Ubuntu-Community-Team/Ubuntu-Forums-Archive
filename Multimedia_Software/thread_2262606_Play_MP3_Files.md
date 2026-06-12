---
title: "Play MP3 Files"
date: 2015-01-26
forum: Multimedia Software
---

### Post by Patreick_Lucas on 2015-01-26
Hi

I am still new to Ubuntu so forgive me if my question is obvious.

I just installed puddletag to edit ID3 tags in my MP3 files. How can I play those files from puddletag using the default MP3 player called Rythmbox Audio Player? All my music plays fine outside puddletag.

Thanks for your help.

Patrick

---

### Post by Jeroen Mathon on 2015-01-26
Why would you need to play them from puddletag.
That software is only there to tag it correct?

And the tag does not affect the song it self only the data read by the Music player.

You could do something like
```
puddletag ; rhythmbox PATH_TO_SONG
```
If you really want to launch it after tagging it.

---

### Post by Yellow Pasque on 2015-01-26
Well, if you want them to play in Rhythmbox, you could use this command in puddletag's preferences:
```
rhythmbox-client --play
```

---

### Post by Patreick_Lucas on 2015-01-27
Thanks guys.

---

### Post by Patreick_Lucas on 2015-01-30
> **Temüjin said:**
> Well, if you want them to play in Rhythmbox, you could use this command in puddletag's preferences:
```
rhythmbox-client --play
```

This does start the player but does not plat the file selected in puddletag.
Any ideas?

---

### Post by mc4man on 2015-01-30
Well there's never anything for sure with RB but try this command instead
```
rhythmbox-client --enqueue --play
```

---

### Post by Yellow Pasque on 2015-01-30
^Thanks, I was wondering if it was going to need the --enqueue switch. I'm not a regular Rhythmbox user and the command I used worked okay for my test, but I didn't have a pre-existing library in rbox.

---

