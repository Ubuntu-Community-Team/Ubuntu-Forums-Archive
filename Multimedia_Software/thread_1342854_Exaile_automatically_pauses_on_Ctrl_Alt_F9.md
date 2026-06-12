---
title: "Exaile automatically pauses on Ctrl Alt F9"
date: 2009-12-01
forum: Multimedia Software
---

### Post by asktoby on 2009-12-01
I run Xubuntu, with two concurrent graphical logins on Ctrl Alt F7 and Ctrl Alt F9, for me and my wife.
When Exaile is playing on my login (F9) and I issue Ctrl Alt F7 to go to my wife's side, Exaile automatically pauses until I issue Ctrl Alt F9 and come back to my side.
Is there a way to stop this happening, so my music continues to play?

---

### Post by asktoby on 2009-12-16
I was using Pulseaudio.

I tried changing it:

[list]
[*]Pulseaudio (Pauses on switch, unpauses on return. Running from terminal, I see nothing in the output when it pauses.)
[*]ALSA (Pauses, but doesn't unpause when I switch back, and when I try to manually unpause it crashes, frozen. Running from terminal, I see nothing in the output when it pauses.)
[*]OSS (Doesn't pause - problem solved!)
[/list]

---

