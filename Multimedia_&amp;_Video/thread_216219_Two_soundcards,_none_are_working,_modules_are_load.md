---
title: "Two soundcards, none are working, modules are loaded."
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by Renko on 2006-07-15
Two days ago I installed Ubuntu, before I was useing Suse Linux. On Suse Linux both of my soundcards worked automaticly.

On Ubuntu I can hear the login sound in GDM. After that every apllication is telling "No sound card found", and the volume control is disabled.

I manualy loaded the right module of my Sound Blaster Live, which is 'snd-emu10k1'. No errors, no output, no difference. I compiled and installed Alsa like mentioned in [this guide](http://www.ubuntuforums.org/showthread.php?t=205449) with support for 'intel8x0' (my onboard sound) and 'emu10k1' (SB). After that I loaded both modules. When loading the intel8x0 module Ubuntu says 'New sound card found, click here to configure', and then it doesn't find any sound card. When loading 'emu10k1' nothing happened, however, at this moment it says 

'renko@smile2:~$ sudo modprobe snd-emu10k1
FATAL: Module snd_emu10k1 not found.
FATAL: Error running install command for snd_emu10k1'.

If one of my soundscards will work I will be happy. I don't need both.

[Output of dmesg](http://meuk.datafeest.net/dmesg)

---

### Post by Renko on 2006-07-15
I think I have a solution.

Because some own stupidity when installing Ubuntu I had to add my user account in the shell useing the 'adduser' (or 'useradd', dont remember) account. The result is that this user has no audio rights. Useing the tool System > Administration > Users and groups I was able to set everything how it has to be.
Now my Volume Control is working, The sound tool (System > settings > sound) is detecing the soundcard. I'm not able to test real sound output now, I haven't yet any MP3 on my system and have to go right now. I'll update later =)

---

### Post by Renko on 2006-07-16
Now I can confirm it.

System > Administration > Users and groups > select user > properties > user privilages > use audio devices. This has to be checked on, if you add a user trough the console command 'adduser'. this is disabled my default.

It makes sense now. Before I login (in GDM) the sound did work (welcome sound), after I login it's broken. That is because the specific user has no access to the audio card.

---

