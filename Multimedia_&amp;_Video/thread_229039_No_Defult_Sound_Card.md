---
title: "No Defult Sound Card"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by smee56 on 2006-08-03
help im only new at this but ubuntu does not pick up my sound card. can any one help me please.

Smee56

---

### Post by Sutekh on 2006-08-04
Hey smee, you could really help us diagnose this problem by telling us some simple things from your setup.

What sort of soundcard is it (make and model if you can)?

When you say it doesn't pick up your soundcard, do you mean there is an error when you try to play a sound or file (such as an 'audio channel not configured', etc) or do you simply mean that no sound plays? Or do you mean that in the System -> Preferences -> Sound menu, there is no default card listed?

You could help even further by opening a Terminal window (from the Applications -> Accessories menu) and then entering in this command at the prompt. It will list the information about your sound card, if it is detected. Please post back the output.
```
lspci | grep audio
``` Then could you also use this command
```
lsmod | grep snd
``` Which will list the sound modules loaded (if any).  Then we can check if the correct modules are loaded.

---

