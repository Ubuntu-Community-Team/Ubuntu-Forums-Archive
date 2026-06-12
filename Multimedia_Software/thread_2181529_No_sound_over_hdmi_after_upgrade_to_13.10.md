---
title: "No sound over hdmi after upgrade to 13.10"
date: 2013-10-18
forum: Multimedia Software
---

### Post by Fanas on 2013-10-18
It had happened before, there were no sound after installing 13.04, but I was able to get it working by installing alsa daily, but now it's not working even after I did that.

---

### Post by Yellow Pasque on 2013-10-18
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Xorlium on 2013-10-18
I have the exact same problem. It WORKS in windows (wtf?), but not in linux. 

My sound info is here: [http://www.alsa-project.org/db/?f=b835d5e76da7efb24784476eefb7e6d0459b75d9](http://www.alsa-project.org/db/?f=b835d5e76da7efb24784476eefb7e6d0459b75d9)

I've tried playing with the audio settings, changing it to hdmi, but it just won't play sound over hdmi. It plays it in the laptop speakers.

Thank you,
Xorlium

---

### Post by Xorlium on 2013-10-21
bump. Anybody? No hdmi sound... only workarounds I've found are for ATI stuff, but no nvidia...

---

### Post by sean-fitzpatrick on 2013-10-27
In my case this was due to the fact that upgrading introduced a new volume control interface that conflicted with the old one (which is still installed). Clicking on the sound indicator in the panel and choosing Sound Settings got me this controller:
[ATTACH=CONFIG]247304[/ATTACH]
It was showing HDMI selected, and sound being output, as above, but no sound was coming out of the speakers. In the last tab, I had the option of setting HDMI to 'off', as in this screenshot:
[ATTACH=CONFIG]247305[/ATTACH]
Doing so switched the sound over to analog, and I got sound from the speakers. (I've got dual input on my speakers; they're connected directly to the computer with the analog output, and to the TV I use as a monitor, which is receiving the HDMI output.) Then I went to System Settings --> Sound, and discovered that the old interface (the one that the sound indicator linked to in 13.04 and earlier) is the one that showed up, as pictured below:
[ATTACH=CONFIG]247306[/ATTACH]
In this settings dialog, analog output was selected. Since I had set HDMI to 'off' in the other interface, I no longer saw the HDMI option. Turning HDMI back on in the first interface and rebooting brought back the HDMI option, and selecting it restored HDMI sound. So my guess is that one interface had HDMI selected while the other had analog selected, but that's just my guess.

---

