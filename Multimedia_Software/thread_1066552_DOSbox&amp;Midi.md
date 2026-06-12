---
title: "DOSbox&amp;Midi"
date: 2009-02-11
forum: Multimedia Software
---

### Post by deamon_knight on 2009-02-11
I'm using 8.10 and I'm trying to get midi effects out of dosbox. Soundblaster works somewhat (its occasionally stuttery),but I'm having no luck with MIDI. I've seen some posts about Timidity but comprehensive lost of what I have to install and how to configure it.

the last threat I found:
[http://ubuntuforums.org/showthread.php?t=618914](http://ubuntuforums.org/showthread.php?t=618914)

but its a bit dated. Some links suggest that PulseAudio is not working or want to recompile dosbox, and thats getting above my head. Anyone actually have this working?

Any advice is appreciated.

---

### Post by deamon_knight on 2009-02-11
Well, I followed the instructions here: [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)

and I think I have Timidity installed & configured properly. I can launch the Timidity player and load a *.mid file and hear the music I expect too. I also think I have dosbox configured properly to use the Timidity server.

I can also use
"pmidi -p 128:0 music.mid" from the terminal to launch midi files.



When DOSbox launched from the console I get 
CONFIG:Loading primary settings from config file dosbox.conf
ALSA:Client initialised [128:0]
MIDI:Opened device:alsa
 So I think that it is connecting to Timidity, but I don't get any midi audio. Audio configured as soundblaster through DOSbox does work normally. 

Any Ideas?

---

### Post by deamon_knight on 2009-02-11
I also found that if I use pmidi to start a midi file on port 128:0, then launch Dosbox, I get the midi music i expect from the game along with the midi file I played, however, the soundblaster sound no longer work.


The DOSbox website recommends using the alsa-oss module, and I am but it makes no difference. I'm stumped.

---

