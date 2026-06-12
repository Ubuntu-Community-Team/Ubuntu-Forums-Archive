---
title: "Terrible sound over HDMI"
date: 2014-02-16
forum: Multimedia Software
---

### Post by icu12345 on 2014-02-16
So I've got an old laptop (ubuntu 13.10 64-bit) with a mobility radeon hd 4000 series graphics controller. At first there was no sound over hdmi because, as I learned later, it was disabled by default. Tried this solution: [http://learnedstuffs.wordpress.com/2013/12/14/enabling-ati-radeon-hdmi-audio-output-on-ubuntu-13-10/](http://learnedstuffs.wordpress.com/2013/12/14/enabling-ati-radeon-hdmi-audio-output-on-ubuntu-13-10/)

So now I am able to play sound through hdmi but the sound quality is bad. Definately not good enough for movies or music. Has anyone had this issue? I tried searching but couldn't find a solution.

---

### Post by Yellow Pasque on 2014-02-16
Can you be a bit more specific about the "bad" sound quality? Is it crackling, skipping, or just plain distorted?

One thing to try (and it's easily reversible): [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by Yellow Pasque on 2014-02-16
Oh, it might be the cable itself causing the issue.

---

### Post by frank18 on 2014-02-16
> **icu12345 said:**
> So I've got an old laptop (ubuntu 13.10 64-bit) with a mobility radeon hd 4000 series graphics controller. At first there was no sound over hdmi because, as I learned later, it was disabled by default. Tried this solution: [http://learnedstuffs.wordpress.com/2013/12/14/enabling-ati-radeon-hdmi-audio-output-on-ubuntu-13-10/](http://learnedstuffs.wordpress.com/2013/12/14/enabling-ati-radeon-hdmi-audio-output-on-ubuntu-13-10/)

So now I am able to play sound through hdmi but the sound quality is bad. Definately not good enough for movies or music. Has anyone had this issue? I tried searching but couldn't find a solution.

Me too have bad sound but when use sound on both hdmi and pc external audio on some streams, but if change to hdmi only is ok.

---

### Post by icu12345 on 2014-02-17
> **Temüjin said:**
> Can you be a bit more specific about the "bad" sound quality? Is it crackling, skipping, or just plain distorted?

One thing to try (and it's easily reversible): [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

Thanks, I did try it but it didn&#7831; help. Sound is crackling. The crackling itself does not depend on the volume setting, just on the frequency.

The hdmi cable, tv, speakers, etc. are all checked. If the laptop boots into windows (it's a dual boot system) the crackling is gone, so it must be some setting within ubuntu...

---

### Post by DeathTorrent on 2014-04-05
iI had the same problem, and this worked for me...I'm not sure why this worked, lol, but it did.
Fist, open a terminal and install the Pulse Audio Volume Control app.
```
sudo apt-get install pavucontrol
```
Once it installs, make sure the application you're using to play the audio is open (for me, it was netflix...lol), and open the Pulse Audio Volume Control app.  Once it's open, futz around with the volume, and for some odd reason, this should fix the issue.  
If it doesn't, open another application that you wont use much (for me, rhythmbox, since I use clementine), and start playing a song or something.  Change the audio output to your computer's internal speakers (assuming you're using a laptop), futz with the volume on your HDMI stream, and you should be good to go.
Like I said, I dont know why this fixes it, it just seems to work for me.  Good luck! 8-)

---

