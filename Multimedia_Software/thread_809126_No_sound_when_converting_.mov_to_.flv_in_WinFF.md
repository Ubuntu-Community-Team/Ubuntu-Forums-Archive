---
title: "No sound when converting .mov to .flv in WinFF"
date: 2008-05-27
forum: Multimedia Software
---

### Post by MAJORdorMo777 on 2008-05-27
I tried converting a .mov to a .flv with WinFF and the .flv had no sound.
How would I fix this?

---

### Post by MAJORdorMo on 2008-05-27
Bump

---

### Post by FakeOutdoorsman on 2008-05-27
WinFF is a GUI for ffmpeg.  I'm not familiar with using WinFF, but I can help with the ffmpeg errors.  What errors does WinFF give you?  If it doesn't give errors, open WinFF with a terminal and it might display the errors through the terminal.

I suspect that the flv is using mp3 encoded audio, but this is a guess without seeing any errors.  FFmpeg in the Ubuntu repos has not been compiled to support restricted formats such as mp3.  You might want to try uninstalling ffmpeg and then getting the version from the [Medibuntu]("http://medibuntu.org") repo which supports restriced formats.

---

### Post by digish778 on 2008-05-27
You could use sound converter, transcode, ffmpeg etc.

You can find the commands for converting to flv over the internet.

---

