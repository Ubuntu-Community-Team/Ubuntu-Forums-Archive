---
title: "KDENLIVE sound waveforms?"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by Terry_Dodson on 2007-12-14
I just installed KDENLIVE on a fresh install of Ubuntu 7.10.  It looks like it works but when i drag sound (Wav or MP3) to the sound timeline i do not see the sound waveform, i do see 2 straight flat lines.  If i click on the little waveform box the lines will go away, if i click again the lines come back.  What do i need to do to get a visible waveform in the sound timeline window?

---

### Post by deadgobby on 2007-12-14
I have not used that program. I use Audacity. Have you tried that program?
Gobby

---

### Post by Terry_Dodson on 2007-12-14
I was wanting to use it for some movie editing, and i wanted the waveforms so i would know where to setup different frames and things.

edit:  I also installed Cinelerra and it shows the waveforms but i have not really used it yet.  I wanted to use KDENLIVE because it seemed simpler for what i wanted to do.

---

### Post by cowanh00 on 2007-12-16
I've just noticed that there is a button to turn on the waveforms in Kdenlive. Down in the left hand corner the 4th button says 'Show Audio Thumbnails' when you hover over it. This will turn on the waveforms.

I hope this helps!

---

### Post by Terry_Dodson on 2007-12-16
I have pressed it.  When it is active i get 2 flat sraight lines in the audio timeline area (where the waveform should be), whe i click it again (to deactivate it) the lines go away.  It is like the waveorm libes are there just not lare enough to see the waveform.

---

### Post by cowanh00 on 2007-12-17
> **Terry_Dodson said:**
> I have pressed it.  When it is active i get 2 flat sraight lines in the audio timeline area (where the waveform should be), whe i click it again (to deactivate it) the lines go away.  It is like the waveorm libes are there just not lare enough to see the waveform.

Oh yeah. Should have read your post fully!! ;) I tried it for myself and it worked with MP3s.

---

### Post by Terry_Dodson on 2007-12-17
I have tried it with mp3's and WAV files and i get the same with both.  Could there be something else i need to install to get it to work?  Cinelerra DOES show waveforms on the same wav's and mp3's.

---

### Post by cowanh00 on 2007-12-17
> **Terry_Dodson said:**
> I have tried it with mp3's and WAV files and i get the same with both.  Could there be something else i need to install to get it to work?  Cinelerra DOES show waveforms on the same wav's and mp3's.

Do you have the extra Audio effects enabled? There were 3 extra packages to install that give you extra Audio effects, perhaps installing these will show you the wavelines?

Try installing these:
[LIST]
[*]ladspa-sdk
[*]libjack-dev
[*]swh-plugins
[/LIST]

---

### Post by Terry_Dodson on 2007-12-17
Thanks.  Yes those 3 are installed.

---

