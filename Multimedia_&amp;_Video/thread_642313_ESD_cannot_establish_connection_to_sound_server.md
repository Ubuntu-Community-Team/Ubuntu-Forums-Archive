---
title: "ESD cannot establish connection to sound server"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by Shrooms on 2007-12-16
Hello everybody!

Got started with Ubuntu 7.10 64-Bit (AMD). Now, (nearly) everything works fine. No major problems. But there are still these small ones... which drive you mad, if you don't deal with them soon ^^

So, i customized everything a bit, also the sounds in the sound preferences ("System > Preferences > Sound", Tab "Sound"). But mostly, I don't hear anything from them! Just the Log-In and Log-Out Sound. Except for marking a checkbox, every event has an associated wav file. I also can listen music etc., but when error messages pop up, the sound misses.
On top of the tab, you habe to turn on "Enable software sound mixing (ESD)". It's enabled, of course. But if I try to choose the ESD Mixer and click "test" in the Tab "Devices" for every option, i get that:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not establish connection to sound server

Does anyone know, what's wrong? 0o

---

