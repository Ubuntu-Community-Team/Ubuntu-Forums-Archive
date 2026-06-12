---
title: "No sound in my Ubuntu [desktop]"
date: 2008-11-24
forum: Multimedia Software
---

### Post by dimis80 on 2008-11-24
My friends, I am facing a problem with my soundcard and my ubuntu..

I have in my desktop pc the Creative X-fi gamer card as also an onboard intel card.

Both of them are refusing to fill with sound my ears!
Firstly I tried x-fi. I went to bios, deactivated the intel and then restart. I went to Ubuntu, sound properties bu nothing.

Afterward I activated Intel, done the same things by choosing Intel but nothing!

I already made default the card that i needed through:
```
asoundconf list
```
and then:
```
asoundconf set-default-card
```

still nothing... what should i do? :confused:

---

### Post by psyke83 on 2008-11-24
> **dimis80 said:**
> My friends, I am facing a problem with my soundcard and my ubuntu..

I have in my desktop pc the Creative X-fi gamer card as also an onboard intel card.

Both of them are refusing to fill with sound my ears!
Firstly I tried x-fi. I went to bios, deactivated the intel and then restart. I went to Ubuntu, sound properties bu nothing.

Afterward I activated Intel, done the same things by choosing Intel but nothing!

I already made default the card that i needed through:
```
asoundconf list
```
and then:
```
asoundconf set-default-card
```

still nothing... what should i do? :confused:

Those steps no longer apply for Intrepid, as PulseAudio is used by default.
See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Note: You should follow the entire guide, but the crucial fix is in Step A, Part 5 where you define the default output device for PulseAudio.

---

### Post by dimis80 on 2008-11-24
Thanks my friend i'll try it out!

---

