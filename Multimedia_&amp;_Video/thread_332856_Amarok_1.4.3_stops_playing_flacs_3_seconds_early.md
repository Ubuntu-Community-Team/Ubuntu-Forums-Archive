---
title: "Amarok 1.4.3 stops playing flacs 3 seconds early"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by alan-the-prof on 2007-01-06
Any thoughts anyone. I have seen some similar problems posted where tracks are reported *starting* 3 seconds late, but my problem is at the other end, with flacs breaking off about 3 seconds early. 

This does not seem to be a problem with mp3s. 

Playback with JuK is almost fine (apart from a tiny glitch if tracks run one into another), but I have come to prefer Amarok's integrated way of searching for files, as well as the ability to add tags such as 'composer' - useful with my sort of music collection and a feaure that JuK seems to lack...

All thoughts appreciated.

Postscript: Updating to the latest Xine-lib has killed flac playback in Amarok entirely. Again.](*,)

---

### Post by dorcssa on 2007-01-12
[http://ubuntuforums.org/showthread.php?t=210683&highlight=amarok+flac](http://ubuntuforums.org/showthread.php?t=210683&highlight=amarok+flac) There's a deb posted in that thread which solves the problem. It's a libxine-main patch. After installing it, you have to lock the version in synaptic, otherwise the update-notifier keep telling you to upgrade. Today I tried out the newest libxine-main version, and it still has the problem. I wonder when they're going to fix it. :roll:

---

### Post by Elim on 2007-01-26
^ I installed that .deb and I have the same problem that he is having...  Any other ideas? :)

---

### Post by dorcssa on 2007-01-26
So the patch haven't sold the problem with flac? It's strange, coz everyone reports back that it's playing flac again after that patch...or almost everyone.

edit: After reading his post again, I realized that you speaking about a different problem, sorry. :D But 3 sec is not much time, is it?

---

### Post by Elim on 2007-01-26
> **dorcssa said:**
> So the patch haven't sold the problem with flac? It's strange, coz everyone reports back that it's playing flac again after that patch...or almost everyone.

edit: After reading his post again, I realized that you speaking about a different problem, sorry. :D But 3 sec is not much time, is it?

I should have been more clear.  The patch solved the FLAC playback problem for the most part -- I can play FLAC just fine.  However, the last track in the amarok playlist (and only the last one, mind) will cut off 3 seconds early.  (When I posted last night I thought it was all tracks, and then I realized it was just the last one.)  So, it's not too much of a problem, but it is mildly annoying.

---

### Post by cdyson37 on 2007-02-18
Have just installed Amarok 1.4.5 from the source and it seems to have fixed this bug. Really not very difficult to get it to work if you can be bothered to install all the -dev packages it needs. Have created a .deb package using checkinstall if anyone wants it (it's 18 meg and I have no hosting though... also I was too lazy to include any dependency information...)

That said if you're not a perfectionist, leaving a "pause track" (I do indeed have an album that actually contains such a thing!) at the end of a playlist is just as good.

---

