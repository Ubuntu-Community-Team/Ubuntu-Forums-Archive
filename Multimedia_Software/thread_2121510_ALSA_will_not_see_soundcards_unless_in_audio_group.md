---
title: "ALSA will not see soundcards unless in audio group"
date: 2013-03-02
forum: Multimedia Software
---

### Post by monkblah on 2013-03-02
Sound on my 12.10 machine was running fine, with pulse audio and ALSA, until a couple of days ago when the trouble started. Now, ALSA no longer can access any of the soundcards in the machine, unless either:

1) It is run by a user who is a member of the 'audio' group, or
2) It is run by the user who logged in at the lightdm greeter.

To explain another way, let's say I have two user accounts, user1 and user2. I turn on the machine, log in at the greeter as user1. Open a terminal and type 'aplay -l'. A bunch of soundcard devices are listed.
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT2020 HP [VT2020 HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
....(etc, more devices)

Now I 'sux - user2' and run 'aplay -l' as the new user. 

```

$ aplay -l
aplay: device_list:252: no soundcards found...

```

Logout and restart the machine. This time I login as user2 at the lightdm greeter. Start a terminal and run 'aplay -l'. This time, the soundcards ARE listed...while if I switch user to user1 and run 'aplay -l', now no soundcards are found for that user.

Same users, their privilages have not changed, but the results are reversed.

I should add that the soundcards are visible to the root user, and to any user in the audio group.

Here are the outputs from alsa-info.sh for a working and non-working user. They seem identical except for the fact that the sound hardward is simply not visible to ALSA for the non-working user.

non-working:
[http://www.alsa-project.org/db/?f=8bc516d779bf439dee84307116cf77bc35fc03fd](http://www.alsa-project.org/db/?f=8bc516d779bf439dee84307116cf77bc35fc03fd)

working:
[http://www.alsa-project.org/db/?f=4659a767e86950300b6d72c67539de4d11cb4896](http://www.alsa-project.org/db/?f=4659a767e86950300b6d72c67539de4d11cb4896)

Right now I added the second user to the audio group as a workaround, but this is specifically not recommended and discouraged by the experts.

Can anyone help me figure out why this happened and how to fix it?

---

