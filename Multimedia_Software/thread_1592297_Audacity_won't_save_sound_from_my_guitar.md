---
title: "Audacity won't save sound from my guitar?"
date: 2010-10-10
forum: Multimedia Software
---

### Post by randomAccess on 2010-10-10
Following this guide ([http://www.youtube.com/watch?v=YXIFi2LPQp0](http://www.youtube.com/watch?v=YXIFi2LPQp0)) I installed Jack Control, Rackarrack and Audacity. I start Jack Control, connect it to jack server, start Rackarrack, set Audacity receive sound from Rackarrack and output it to system. All this goes well, but when I press record button on Audacity, I hear nothing (the guy in this video gets very nice sound :( ).

I tried increasing Line in sound to the limit I hear a horrible creek sound in speakers. All in vain.

Anyone might know where I'm making mistake? :(

I have Ubuntu 10.04 x64 and Asus P5k motherboard. I connect guitar via Line in port.

---

### Post by cchhrriiss121212 on 2010-10-10
Audacity does not work so well with jack normally, and according to some other poster on here audacity no longer has 64bit jack support. I suggest you try out Qtractor which is far more capable.

---

### Post by randomAccess on 2010-10-11
I tried it, but still no sound. Then I found this sentence on Qtractor site
> Target platform is Linux, where the Jack Audio Connection Kit (JACK) for audio...

Could it be the problem with Jack? I have no problem connecting it to a jack server. :confused:

---

### Post by cchhrriiss121212 on 2010-10-11
If you can hear rakarrack through jack, then jack is not the problem. I don't know what you mean when you say no sound, can you hear your input when you monitor the track, or is it that nothing gets recorded?
You should install ubuntu-restricted-extras if you haven't, as this may be a missing codec (wav is default recording codec) issue.

---

### Post by randomAccess on 2010-10-11
> **cchhrriiss121212 said:**
> If you can hear rakarrack through jack, then jack is not the problem. I don't know what you mean when you say no sound, can you hear your input when you monitor the track, or is it that nothing gets recorded?
You should install ubuntu-restricted-extras if you haven't, as this may be a missing codec (wav is default recording codec) issue.

When I "play" on guitar, I do not hear anything nor I can save anything. ubuntu-restricted-extras are installed from ages :).

Am I doing the right with Qtractor: add new audio track, enable record under the track name, press record button, give session name and save it ?

---

### Post by cchhrriiss121212 on 2010-10-11
If you cannot get input>rakarrack>output to work then forget about recording for the time being, as the problem is with your line-in and not jack or any other software.

Can you test your line-in without using jack? Just try audacity or something simple.

---

