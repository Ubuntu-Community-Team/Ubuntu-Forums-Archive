---
title: "No sound on standard users, 12.10 64bit"
date: 2013-04-20
forum: Multimedia Software
---

### Post by driven1 on 2013-04-20
I had a system crash and did a fresh install of 12.04 (didn't affect partition with home folder). Then I upgraded to 12.10. Ever since, none of the standard users have sound. I still have it available under the admin account plus any new users created have sound. For existing users, the sound control panel doesn't show any output devices available. I assume that this is a configuration problem, but I don't really know where to go, or how to fix it. I've read several blogs/forum posts, but am none the wiser. Anyone have any advice?

---

### Post by CatKiller on 2013-04-21
I vaguely recall that there's a group (which I wouldn't be surprised is called audio or similar) that controls which users can access an audio device. Users who aren't members of that group can't access that device.

Does that seem likely with the way you created the users? As I say, I'm fuzzy on the details, but it might be a place to start.

---

### Post by Yellow Pasque on 2013-04-22
@CatKiller: only the "pulse" user should be in the audio group. See: [http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

@driven1: I suggest logging in as a user without sound and running:
```
rm -r ~/.pulse*; pulseaudio -k
```

See if sound comes back then. If it does, repeat for other "deaf" users.

---

### Post by CatKiller on 2013-04-22
Thanks, that explains why it was a vague memory: I've messed around with JACK in the past.

---

### Post by driven1 on 2013-04-25
It wasn't elegant, but I ended up deleting all of the users and creating new accounts. I only restored the user data, but none of the settings or config files. As I said, it wasn't pretty, but everyone has sound now.

---

