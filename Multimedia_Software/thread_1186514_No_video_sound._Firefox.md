---
title: "No video sound. Firefox"
date: 2009-06-13
forum: Multimedia Software
---

### Post by drifter2502 on 2009-06-13
After days of trying to get sound streaming video in firefox,installing and reinstalling ubuntu 8.04 and 9.04 I found this solution that works for me,at last!
[https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/49779](https://answers.launchpad.net/ubuntu/+source/firefox-3.0/+question/49779)

sudo killall pulseaudio
sudo alsa force-reload
    (Hit the reset confirmation)
and then go to System>Preferences>Sound and change everything to ALSA

Update:- After this I could not record "What you hear" in sound recorder but after following this..[http://ubuntuforums.org/showthread.php?t=1005196&highlight=power+pulse](http://ubuntuforums.org/showthread.php?t=1005196&highlight=power+pulse)
I was able to use Audacity for recording all inputs. Very happy!

Works for 8.04. Not tried yet in 9.04.

---

### Post by ajgreeny on 2009-06-13
I agree that 8.04 was a bit of a dog's breakfast as far a pulse was concerned, but I have to admit, 9.04 is so much better and has not had any of the sound problems on my computer, that I got from 8.04.  Perhaps worth trying it yourself; in my case it is all, not just sound, so much better than 8.04.

---

### Post by drifter2502 on 2009-06-13
#2. Just about to re install 9.04. I have it on a laptop with KDE desktop. Everything works just fine. Just getting sound and video problems on my P.C. Not re booted yet since I found the above fix and I am not confident that the P,C will remember the change in settings!

---

