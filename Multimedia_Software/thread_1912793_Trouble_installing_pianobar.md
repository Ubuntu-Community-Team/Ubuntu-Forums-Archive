---
title: "Trouble installing pianobar"
date: 2012-01-21
forum: Multimedia Software
---

### Post by Robert Finley on 2012-01-21
I installed pianobar through synaptic.

I got: "Error: Protocol incompatible. Please upgrade libpiano."  when I started it.

I would love to have pianobar. I listen to Pandora all day.  What do I need to do?

---

### Post by SteveDee on 2012-01-22
> **Robert Finley said:**
> ...What do I need to do?

It looks like a general problem with: libpiano-dev

Suggest you do a general web search (e.g. "libpiano") and try some of the suggestions there.

---

### Post by Robert Finley on 2012-01-22
I have done that.. I kept getting an error.  I was hoping someone here might help.  Now, I have reinstalled my entire system wondering if my problem didn't stem from the fact that I was running lubuntu instead of Ubuntu.

Unfortunately, even with GNOME I still get: fatal error: "gnutls/gnutls.h: No such file or directory" when I try to "make"

This is the steps I am taking: [http://www.foscode.com/install-pianobar-ubuntu/](http://www.foscode.com/install-pianobar-ubuntu/)

This is what I see when I get to "make" :

 CC  src/main.c
In file included from src/main.h:28:0,
                 from src/main.c:52:
src/libwaitress/waitress.h:30:27: fatal error: gnutls/gnutls.h: No such file or directory
compilation terminated.
make: *** [src/main.o] Error 1


Can someone help me out please?

---

### Post by alexhayes on 2012-04-04
I just made a script to take care of everything you need to update pianobar.

Check out[ http://ubuntuforums.org/showthread.php?t=1533357&highlight=pianobar&page=3]("http://ubuntuforums.org/showthread.php?t=1533357&highlight=pianobar&page=3"). 

The version in the repos isn't the most recent, so you get the incompatible protocol error.

---

