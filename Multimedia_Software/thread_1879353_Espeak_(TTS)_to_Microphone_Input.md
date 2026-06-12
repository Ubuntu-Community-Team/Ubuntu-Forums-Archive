---
title: "Espeak (TTS) to Microphone Input"
date: 2011-11-11
forum: Multimedia Software
---

### Post by Bob535 on 2011-11-11
I can't seem to find a thread directly on this issue.

I've lost my voice (sick) but would still like to be able to speak on voice chat. I've got espeak running, which lets me type and then it reads it, I'm just trying to find a way to route that information to my microphone input.
 
It would be nice if it would also play to my headset as it went out.
It would be nice if it was something I could easily turn on/off.
An additional bonus would be being able to play pre-recorded sounds.

Any help? I assumed this would be possible just based on accessibility tools.

---

### Post by Yumi on 2011-11-15
I found two hardware suggestions, basically connecting the speaker-port to the mic-port. See:

[http://answers.yahoo.com/question/index?qid=20080214114537AAT7zHy]("Answer 1")

[http://answers.yahoo.com/question/index?qid=20100511215923AAxHNX6]("Answer 2")


But I also have a question of my own. How did you manage to install espeak? I did so but get the error:

> Wrong version of espeak-data at:
/home/michael/espeak-data
Version 0x14500 (expects 0x14300)

Obviously the program file and the data file do not match. Any other source to download and install then ubuntu repositories?

Michael

---

### Post by WasMeHere on 2011-11-15
> **Yumi said:**
> I found two hardware suggestions, basically connecting the speaker-port to the mic-port. See:

[http://answers.yahoo.com/question/index?qid=20080214114537AAT7zHy]("Answer 1")

[http://answers.yahoo.com/question/index?qid=20100511215923AAxHNX6]("Answer 2")


But I also have a question of my own. How did you manage to install espeak? I did so but get the error:



Obviously the program file and the data file do not match. Any other source to download and install then ubuntu repositories?

Michael

Hi!

Interesting usage of espeak! I use it for a speaking clock. And I have downloaded it from the repositories
```
sudo apt-get install espeak
``` If that creates problems for you, it might be because your locale (language etc) is not supported.

Having fun finding out :-)
Olle

---

