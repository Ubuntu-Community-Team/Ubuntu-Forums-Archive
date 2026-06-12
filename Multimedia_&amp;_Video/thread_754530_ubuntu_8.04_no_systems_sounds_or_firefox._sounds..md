---
title: "ubuntu 8.04 no systems sounds or firefox. sounds."
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by neomaxi on 2008-04-13
I have ubuntu 8.04 beta.  No sound in Firefox when i go to anything on the internet .  When I go to system/preference/sound.  on the devices tab, sytems  tests work.... but on the sounds tab none of the systems sounds work. when I play games like ioqake.. I DO have sound.... Adobe flash (latest version) is installed. not Gnash..

---

### Post by h4mx0r on 2008-04-14
I'm still waiting for someone to fix this pulseaudio crap some apps don't have support for it yet and most beta testers are stuck without sound, so as you can see there is pretty much no guarantee sound will work on most apps because it hasn't been thoroughly tested. The latest alsa is here and it fixes many things for my system as I can see I actually got an internal mic on it, but I can't do any sound features...

Some things you might try would be messing with that libflashsupport app see what it actually does if any help and firefox I got going crashes everytime I open a flash anything, most are too busy gloating about gnash to help you though. From what I can tell it might be a gtk thing.

---

### Post by neomaxi on 2008-04-14
> **h4mx0r said:**
> I'm still waiting for someone to fix this pulseaudio crap some apps don't have support for it yet and most beta testers are stuck without sound, so as you can see there is pretty much no guarantee sound will work on most apps because it hasn't been thoroughly tested. The latest alsa is here and it fixes many things for my system as I can see I actually got an internal mic on it, but I can't do any sound features...

Some things you might try would be messing with that libflashsupport app see what it actually does if any help and firefox I got going crashes everytime I open a flash anything, most are too busy gloating about gnash to help you though. From what I can tell it might be a gtk thing.

I tryed uninstalled Libflashsupport and that didn't help. 
I guess I'll wait until RC1 or the final for the fix.. if it doesn't get fixed. Im gonna go back to PCLOS or mandriva 2008.1

At least everything works right out of the box for me..

---

### Post by neomaxi on 2008-04-14
> **h4mx0r said:**
> I'm still waiting for someone to fix this pulseaudio crap some apps don't have support for it yet and most beta testers are stuck without sound, so as you can see there is pretty much no guarantee sound will work on most apps because it hasn't been thoroughly tested. The latest alsa is here and it fixes many things for my system as I can see I actually got an internal mic on it, but I can't do any sound features...

Some things you might try would be messing with that libflashsupport app see what it actually does if any help and firefox I got going crashes everytime I open a flash anything, most are too busy gloating about gnash to help you though. From what I can tell it might be a gtk thing.

I tryed uninstalled Libflashsupport and that didn't help. 
I guess I'll wait until RC1 or the final for the fix.. if it doesn't get fixed. Im gonna go back to PCLOS or mandriva 2008.1

At least everything works right out of the box for me..

---

### Post by odinfromvalhalla on 2008-04-14
try this:

```
killall -9 pulseaudio
```

then restart firefox

---

### Post by neomaxi on 2008-04-14
> **odinfromvalhalla said:**
> try this:

```
killall -9 pulseaudio
```

then restart firefox

thanks.. that seems to make my headphones to have sound at least.. but not my regular speakers.

Very odd this whole audio thing in ubuntu really is bad...

---

### Post by surman87 on 2008-04-27
This has been an impossible task for me as a ubuntu noob.  Even if I do manage to find a post on this topic that isnt from 2006 the amount of "try this... try this" has left my fresh install with all kinds of random things done to it.  

I think I'm just gonna give up on finding a working fix for flash audio in firefox.

---

### Post by bouchmil on 2008-04-27
Some people solve this problem by installing libflashsupport :
```
sudo apt-get install libflashsupport
```

I've found it on [URL="http://http://ubuntuforums.org
/showthread.php?t=763664&highlight=sound+flash+firefox"]this tread [/URL]

---

