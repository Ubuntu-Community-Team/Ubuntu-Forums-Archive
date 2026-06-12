---
title: "Sound failure after VLC install issues, light crackle at high volume."
date: 2009-07-12
forum: Multimedia Software
---

### Post by mobrien118 on 2009-07-12
Hello,

For one reason or another, I decided to add VLC to Ubuntu using ap-get. The install hung at "Processing triggers for meun..." (right after man-db triggers). I waited 5 hours and it hung there. Finally killed the terminal, then rebooted, no there is no sound. I had to re-run apt-get because the installation of the 12 packages (VLC + required dependencies) was incomplete.

I tried removing VLC (obvious?) but it didn't remove the other 11 packages that were required during install (even if "apt-get autoremove"). If I turn up the speakers, there is a "light" crackle when there should be sound. I've checked "alsamixer" and everything is turned up and not muted. I ran "pavumeter" and can see that is is trying to play the sounds. There is nothing in dmesg about alsa or pulse ("dmesg | grep pulse && dmesg | grep alsa).

This is a system that I have hooked up to my LCD TV for video viewing, so I kind of need the sound on it.

Can anyone help me diagnose further?

Thanks,

--mobrien118

EDIT: I solved this by removing (+purge option) and re-adding "linux-sound-base" "alsa-base" and "alsa-utils"

---

### Post by igorzwx on 2009-07-12
To diagnose what?

Which operating system, processor, etc.

It it a very old box or it is a netbook?

---

### Post by mobrien118 on 2009-07-12
> **igorzwx said:**
> To diagnose what?

Which operating system, processor, etc.

It it a very old box or it is a netbook?

Sorry, I should have divulged that, shouldn't I?

It's an Intel Core 2 Duo and the sound card is an "Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)". It's a desktop box.

So, no, it's not too old.

I mean, it looks like sound should be working I don't see any reason it wouldn't, but I reached the end of my diagnostic abilities with problems like thsi. The key thing is that 3 minutes b4 the VLC install, sound was fine. I am thinking one of the 11 dependencies of VLC botched something up, because after the semi-failed install the sound no  longer works.

Like I said, "apt-get autoremove" isn't removing those dependencies, so is there maybe some other way I can find out what those packages were and remove them manually? Maybe a log file or something?

Thanks,

--mobrien118

---

### Post by igorzwx on 2009-07-12
Unbelievable!!!

Do you want to say that dual core cannot work with Pulse?
Try with quadro core.

---

### Post by mobrien118 on 2009-07-12
> **igorzwx said:**
> Unbelievable!!!

Do you want to say that dual core cannot work with Pulse?
Try with quadro core.

Huh? I didn't say that pulse couldn't work with dual core.

Maybe I missed something. I don't think there is anything wrong with the hardware. Something happened to the software/configuration to make this stop working. That's why I need help figuring out what, specifically, happened. Like I said, it has been working on this system for over a year before this. A package installation seems to have caused some kind of corruption. Should I add and remove some packages or something, or maybe remove then re-add... I don't know.

I would appreciate any help anyone cares to offer.

Thanks!

--mobrien118

---

### Post by benerivo on 2009-07-12
If you use synaptic, you can find those eleven packages by opening synaptic and looking under Main Menu > File > History.

Also try doing Ctrl+Alt+F1 and typing```
aplay /usr/share/sounds/alsa/Front_Center.wav
```which is a standard sound test for alsa. I'm not sure how the vlc installation would have spoiled the sound for the whole system (is it spoiled for all users?). Double check all sound settings on the left and right click options that you get on the volume control on the panel.

---

### Post by mobrien118 on 2009-07-12
> **benerivo said:**
> If you use synaptic, you can find those eleven packages by opening synaptic and looking under Main Menu > File > History.

Is there a similar method for apt-get? That's what I used...

EDIT: NM. I got my apt log. I'll try removing the packages.

> **benerivo said:**
> Also try doing Ctrl+Alt+F1 and typing```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

Tried that. If I turn the volume up to about 60% on my speakers (about what I watch movies at), I get what I would best describe as what sounds like a small fire in a fireplace. Just a few pops. The same thing happens when I try to play a movie or anything that uses sound. Everything LOOKS normal, just that the sound is not normal. Also, I eliminated the speaker system as the possible defect by trying it with my laptop. Worked fine there, so it's definitely Ubuntu causing the promlem.

Thanks benerivo, have any more ideas?

--mobrien118

---

### Post by mobrien118 on 2009-07-12
OK, so I removed these packages (dependencies of VLC):

libdvbpsi4 libebml0 libiso9660-5 liblua5.1-0 libmatroska0 libmatroska0 libtar libvcdinfo0 vlc-data libvlccore0 libvlc2 vlc-nox vlc

Then I rebooted (actually shut down, unplugged, waited to ensure hardware capacitors were cleared, then powered back on). Still, no *real* sound.

Then I reinstalled vlc again. The same dependencies were required. Still no sound.

Then I rebooted. Still no sound.

When I say "no sound" what I mean is, when there should be sound, there is light crackle. So, the server is running and accepting sound, only I guess it isn't being processed correctly.

Thanks!

---

### Post by benerivo on 2009-07-13
Have you tried removing pulseaudio?

---

### Post by mobrien118 on 2009-07-13
> **benerivo said:**
> Have you tried removing pulseaudio?

OK, I tried ```
sudo apt-get --purge remove pulseaudio
``` (which removed "ubuntu-desktop" as well"). So then I ran ```
sudo apt-get install ubuntu-desktop
``` which re-installed pulseaudio. Still just a crackle.

Then I rebooted, still just the crackle.

A note: when the system is shutting down, when it would normally just show the "splash" shutdown screen, it switches to a text screen where it lists the daemons stopping. It pauses for about 5 seconds on "Shutting down ALSA..." (may not be exact terminology). Hmmm...

---

### Post by igorzwx on 2009-07-13
Benerivo!

I tried everything with Pulse, but the evil mutates every day.
The logic is simple: Why not hack ALSA modules (and everything else)
to fix Pulse? And what about security holes. Is that buggy thing
invulnarable to exploits?

---

### Post by benerivo on 2009-07-13
You can safely remove pulseaudio and ubuntu-desktop, and then try rebooting. The ubuntu-desktop package is just a meta-package that is a pointer to all the packages that make up the ubuntu-desktop. Removing it does not actually remove any of these packages.

You might also try re-installing alsa with```
sudo apt-get --reinstall install alsa-base
```

---

### Post by mobrien118 on 2009-07-15
> **benerivo said:**
> You can safely remove pulseaudio and ubuntu-desktop, and then try rebooting. The ubuntu-desktop package is just a meta-package that is a pointer to all the packages that make up the ubuntu-desktop. Removing it does not actually remove any of these packages.

You might also try re-installing alsa with```
sudo apt-get --reinstall install alsa-base
```

Yep. I tried all of that. I even tried going into the BIOS and disabling the sound card and rebooting a few times.

Even after all of this, the (possibly unrelated) symptom of having it switch to the text screen during shutdown and sitting for about 10 seconds still exists even with the sound card disabled. Please note that this symptom was not present before this problem occurred.

This is so frustrating... but hey... at least it's not windows!

---

### Post by mobrien118 on 2009-07-20
So, I booted into a 8.04 live CD and the sound worked perfectly.

This means that I can officially rule out all hardware.

Can it be possible that I am the only one having this issue?

I would think that some audio guru would be able to target this error in, like, 2.5

The strangest thing is that there is SOME sound coming out of the system! It just sounds like a fireplace crackling though, and at about half volume. If I turn it up, the crackling gets louder, and it only happens when sound is supposed to be playing, so I know it's not some kind of external interference.

This is the strangest issue I've seen since I used to use Windows!

---

### Post by mobrien118 on 2009-07-21
NM!!!!

I actually fixed it by reinstalling the sound packages.

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

then:

```
sudo apt-get install ubuntu-desktop
```

I feel pretty bad, though, for wasting the time of anyone who may have read this thread. I should have tried this sooner.

I wonder what oddity caused this issue to begin with... I guess I'll never know!

Cheers!

--mobrien118

---

