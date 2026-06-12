---
title: "No sound, running Ubuntu on IBM ThinkPad laptop"
date: 2008-08-24
forum: Multimedia Software
---

### Post by canyonlands on 2008-08-24
I have no sound at all. I've installed Ubuntu this weekend. I got the internet connection working and downloaded all the updates listed on the notification. I ran the hardware testing program in System, Hardware Testing and all passed except the audio. The audio testing detected a sound card (I82801DBICH4). I sent the test results to LaunchPad - haven't heard back. I can play movies (no sound though) and other things seem to work.
I've unmuted sound on all the controls I can find. There is no sound for any events. For example there are no beeps for login or any other events.
The laptop is an IBM ThinkPad, X31, and Ubuntu is the only operating system on it.

Thanks in advance for your time and attention!

---

### Post by bullfrog41 on 2008-09-14
Open the /lib/modules/2.6.24XXX/module.alias and comment out the first two occurences of AES that link to (padlock and geode hardware) towards the botton of the file. Reboot and boot will speed up, wifi will work, and sound will return. Worked for my x31.

---

