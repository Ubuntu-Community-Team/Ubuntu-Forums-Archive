---
title: "questions about ALAC free codec [also how to make a Xmms alac plugin]"
date: 2012-11-14
forum: Multimedia Software
---

### Post by shantiq on 2012-11-14
ok so [URL="http://alac.macosforge.org/trac/wiki"][B]it is now free and open source
[/B][/URL]


and doing this puts it on my system


```
sudo apt-get install subversion
```
```
svn checkout http://svn.macosforge.org/repository/alac/trunk ALAC
```
```
cd ALAC/codec
```
```
make
```


**BUT**   that all goes well   but when i run alacconvert as a command


i get ```
alacconvert: command not found
```



so my first question is how do you use this to compress and decompress alac files


**=====================**


my second question is  how to make a Xmms alac plugin; since it is now open source there are no obstacles apart from knowing how to:KS:KS


any of you learned chaps see a way there?

---

### Post by andrew.46 on 2012-11-14
To build the alacconvert utility there is an extra step, try running the following 3 commands:

```

$ cd ALAC/convert-utility
$ sed -i_bak 's/$(CC) $(LFLAGS) $(OBJS) -o alacconvert/$(CC) $(OBJS) -o alacconvert $(LFLAGS)/' makefile
$ make

```

and then copy *alacconvert* to somewhere on your $PATH such as /usr/local/bin. Hopefully that gets it going for you?

---

### Post by evilsoup on 2012-11-14
My version (the medibuntu version) of avconv says that it supports both decoding and encoding of ALAC, if that helps.

---

### Post by shantiq on 2012-11-14
ok thnx   well Andrew that helps altho it does not run an alac as m4a but a caf    what the funk is a caf?

yes thanx evil one avconv and ffmpeg do conversions for that really well


just trying to see about this source code thing tho




NOW    the prize money   my real wish here is for an xmms plugin

who has the know-how to work from the source code to the plugin?   sadly i do not

---

### Post by andrew.46 on 2012-11-14
> **shantiq said:**
> ok thnx   well Andrew that helps altho it does not run an alac as m4a but a caf    what the funk is a caf?

[http://en.wikipedia.org/wiki/Core_Audio_Format](http://en.wikipedia.org/wiki/Core_Audio_Format)

---

### Post by FakeOutdoorsman on 2012-11-17
> **evilsoup said:**
> My version (the medibuntu version) of avconv says that it supports both decoding and encoding of ALAC, if that helps.

FFmpeg reverse engineered ALAC decoding in 2005, and encoding in 2008 (I think). However, nobody has implemented the reference decoder or encoder. Probably not much interest since the native ones work well.

---

### Post by Yellow Pasque on 2012-11-18
> **shantiq said:**
> my real wish here is for an xmms plugin
Why? Just convert that ALACrap to FLAC.

---

### Post by shantiq on 2012-11-18
nothing crap about alac Temujin;   i love that format:KS   flac is good too

---

