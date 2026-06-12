---
title: "streaming live tv possible?"
date: 2008-04-27
forum: Mythbuntu
---

### Post by thafemann on 2008-04-27
Hey there,

I just got things working.  When I am watching tv on the mythbuntu server, it is able to be played with a remote myth player, right.  I did nothing and it showed up in the recordings.

I do not want to record live tv and take up the space.

Here is ultimately what I would like to to.  I would like to set 1 or 2 channels to permanently on, and be able to record other channels simultaneously.

When I turn off the TV on the server, recording stops and I can no longer watch tv.

Any suggestions?

Tom

---

### Post by dsbw on 2008-04-27
Set up the MythTV external to the TV/cable set up, and watch it with a different input.

In other words, if you're using an aerial, set up the aerial to feed directly into the TV, and set up a different feed (or feeds) into MythTV. When you want to use MythTV, switch inputs on the TV so you can see it and record or playback.

That's how I'd do it.

---

### Post by amphibem on 2008-04-28
> **thafemann said:**
> Hey there,

I just got things working.  When I am watching tv on the mythbuntu server, it is able to be played with a remote myth player, right.  I did nothing and it showed up in the recordings.

I do not want to record live tv and take up the space.

Here is ultimately what I would like to to.  I would like to set 1 or 2 channels to permanently on, and be able to record other channels simultaneously.

When I turn off the TV on the server, recording stops and I can no longer watch tv.

Any suggestions?

Tom

How much hard drive space do you have? By default mythtv auto-expires Live TV recordings after a day, and earlier if the space is required. In fact it will be the first thing deleted if you run out of space.

Other than that my expertise runs out :P

---

### Post by thafemann on 2008-04-28
Hum....

I have 500 GB of hard drive space.  I know there must be a way to just pass live tv onto the wire, or even just record it for an hour and then delete it.

Here is the issue, I do not want the "server" to have to have a channel on  in order to stream the TV.  Right now, in order to see anything that is not recorded, I have to have "watch TV" selected and that is what people are able to see.  Now, when I stop it to program it to record, the live feed goes away and people have to reconnect.

Tom

---

### Post by justanotherhack on 2008-04-29
This ain't a function of MythTV? Thought so. But maybe I'm mixing things up with LinuxMCE... or just make it up myself ;) .

Hmm... I can't try a solutions away from my HTPC, but I can cast a few ideas into space.

It should be possible to use the Live TV function outside the regular MythTV. Even if it would be running a different process.

The current stream is saved to disk in MPEG. One should be able to open it in any player while being reorded, since the format is streamable. (Basically I assume that is what MythTV does.) Maybe one could access them from another box over a shared directory. The only concern regardig the file is, that it grow permanentely. Not sure how MythTV handles this, if you don't stop the TV function. Anyway, you might have to find a way to cut or crop the file.

The VLC player (one of the possible players on MythTV) has the ability not only to watch videos, but also to stream them. You could change the setup, so that VLC is used to show and stream the current TV.

Just a few thoughts that came to my mind.

---

