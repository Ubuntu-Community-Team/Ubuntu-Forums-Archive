---
title: "Now You've Done It!"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Tyche on 2006-08-06
It was  bad enough that, during the previous kernal update, my sound was somehow eliminated - despite the fact that the system could find the sound card and the proper drivers were installed.

NOW - the system can't even find my sound card other than as hardware.

I know the sound card works, as a PCLinuxOS Live-CD is able to activate sounds without any problem.

System:
  Tyan Motherboard
  Pentium III (Copermine), 750 MHz CPU
  Linux Kernal 2.6.15-26-386
  512 M Memory
  Sound Card Creative Labs SoundBlaster Live! - EMU10k1 (rev0a)

<command> lspci -v lists the sound card as existing, spelled out much as I have spelled it out, above.

<command> aplay -l states "aplay: device_list:221: no soundcards found..."

I have already removed and installed the alsa-base, etc., per the instructions in the "comprehensive sound problem solution guide", including re-installing the gdm and Ubuntu-desktop. 
 
What will this distribution break NEXT?
If this persists, I will be forced to consider ANOTHER distribution.  I had already moved away from FedoraCore because even during installation all I got on the screen was garbage, and was unable make proper responses to it.  If anything else breaks, I'll be forced to leave this and search for a distribution that actually works.  Or worse: return to [GASP] Microsoft.

PLEASE:  If you can't fix something, DON'T BREAK IT!

:twisted:

---

### Post by Tyche on 2006-08-06
Bump

---

