---
title: "[SOLVED] Lost sound in TV apps"
date: 2008-12-02
forum: Multimedia Software
---

### Post by stoppage on 2008-12-02
Hi, I'm hoping somebody can help me out here, I've lost sound on both my TV apps &#8222;Tvtime&#8220; and &#8222;XdTV&#8220; and microphone also fails. Running &#8222;Gutsy&#8220;....nForce3 250Gb AC'97 Audio Controller....using Nvidia CK8S ALSA capture device and tuner is SAA7134/SAA7135HL Video Broadcast Decoder. I connect straight from tv card into sound card with audio lead and the sound from output of tv card is o.k., the sound card just isn't processing it through although everything played internally works. I have two identical &#8222;Gutsy&#8220; installations (one I use just as test, which is fully-functional including all sound), so I use exactly identical mixer settings and still no sound....the problem lies elsewhere. I've tried a multitude of other settings, I've tried a reinstall (Synaptec) of both ALSA and OSS, nothing works, I'm way out of my depth here and would really appreciate any help, am still more or less new to Ubuntu.

---

### Post by stoppage on 2008-12-08
So I've stumped the entire Ubuntu community, huh?

---

### Post by stoppage on 2008-12-09
To those with a similar sound scenario, I eventually found a combination of settings which solved microphone and other problems.....
In volume control/ edit/preferences &#8222;Channel Mode&#8220; activated and set to 2 channels.
Settings under System/Preferences/Sound also changed, see screenshot..[http://img408.imageshack.us/img408/7744/soundpreferencesso6.png]("http://img408.imageshack.us/img408/7744/soundpreferencesso6.png")
Sound in Ubuntu, in my opinion, is too much hit 'n' miss, many other people have had similar problems, just check out the forums

---

