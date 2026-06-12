---
title: "No sound with Jaunty 64-bit on Dell Latitude E6400, works on install CD"
date: 2009-06-04
forum: Multimedia Software
---

### Post by Xianath on 2009-06-04
Hi all,

I got a new laptop and just moved my HDD with Kubuntu Jaunty 32-bit from the old box. Everything worked except sound. I decided to reinstall, and switch to 64-bit now that I have the CPU to support it. The install CD detected all hardware with no issues -- video, sound, and wireless -- and so did the fresh installation. As soon as I mounted my old /home partition and logged back in, all sound was lost.

So, I know I have all the pieces working ant it's a config issue, but I can't put my finger on it. Every channel is maxed out and unmuted in both alsamixer, kmix and the PulseAudio mixer. I can see the monitors active in the PulseAudio control panel when music plays in Amarok. And yet, there's no sound.

Before I mounted /home, I backed up the home directory that was created as part of the installation which had sound working. I am attaching the list of files. Which files do I need to copy over to my normal home directory to get it working?

Thanks,
Peter

---

### Post by Xianath on 2009-06-08
OK, so I did a diff and compared this .kde directory to my current one, found some differences in the Phonon configuration, thought it made sense to give that a try and... nada! So I gave up and thought I'd wait for the forum to help out. Then all of a sudden, several days later, I started my laptop this morning and it greeted me with sound!

My guess at this point is that something else is competing for that sound card and winning the race most of the time, but not always. I'll go with VMWare as it sounds like the most likely culprit. Anyone know what logs I should look into for evidence, and what I should expect to see when it works and when it doesn't? Any diagnostics I can run if it breaks again?

Thanks,
Peter

---

