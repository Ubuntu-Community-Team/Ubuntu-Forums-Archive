---
title: "Realtek ALC892 sound issues"
date: 2011-08-20
forum: Multimedia Software
---

### Post by bbossola on 2011-08-20
Hi all,

I was experiencing various problems with the audio of my machine:
[http://www.alsa-project.org/db/?f=74f5d3540ffe308a21f0c393eba675e3598e1532](http://www.alsa-project.org/db/?f=74f5d3540ffe308a21f0c393eba675e3598e1532)

So I decided to try to install the Realtek drivers, as it seems that this ALC892 is a kinda problematic chipset. Downloaded from LinuxPkg_5.16rc17.tar.bz2 from [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

I followed the instruction (ehm... I am a bit rookie here) and apparently everything went well. However, after the reboot, I discovered that all my audio devices are gone. Apparently no driver are loaded at the moment:
[http://www.alsa-project.org/db/?f=4add4eb09659e836cd48a1bb71baadd7c20eae54](http://www.alsa-project.org/db/?f=4add4eb09659e836cd48a1bb71baadd7c20eae54)

What's the best thing to do now? I'd like to leverage the Realtek install, but at the moment I'm kind of stuck.

Any help will be really appreciated!
Thanks in advance,

    Bruno

---

### Post by bbossola on 2011-08-20
Reinstalled everything using these instructions:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

However, original issues are back:
- no switch between earphones / speaker when jack is in
- no sound from the external mic

Very frustrated atm :(

---

### Post by .... on 2011-08-20
See if this helps after restarting:
```
echo "options snd-hda-intel model=clevo" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

[http://forums.fedoraforum.org/showthread.php?p=1499651#post1499651](http://forums.fedoraforum.org/showthread.php?p=1499651#post1499651)

---

### Post by bbossola on 2011-08-28
No joy :( when I insert the plug the speakers are still working. 

The FN+5 can mute/unmute the speakers, but it's a manual operation that you need to to each time you plug / unplug the earphones... quite impractical

Any other hint?

---

### Post by skyy143 on 2011-09-21
[http://www.alsa-project.org/db/?f=99f4ac622fd11b8f2beb7fbef4279578a49b66e1](http://www.alsa-project.org/db/?f=99f4ac622fd11b8f2beb7fbef4279578a49b66e1) 
hi i did the same thing and im still stuck with no sound i do not know what to do im a linux virgin thanks

---

### Post by bbossola on 2011-10-08
If you reinstall everything using these instructions:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

you will have your system as before (with the original issues)

---

