---
title: "Amarok: &quot;xine was unable to initialize any audio drivers.&quot;"
date: 2008-07-17
forum: Multimedia Software
---

### Post by Roasted on 2008-07-17
Ubuntu Hardy Heron 64 bit.

I installed this about 2 weeks ago. Lovin 64 bit so far. I had everything working perfectly. Then, I tried to install pulse. Disasters happened and hours were wasted, so I reverted back to Alsa.

Everything under System-Pref-Sounds is set to Alsa. Setting it to auto-detect yeilds no difference.

Also, Audacious is down too. When I open an mp3 through it, Audacious will open, yet it just sits there... not moving, not playing it, etc.

What can I do to get this working?

Last night I uninstalled Amarok, rebooted, reinstalled Amarok, and it worked. Computer hasn't shut off since I rebooted that one time, and now magically after coming home from work, the problem is back.

---

### Post by Roasted on 2008-07-17
I set my sound under sys-pref-sounds to auto detect. I also set my sound preferences in Amarok to auto detect. Now, it works. But everything set to Alsa, it prompts me with the error. Why?

I heard something about a bug involves with flash in firefox. I always run youtube, always. Maybe that's it?

Is there any harm in letting everything auto detect? I'd REALLY like to be able to set stuff to Alsa. I just like knowing everything is "fixed" up the way it should be.

EDIT - update... sys-pref-sounds can be in alsa and be fine. However, the amarok setting MUST be auto detect. Otherwise alsa bitches at me. After doing this, if I go back to sys-pref-sounds and hit "test" where I have everything selected to alsa, I get an error. However, Amarok still works. Audacious does not.

When I killall pulseaudio at terminal and go back, bam, suddenly everything works.

Isn't there just a way to completely block pulseaudio right now? It's so ungodly annoying.

EDIT 2 - FF requires a reboot for flash to work after doing this. What is happening?

---

