---
title: "No red record button on vlc"
date: 2012-12-03
forum: Multimedia Software
---

### Post by Ben Aur on 2012-12-03
I'm trying to record internet streams and other pc activity on vlc. I've got 'view->advanced controls' selected as recommended but the record button is still grey and inactive. Any tips?

---

### Post by moma on 2012-12-03
Hello,
Can you try with a local music file. Start playing and the rec-button should get active.
Google also for <VLC record stream>.

[SIZE="2"]You can also record with ... audio-recorder.
[http://ubuntuforums.org/showthread.php?p=12306562](http://ubuntuforums.org/showthread.php?p=12306562)[/SIZE]

VLC can control the recorder if you select:
Preferences -> all:  Interface -> Control Interface -> [x] Dbus-Control Interface.
This activates the player's DBus-interface and it will send messages to the audio-recorder.
All major media players comply to [MPRIS2-standard]("http://specifications.freedesktop.org/mpris-spec/latest/") (media player standard 2) and send well defined messages to the DBus. Other apps can then pick'em and...

---

### Post by Ben Aur on 2012-12-06
Hello and thanks. Local mp3 and mp4 are recording well.
How easy is it to capture e.g. inernet videos as they play?

---

### Post by Ben Aur on 2012-12-06
... the recommended vld google search seems to have done the trick. Thanks for the help.

---

### Post by moma on 2012-12-08
That's lovely. Well done Ben Aur.
Good listening.

---

