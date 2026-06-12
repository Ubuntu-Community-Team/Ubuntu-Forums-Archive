---
title: "Trying to setup Audacity to record from line-in"
date: 2011-03-05
forum: Multimedia Software
---

### Post by keithgroben on 2011-03-05
Hello everyone. I am trying to get Audacity to record from a line in. Seems like it should be a fairly easy setup. I discovered that Audacity needs PulseAudio. So I installed that, and don't know how to configure it.

I set the sound preferences >> Input to line in. I am using a desktop that has a line-in on the front and back, so I'm not sure which it will pick up, so I have been testing both. :???:

I'm sort of stuck and am hoping that I can get this figured out.

---

### Post by shantiq on 2011-03-12
ok there keith the **line-in** is mute by default which is baffling but that is the way it is


i am doing this with **alsa** here which works fine too but i am sure pulse will work too  (use pavucontrol if you want to stay with pulse instead of alsa-mixer but i suggest try with alsa first)



so first thing is to enable the **line-in**


to do this we can use [**kpoole advice** ]("http://ubuntuforums.org/showpost.php?p=10515086&postcount=24")


to install open terminal   ```
sudo apt-get gnome alsa-mixer
```   or install it through synaptic or ubuntu software centre



then find it under    applications/sound and video

unclick the relevant ones for you  depending on your setup


=================================================


then go to audacity


and click on view/toolbars/devices


click on that then pick your device you want as a line-in



=================================================

**or** you can go to edit/ preferences/devices as another route


=================================================


**you will then see** a drop-down box on your audacity see attached picture   pick   **mix0**



**PS:    Also make sure when you go to system/ preferences/sound you have chosen the right input for the line -in you want in this case**



you should be good to go:KS

---

### Post by shinobi9 on 2011-12-13
So simple I never though of checking, makes no sense... Also using alsa, been driving me crazy... lol

Thank You!!! 

> **shantiq said:**
> ok there keith the **line-in** is mute by default which is baffling but that is the way it is


i am doing this with **alsa** here which works fine too but i am sure pulse will work too  (use pavucontrol if you want to stay with pulse instead of alsa-mixer but i suggest try with alsa first)



so first thing is to enable the **line-in**


to do this we can use [**kpoole advice** ]("http://ubuntuforums.org/showpost.php?p=10515086&postcount=24")


to install open terminal   ```
sudo apt-get gnome alsa-mixer
```   or install it through synaptic or ubuntu software centre



then find it under    applications/sound and video

unclick the relevant ones for you  depending on your setup


=================================================


then go to audacity


and click on view/toolbars/devices


click on that then pick your device you want as a line-in



=================================================

**or** you can go to edit/ preferences/devices as another route


=================================================


**you will then see** a drop-down box on your audacity see attached picture   pick   **mix0**



**PS:    Also make sure when you go to system/ preferences/sound you have chosen the right input for the line -in you want in this case**



you should be good to go:KS

---

