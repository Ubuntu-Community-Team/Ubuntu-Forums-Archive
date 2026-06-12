---
title: "Totem doesn't play .avi, others do"
date: 2009-06-26
forum: Multimedia Software
---

### Post by Vostrocity on 2009-06-26
I like Totem the best out of all the media players, but for some reason it won't play my .avi videos. It says I need to install plugins, goes searching for one, says it can't find any, and then just plays the sound but not the picture. VLC and Xine both work perfectly but I don't like their interface much. MPlayer gives a warning about unknown codec but plays it anyway just fine.

---

### Post by philcamlin on 2009-06-26
hmm why dont you just use vlc or something :popcorn:

---

### Post by Vostrocity on 2009-06-26
Because I prefer Totem's interface, and that it generates video thumbnails.

---

### Post by philcamlin on 2009-06-26
hmm mine finds the plugins

try it again

---

### Post by Vostrocity on 2009-06-26
No luck but I'm pretty sure avi was supposed to be supported by default.

---

### Post by philcamlin on 2009-06-26
sudo apt-get purge totem 

sudo apt-get install totem

try that :popcorn:

---

### Post by Vostrocity on 2009-06-26
Gasp you used :popcorn: again.

EDIT: Nope still not working.

EDIT2: I just installed w32codecs from Medibuntu, and it's still not working! Should I uninstall it then?

---

### Post by Vostrocity on 2009-07-10
Bump!

Still haven't solved this. I'm trying to use Cinelerra, but when I import the .avi files it only shows the audio track which is similar to what happens with Totem.

---

### Post by fooman on 2009-07-10
have you tried the "ubuntu-restricted-extras" package?  it should be in synaptic,  or in a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

i think that will do the trick.  ...hope it helps.

---

### Post by Vostrocity on 2009-07-10
I already had that installed.

---

### Post by hansdown on 2009-07-10
Hi Vostrocity.

There are a whole bunch of bug reports for totem.

[http://www.google.ca/search?q=.avi+files+in+totem+in+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=.avi+files+in+totem+in+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Totem-xine "may" work better.

---

### Post by Vostrocity on 2009-07-11
So I guess there isn't much of solution yet. My main problem is getting it to work in Cinelerra since for playback I can just use VLC. But I suspect the two apps have the same issue.

---

