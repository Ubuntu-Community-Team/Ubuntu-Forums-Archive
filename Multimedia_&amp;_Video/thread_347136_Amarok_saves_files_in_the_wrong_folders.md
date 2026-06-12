---
title: "Amarok saves files in the wrong folders"
date: 2007-01-26
forum: Multimedia &amp; Video
---

### Post by Lord Of The Dance on 2007-01-26
I use Amarok to play music in Ubuntu, and itunes in windows, but I use the same music files.
The problem is that Amorak saves my music in the form *"/artist/album (disc #)/title"* and itunes  *"/artist/album/title"*. 

Is it possible to remove the disc number from the path that Amarok saves music in?

---

### Post by Buck2348 on 2007-01-26
Right-click on a track. Choose Manage Files --> Copy Track to Collection.  Click on Details >>
Under "File Naming Scheme" select "Custom Format."   In "Filename Format" I suggest you  write down or save the string that is there before changing it, then delete { (Disc %discnumber)} and see if that fixes it.

Buck

---

### Post by Lord Of The Dance on 2007-01-26
Thanks, that fixed it.
Though I feel a little stupid for not noticing the custom format box.

---

