---
title: "Optical S/PDIF output no longer works"
date: 2008-05-24
forum: Multimedia Software
---

### Post by jmverner on 2008-05-24
I am a noob scratching my head and would appreciate any help.
Was on 7.10 and had sound working through my AV receiver with IEC958 output using AlsaMixer.  One day last week it just suddenly stopped working.  I tried everything the various forum postings (a LOT of people are experiencing this) including:
- Made sure IEC958 checked on Switches tab of vol control
- Made sure IEC958 output not muted in AlsaMixer
- Created .asoundrc file with "proper" config for my Turtle Beach Montego sound card:
```
pcm.!default { 
	type hw 
	card 0 
	device 2 
}
```
- After none of that work (in desperation) hearing that Hardy used a new sound architecture (PulseAudio) I upgraded today.  After the upgrade still no optical output sound but regular sound still works fine.
But as far as I can tell my upgraded system does NOT use PulseAudio.  I ran gstreamer-properties and selected PulseAudio but that did nothing useful.  Also tried to follow the PerfectSetup for PulseAudio but found that the files were installed - except none of the utilities like pavucontrol were installed!?  Do I have it installed or not?

If anyone has figured this stuff out I would appreciate a noob tutorial.
Thanks!

---

### Post by jmverner on 2008-05-27
bump

---

### Post by jlindbergh on 2008-08-10
I have a similiar problem that's really bugging me:
[http://ubuntuforums.org/showthread.php?p=5549937](http://ubuntuforums.org/showthread.php?p=5549937)

---

