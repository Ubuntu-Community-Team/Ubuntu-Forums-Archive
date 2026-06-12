---
title: "Rosegarden render output to Audio CD?"
date: 2008-02-19
forum: Multimedia Production
---

### Post by beebeeee on 2008-02-19
Ok, I thought after installing flac, I'd be able to export/render the audio stream from rosegarden to a flac file. no such luck it seems.

How do you render the output from rosegarden to a: flac/wav/? file so I can burn it to an audop CD?

---

### Post by eric71 on 2008-02-20
The easiest way is to make a new audio track and set its input as "master". Set it to record and it will mix everything down into a new audio track. Double click on the new audio track and it will open the wav file in your default editor (I use Audacity). From there, save it as any file type you like, flac, ogg etc.

---

### Post by beebeeee on 2008-02-20
ok thanks... the old bounce down trick.

---

### Post by indecisive on 2008-03-12
I recorded my song into a master track, but neither Rosegarden nor Audacity recognize any sound in it.  Any suggestions?

---

### Post by robeast on 2008-03-14
Are you routed your signals correctly into the master track? Can you see a waveform or is it just blank?

---

### Post by indecisive on 2008-03-18
I am not sure if I have routed the signals correctly, though the waveform is just a straight line.

---

