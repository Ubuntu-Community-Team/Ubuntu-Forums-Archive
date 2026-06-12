---
title: "Firefox 3.0b5 flash sound problem"
date: 2008-04-30
forum: Multimedia Software
---

### Post by Hamstermerc on 2008-04-30
Hey, so i'm a new user to the world of Linux and loving it. However my problem is that firefox 3.0b5 isn't playing any sound on flash videos and on mysapce music i get: "Error loading XML document". 

I've tried looking around the forums. I've reinstalled firefox reinstalled flash player 9 etc. but nothing seems to work.

I'm running the Hardy Heron release if that helps anyone and i've installed it alongside Windows on my computer until I've got used to Ubuntu however many people said that isn't the problem.

Interesting to note that Firefox 2's flash sound works fine so maybe it has something to do with files in the wrong directories??

On top of that Firefox 2 is being a slight bit buggy so i cant just use that. Oh and also the toolbar "File Edit etc." is coloured in a light gray colour constantly making it very hard to read but this is less of a problem than the flash problem. 

Any help would be much appreciated as i'm very keen to learn more about Ubuntu. 

Thanks all.

---

### Post by NilsE on 2008-04-30
Install libflashsupport from Synaptic. It should fix the sound.

---

### Post by Hamstermerc on 2008-04-30
Hmmm was already installed :( reinstalled the package but with no result :( Any other ideas?

---

### Post by schtufbox on 2008-04-30
> **NilsE said:**
> Install libflashsupport from Synaptic. It should fix the sound.

and cause firefox to becomne unbstable. One of the fixes they did prior to release was to remove the need for libflashsupport.  I get sound fine in firefox without it and much fewer crashes.

---

### Post by Hamstermerc on 2008-04-30
> **schtufbox said:**
> and cause firefox to becomne unbstable. One of the fixes they did prior to release was to remove the need for libflashsupport.  I get sound fine in firefox without it and much fewer crashes.
True after installing it one of the flash videos i stumbled on worked with sound but the video stuttered and then firefox crashed... any other ideas? It's the main thinking that makes me have to keep switching back to windows

---

### Post by NilsE on 2008-04-30
> **Hamstermerc said:**
> True after installing it one of the flash videos i stumbled on worked with sound but the video stuttered and then firefox crashed... any other ideas? It's the main thinking that makes me have to keep switching back to windows
I knew it would do that, it was just to see if you got sound.  I don't use it myself but some people report they have to use it.

The following is all you should have to have installed that you find by searching for the word flash in synaptic.

libswfdec-0.6-90 (0.6.4-2)
flashplugin-nonfree (9.0.124.0ubuntu2)
ubuntu-restricted-extras (15)

If you have those 3 installed you may want to see what you can find on here about pulseaudio since the problem is the interaction between flash and pulse which by the way is what libflashsupport was supposed to fix.

---

### Post by dvord on 2008-04-30
Same problem here.  Tried the above.  I even reinstalled flash-notfree & FF but to no avail.

---

### Post by Jeff Beezy on 2008-05-04
anyone figure this one out? i cant listen to any music on myspace either, getting the same error

---

### Post by dvord on 2008-05-04
Nope, nothing here so far.  I'm subscribed to a few threads and it does seem to be a continuing problem for many.

---

