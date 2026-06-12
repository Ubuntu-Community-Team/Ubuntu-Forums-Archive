---
title: "Default sound card"
date: 2009-03-18
forum: Multimedia Software
---

### Post by ssj3g0ku on 2009-03-18
i have a problem with my default sound card
i have 2 sound cards one is on board named "Intel High Definition Audio"
and one is cmedia 8738
i tried 
"asoundconf list
Names of available sound cards:
CMI8738
Intel
CX8801"
than "asoundconf set-default-card Intel"
when i reboot the startup sound is again from cmedia
how do i make high definition audio as default ?
thank you

---

### Post by ssj3g0ku on 2009-03-18
please help me.. i need to fix this :(

---

### Post by kostkon on 2009-03-18
Then, the thing you need to do is to install the *PulseAudio Device Chooser* utility (It will create a menu entry in Applications &#8594; Sound & Video). Run it, left-click on its icon in your system tray and select *Volume Control*.

In the *Input Devices* and *Output Devices* tabs you can set the default input and output device to be used by your applications. Right-click on the device you want and enable the *Default* option.

---

### Post by ssj3g0ku on 2009-03-18
its not working :|
i set my default sound and after the reboot the sound is coming from cmedia 
how can i uninstall for good cmedia so i can have only one sound card ?
......
and another thing im trying to apply a rezolution on my monitor from nvidia settings from terminal "sudo nvidia-settings"
when i choose "Save to X configuration file" it closes and in terminal show
"Segmentation fault"
im on ubuntu 8.10(i forgot)

---

### Post by markbuntu on 2009-03-18
If you want to get your sound set up properly go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For multipls sound cards go here

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

For more extensive help go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

