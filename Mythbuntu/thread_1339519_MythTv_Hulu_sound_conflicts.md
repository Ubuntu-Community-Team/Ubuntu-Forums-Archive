---
title: "MythTv Hulu sound conflicts"
date: 2009-11-27
forum: Mythbuntu
---

### Post by lordkalkin on 2009-11-27
Greetings,
I recently bought a Meerkat Ion net top box to use as our household media pc.  I installed Mythbuntu Control Centre and set up MythTV, so far, so good.  I then installed Hulu Desktop and edited my MythTV menus to make Hulu Desktop an option.  Again, no problems.

However, when I launch Hulu Desktop from MythTV, I get video but no sound.  When I run Hulu Desktop by itself, without MythTV running, sound comes through fine, so I assume that MythTV is suppressing sound from other applications, but I can't figure out how to alter that behaviour to accommodate Hulu.  

Any suggestions?

---

### Post by azmyth on 2009-11-28
I believe you want to start Hulu with the EXEC command in you menu edit for example EXEC /usr/bin/hulu.

---

### Post by tgm4883 on 2009-11-28
> **lordkalkin said:**
> Greetings,
I recently bought a Meerkat Ion net top box to use as our household media pc.  I installed Mythbuntu Control Centre and set up MythTV, so far, so good.  I then installed Hulu Desktop and edited my MythTV menus to make Hulu Desktop an option.  Again, no problems.

However, when I launch Hulu Desktop from MythTV, I get video but no sound.  When I run Hulu Desktop by itself, without MythTV running, sound comes through fine, so I assume that MythTV is suppressing sound from other applications, but I can't figure out how to alter that behaviour to accommodate Hulu.  

Any suggestions?

Did you install on top of Ubuntu or did you install Mythbuntu? I believe that PulseAudio is causing the issue here.

---

### Post by lordkalkin on 2009-11-29
I installed on top of Ubuntu.  Do I need to disable PulseAudio or change a setting? (If so, how?)

---

### Post by lordkalkin on 2009-11-29
> **azmyth said:**
> I believe you want to start Hulu with the EXEC command in you menu edit for example EXEC /usr/bin/hulu.

I checked the commanded in the edited menu, and it is the same as the one you suggested.  Thanks anyway.

---

### Post by blackoper on 2009-11-29
uninstall pulseaudio and it should work. Just so you are aware though, I can't get boxee to work in normal mythbunu due to boxee's inept sound management. XBMC works fine.

---

### Post by lordkalkin on 2009-12-04
Ok, time for an update.  

Thanks for all the suggestions.  Unfortunately, the problem persists, so let me list what I've done.

I looked into removing pulseaudio, and quickly found that ubuntu-desktop lists it as a dependency.  Rather than run through the guides for removing pulseaudio and preserving ubuntu-desktop, I installed xubuntu-desktop from the Mythbuntu Control Centre.  I then logged into xubuntu and removed ubuntu-desktop, again using Myhtbuntu Control Centre.  From there, I removed pulseaudio using apititude.  

However, I'm having the same problem with Hulu.  Hulu Desktop works fine alone, but when launched from MythTV, there is no sound in Hulu.  Any further suggestions?

---

### Post by lordkalkin on 2009-12-04
ok, one further update.  I discovered just now that I have no sound in hulu at all now.  Any suggestions on this yet?

---

