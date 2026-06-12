---
title: "Tascam US122 with 12.04"
date: 2012-05-31
forum: Multimedia Software
---

### Post by Evil-Ernie on 2012-05-31
Hello all, I have a Tascam US122 (older version not MK2) and I am trying to get it working in Ubuntu 12.04 desktop.

I have got the lights working and the input is showing in ALSA but I can't get output from it :(

Anybody know how I can get output from the card?

---

### Post by bnr on 2012-06-21
Not sure what you mean by "output from the card"; Once the lights are on it just works for me.

Do you mean that you can't get sound from the tascam into the computer (technically this is input not output) or are you trying to send sound out the line out or midi out (I believe the phones are just a pass through, but I could be wrong). If you are using the tascam as an output device it needs to be selected by the sound server as the main output, this would be in your DE (gnome, kde, unity, etc,) sound settings.

My set up is to just use the tascam as input and use the normal sound card as output, and as I mentioned it just works.

**Edit** 

I do believe that some software (jackctrl) lets you pick wich device is the output regardless of what the sound server settings are.

---

### Post by thalro on 2012-09-19
Hello,

I have exactly the same problem. Has this been solved? I can't seem to find any useful information regarding Ubuntu 12.04 and the us-122. I remember that on previous Ubuntus, i had to follow some lengthy instructions and then it worked. Now, installing the alsa-firmware brings up the light on my us-122 but i do not get sound.  The card appears in the sound settings menu, but when I select it as the output, nothing comes out of it (rhythmbox even stops playback). If I try to start Jack it says:
ALSA: cannot set hardware parameters for playback

 The card works fine in windows. Any ideas?

cheers,

t.

---

