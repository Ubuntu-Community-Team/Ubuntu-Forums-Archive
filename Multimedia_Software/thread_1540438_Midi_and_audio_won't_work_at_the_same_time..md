---
title: "Midi and audio won't work at the same time."
date: 2010-07-27
forum: Multimedia Software
---

### Post by zonination on 2010-07-27
Hello.

As an arranger of collegiate a cappella music, I often times need to listen to a song as I'm playing with a midi sequencer or some arranging software. On Ubuntu, since Gutsy, I've often run into the same problem from distribution to distribution:

**Midi and audio won't work at the same time.** If I have an audio file open on VLC or FireFox, I can't play Midi sequences on my arrangement. If I'm arranging and listening to Midi notes, I can't play music. Note that it's incredibly inconvenient to constantly close one so I can play the other to finish arrangements.

I've Googled my issue and it doesn't seem to come to light. I also checked the FAQ, and it doesn't say anything about multitasking the audio. Any help?

---

### Post by cchhrriiss121212 on 2010-07-28
What program(s) are you using for your midi arrangements?
Are you using jack?

---

### Post by zonination on 2010-07-30
I've started with Rosegarden 9 + Timidity to arrange. I've also used NoteWorthy in WinE with Timidity. Every time I get the same problem.

Jack is installed, but I don't know if that's all I need. Is there any specific way I need to set it up?

---

### Post by cchhrriiss121212 on 2010-07-31
I think that some sound cards do not function with more than one source when using ALSA (I say I think as mine seems to work fine). 
But you should be able to get jack doing this if you follow the steps going on [here]("http://ubuntuforums.org/showthread.php?t=1541839"). First you will need to open jack and press the start button.
[This tutorial]("http://www.youtube.com/watch?v=4QNhdygsAqg&feature=PlayList&p=6C376EDBA9489E81&playnext=1&index=11") will show you what jack can do with audio and midi.

---

