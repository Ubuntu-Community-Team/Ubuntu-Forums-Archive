---
title: "No sound in Flash Player."
date: 2009-04-26
forum: Multimedia Software
---

### Post by NECHTOVIKING on 2009-04-26
Hi all,

I just upgraded to Ubuntu 9.04 and when I tried to watch a YouTube video it would not produce any sound. I have tried countless things; reinstalling flash player, trying a different player, and trying different headphones (I use USB headphones), but nothing is working.

I checked the rest of this section and there were other topics on how to fix it, but even when I tried those my flash player still produces no sound. Thanks for the help.

---

### Post by TheBuzzSaw on 2009-04-26
I am having the same problem. I just upgraded to 9.04 and after fixing Flash (it was non-existent before), suddenly I get no sound from YouTube videos. :(

---

### Post by Frodo232 on 2009-04-27
+1 same issue here - on 9.04 64bit

anyone got any ideas?

---

### Post by Andysan on 2009-04-27
Same problem for me using Kubuntu 9.04 - system sounds work fine.

---

### Post by TheBuzzSaw on 2009-04-27
My solution was to explicitly disable Flash in Firefox and then uninstall it from the package manager. Install the 64-bit Linux Flash plugin: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Just put the .so file into your ~/.mozilla/plugins/ folder.

---

### Post by caveman59330 on 2009-04-28
I tried that and it didn't work either I still have no sound when going to youtube or the onion news network and try to play videos.man I hope someone finds a solution I researches it on the internet and nothing has worked for me.I am about to go back to a earlier version of Ubuntu cause this sucks.

---

### Post by NECHTOVIKING on 2009-04-28
> **TheBuzzSaw said:**
> My solution was to explicitly disable Flash in Firefox and then uninstall it from the package manager. Install the 64-bit Linux Flash plugin: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Just put the .so file into your ~/.mozilla/plugins/ folder.
This didn't work for me as well.

---

### Post by davidgurvich on 2009-04-28
Have you tried unmuting the channels with pulseaudio?  In jaunty, pulseaudio has become the default for sound.

---

### Post by NECHTOVIKING on 2009-04-29
> **davidgurvich said:**
> Have you tried unmuting the channels with pulseaudio?  In jaunty, pulseaudio has become the default for sound.
Aye, nothing doing.

---

### Post by psyke83 on 2009-04-29
It's likely that PulseAudio is not working correctly on your system. Follow my PulseAudio guide to ensure you have a "clean" PulseAudio configuration, and there's also some troubleshooting steps that may be of assistance.

If audio works in PulseAudio with other applications, I suspect it's a problem with the lib32asound2-plugins not working correctly with Adobe Flash.

Ensure you're not missing dependencies:
```
$ ldd /usr/lib/adobe-flashplugin/libflashplayer.so
```

---

### Post by NECHTOVIKING on 2009-04-29
> **psyke83 said:**
> It's likely that PulseAudio is not working correctly on your system. Follow my PulseAudio guide to ensure you have a "clean" PulseAudio configuration, and there's also some troubleshooting steps that may be of assistance.

If audio works in PulseAudio with other applications, I suspect it's a problem with the lib32asound2-plugins not working correctly with Adobe Flash.

Ensure you're not missing dependencies:
```
$ ldd /usr/lib/adobe-flashplugin/libflashplayer.so
```
Followed your PA guide, worked like a damn charm. Thanks mate.

---

