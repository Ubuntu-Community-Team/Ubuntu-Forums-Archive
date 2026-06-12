---
title: "ALSA: Headphones work but not unbuilt speakers"
date: 2008-08-09
forum: Multimedia Software
---

### Post by theirishfozz on 2008-08-09
I'm aware there are quite a few people who have had problems like this but I cant seem to fix this issue despite all the proposed solutions.

Sound works with headphones although its fairly quiet. I can access the default volume control (OSS mixer I think) and change volume levels.

Here is the output of aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 5: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


When I try to run alsamixer it gives this error:
> ALSA lib simple_none.c:1741:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument

I tried installing the patch here: [http://ubuntuforums.org/showpost.php?p=4871189&postcount=30]("http://ubuntuforums.org/showpost.php?p=4871189&postcount=30") however it resulted in no devices showing up in the aplay -l list. bah. I tried following the comprehensive sound guide but it fails when it says to run alsamixer :(.

any ideas?
thanks

---

### Post by punkybouy on 2008-08-09
Right click on the speaker up on the upper panel and open the volume control.  Under the file menu item go to "change device" and go through each device there and make sure there isn't something that isn't muted.  I spent about 30 minutes today trying to get Skype to work on a Hardy update and ran across one of the devices that had a microphone muted and that fixed it.

---

### Post by Yellow Pasque on 2008-08-09
Try OSS4: [http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

---

### Post by theirishfozz on 2008-08-10
Hey, thanks for the responses guys. I seem to remember volume control having no effect. I tried to use OSS4 which didnt end well but I'll have a look at that tutorial and have another go. Hopefully it'll work.

EDIT: I tried running through your guide Tem, but certain aspects of it didnt work. Part of the OSS install worked with errors (not sure which) and I ended up with no sound at all. For a while I had drivers detected but my devices list in the sound options page was empty. ossxmix is about 3000px wide and fairly useless. Im going to try and revert to alsa and get some sound working I think. 

I tried to reinstall oss but when I try to install the deb package it complains about some missing directories. I dont know where they could have gone since the last install. I also dont know what step I could have left out that created the directories. Argh. Back to square one.

---

### Post by StrangeFreedom on 2008-08-16
I have the exact same problem. No solution jet unfortunately.

---

### Post by Yellow Pasque on 2008-08-16
Perhaps the issue has been fixed in ALSA 1.0.17: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by theirishfozz on 2008-09-05
In the end I switched to OSS. Sometimes sound doesnt work when I have acpi disabled and I have to start up with acpi enabled to get it working again. Before an application or the system starts using sound there is a crashing noise from the speakers but internal speakers and the green line-out work fine so Im happy. I also got sound working in more or less every application.

---

