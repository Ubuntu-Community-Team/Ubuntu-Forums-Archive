---
title: "Audacious pitch plugin"
date: 2010-12-18
forum: Multimedia Software
---

### Post by Jorgje on 2010-12-18
Hi all,

Recently I changed my multimedia computer system from Windows XP Pro to  Ubuntu 10.04 LTS. I am now using Audacious as music player and looking for a proper pitch plugin for Audacious. The sndstrech plugin  that comes with Audacious does not work very well here, it messes up the  audio quality.

Can anybody give me some advice? I prefer a simple plugin (just pitch, nothign more) and easy to install.

---

### Post by tgalati4 on 2010-12-18
Have you tried sox?

[http://ubuntuforums.org/showthread.php?t=1576554&highlight=sox+pitch](http://ubuntuforums.org/showthread.php?t=1576554&highlight=sox+pitch)

---

### Post by Jorgje on 2010-12-18
> **tgalati4 said:**
> Have you tried sox?

[http://ubuntuforums.org/showthread.php?t=1576554&highlight=sox+pitch](http://ubuntuforums.org/showthread.php?t=1576554&highlight=sox+pitch)
I just installed it via Ubuntu Software Center, but the question is does sox have something which directly plugs into Audacious? I can't find it.

---

### Post by tgalati4 on 2010-12-18
No, the -p 200 switch will convert a file from one key down a full key.  Realize that changing pitch while preserving tempo is a difficult manipulation and going beyond a few semitones (+ or -p 300) will distort the sound.  I think the audacity plug-in uses the same (or similar) code and would have similar limitations.  The sox -p switch is helpful for minor pitch corrections for live recordings or mixing.  For special effects, (i.e. gross voice alteration) it's less useful because of the distortion.

---

### Post by Jorgje on 2010-12-19
> **tgalati4 said:**
> No, the -p 200 switch will convert a file from one key down a full key.  Realize that changing pitch while preserving tempo is a difficult manipulation and going beyond a few semitones (+ or -p 300) will distort the sound.  I think the audacity plug-in uses the same (or similar) code and would have similar limitations.  The sox -p switch is helpful for minor pitch corrections for live recordings or mixing.  For special effects, (i.e. gross voice alteration) it's less useful because of the distortion.
Let me clarify my question: what I am looking for is a plugin for Audacious which does "normal" pitch control just like a CD player or turntable that has pitch control. I don't want to preserve master tempo. Editing audio files before playing them is not an option for me since I want to be able to play around with the pitch control during playback.

Anybody?

---

### Post by lykeion on 2010-12-19
You can try the LADSPA Host plugin to load for example the AM pitchshifter.

---

### Post by Jorgje on 2010-12-19
> **lykeion said:**
> You can try the LADSPA Host plugin to load for example the AM pitchshifter.
Thanks, I've tried that one but it only does pitch shifting. What I am looking for is a plugin that I can use to adjust the playback speed (like 3% faster, for instance).

---

### Post by lykeion on 2010-12-19
You could try to install the pitch shifting LADSPA plugin rubberband (search for "rubberband ladspa" in Ubuntu Software Center) to use it with the LADSPA host in Audacious. According to its description it can change tempo and pitch independently of one another.

Another solution - but perhaps a bit overkill - is to use a DJ mixer software, like Mixx. It surely has the features you want. Online manual [here]("http://www.mixxx.org/wiki/doku.php/manual"), install via Ubuntu Software Center.

---

### Post by cchhrriiss121212 on 2010-12-19
> **Jorgje said:**
> Thanks, I've tried that one but it only does pitch shifting. What I am looking for is a plugin that I can use to adjust the playback speed (like 3% faster, for instance).
Alsaplayer does this out of the box, no plugin required.

---

### Post by tgalati4 on 2010-12-19
What you want is a DJ mixing console.  There are quite a few of those.  I've played with mixxx.

---

### Post by indiandruid on 2010-12-29
[http://scizzor.sourceforge.net/](http://scizzor.sourceforge.net/)

---

### Post by indiandruid on 2010-12-30
OR separate app

[http://29a.ch/playitslowly/](http://29a.ch/playitslowly/)

---

