---
title: "No sound at all after closing session"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Ferio on 2010-05-08
Hi, I was listening to the radio using Spotify on Wine, and then closed my session without exiting Spotify; when I came back, I had no sound at all (not using VLC, Rhythmbox...) and I don't know how to get it back. I've tried re-installing ALSA and PulseAudio, but there's been no change at all. Could anybody help me, please? Thanks in advance.

---

### Post by mistermentality on 2010-05-08
I`m a Linux Newb so not sure this will help but I had a similar audio problem when my pc went into hibernate and when I rebooted (as it didn`t hibernate for some reason) the startup ubuntu sound played fine but I had no audio in anything.

For me the option was that it had somehow changed my default soundcard to the built in pc audio. No idea why the start up sound worked but using the audio preferences I changed the default output back to the correct one and it was okay again.

Might be a possibility in your case.

---

### Post by Ferio on 2010-05-08
No, the sound card seems to be the right one, but thank you!

---

### Post by Kevanx on 2010-05-08
Really strange behaviour. I'm not really familiar with Spotify, but my guess would be that something is muted by accident, and it's possible that uninstalling/reinstalling doesn't clear the preferences entirely.

Open your sound preferences (right click on the volume icon) - be sure that no "mute" boxes are checked. Try adjusting the volume.

If that doesn't work, open a terminal (Accessories > Terminal)
and type:
```
alsamixer
```

If any of the volumes are at 0, or have the letters "MM" underneath them, hit m to unmute, or increase the volume, as appropriate.

If that doesn't work try installing PulseAudio's volume control:
```
sudo apt-get install pavumeter
```, and fiddling with the settings there.

---

### Post by Ferio on 2010-05-08
I think it must have been some Medibuntu update or something, I've just reinstalled the whole system but /home and it works like a charm. Thank you!

---

### Post by Ferio on 2010-05-09
Oh, no, it's happened again, and I was using Spotify, so I can tell it's related to it.

---

