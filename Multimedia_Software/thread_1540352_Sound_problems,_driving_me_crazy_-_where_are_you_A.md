---
title: "Sound problems, driving me crazy - where are you ALSA?"
date: 2010-07-27
forum: Multimedia Software
---

### Post by jayemee on 2010-07-27
Hey there,

  I'm just sending out some feelers, because I'm at my wit's end trying to get the sound to work on this set up - any help would be much appreciated, and will help prevent my premature embolism.

  So I'm running Lucid, and the sound was buggy from the beginning - the particular problem that caused me issues is that I could only have sound outputting from one program at a time, so if I had amarok playing (or even paused) I couldn't watch a flash video or something, which was a bit unworkable for me. Cue much googling around these forums, and much faffing about with as many different pulseaudio/ALSA configurations as I could find advice on, to no avail. 

  I'd seen OSS mentioned a few times as a bit of a cure-all, so I thought it'd probably be worth a try. I followed the instructions described here:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

  Then on next boot, hey presto, I could have simultaneous sound from all my programs! Fantastic! Or so I thought. When I next went to alter my volume from the tray at the top, the icon had disappeared. No problem I thought, I've obviously just removed the indicator applet by accident - but no, the envelope was still there, the applet just wasn't showing the volume indicator.

  If I go to system>pref>sound I get a "waiting for sound system to respond" error, which never goes anywhere.

  Aplay -l tells me that I have no sound card installed.

  Trying to follow the sound troubleshooting page (below) doesn't avail me any, as it makes reference to the ALSA driver and module, neither of which I seem to have anymore.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

(this page actually details how to output a nice URL factsheet, the latest one being here [http://www.alsa-project.org/db/?f=d061e070b1bda845e1c3f8ffc99c3c132a3f27fd](http://www.alsa-project.org/db/?f=d061e070b1bda845e1c3f8ffc99c3c132a3f27fd) - note lack of drivers etc / recognised sound card, which is clearly working due to the lovely music coming out of it)

  I've tried installing/re-installing ALSA, but nothing I try seems to work, and I'm really at a loss - I'm really just stabbing in the dark. I kind of feel some way of scrapping it all and starting over is probably the way, but I really don't want to do a clean install (as the rest of my system took so long to tweak), and I also don't want to go back to the way things were fresh after getting lucid going. I mean, I'd rather have simultaneous playback than a convenient volume slider, but still, I'd much rather have both.

  Apologies for vagueness and general confusion - am afraid I've been  trying everything I can with not much order (often going in cycles), so I  forget what I've tried and how (plus I'm still a newb when it comes to  linux and the terminal and whatnot).

  Any help you could provide would earn you my eternal gratitude, and  possibly make you reincarnate as a totally awesome pirate ninja person.

---

### Post by Yellow Pasque on 2010-07-28
See the instructions for ossxmix and gnome volume control here:
[https://help.ubuntu.com/community/OpenSound#Configuring%20Applications%20to%20Use%20OSS](https://help.ubuntu.com/community/OpenSound#Configuring%20Applications%20to%20Use%20OSS)
This PPA works for Lucid too: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)
pirate ninja, eh?

---

### Post by lidex on 2010-07-28
The process you went through removed pulseaudio, which provided the volume control. There is a way to get a similar one:
[http://guide.ubuntuforums.org/showthread.php?p=9570719](http://guide.ubuntuforums.org/showthread.php?p=9570719)
Do you want to stick with OSS or go back to pulse/alsa?

Edit: Speak of the devil...^

---

### Post by Yellow Pasque on 2010-07-28
> **lidex said:**
> Speak of the devil...^

MUAHAHAHA :twisted:

---

### Post by jayemee on 2010-07-28
Thanks for the quick replies guys, very much appreciated!

Lidex, I think  my inclination at present is to stay with OSS for a little bit and give it a few tweaks, as so far it's the closest I've coming to what I want (at least in terms of being able to play multiple programs at once).

Temüjin, I've done the ossxmix (which is really useful!), but I'm not sure if about the gnome volume control - I'm presuming the PPA mentioned in that guide is the same one you and Lidex are both talking about, but I'm not sure if I'm doing the right thing to install it. I've followed the instructions about adding the PPA and updating (following the 'read about installing' bit), but I'm not sure if that's installing the packages I need, or just enabling me to do so...

And yes, pirate ninja. If it helps, you'll probably be able to fly as well.

---

### Post by jayemee on 2010-07-29
OK, so I think I got a better handle on this PPA lark - so having installed the PPA (or whatever the correct terminology is) I then went to terminal and successfully added (I think) gnome-applet, -media and settings-daemon (although I couldn't add the last one, libcanberra). Have restarted, and still no volume control - not sure if I need to activate anything...

I also no longer have a 'Sound' option in system, which is a little worrying, but I can live without it.

---

### Post by Yellow Pasque on 2010-07-29
Right-click the panel, select 'Add to Panel' and 'Volume Control'

---

### Post by jayemee on 2010-07-29
Hmm, that's not an option, which I'm presuming means I've done something wrong somewhere along the line..?

Also, just want to thanks, I really appreciate the time you're taking to help.

---

