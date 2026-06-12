---
title: "No sound in firefox extensions"
date: 2010-04-06
forum: Multimedia Software
---

### Post by metrofun on 2010-04-06
Hello. I have a problem with sound in firefox extensions.I have sound in flash, but not in firefox itself.This maybe because they are using defferent backends (alsa, pulse) but i don't know exactly, or how to change it for firefox(i haven't found any firefoxrc file).Also sound often is breaking on my system.So please help me.
I am running Kubuntu 9.10 on ASUS K40AB, if needed i'll provide all additional info about my system.

---

### Post by lovinglinux on 2010-04-06
What do you mean by sound on extensions? Extensions don't render sound by themselves. If you mean that you don't have sound when clicking buttons and such, then you need to change the system sound settings. 

EDIT: i just noticed you are using Kubuntu,  so I removed the instructions for Gnome.

---

### Post by metrofun on 2010-04-06
I mean extensions for firefox that uses "nsIsound" interface for sound output.
When i run firefox in gnome or windows xp,  i can  hear sound from my extensions, but on kubuntu i can't hear.
I thinks that flash and firefox itself may have different configs for sound.
But i can be wrong.Anyway thanks for your reply.

---

### Post by lovinglinux on 2010-04-06
> **metrofun said:**
> I mean extensions for firefox that uses "nsIsound" interface for sound output.

If you can't hear any of the nsISounds, then you shouldn't be hearing any Firefox event sounds, like button clicks and such. 

Can you hear other Firefox event sounds, not related to extension functionality?

What is your Firefox version? 

Could you provide the name of an extension that you use and should be using nsISound, but doesn't work properly, so I can test it?

> **metrofun said:**
> When i run firefox in gnome or windows xp,  i cab hear sound from my extensions, but on kubuntu i can't here.
I thinks that flash and firefox itself may have different configs for sound.
But i can be wrong.Anyway thanks for your reply.

Yes, flash is probably tied to the video sounds, while nsISound is part of Firefox event sounds. Go to "System Settings >> Computer Administration >> Multimedia >> Device Preference >>> Audio Output >>> Notifications" and switch to Pulseaudio.

---

### Post by metrofun on 2010-04-06
My firefox version is 3.5.8.You are right - I also can't hear any other sounds from firefox like button clicks.
I went to "System Settings >> Computer Administration >> Multimedia >> Device Preference >>> Audio Output >>> Notifications" chose Pulseaudio and pressed button "Test", i really heard a test sound, but it also killed sound from flash in firefox.
There was also another default option in "System Settings >> Computer Administration >> Multimedia >> Device Preference >>> Audio Output >>> Notifications" - HDA ATI SB (VT1708S) which also produced sound on test.

---

### Post by metrofun on 2010-04-06
In addition it killed all sound on my system, and i can't get it work even after killing all processes using pcm, and restarting alsa-conf.

---

### Post by lovinglinux on 2010-04-06
> **metrofun said:**
> My firefox version is 3.5.8.You are right - I also can't hear any other sounds from firefox like button clicks.
I went to "System Settings >> Computer Administration >> Multimedia >> Device Preference >>> Audio Output >>> Notifications" chose Pulseaudio and pressed button "Test", i really heard a test sound, but it also killed sound from flash in firefox.
There was also another default option in "System Settings >> Computer Administration >> Multimedia >> Device Preference >>> Audio Output >>> Notifications" - HDA ATI SB (VT1708S) which also produced sound on test.

Play with those settings to see if you can find a combination that produces sounds for flash and Firefox events.

---

### Post by metrofun on 2010-04-06
Doesn't help.Sometimes when i click test pulseaudio i get notofocation about error and falling back to HDA ATI, but any clicks on test button kills sound on my system, sometimes it's enough to restart application with sound, sometimes to restart kdm.

---

### Post by lovinglinux on 2010-04-11
Ironically, I have lost Firefox system sounds too :)

I happened since I installed Lucid Lynx. I'm using the default Firefox installation (3.6.3), but have tested other versions downloaded from Mozilla.

What version of KDE you are using?

I will investigate this.

---

### Post by richtl on 2010-05-13
I'm having the same problem since I upgraded to the plain version of Ubuntu Lucid. No sound from anything having to do with firefox. Sound works fine everywhere else.

Rich

---

### Post by lovinglinux on 2010-05-13
> **richtl said:**
> I'm having the same problem since I upgraded to the plain version of Ubuntu Lucid. No sound from anything having to do with firefox. Sound works fine everywhere else.

Rich

Unfortunately, I don't have a solution yet. Do you have sound on videos? You might want to check the volume sliders for PCM and Master.

---

