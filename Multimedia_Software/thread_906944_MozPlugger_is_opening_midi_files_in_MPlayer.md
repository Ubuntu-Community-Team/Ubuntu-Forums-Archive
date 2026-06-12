---
title: "MozPlugger is opening midi files in MPlayer"
date: 2008-09-01
forum: Multimedia Software
---

### Post by Johnny K on 2008-09-01
Firefox handles .mid files with MozPlugger. My /etc/mozpluggerrc file has the following lines:
```
audio/mid:midi,mid:MIDI audio file
audio/x-mid:midi,mid:MIDI audio file
audio/midi:midi,mid:MIDI audio file
audio/x-midi:midi,mid:MIDI audio file
	controls noisy stream: timidity -Od "$file"
	controls: playmidi "$file"
```

However, when I visit a website that tried to load a .mid file in the background I get an error from Gnome MPlayer saying that it cannot open the file.

Does anyone know why this could be? I know plenty of people have had problems with background midi files in the past.

---

