---
title: "intrepid: ridiculously low sound volume with onboard sound (asus m2n68 mobo)"
date: 2009-04-23
forum: Multimedia Software
---

### Post by phormion on 2009-04-23
Hi, 

I have a new Asus M2N68 motherboard and I'm trying to use its onboard soundcard under Intrepid (will wait at least a few days before upgrading to Jaunty). I upgraded most of my old components after my old Albatron motherboard died. Ubuntu was able to boot without problems after the update and it seems to have recognized most hardware. The only problem I have is the sound volume is ridiculously low - I used to have my speakers at about half the volume, and the sound device was not at max volume either. Now with both set to max the sound barely gets as loud. Some more quiet mp3s are even barely audible. 

Any of you experience anything similar? I've tried to follow the pulseaudio guide from the forum ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) without much improvement. There's an ALSA page for Intel HDA soundcards debugging ([http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA](http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA)), but it's not helpful to me. 

I also have another sound device from my TV tuner, not sure if that can have any impact.

---

### Post by orkinoks on 2009-04-23
Hi;
why do you think Alsa is not useful for you?
I have had the same issue in Intrepid with my asus motherboard.I have installed Gnome Alsa Controller, changed the preferred system to Alsa and enabled 5.1 support.My computer started to sound just fine.

---

### Post by kamitsukai on 2009-04-23
Type this into the terminal (applications > accessories > terminal):

```
sudo apt-get install gnome-alsamixer
```

and it will ask for you password and then press enter, it will then install gnome-alsamixer which you can find in applications > sound & video.

once you've got it running make sure that PCM is turned up and that none of the other bars are set to mute or just very low =]
[B][U]
EDIT*
[/U][/B]
Nevermind..this is the same as typing 

```
alsamixer -Dhw
```

into the terminal to check on PCM...which is the in pulseaudio fixes that you posted already, sorry =]

---

### Post by phormion on 2009-04-24
I'll be damned! gnome-alsamixer fixed the problem. alsamixer was only giving me 2 controls to play with; that was maybe from the second card; the '-Dhw' part from the pulseaudio guide is confusing, because it's not very clear what you should use instead of 'hw'. With the gnome tool I could see that my master volume was at a near minimum. 

Thanks a lot guys!

---

### Post by kamitsukai on 2009-04-24
> **phormion said:**
> I'll be damned! gnome-alsamixer fixed the problem. alsamixer was only giving me 2 controls to play with; that was maybe from the second card; the '-Dhw' part from the pulseaudio guide is confusing, because it's not very clear what you should use instead of 'hw'. With the gnome tool I could see that my master volume was at a near minimum. 

Thanks a lot guys!

Well I'll be damed I actually helped someone instead of confusing them:lolflag:

---

