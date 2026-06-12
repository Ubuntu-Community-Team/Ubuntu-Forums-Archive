---
title: "play multiple files with the default application"
date: 2019-04-03
forum: Multimedia Software
---

### Post by daroba on 2019-04-03
Hello everyone, something very funny happens to me.
To play music I usually browse my folders with nautilus, select several audio files from a folder and press Enter.

Well, I have tried several players (audacius, mpv, ...) and the following happens to me: if they are not the default application (right click, open with ..., I choose the player) they load the playlist perfectly and begin to play the first file. As it should be.
But if the same application I put it as the default application (select files and press enter): I do not load the list of audio files, just load one, the last one. That is, one track is superimposed on another and in the end only the last remains.

Any idea how I can fix this? Thank you.

---

### Post by huff2 on 2019-04-03
What is your default player right now?

---

### Post by daroba on 2019-04-03
the same thing happens to me with audacius as with mpv

It also happens to me since I installed ubuntu 18.04.
Before with 14.04 I did not have any problems, I used totem. Now totem makes me the same as these and also I do not see the playlist anywhere

Thank you

---

### Post by mc4man on 2019-04-07
Works fine here in 18.04 with all 3 players mentioned, i.e when they are default for a file type a shift click on some files > enter opens the player with all the files selected loaded.
(totem doesn't have a 'playlist' anymore, just next and previous buttons.

For mpv, after selecting some files > enter, does F8 show anything?

---

### Post by daroba on 2019-04-08
Looking at more forums and doing checks I have seen what the problem is. It is not from the player.
Let's see:
- Ubuntu 18.04 just installed.
- Audacious as default player
- If I select several music files in Nautilus and press enter (or right mouse button, "Open") just load a song. That is, open multiple instances, one with each song, and keep the last.
- But if I select several music files in Nautilus and right click, "Open with ...", I select Audacious: load the entire list and start playing it from the beginning. As it should be.

So the problem is in the "Open" command, because "Open with ..." works fine.

In another forum, that of Audacious, I have been told:
"Okay, it looks like it's a bug in Nautilus:
[https://gitlab.gnome.org/GNOME/nautilus/issues/117](https://gitlab.gnome.org/GNOME/nautilus/issues/117) "

But I do not clarify, how to fix it?

---

