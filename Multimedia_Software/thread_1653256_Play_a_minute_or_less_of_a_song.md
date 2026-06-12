---
title: "Play a minute or less of a song"
date: 2010-12-26
forum: Multimedia Software
---

### Post by meho_r on 2010-12-26
Hi.

I'm sure I've seen in a player the option to play only first minute of songs in a playlist, but cannot remember which one that was. Any ideas?

---

### Post by meho_r on 2011-01-01
A... bump? :D

---

### Post by loell on 2011-01-01
I assume you're using the default player? Rhythmbox?

in **music** menu --> playlist --> New Automatic Playlist --> Add criteria

---

### Post by meho_r on 2011-01-02
Thanks for the idea. However, I still haven't been able to make this working. Just to avoid misunderstanding, what I want to do is the following:

1. Add couple of songs to a playlist
2. Play only a minute of the first song, then automatically switch to the next one, play a minute of the second song then switch to the third etc. So, I don't want to listen to full songs, but only first minute of every of them.

It is not important if the player is Rhythmbox or any other.

---

### Post by meho_r on 2011-01-03
A non-GUI solution would be the following:
```

mpg123 --list name_of_a_playlist --frames number_of_frames

```

Another potential solution would be Audacious with song change plugin, but I have no idea how to use it for this purpose.

---

### Post by mc4man on 2011-01-03
> Audacious with song change plugin
I suspect you could use that, how well would depend on the command set (script) and whether aud is opening your files (playlist ) in a playlist or temporary playlist. (could never quite figure that difference out

The other thing would be that w/ a simplistic script the last track would always play fully, there isn't any setting in the plugin specifically for last track

So a simple script to maybe get you going, in the plugin preference you'd add the path to it in the top box (when aud starts new song

(I use a bin in home folder so just added the script name

One could be like this
```
#!/bin/bash
sleep 60 && audacious --fwd
```

or another way (w/ xdotool installed
```
#!/bin/bash
sleep 60 && xdotool search --name audacious  key b
```
Seems to work fine (exception last track) when going either File - add files or a right click on a folder - open with audacious

(the plugin may not be used when restarting an existing playlist in a current open audacious
With a more extensive script you may be able to idenify the last track and end with a v key command after x sec's

---

### Post by meho_r on 2011-01-03
Thanks a lot, this was very useful.

---

