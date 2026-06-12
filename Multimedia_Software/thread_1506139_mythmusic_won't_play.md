---
title: "mythmusic won't play"
date: 2010-06-10
forum: Multimedia Software
---

### Post by gunterhausfrau on 2010-06-10
From the import music menu, I can add music, and once selected can play a song, but once imported, whenever I try to play a song (from the normal menu item) I can select, it shows the correct song length, but it just sits there waiting to start. The log shows this.

"AV decoder. Error: -2"

Why would one portion of the program play and another have an issue. I've played with permissions, didn't seem to help.

Rhythmbox seems to work just fine on the same files.

Thanks.

update:
not sure what I did, but it seems to be working. I went over the FAQ about what to do if no sound, did a few of the suggestions, but the only things that makes sense (granted to me, maybe not the best source of sense) is that I added a user to the audio group? or maybe it was Getting more than one application to use the soundcard at the same time?

either way, seems to work. I hope this helps someone else who has this problem.

---

### Post by picbits on 2010-06-11
I'm getting the same problem

Music is stored on the backend with a symbolic link to my music directory - I get the error -2. I can listen to the music on MythWeb 

If I copy the music directly to my backend /var/lib/mythtv/music directory I get the same problem

If I copy the music to the /var/lib/mythtv/music  frontend directory it will play fine.

The frontend recognises the backend music is present but refuses to play it.

If I get anywhere with it I'll let you know.

---

### Post by siabost on 2012-01-09
Hey gunterhausfrau

Thanks.

I was getting "AV decoder. Error: -2" also.

Adding myself as a user to the "Audio" group did the trick :-)

Try the same picbits, it should work.

Good Luck. :D

---

### Post by picbits on 2012-01-11
> **siabost said:**
> Try the same picbits, it should work.

Good Luck. :D

I solved my problem by mapping a network drive via SMB to the same place on the frontends as on the server.

When I build a new frontend I might try the solution mentioned above :)

---

