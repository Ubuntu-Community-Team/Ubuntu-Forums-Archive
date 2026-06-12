---
title: "Another Karmic sound thread!!"
date: 2009-11-06
forum: Multimedia Software
---

### Post by fidelandche on 2009-11-06
Hi,

 I upgraded from Jaunty using the update manager and lost sound. I have tried searching the forums, Launchpad and Google for answers. I have tried everything suggested but still no sound. I have the correct grub installed, I have updated the system.

The only thing that worked was this [http://ubuntuforums.org/showthread.php?t=1307491&page=3  ]("http://ubuntuforums.org/showthread.php?t=1307491&page=3")

But only until I rebooted then the sound was lost again. There is no sound card picked up in the sound preferences. The onboard sound card is Sigma Tel STA9250.

The laptop is a Gateway ML6226B

---

### Post by kostkon on 2009-11-06
Have you tried [these suggestions]("http://ubuntuforums.org/showthread.php?t=1307019")?

---

### Post by fidelandche on 2009-11-07
Yes apart from slmodemd, as unsure where to find out if it is running. I have tried looking in the system monitor but cannot see it running there, any idea of where I can find out if it is running and if it is how to kill it.

---

### Post by Defrector on 2009-11-07
My install likes to mute and/or lower my volume all the way down at boot. Have you checked your volume settings?

Note: Volume could be up while still muted. Both must be up.

EDIT: Sorry I missed the part where the sound didn't appear in prefs, but I'll leave this here anyway.

---

### Post by fidelandche on 2009-11-07
Both are up but I am unable to unmute and in sound preferences the sound card is not picked up at all

---

### Post by fidelandche on 2009-11-07
When I do this,

# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload

It works while the laptop is on, but when I reboot I have lost sound again, is there any way of saving this?

---

