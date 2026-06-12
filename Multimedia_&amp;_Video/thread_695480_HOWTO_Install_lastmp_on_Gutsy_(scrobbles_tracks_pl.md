---
title: "HOWTO: Install lastmp on Gutsy (scrobbles tracks played in mpd to Last.fm)"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by Emblem Parade on 2008-02-13
The lastmp package installs two little daemons that together scrobble anything played with mpd to Last.fm.

Unfortunately, the Gutsy Gibbon and Hardy Heron (beta) packages each break the necessary connections between these two daemons, in different ways.

The following should fix this.

Gutsy:

```

sudo chgrp lastfm /var/spool/lastfm
sudo chmod g+w /var/spool/lastfm
sudo /etc/init.d/lastmp restart

```

Hardy (beta):

```

sudo mkdir /var/run/lastfm
sudo chgrp lastfm /var/run/lastfm
sudo chmod g+w /var/run/lastfm
sudo /etc/init.d/lastmp restart
sudo /etc/init.d/lastfmsubmitd restart

```

---

### Post by chochem on 2008-02-13
My submissions still aren't getting through. But the last.fm site seems pretty sluggish too. And the recent tracks have been hidden away... :confused:

---

### Post by Emblem Parade on 2008-02-13
Here's how I debugged it.

First, stop both daemons:

```
sudo /etc/init.d/lastmp stop
sudo /etc/init.d/lastfmsubmitd stop
```

Then, start each of them manually, as non-daemons, with debug output, preferably in separate terminals:

```
sudo lastmp -d -n
sudo lastfmsubmitd -d -n
```

With the terminal open, you'll be able to see their debug messages. This is how I found out that lasmp did not have the right access privileges for lastfmsubmitd's spool.

If you solve your problem, please post the solution here!

---

### Post by chochem on 2008-02-13
Thanks for replying (and for the original post too - just in time :) ) I'm sorry for the inconvenience - I just check last.fm and we're back up! Must have been the web site or something because it also lists the songs I was playing earlier today just to check up on it...

EDIT: Found this note on last.fm
> Some tracks you submitted have not been added to your profile for the following reason:
Spam protection triggered: You submitted a track dated earlier than your last submission. 
Hopefully it was just a hickup - gonna close it and see if it comes back on. 

MPC/MPD is truly excellent. I'm starting to believe I don't even need a frontend anymore.... BTW I know this is off-topic but you wouldn't happen to know how to start and terminal and pass a command to it? The Xfce4-terminal has an option (-e <command> ) but it'll immediately shut the terminal down again which is no good if you want status or playlist...

---

