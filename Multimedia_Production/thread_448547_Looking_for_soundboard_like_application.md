---
title: "Looking for soundboard like application"
date: 2007-05-19
forum: Multimedia Production
---

### Post by digglah on 2007-05-19
Hi

I am looking for a tool/app that lets me cue sound effects/songs/etc that can play just by pushing a button
i also want it to be able to output to JACKD because i wanna do some live recording

anyone know of that kind of app?

---

### Post by drosky on 2007-05-19
> **digglah said:**
> Hi

I am looking for a tool/app that lets me cue sound effects/songs/etc that can play just by pushing a button
i also want it to be able to output to JACKD because i wanna do some live recording

anyone know of that kind of app?

My memory is a little sketchy on this, but one time I had a similar requirement to cue background sound effects when I was doing the sound for a play.  There was a lot going on in the play, and I wanted to be able to just hit a single keys to start specific sound effects.  At the time I couldn't find any normal GUI-based player that would let you assign specific keyboard keys to play specific tracks. What I ended up using was a combination of MPD and xbindkeys.

MPD is a music player daemon that runs in background using standard playlists you create, and it can be controlled with a client program, MPC, which controls the MPD daemon.  The control client is quite versatile and can do various things including telling MPD to play specific entries in the playlist.

Xbindkeys is a small daemon that allows you to assign any key to a command.  So, the idea is to use xbindkeys to assign keys to commands that tell MPD to play the specific tracks you want by typing those keys.  I don't remember all the details of setting it up at the moment, but it should be fairly clear from the documentation for MPD and xbindkeys.

Dave

EDIT: Forgot to mention, I don't know for sure if MPD works with Jack.  I believe it was being worked on, but don't know if it's fully functional yet.

---

### Post by digglah on 2007-05-20
Thanks! Will check that out.

Now i just have to fix jack... its broken down on me :(
i have a thread up about [here]("http://ubuntuforums.org/showthread.php?t=449359")

---

### Post by kayosiii on 2007-05-24
freewheeling in singleshot mode works fairly well for this... You need to have the sounds preloaded in. Which means recording them in.

Freewheeling supports using a joysticks as input devices they need to be configured. I have done a show where I used a dancemat as a trigger board for sound fx... unfortunately the singleshot mode is broken last time I check
but It performed admirably.

---

