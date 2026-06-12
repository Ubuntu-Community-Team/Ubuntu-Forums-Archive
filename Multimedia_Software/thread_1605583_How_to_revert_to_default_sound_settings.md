---
title: "How to revert to default sound settings?"
date: 2010-10-25
forum: Multimedia Software
---

### Post by boddhisatva on 2010-10-25
Hi. Since I installed the system-wide equalizer I've been having some problems with my sound system. The problem is it has changed some system settings (visible in gconf) and after I uninstall it, I can't change any sound settings, except the volume in a given application, but the system-wide volume doesn't work, even the tray icon shows three dashes next to the little speaker and the sound settings won't start. I'd like to revert the settings to the original after removing the equalizer, as at this moment I can't change any settings even with the equalizer enabled. Is there any way to reset the sound settings (I suppose it must be in gconf, but I don't know what the values should be. Currently the musicaudiosink settings are:
audioresample ! audioamplify amplification=0  ! pulsesinkv)
Those are the settings that definitely changed after installing the equalizer, but they obviously won't change back after uninstalling it.

---

### Post by lidex on 2010-10-25
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
To remove audio config files.
Then look in ```
~/.gconf/system/pulseaudio
``` for anything named equalizer and delete.

---

### Post by boddhisatva on 2010-10-26
Thanks! I've actually just deleted the .pulse folder in the meantime (after uninstalling the equalizer via Synaptic) and it seems to have helped. But I'll keep your info, I might still need it. :)

---

### Post by lidex on 2010-10-26
> **boddhisatva said:**
> Thanks! I've actually just deleted the .pulse folder in the meantime (after uninstalling the equalizer via Synaptic) and it seems to have helped. But I'll keep your info, I might still need it. :)

I uninstalled the equalizer also but still showed as an audio device in 'Sound Preferences'. Keep an eye out for that.

---

