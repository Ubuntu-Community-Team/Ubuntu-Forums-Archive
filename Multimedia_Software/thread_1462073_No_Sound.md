---
title: "No Sound"
date: 2010-04-25
forum: Multimedia Software
---

### Post by FireStorm102389 on 2010-04-25
There has been some problems with my sound that I have been experiencing.  Most of the time, and i mean about 99% of the time, my sound will work when i boot my computer and login.

However, When I go to play Runescape, my sound totally just cuts out.  In order to get sound back on and playing outside the Java platform, I have to continuously switch the hardware options in System>Preferences>Sound.

Most of the time, 85% of the time, this will work and my sound will start to work again.  But the other 15% of the time it just never comes back.  I don't understand what is wrong with my sound.  And just when i booted my computer now, there was no volume and I couldn't get it to come back at all.

Is there something I can do to fix this issue? And what might be causing this? I never had volume issues when I had this on my computer before.

Pictures of this activity:
Outputs I can pick from
[http://i165.photobucket.com/albums/u72/FireStorm102389/OutputOptions.png](http://i165.photobucket.com/albums/u72/FireStorm102389/OutputOptions.png)

Analog Stereo Duplex Option:
[http://i165.photobucket.com/albums/u72/FireStorm102389/StereoDuplex.png](http://i165.photobucket.com/albums/u72/FireStorm102389/StereoDuplex.png)

Analog Stereo Output Option:
[http://i165.photobucket.com/albums/u72/FireStorm102389/StereoOutput.png](http://i165.photobucket.com/albums/u72/FireStorm102389/StereoOutput.png)

---

### Post by lidex on 2010-04-25
Do 'Part A' here and post results:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by kostkon on 2010-04-26
Are you using Sun Java? Because it has problems working with the software mixer in Ubuntu, that is PulseAudio.

Java tries to access your sound device directly and by doing that it blocks the device, thus your other software is unable to access it (in our case PulseAudio).

You could try [this solution]("http://www.tuxyturvy.com/blog/index.php?/archives/66-Making-Sun-Java-1.6-play-via-PulseAudio.html") and/or search the net for other solutions.

---

### Post by kostkon on 2010-04-26
Actually, a simple solution would be to edit the launcher for Runescape. You could post here the contents of the launcher, if you want to help you modify it accordingly.

---

