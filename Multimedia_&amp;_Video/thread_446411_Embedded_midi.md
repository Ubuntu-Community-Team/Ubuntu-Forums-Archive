---
title: "Embedded midi"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by KoRnholio on 2007-05-16
Embedded midi is not working on Feisty.  Timidity plays all midis fine, but after installing mozplugger, they do still not play on any sites.  Here is the relavent output from ps -ax when a midi file is encountered: 

19059 ?        Sl     0:23 /usr/lib/firefox/firefox-bin
19142 ?        Ss     0:00 mozplugger-helper 7436,2147483647,62,0,0,0,0,0 timidity -Od "$file"
19143 ?        S      0:00 mozplugger-controller timidity -Od "$file"
19199 ?        S      0:00 /bin/sh -c timidity -Od "$file"
19200 ?        S      0:00 timidity -Od [http://www.visionmusic.com/members/jamtracks/jazz/dayswine.mid](http://www.visionmusic.com/members/jamtracks/jazz/dayswine.mid)

---

Downloading a midi file, and running it in the terminal with those same options - timidity -0d, does work.
Would it have to do with the fact that thats a members-only site, with the midi files directly password-protected?  I do of course have an account, and login fine - but that might be throwing a wrench into mozplugger?

---

### Post by silhouette on 2007-05-21
I have the exact same problem. I am positive that Timidity works outside of Firefox, but inside is another story. I have tried editing /etc/mozpluggerrc so that it calls Timidity with "-id" (dumb interface) thinking that maybe the ncurses interface is interfering with its playing correctly, but this seemed to do nothing.

---

### Post by silhouette on 2007-05-21
Okay, I think I may have found a solution. Try this - open a terminal window and enter

```
sudo nano /etc/mozpluggerrc    # or, sudo gedit /etc/mozpluggerc, if you like a GUI
```

Then, look for the following lines:

```

audio/mid:midi,mid:MIDI audio file
audio/x-mid:midi,mid:MIDI audio file
audio/midi:midi,mid:MIDI audio file
audio/x-midi:midi,mid:MIDI audio file
        controls noisy stream: timidity -Od -id "$file"
        controls: playmidi "$file"

```

Change

```
controls noisy stream: timidity -Od "$file"
```

to just

```
noisy stream: timidity -Od "$file"
```

The "controls" flag is telling Firefox to render stop, play, etc. buttons, but it only works if the MIDI is playing via an <EMBED> tag (or so sez the man page). You don't normally see that sort of thing anymore, so IMO it's kind of pointless to have the flag in at all. If you still want that, though, I suppose you could add another line instead of changing the line.

HTH...

---

### Post by System16 on 2007-05-28
This worked perfectly for me with the extra step that I had to add my HTTP proxy to Timidity's config file.  So if you're running through a proxy:

```
sudo vi /etc/timidity/timidity.cfg
```

and add this line to it:

```
#extension HTTPproxy proxy:port
```

---

