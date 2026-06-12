---
title: "Rhythmbox crashes in XFCE"
date: 2008-11-15
forum: Multimedia Software
---

### Post by whitefang5412 on 2008-11-15
Exactly what the thread title says. When I run Rhythmbox from the terminal I get a message about missing dependencies or something. Any idea's guys? Banshee did the same thing, but I'd rather be using rhythmbox so lets stick to that.

```
travis@travis-laptop:~$ rhythmbox

(rhythmbox:16223): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

(rhythmbox:16223): Gtk-WARNING **: AudioCdSourcePopupCopyCd: missing action MusicAudioCDDuplicate

(rhythmbox:16223): Gtk-WARNING **: AudioCdSourcePopupCopyCd: missing action MusicAudioCDDuplicate

]
```

---

### Post by whitefang5412 on 2008-11-15
Aaannnyyy ideas?

---

### Post by whitefang5412 on 2008-11-15
You folks are a lot of help.

---

### Post by tgalati4 on 2008-11-15
Try running:

>rhythmbox --debug

Try deleting your rhythbox database; it may be corrupted.

Forums are busy.  Patience is helpful.

---

### Post by whitefang5412 on 2008-11-15
The debug didn't work, and how do I delete the data-base?

---

### Post by whitefang5412 on 2008-11-15
Anymore idea's?

---

