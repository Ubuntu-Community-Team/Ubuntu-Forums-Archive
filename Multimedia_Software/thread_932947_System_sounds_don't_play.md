---
title: "System sounds don't play"
date: 2008-09-28
forum: Multimedia Software
---

### Post by SomeGuyDude on 2008-09-28
Ubuntu 8.04 here

The problem I'm having is that aside from my little "bleep!" sound when the login window pops up, absolutely no system sounds play. They don't play in the Preferences -> Sound dialog when I hit "play" and I don't get them when I login or logout. Otherwise all sound works just fine.

I'm using the OSS mixer for all sounds, Conexant Analog.

---

### Post by mrbinitie on 2008-10-02
I have the same problem and all my sounds are set to ALSA. The annoying thing is that the login sounds worked till a couple of days ago. I did an update with Proposed Updates and it worked just before I restarted and then once again 'Poof' gone. Does not work anymore? Weird? any fixes?

---

### Post by Yellow Pasque on 2008-10-02
> **SomeGuyDude said:**
> Ubuntu 8.04 here

The problem I'm having is that aside from my little "bleep!" sound when the login window pops up, absolutely no system sounds play. They don't play in the Preferences -> Sound dialog when I hit "play" and I don't get them when I login or logout. Otherwise all sound works just fine.

I'm using the OSS mixer for all sounds, Conexant Analog.
Short answer: System Sounds on GNOME suck

Long answer: I played with esd in OSS4/vmix one time (I don't currently have esound installed because I don't care for system sounds). I found that the esd process tends to randomly die with OSS4. It's a poorly written, old daemon, and GNOME devs hate it (but they don't care enough about system sounds to fix it). Be thankful for vmix, because without it, esd can hog sound resources. (In fact, some launcher scripts for apps that use audio are so used to esd interference that they have a line to "killall esd")

I guess if you must have system sounds with OSS4/vmix, you could use a cron job to load esd if it has died.

---

### Post by minky311 on 2008-10-02
> **mrbinitie said:**
> I have the same problem and all my sounds are set to ALSA. The annoying thing is that the login sounds worked till a couple of days ago. I did an update with Proposed Updates and it worked just before I restarted and then once again 'Poof' gone. Does not work anymore? Weird? any fixes?

Try checking to see if you have esound installed by going to System->Administration->Synaptic package manager and searching for esound.
If you don't, install it and then head over to System->Preferences->Sound
and click on the sounds tab. Check "Enable software sound mixing(ESD)" and then check the "Play system sounds". Then you can go ahead and see if any system sounds work.

---

### Post by mrbinitie on 2008-10-02
Thanks. Its an interesting one. I went to Synaptic and on selecting esound got a threat that it would remove Ubuntu-Studio desktop. Not sure what it means but, I do like my Ubuntu-Studio so I deselected. I did select the esound_clients though. How on earth did the system sounds work before? This soundlessness is a new development. ESD is checkd though and has been for a while

---

### Post by markbuntu on 2008-10-03
Actually, esound has been sneakily replaced with pulseaudio and if you don't have your sound setup properly, no system sounds. Someone did a really terrible job setting up the default sound system for Hardy so the sound servers are often in conflict and as a result system sounds can get just shut out from the sound card. After much painstaking research, I have mostly figured this all out, even for UbuntuStudio and jack, though getting system sounds while jack is running...why would someone want that?

Anyway, here is my 40,000 page guide to getting your sound dialed in:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

