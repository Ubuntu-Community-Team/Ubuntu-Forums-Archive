---
title: "Totem movie player won't fast-forward or rewind midi's...alternative or fix?"
date: 2017-06-09
forum: Multimedia Software
---

### Post by Dominicus on 2017-06-09
I'm running Ubuntu 16.04.

The default application that launches .midi files is Totem Movie Player.  It plays well, with very decent soundfont.
The issue is, I work on midi's incrementally, needing to review the last few seconds.
For some reason, this application doesn't provide fast-forward or rewind buttons on midi's, and won't allow me to slide the playback cursor back/forward to an arbitrary spot on the sequence.

I tried manually opening midi's with Rythmbox with similar results: no FFW/RWD and, although it lets me slide the playback cursor, the change doesn't stick...just springs back to the same location.

Is there an alternative lightweight midi player that allows the user to slide to a specific timespot in a midi sequence?

Thx!

---

### Post by Dennis N on 2017-06-10
> Is there an alternative lightweight midi player that allows the user to slide to a specific timespot in a midi sequence?

Audacious can jump to specific time or you can click on or drag the position slider to any spot. Configure the AMIDI plug for the location of the soundfont and you are set to go.

---

### Post by Dominicus on 2017-06-10
Installed Audacious, then found the location of the *.sf2 soundfont file, opened the plug-ins dialog, selected AMIDI plugin, went to its Settings..., added the soundfont location.
Perfection!
Not only can I now move to arbitrary timespot, but noticed another benefit: when the MIDI generator updates the MIDI file I'm working on, I don't need to relaunch the MIDI player to play the updated file, which I had to do with Totem player.  Just stop/play again, and Audacious plays the revised file.
It's a thing of beauty.
Much appreciated!

---

