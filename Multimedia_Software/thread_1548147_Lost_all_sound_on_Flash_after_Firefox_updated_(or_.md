---
title: "Lost all sound on Flash after Firefox updated (or shortly thereafter)"
date: 2010-08-07
forum: Multimedia Software
---

### Post by mathum on 2010-08-07
Lost all sound on Flash after Firefox updated (or shortly thereafter)
In other words Youtube and the like are silent (which is a kind of a blessing, really).

10.04LTS 32bit
Firefox 3.6.8 - (for Ubuntu - Canonical 1.0)
Flash 1.0.10 (tried r&r already)
External USB sound card, desktop system

Sound works great everywhere else, including mp3's on web through Firefox. I searched the forum, of course, but didn't find anything that seemed relevant or up-to-date.
I'm no hacker, and am apt to get lost, so does anyone with a bit of patience have a clue how i can fix this?

Thanks for any help..

~m

---

### Post by kostkon on 2010-08-08
> **mathum said:**
> External USB sound card, desktop system
Here is your clue.
Install the *PulseAudio Volume Control* utility (using the Software Centre), it's a nice application, you may need to use it again.

Put a youtube video playing in Firefox, then run the volume control utility and in the *Applications* tab you should be able to see its audio stream. Just select your USB card from the list to set it as the default output device for Flash audio streams.

---

### Post by mathum on 2010-08-08
Excellent! Worked perfectly. Thanks very much.

~m

---

