---
title: "Shut up, Rhythmbox!"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Excalibre on 2007-10-28
So I've discovered Rhythmbox, and I like it a lot, except for one thing.

It won't stop playing songs.

I generally stick together a play queue when I listen to music, since I don't like random playlists and I just want to listen to whatever songs I feel like at the moment, or queue up one album, or whatever. But when it gets to the end of the queue, I'd like it to stop playing. Instead, it just starts playing something else! It's usually the first album listed by some artist I've listed to recently, but there doesn't seem to be any rhyme or reason to whether it picks the same artist as the song it just played or something else.

At any rate, I'd just like it to stop playing when it finishes the play queue, instead of randomly playing something else. I can't find a setting for it. Any ideas?

---

### Post by anubhavrocks on 2007-10-28
In the menubar,uncheck 

```
Control->Repeat
```

---

### Post by Excalibre on 2007-10-28
It's not checked. And, uh, if you read my post, it's not repeating.

---

### Post by anubhavrocks on 2007-10-28
I just put a play queue and after it finished the player stopped.In fact after each song is played it vanishes from the playlist.

---

### Post by Excalibre on 2007-10-28
Like I said in my first post, it's not repeating the songs from the queue. It's randomly playing other stuff when it's done.

---

### Post by anubhavrocks on 2007-10-28
What i said was ,it _stops_ after the queue is complete.I put songs in the queue  by dragging and dropping from Album List.If that helps.

---

### Post by Excalibre on 2007-10-28
Right. And what I said was that on my machine, it DOESN'T stop when the queue is empty. That's the reason I posted this in the first place.

---

### Post by anubhavrocks on 2007-10-28
Can you post the output of 
```
lsb_release -a
```

---

### Post by Excalibre on 2007-10-28
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

```

---

### Post by anubhavrocks on 2007-10-29
You can try one thing,create a new user and try Rhythmbox,if it behaves the right way,most probably you can just purge your Rhythmbox conf.

---

### Post by Sensenseppl on 2007-10-29
If I haven't misunderstood Excalibre, I think what he meant is the following, default, rhythmbox behaviour, that occurs if you follow those steps:
1. listen to music _without_ using the playlist
2. create a playlist and listen to those songs
3. rhythmbox continues playing where you were last listening to music _without_ using the playlist (step 1)

Since I like that kind of behaviour, I have no idea on how to turn it off, but probably this step-by-step explanation helps to clarify what the problem is.

My guess is that there needs to be a checkbox somewhere that controls that behaviour - no need to mess with users/configs.

greetings,
Sensenseppl

---

### Post by anubhavrocks on 2007-10-29
Okay got it :)
So to get over your problem you should create a new playlist and let it play.Do not use the 
Play Queue.

---

### Post by Sensenseppl on 2007-10-29
I just realized I mixed up playlists and queues in my last post. Sorry!
The step-by-step refers to queues only, I don't use playlists at all.

[quote="anubhavrocks"]
Okay got it
So to get over your problem you should create a new playlist and let it play.Do not use the
Play Queue.
[/quote]

But not using a nice feature can't be the best solution, can it? :)

---

### Post by valadil on 2007-12-31
Try selecting play queue in the Library dropdown instead of library.  In my experience, leaving library open with an active play queue will run through the queue then go back to playing from the library.  If you play from the play queue it usually stops when it runs out of songs.

---

