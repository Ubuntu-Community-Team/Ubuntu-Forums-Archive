---
title: "gtk-recordMyDesktop not recording system sound"
date: 2010-06-14
forum: Multimedia Software
---

### Post by go_beep_yourself on 2010-06-14
I've been trying to make screencast, but I also want it to capture the sound coming from the computer; In other words, I do not mean the microphone. I tried changing the sound device from DEFAULT to pulse with no avail. Please somebody tell me how I can do it.

---

### Post by mocha on 2010-06-15
Use this instead [http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

I haven't touched recordmydesktop ever again.

---

### Post by Breambutt on 2010-06-15
ALSA doesn't have the right kind of loopback stuff (without additional config files) as far as I'm aware of, but if you have PulseAudio you can fidget the recording source from the PulseAudio Volume Control from "Foo" to "Monitor of Foo" from some dropdown menu.

---

### Post by williamts99 on 2010-09-20
You can record everything that comes out of the speaker using recordmydesktop and pulse.

In recordmydesktop I changed the Advanced>Sound>Device name from 'DEFAULT' to 'default'.
Then I installed pavucontrol using ```
sudo apt-get install pavucontrol
```
Run pavucontrol and go to the recording tab **while recordmydesktop is actively recording** something, you will see an item called
"ALSA plug-in[recordmydesktop]:ALSA capture from"
You must change this to Monitor of Internal Audio Analog Stereo

Best Regards,
Will

---

### Post by gerowen on 2010-10-12
> **williamts99 said:**
> You can record everything that comes out of the speaker using recordmydesktop and pulse.

In recordmydesktop I changed the Advanced>Sound>Device name from 'DEFAULT' to 'default'.
Then I installed pavucontrol using ```
sudo apt-get install pavucontrol
```
Run pavucontrol and go to the recording tab **while recordmydesktop is actively recording** something, you will see an item called
"ALSA plug-in[recordmydesktop]:ALSA capture from"
You must change this to Monitor of Internal Audio Analog Stereo

Best Regards,
Will

Thanks, this really helped me out with my issue.

---

### Post by tlan on 2012-05-22
> **williamts99 said:**
> You can record everything that comes out of the speaker using recordmydesktop and pulse.

In recordmydesktop I changed the Advanced>Sound>Device name from 'DEFAULT' to 'default'.
Then I installed pavucontrol using ```
sudo apt-get install pavucontrol
```Run pavucontrol and go to the recording tab **while recordmydesktop is actively recording** something, you will see an item called
"ALSA plug-in[recordmydesktop]:ALSA capture from"
You must change this to Monitor of Internal Audio Analog Stereo

Best Regards,
Will

YES, This fixed my issue too, i noticed using kazam there were two options for sound recording and i was looking for this option with gtk-RMD, I did not know about PavControl, Excellent fix and i am running 12.04 64bit. RMD is working again, Thanks Will :P

---

