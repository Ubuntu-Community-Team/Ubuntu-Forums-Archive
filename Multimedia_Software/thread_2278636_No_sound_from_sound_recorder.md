---
title: "No sound from sound recorder"
date: 2015-05-18
forum: Multimedia Software
---

### Post by bobmac on 2015-05-18
Folks,

I've been trying to copy music from an Internet radio station. The Sound Recorder appears to copy OK, and I seem to be able to save the file. However, when I try to play the file, the Sound Recorder, VLC, etc, all appear to be running the file but there's no sound from my speakers.

Can anyone give me a clue as to what I'm doing wrong

Regards,

Bob

---

### Post by ajgreeny on 2015-05-18
What sound-recorder are you using?  There is no package called sound-recorder, only audio-recorder.

If you are using audio-recorder have you checked the settings to see it is monitoring and recording the right source, as in my screenshot?

---

### Post by bobmac on 2015-05-19
ajgreeny,

I'm running version 12.04. The default recorder seems to be named Sound Recorder (see attachment).
I've also included an image of the default sound system in use[ATTACH=CONFIG]262060[/ATTACH][ATTACH=CONFIG]262061[/ATTACH]

---

### Post by ajgreeny on 2015-05-19
Sorry but I can't help with sound-recorder as I never used it even when I had 12.04.  Audio recorder was available then for 12.04 and was far better than sound-recorder, in my opinion.

Enable the ppa at [https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder](https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder) and then install it to see if that helps.

---

