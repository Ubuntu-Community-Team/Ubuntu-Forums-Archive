---
title: "Startup volume/mute control"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by dcroxton on 2006-06-14
Okay, I got sound working with some difficulty, but I still have this odd problem:  ubuntu ignores all the mixer settings that I last used, and resets everything when I reboot.  This might not be so bad except that the defaults are terrible -- most things are muted, and PCM is off, which totally disables my sound (I have no idea what PCM is, but I know it has to be on :) ).

What do I have to do to get the mixer settings to persist when I reboot?

Sincerely,
Derek

---

### Post by c-prompt on 2006-06-15
Although I've never had to do this in Ubuntu, set your mixer settings using alsamixer (run from terminal).  After you do this, do 'alsactl store' and see if that doesn't fix your reboot issue.

---

### Post by dcroxton on 2006-06-15
I appreciate that suggestion, but unfortunately it didn't work.  I found another thread suggesting adjusting the mixer as root, but that didn't work either.

Any other suggestions?

Sincerely,
Derek

---

### Post by c-prompt on 2006-06-16
Are you using gnome or kde?

---

### Post by dcroxton on 2006-06-17
[QUOTE=c-prompt]Are you using gnome or kde?[/QUOTE]

Plain old Ubuntu with Gnome.

---

### Post by c-prompt on 2006-06-19
I'm outta ideas then... I did a quick google search on the issue though and there seem to be quite a few cases of this out there.  I remember having this in Gentoo, but that was because the volume settings weren't restored at boot.  Ubuntu, by default, restores these settings at boot.
Maybe something changed your startup procedures; however, I'm not sure in which file the sound settings are recalled upon boot.

---

### Post by dcroxton on 2006-06-19
[QUOTE=c-prompt]I'm outta ideas then... I did a quick google search on the issue though and there seem to be quite a few cases of this out there.  I remember having this in Gentoo, but that was because the volume settings weren't restored at boot.  Ubuntu, by default, restores these settings at boot.
Maybe something changed your startup procedures; however, I'm not sure in which file the sound settings are recalled upon boot.[/QUOTE]

Oh well, thanks for trying!  I'll try in some other forum...

Sincerely,
Derek

---

