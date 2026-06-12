---
title: "Youtube sound problems"
date: 2008-07-31
forum: Multimedia Software
---

### Post by sporkubus on 2008-07-31
Whenever I go to a Youtube video and I have any media player open in Ubuntu, I don't get any sound from the video, and it also causes ALL media players to not be able to play any files until I reboot my computer.

---

### Post by Hachi-Roku on 2008-08-05
yeah i think i just got the same problem. Im pretty sure i have all the plugins and streamers installed...
let you know if i solve it after some research and fiddling....

---

### Post by tuxxy on 2008-08-05
Have you tried enabling ALSA in system > prefs > sound

---

### Post by Hachi-Roku on 2008-08-06
gave that a shot just then. Alsa didnt seem to test, I got error messages. All worked fine when i set it to autodetect or pulseaudio.

about the other stuff....

I went here;

[http://ubuntuforums.org/showthread.php?t=766683&highlight=youtube+problems+hardy](http://ubuntuforums.org/showthread.php?t=766683&highlight=youtube+problems+hardy)

and picked out relevant parts for me.
Now youtube works fine on its own. But theres another problem...like always!

I get a conflict between audio things i.e.;
Im running amarok and firefox 2 at the same time and if i overlap sound usage (have amarok playing media when i open a youtube page) then youtube loses sound and amarok has a total spasm, crashes, and wont restart.

i dont think im using a amarok plugin so i dont really know why these two things seem dependent on something common (other than the sound card of course).

any ideas?

---

### Post by Ryadt on 2008-08-06
Disabling pulse audio will solve the problem.```
killall pulseaudio
```

---

### Post by Yellow Pasque on 2008-08-06
Do you have libflashsupport package installed?

---

### Post by sporkubus on 2008-08-06
> **tuxxy said:**
> Have you tried enabling ALSA in system > prefs > sound

What should I select for the Default Mixer Track?

HDA Intel (Alsa mixer)
Realtek ALC268 (OSS mixer)
Playback: ALSA PCM on front:0 (ALC268 Analog)

and then there's two choices that start with Capture: ...

---

### Post by pinsky on 2008-08-08
Had the same problem. Even installed flash 10, but nither that helped.
Then downloaded libflashsupport from synaptic and sound appeared in youtube :)

---

### Post by l3dx on 2008-08-08
> **sporkubus said:**
> Whenever I go to a Youtube video and I have any media player open in Ubuntu, I don't get any sound from the video, and it also causes ALL media players to not be able to play any files until I reboot my computer.

I had kind of the same problem. I didn't have to reboot, but every time I wanted to get sound from flash, I had to ensure no other app was occupying the sound device.

> Have you tried enabling ALSA in system > prefs > sound 
This made it for me. I've actually never changed my sound settings ever using ubuntu, so I kind of expected the system to use ALSA already. 

This was not a problem for me before upgrading to Hardy though.

---

### Post by sporkubus on 2008-08-28
I followed all the advice here and everything seemed to be working for a while. But now I'm having the same problem again... if I'm using Banshee and I go to a Youtube video, I have to close Banshee and reload the page to even allow the video to play.

---

### Post by wolfen69 on 2008-08-28
see [this]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio") thread. works for alot of people.

---

### Post by sporkubus on 2008-08-28
> **wolfen69 said:**
> see [this]("http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulseaudio") thread. works for alot of people.

Works now. Thanks so much!

---

