---
title: "Streaming radio not working"
date: 2008-07-27
forum: Multimedia Software
---

### Post by uzzo2 on 2008-07-27
hello all, was just trying to listen to radio via the internet and it's not working for some reason. i have gecko mediaplayer and gnome-mplayer installed, is there anything else i need?

---

### Post by nikgare on 2008-07-27
Can you give as a URL for the redio staion you are trying to play?
There are many different ways to stream radio over the net, so narrowing it down would help.

---

### Post by uzzo2 on 2008-07-27
[http://player.play.it/player/player.html?id=2144](http://player.play.it/player/player.html?id=2144)
that's one of them, but i found out after i posted that other radio stations would play. so it may be problems with specific stations, thanks.

---

### Post by nikgare on 2008-07-27
This one is delivered via flash (and works fine here), so you need to make sure that you have **flashplugin-nonfree** installed, not **gnash**

---

### Post by uzzo2 on 2008-07-27
> **nikgare said:**
> This one is delivered via flash (and works fine here), so you need to make sure that you have **flashplugin-nonfree** installed, not **gnash**
thanks, i checked synaptic and i do have this one installed.

---

### Post by nikgare on 2008-07-27
What browser are you using, and what happens when you go to that page? Does the flash work?

---

### Post by uzzo2 on 2008-07-27
> **nikgare said:**
> What browser are you using, and what happens when you go to that page? Does the flash work?
i'm pretty sure i'm using firefox 3, on that particular one it opens but doesn't load, you can see like a little clock with the hand turning clockwise and says loading. but it never does, a few of the others i tried would open up and start to play and then it would stay "stopped" therefore doing nothing. then i tried a few others and they would play, go figure. i was trying to listen to the nascar race but couldn't on any of the stations listed at radiotime.com for the motor racing network. i went to the nascar website and there was a link there for IMS radio, i've got it playing as i'm typing this, no problems.

---

### Post by nikgare on 2008-07-29
You could create another user on you system, and then try the streaming radio with this new account to see if this works.
This would be using a default config, and if this works better, would indicate that there is something in your configs that is stopping the radio streaming.

---

### Post by uzzo2 on 2008-07-29
> **nikgare said:**
> You could create another user on you system, and then try the streaming radio with this new account to see if this works.
This would be using a default config, and if this works better, would indicate that there is something in your configs that is stopping the radio streaming.
ok, tried switching users, went on my wife's user and it still did the same thing.

---

### Post by David Oxland on 2008-07-29
I'm facing much the same problem;
[http://www.cbc.ca/listen/streams/r1_vancouver_32.html](http://www.cbc.ca/listen/streams/r1_vancouver_32.html)
opens downloads for about one second and then says STOPPED

---

### Post by nikgare on 2008-07-30
> I'm facing much the same problem;
[http://www.cbc.ca/listen/streams/r1_vancouver_32.html](http://www.cbc.ca/listen/streams/r1_vancouver_32.html)
opens downloads for about one second and then says STOPPED

This is another problem, but you can work around this by copying the url from the mplayer plugin, and then pasting it into totem.
This works for me here - I have the totem-xine backend, but it presumably works just as well with the gstreamer backend

---

### Post by wheezer on 2008-09-01
I am having the same problem.  I installed  the Mplayer packages for mozilla.  When i try to load the stream from radiotime.com, the firefox3 page opens, and it starts buffering, and then just says "stopped"

[http://www.progressivetalk1260.com/cc-common/streaming_new/index.html?refreshed=yes](http://www.progressivetalk1260.com/cc-common/streaming_new/index.html?refreshed=yes)

When it comes to multimedia, Linux sure ain't exactly plug and play. It' salways something like this.

Any advice, deeply appreciated.

---

### Post by uzzo2 on 2008-09-01
> **wheezer said:**
> I am having the same problem.  I installed  the Mplayer packages for mozilla.  When i try to load the stream from radiotime.com, the firefox3 page opens, and it starts buffering, and then just says "stopped"

[http://www.progressivetalk1260.com/cc-common/streaming_new/index.html?refreshed=yes](http://www.progressivetalk1260.com/cc-common/streaming_new/index.html?refreshed=yes)

When it comes to multimedia, Linux sure ain't exactly plug and play. It' salways something like this.

Any advice, deeply appreciated.
I never really did get this problem solved with mine, some stations will work and some won't. Luckily i was able to go directly to the nascar website and listen in to the races which was all i was after anyway, good luck.
It may actually be a problem with firefox, you can try [www.mozilla.com](www.mozilla.com) and look through their knowledge base and forums to see if you can find anything about it.

---

### Post by freeediver on 2009-08-13
And my radio player has been working and just stopped today.
I did a Ffox update last night, any idea where I should be looking for the problem?

---

