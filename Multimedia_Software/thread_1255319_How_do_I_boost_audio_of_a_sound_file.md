---
title: "How do I boost audio of a sound file?"
date: 2009-09-01
forum: Multimedia Software
---

### Post by Rytron on 2009-09-01
Hi.
How do I boost audio of a sound file?
I know this can be done in Audacity but are there more methods?
I find the options in Audacity to be a bit limited for this.
Thanks.

---

### Post by barisurum on 2009-09-01
Audacity is the perfect tool for this but you may as well try ardour or rezound, but then again audacity is the cleanest way.

---

### Post by Rytron on 2009-09-01
> **barisurum said:**
> Audacity is the perfect tool for this but you may as well try ardour or rezound, but then again audacity is the cleanest way.

Thank you barisurum. I will give ardour & rezound a try. I know Audacity is great, I am just wondering if there is also command line methods.

---

### Post by lykeion on 2009-09-01
> **Rytron said:**
> Thank you barisurum. I will give ardour & rezound a try. I know Audacity is great, I am just wondering if there is also command line methods.

If you mean boost as in normalize audio you could try the command-line tool **normalize-audio**. It's in the universe repository.

---

### Post by Rytron on 2009-09-01
> **lykeion said:**
> If you mean boost as in normalize audio you could try the command-line tool **normalize-audio**. It's in the universe repository.

Thank you lykeion. I had great success with ReZound. I will also give normalize-audio a shot.

---

### Post by lykeion on 2009-09-02
I had to test rezound and it looks really good, and I notice it also has JACK support :P

---

### Post by cascade9 on 2009-09-02
Gah! 'boosting'  and normalise tend to degrade audio quality. (If not always degrade, but thats debatable).

If your just playing the files, why not use the 'volume' control? If thats too hard, or you dont want to change volume with every track, theres replaygain. 

[http://en.wikipedia.org/wiki/Replay_Gain](http://en.wikipedia.org/wiki/Replay_Gain)

---

### Post by lykeion on 2009-09-02
Normalizing doesn't degrade any audio quality (as long as it's under 0.0 dB), it's just an overall change of the amplitude of the entire audio signal.

And replaygain is fine as long as you just want to play the audio on the computer and don't need to play it in any external players (mp3-players and such), where replaygain support is near null.

---

### Post by Rytron on 2009-09-02
> **lykeion said:**
> I had to test rezound and it looks really good, and I notice it also has JACK support :P

rezound does appear to be a hidden gem.

---

