---
title: "Best settings for Creative Sound Blaster X-Fi Extreme in Ubuntu/kubuntu?"
date: 2012-02-10
forum: Multimedia Software
---

### Post by Dlambert on 2012-02-10
Hello, I have the Creative Sound Blaster X-Fi Extreme. And yes, I know, I know support isn't great....but my sound works...at default settings, but it "stutters." I was wondering what the best settings for this sound card are in Ubuntu/Kubuntu? Thank you!

---

### Post by Dlambert on 2012-02-11
Bump

---

### Post by Dlambert on 2012-02-12
Bump

---

### Post by Dlambert on 2012-02-15
So I installed Comice OS 4, and the preconfigurations of that Distro worked great!

---

### Post by Dlambert on 2012-02-29
Nvm, the problem with ubuntu still exists. Any ideas? The sound is jumbled, almost "skipping". I've disabled all other audio devices, what should I set the speaker mode to? Ive got 2 speakers (Green plug). I've also tried alsamixer.

---

### Post by Dlambert on 2012-03-01
Someone please help! bump.

---

### Post by Dlambert on 2012-03-02
Bump :(

---

### Post by Dlambert on 2012-03-04
I'm going to try this: 
 
```
[FONT=monospace]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa[/FONT]
[FONT=monospace]sudo apt-get update[/FONT]
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

---

### Post by Dlambert on 2012-03-09
> I found the solution! 
The first song I listened to was Jimi Hendrix - Bold as Love - then to make doubly sure started watching Machete :grin:

 Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG  IS supported in alsa.

the fix found: [http://ubuntuforums.org/showthread.php?t=1804083](http://ubuntuforums.org/showthread.php?t=1804083)
is to add 
"options snd-hda-intel position_fix=1  model=3stack" 
into /etc/modprobe.d/alsa-base.conf in the options section.

reboot and enjoy!:popcorn:

This fixed it for me!

---

### Post by imbezol on 2012-04-10
> **Dlambert said:**
> This fixed it for me!


Finally.. fixed it for me too. Been fighting with this for a while.

I now have working stereo sound over the optical output to my amp. Seems weird that in the system audio settings I have to select analog stereo output though. No surround sound to the amp I guess. Any attempts to select any other surround (5.1, 7.1 etc) analog or digital settings leads to no sound at all.

---

### Post by Dlambert on 2012-04-10
> **imbezol said:**
> Finally.. fixed it for me too. Been fighting with this for a while.

I now have working stereo sound over the optical output to my amp. Seems weird that in the system audio settings I have to select analog stereo output though. No surround sound to the amp I guess. Any attempts to select any other surround (5.1, 7.1 etc) analog or digital settings leads to no sound at all.

Good to hear!

---

### Post by cgaie on 2012-04-19
> **imbezol said:**
> Finally.. fixed it for me too. Been fighting with this for a while.

I now have working stereo sound over the optical output to my amp. Seems weird that in the system audio settings I have to select analog stereo output though. No surround sound to the amp I guess. Any attempts to select any other surround (5.1, 7.1 etc) analog or digital settings leads to no sound at all.



Can you explain how you fix it?  I have the same problem

Thanks

---

