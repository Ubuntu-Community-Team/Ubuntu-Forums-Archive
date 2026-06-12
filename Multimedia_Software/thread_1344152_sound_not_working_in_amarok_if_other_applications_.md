---
title: "sound not working in amarok if other applications open"
date: 2009-12-02
forum: Multimedia Software
---

### Post by LordIshamael on 2009-12-02
Hey, I have a Dell XPS 13 running Kubuntu Karmic 64 bit. This is a new computer, so I don't know if this problem existed in previous versions of Kubuntu.

Whenever I open amarok and then open some other application which uses sound like opera, sound works in both applications. I can listen to music in amarok and watch videos in opera.

However, if I restart amarok, or in general if any sound-using application is opened before amarok, it simply says that none of my audio cards work, falling back to pulse audio, which does not give any sound. The other applications that were using sound work perfectly at this point.

I do have one desktop effect that occasionally produces sound, and it does not seem to make a difference that this effect is open and using sound before amarok is opened. Any ideas on what I should do?

Thanks!

Edit: To clarify, I noted that if amarok is opened first then sound works in both. I just realised that this is not the case. Sound will not work in opera while amarok is open. However, immediately upon closing amarok, sound works in opera, whereas simply closing opera will not make sound work in amarok - I need to restart amarok as well.

---

### Post by LordIshamael on 2009-12-07
Ok, this issue was solved by opening PulseAudio preferences, going to the simultaneous output tab and checking the 'Add virtual output device' option.

---

