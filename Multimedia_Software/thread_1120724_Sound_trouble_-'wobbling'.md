---
title: "Sound trouble -'wobbling'"
date: 2009-04-09
forum: Multimedia Software
---

### Post by lordyosch on 2009-04-09
Hi,

I've searched for this, using a variety of keywords but I can't find what I want...

When I'm listening to music and doing other stuff the sound seems to 'wobble' -I'm not sure what the correct adjective is for this! For a second or two it sounds like an old cassette that's got a bit stretched!

This also happens with the ubuntu login drums sound.

I thought it may be memory, so I ugraded to 2GB. No solution. I'm using the maximum buffer size allowed by Rhythmbox.

The sound problem occurs during login, when I change windows, when I scroll in firefox.


My sound card is a C-Media CMI8738 and it uses ALSA mixer.


Cheers,

Jay

---

### Post by markbuntu on 2009-04-09
Check that your users and root are members of the following groups which you can check in System/Administration/Users and Groups. This will give your applications using pulseaudio higher kernel priority which should fix your problem. If it does not there are other things you can do so let us know how you make out.

pulse
pulse-rt
pulse-access

---

### Post by lordyosch on 2009-04-15
> **markbuntu said:**
> Check that your users and root are members of the following groups which you can check in System/Administration/Users and Groups. This will give your applications using pulseaudio higher kernel priority which should fix your problem. If it does not there are other things you can do so let us know how you make out.

pulse
pulse-rt
pulse-access


I've checked and all users are listed as members of all 3 groups.

My sound settings specify ALSA -is this a different device/program to pulse?


Thanks

Jay

---

