---
title: "MP3 player doesn't appear in Rhythmbox"
date: 2008-11-09
forum: Multimedia Software
---

### Post by pumex1990 on 2008-11-09
Hi,

always if I plugged my MP3 player (sansa M240) in, when I opened Rhythmbox I had it's icon on the list at left, and I was able to drag&drop files from my music collection directly do the mp3 player.
But since I've got Ubuntu 8.10 I don't have the player on the list in Rhythmbox, although, I have it mounted, and I can normally open it and use from the icon on the desktop.

How can I make MP3 player visible in Rhythmbox?

---

### Post by cobalaminco on 2008-11-12
i have the same problem, 

with hardy i would plug my creative zen and it would appear at the left pane. It was possible to move files in there and the program understood that the files were in the mp3 memory and after unmounting it it wouldn't say Missing Files, now it does.

What's going on?

Thanks

---

### Post by spamking2000 on 2009-01-07
Well.... I know I'm not much of a help... but I'm having the same problem too. I have a Sansa e260 and its always worked great (MSC mode). I just tried it on my Hardy box and now it doesn't show up. It automounts, I can access the files via Nautilus, but Rhythmbox wouldn't see it.

So..... ran it over to the 8.10 machine and it loaded up just fine.

Brought it back to the Hardy box, plugged it in and now I get import errors off the Sansa where it gives the "Mime type not recognized" errors on certain files on the Sansa, but it still doesn't show the device.

I have no idea what to do... other than to share out my music on my Hardy box and load the Sansa on the Ibex box and connect over the lan to get to my music. That's slow though... I'd rather not.

Any help would be appreciated.

Thanks!!

---

### Post by doug1212 on 2009-01-07
Not sure if this any help but there is a trick with Rhythmbox of adding a hidden file to the root of the DAP player named:

```
.is_audio_player
```

and a line in the file pointing to the music directory, something like:

```
audio_folders=MUSIC/
```

Doug.

---

