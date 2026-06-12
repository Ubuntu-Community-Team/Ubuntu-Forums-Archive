---
title: "Issue with sound card."
date: 2009-03-09
forum: Multimedia Software
---

### Post by gdonwallace on 2009-03-09
I've been running Ubuntu for about 6 to 7 months now.  

Previously I worked in a Unix eviro, so not a complete newby to Unix/linux.  

Anywho, I've started having issues with sound.  After leaving my system up for about 3 -4 days, I have no sound.  I start the sound app from the preferences menu and try to run the test opiton and get an error that there is no sound-card for ALSA to connect to.

However; when I reboot my machine, sound works fine.  

I'm running Ubuntu 8.10 on a Dell Vostro 200.  So I have all Dell hardware.  The onboard sound is Intel HD Audio.

---

### Post by markbuntu on 2009-03-09
This is a known problem with the sound driver that can only be fixed when an update comes along. But, for now you can avoid having to reboot by restarting alsa and pulseaudio. In a terminal:


```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```

---

### Post by gdonwallace on 2009-03-09
Thanks for the help.

I'll try that the next time I loose sound.

---

