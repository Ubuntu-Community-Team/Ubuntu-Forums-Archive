---
title: "Skype and PulseAudio will NOT get along."
date: 2013-03-08
forum: Multimedia Software
---

### Post by CinoxFellpyre on 2013-03-08
Ok.

I cannot make calls properly when using skype without elevated privileges. Sudo works, but every file transfer is treated as root permission only, and it's really irritable.

Specifically, when I make a call, I can't talk, the other guy hears his own voice, and the Pulseaudio sound meters that tell you how loud it is, it freezes.

Any suggestions without doing some crazy stuff? We can save the crazy stuff for emergencies :V

---

### Post by xc3RnbFO8P on 2013-03-08
Did you check Phonon settings

---

### Post by CinoxFellpyre on 2013-03-08
Yea, internal mic, and things seem ok.

---

### Post by CinoxFellpyre on 2013-03-12
bump

---

### Post by chip616 on 2013-03-17
I battled with two of my machines and Skype 4.1 this weekend.  I had two issues with the Asus netbook, only one with the Dell laptop.

My Asus X202e does not have built in microphones. No wonder I couldn't make them work.

My Dell laptop does not have a lid camera, so on both of these machines I use an external USB camera / mic combo.

Phonon was indeed the key to getting the USB camera/mic combo to work. When I have the USB camera/mic plugged in, it will show up in the Device Preference tab of Phonon in Audio Recording | Communication, Audio Recording | Recording, and Audio Recording | Control. What I didn't realize is the way that Phonon works. Though I would select a device, that is not what Phonon is expecting. One needs to PROMOTE that device to the top of the list, then apply it so it 'sticks'. I did this in all 3 of the above settings, promoting my Quick Cam Pro to the top of the list under all three categories under Audio Recording. I don't know if this was necessary in all of these places, but it now works.

By the way, this is on Kubuntu 12.04 with Pulse fully enabled.

Hope this helps you.

Frank.

---

