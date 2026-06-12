---
title: "starting mpd without sudo?"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by mailbox on 2007-11-19
How can I alter mpd so that I don't need to put sudo at the beginning of 'sudo /etc/init.d/mpd start' in order to start mpd?
I'm having problems with mpd locking my soundcard so that other players like totem and vlc lock up when playback ends, and i'm fairly confident this will fix it.

---

### Post by mailbox on 2007-11-19
Bump.
Anyone?
Even if it can't be done, let me know, so I don't think this is a dead forum.

---

### Post by Mithrilhall on 2007-11-19
Chown it?

```

chown -v yourname:yourname mpd

```

Does that work for you?

---

### Post by mailbox on 2007-11-19
> **Mithrilhall said:**
> Chown it?

```

chown -v yourname:yourname mpd

```

Does that work for you?

I tried that earlier, but without the -v (what does that do?), and it returned "ownership of `mpd' retained as dissonance:dissonance", then this:```
dissonance@iridium:~$ /etc/init.d/mpd start
Starting Music Player Daemon: cannot setgid for user "mpd" at line 35: Operation not permitted
failed.
```

---

### Post by Mithrilhall on 2007-11-19
My bad...I forgot the sudo.

```

sudo chown yourname:yourname mpd

```

The v is for verbose.

---

### Post by mailbox on 2007-11-19
> **Mithrilhall said:**
> The v is for verbose.

Ah, okay.
Well, same result.
I'm supposed to be changing the ownership of /etc/init.d/mpd, correct?

---

### Post by Mithrilhall on 2007-11-19
Yep.

Is that a directory or 1 file?

If it's a directory....
```

sudo chown -Rv name:name mpd

```

---

### Post by markupstart on 2007-11-19
I usually change /etc/mpd.conf file.  One of the lines has User "mpd".  I just change that to my username.  My user name is mark, so I just change it to "mark", then sav the file, and start mpd without sudo.  It always seems to work for me.

---

### Post by Mithrilhall on 2007-11-19
That seems much better than my fix.

---

### Post by mailbox on 2007-11-19
Excellent, tried markupstart's suggestion, then Mithrilhall's to chown mpd directories... and it works!
Ubuntu forums finally come through!

---

### Post by nutter78 on 2007-11-20
I've just got this to work - really great!!!! :)
only problem is that mpd is reading from /etc/mpd.config io ~/.mpd.config

---

### Post by Echow on 2008-01-07
You will need to rename the ~/.mpd.config to .mpdconf then it shuold work.

---

