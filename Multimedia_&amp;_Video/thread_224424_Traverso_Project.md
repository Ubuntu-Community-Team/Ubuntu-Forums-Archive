---
title: "Traverso Project"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by just1m on 2006-07-27
I have to say I like this idea alot. Please check this out and support this new program. It's the closest thing to ProTools I've seen so far that's still being worked on. Has anyone used it? Has anyone even heard of it? It appears that it's one of the guys who helped to program Protux.

---

### Post by just1m on 2006-07-27
Here is the site if anyone is interested in checking it out
[http://vt.shuis.tudelft.nl/~remon/traverso/home.html](http://vt.shuis.tudelft.nl/~remon/traverso/home.html)

---

### Post by huwshimi on 2006-07-28
> **just1m said:**
> It's the closest thing to ProTools I've seen so far that's still being worked on.

Not to hijack your thread but if it's a ProTools like program you're after then you should really try Ardour (and more importantly Ardour 2 when it comes out).

---

### Post by dolson on 2006-07-28
Remon is always in the Ubuntu Studio channel on IRC... He's the author.

---

### Post by zettberlin on 2006-07-28
Very cool - a second HD-Recording Suite that works with jack with some concepts that are different from ardours is very welcome!

I have always liked protux even though i found the non-mouse/menue-thing quite a bit too radical. At the other hand the stuff worked very clean and appeared quite promising to me...

No that there is jacksupport and additional menues i am eager to get my hands on this!!!:D :D

edit:
Now i got it! Installs very smooth :-)

But: 
It is true, that there are more keys on the keyboard than on the mouse but there are 3 Buttons and a weel on the mouse also and i do not see any advantage in not using those at all.
Especially for marking parts of a track ther is no better way but leftclick and drag... Others like changing the height of the track are also best done with the mouse.
More annoying is, that the way,  keystrokes can be used  is confusing - how can i make the thing play, from where the green cursor is placed???
And: there seems to be no jacksupport in the binary for dapper - if jackd is running, traverso uses the nulldevice...

hmmmmm.....

---

### Post by just1m on 2006-07-28
Tell Remon on his forum. He welcomes advice. He wants to make it as user friendly as possible.

---

### Post by rsijrier on 2006-07-29
Hi all,

Since just1m posted a link to this thread in the traverso forums, and me being curious, followed the link :-)

Just to make sure, Traverso is still in it's early development phases, though things are looking really promising right now!

As where the project is heading, don't know yet. But it's certainly not an attempt to immitate any kind of software available today!
That is, it's not a reimplementation of ardour or protools. There is no need to do so, if you need ardour, use ardour :-)

Traverso is a very open project, and I would love your feedback, comments, critics and so on.
The nice thing with Traverso is that you can open your mind and think "what would I like to see", or "how would a certain feature be accessed the most efficient way", and so on.

Travero still suffers from it's roots. That means that mouse usage and placement of quick access buttons are still very scarce.

Large parts of the keyboard handling and related infrastructure has been rewritten in Traverso to be more powerfull, and in fact simpler!
This has been a major undertaken.
The other part was rewriting the whole audio processing code in a more sensible manner, including support for transparent 16/24/32 bit support, and support for multiple backends, including Jack!
(not even speaking of the un/redo framework, core/gui seperation and so on)

But I'm working on it alone (from coding point of view), so it simply takes time!
Mouse support has been added, but it's only there (yet) for verticall track scrolling.
I _certainly_ agree that use of the mouse buttons can be _very_ helpfull.
I would love to hear your ideas about it!

Traverso defaults to alsa driver, since a lot of people don't have jack running by default.
It currently doesn't try the jack driver if the alsa driver fails, though it seems to be a good idea to enable this.
When you started Traverso, open the Project Manager view with F4, go to the settings dialog, and select Jack as the driver. Restart driver if needed.

Use the workcursor (dashed red line) to set the position of the play head. Currently, the green cursor only follows the mouse.
Open the help dialog, go to the "quick reference", and most of your questions will be answered, like 
< shift >, that is, type the shift key, and the work cursor will be placed there.
Like in all audio applications, use the space bar to start/stop playing :-)

Keep the feedback going please, and if possible, in the user mailinglist, or forum.

Thanks,

Remon

---

### Post by zettberlin on 2006-07-29
very helpfull hints, i´ll check it out :-)

thanks for the good work :-)

And again: a second, differnt HD-Recordingsuite besides Ardour is most welcome !!!

---

