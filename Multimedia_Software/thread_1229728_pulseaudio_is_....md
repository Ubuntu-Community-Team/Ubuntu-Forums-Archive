---
title: "pulseaudio is ..."
date: 2009-08-02
forum: Multimedia Software
---

### Post by bootdoc on 2009-08-02
how about a sub forum for pulseaudio.  Why is it that I have sound one day and no sound the next???!  I have followed all recommended howto's for sound in Ubuntu but pulseaudio still drives me NUTS!

---

### Post by coldReactive on 2009-08-02
```
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio
```
reboot, profit.

---

### Post by igorzwx on 2009-08-02
And what to do next?

I think that it is really a good idea to remove pulse,
but this is only beginning of the story.

---

### Post by coldReactive on 2009-08-02
> **igorzwx said:**
> And what to do next?

I think that it is really a good idea to remove pulse,
but this is only beginning of the story.

I don't think you read all of the actions taken in my reply to the thread.

one of them is **apt-get install esound**, which will install esound, another sound system, which doesn't take up space in the process listing.

---

### Post by SuperSonic4 on 2009-08-02
There is always Phonon ;)

I don't think Pulseaudio needs a subforum - it would fit nicely into Multimedia

---

### Post by igorzwx on 2009-08-02
I am affraid it is not always sufficient.
I had already experience with this.
The you may need to fix something.

---

### Post by igorzwx on 2009-08-02
More exactly, I had that "esound" on Ubuntu 6.10
I was not very happy with it.

---

### Post by coldReactive on 2009-08-02
> **igorzwx said:**
> More exactly, I had that "esound" on Ubuntu 6.10
I was not very happy with it.

And you haven't tried it now? :|

esound plays the startup and login sounds now.

---

### Post by igorzwx on 2009-08-02
"And you haven't tried it now? :neutral:"

Not, the very idea to try esound once more was not very attractive.
I prefered to jump into the unknown
and installed OSS4

---

### Post by igorzwx on 2009-08-02
Sorry!
I did install esound with OSS4
to fix playback of some apps, perhaps.
I do not remember now exactly.
In any case, everything works well.

---

