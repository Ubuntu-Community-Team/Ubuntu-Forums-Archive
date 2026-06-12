---
title: "problem with keyboard volume control after switch from 8.04 to 9.04"
date: 2009-05-12
forum: Multimedia Software
---

### Post by alex sun on 2009-05-12
Hi!
Could you please help with one little issue?
Sorry in advance if it is the wrong place for this topic or if I missed the similar discussion.
I've just installed Ubuntu 9.04 on HP tx1000 and realised that 'Volume Up' and 'Volume Down' keyboard buttons effect only sound _capture_.
I would be very happy to return my keyboard connection with sound _playback_ as it was in Ubuntu 8.04 before re-installation and as it is in Windows.
I checked that in the Volume Control Preferences my 'HDA NVidia Alsa mixer' is selected as device to control, and 'Master' is selected as track to control. I tried choosing the 'Headphone' track with no effect.
I also checked in the Keyboard Shortcuts that all sound-related buttons are assigned correctly.
Thanks in advance!

---

### Post by alex sun on 2009-05-12
SOLVED!
Needed to choose 'HDA NVidia Alsa mixer' in System -> Preferences -> Sound
:KS

---

### Post by Chronon on 2009-05-12
Thanks!  That did the trick.  :)

---

