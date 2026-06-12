---
title: "3 monitors on 11.10 - catalyst keeps crashing"
date: 2011-12-29
forum: Multimedia Software
---

### Post by chaosdesigner on 2011-12-29
Until recently I have been running 10.10 and everything there worked like a charm. I had the catalyst installed for my two hd3600 radeons and I could easily work with all my 3 monitors. After long consideration I eventually updated to 11.10 and now (of course) nothing works anymore. 

With ubuntu 10.10 the official amd catalyst driver was the only one that let me configure the two graphic cards so I figured its my best shot with 11.10. The newest version (11.12) installs fine but then when I try to make changes to the settings it just crashes always when I press 'Apply'. How do I get the driver working so that I can have all my monitors back in use. Anybody else experience these crashes?

Thank you

---

### Post by 4Orbs on 2011-12-29
I run only two monitors, but had the same problem with catalyst crashing when trying to save settings (with Ubu, Xubu and Lubuntu). Don't know if this is the only way to do it, but it was the easiest way for me. Install the kde desktop; log into a kde session; configure and save catalyst settings; logout then log into Ubuntu session.

Of course, installing the kde desktop uses a hefty amount of extra disk space and adds a bunch of apps that clutter the system menu... but it made the Catalyst Control Center functional. I actually enjoy using the kde session occasionally.

---

### Post by unnddd on 2011-12-29
I'm not using Ubuntu at the moment but if I recall correctly it will work fine if you just run "sudo amdcccle" from a terminal. There's no need to install KDE or anything like that. My guess is that it's some sort of conflict with gksu.

Also, I must add that compositing + Xinerama on ATI is impossible. That's what's keeping me on Windows, after trying several different distributions and failing to get that combination to work. The open-source drivers don't cut it for gaming in Wine, unfortunately.

---

### Post by chaosdesigner on 2011-12-29
Wow, thanks a lot! I installed KDE and there I really actual could configure catalyst, and under KDE all three displays work like a charm. Under gnome the amdcccle command did work as well, and I am now also able to configure my drivers there. The only problem I'm currently having is that both my extra screens are just white right now. I can go to them with the mouse but the courser turns into a black 'X' and I can't drag windows into these desktops.. This only happends with gnome.

---

### Post by unnddd on 2011-12-29
> **chaosdesigner said:**
> Wow, thanks a lot! I installed KDE and there I really actual could configure catalyst, and under KDE all three displays work like a charm. Under gnome the amdcccle command did work as well, and I am now also able to configure my drivers there. The only problem I'm currently having is that both my extra screens are just white right now. I can go to them with the mouse but the courser turns into a black 'X' and I can't drag windows into these desktops.. This only happends with gnome.

Did you manage to get compositing and Xinerama both working in KDE? If so I'll have to give Kubuntu another go!

---

### Post by chaosdesigner on 2011-12-30
> **unnddd said:**
> Did you manage to get compositing and Xinerama both working in KDE? If so I'll have to give Kubuntu another go!

Xinerama is working flawlessly, now even under gnome. Haven't tried getting into compositing, not sure if I want to right now to be honest. Have made a lot of traumatizing experiences with it and for now I want to enjoy my working configuration for at least a while before I mess everything up again ;).


Been always a amd/ati-man but after a while it really becomes a pain under Linux..

---

### Post by Circlingthesun on 2011-12-31
> **unnddd said:**
> I'm not using Ubuntu at the moment but if I recall correctly it will work fine if you just run "sudo amdcccle" from a terminal. There's no need to install KDE or anything like that. My guess is that it's some sort of conflict with gksu.

Also, I must add that compositing + Xinerama on ATI is impossible. That's what's keeping me on Windows, after trying several different distributions and failing to get that combination to work. The open-source drivers don't cut it for gaming in Wine, unfortunately.

For me "sudo amdcccle" only worked after installing Kubuntu.

---

### Post by alphacrucis2 on 2011-12-31
> **chaosdesigner said:**
> Until recently I have been running 10.10 and everything there worked like a charm. I had the catalyst installed for my two hd3600 radeons and I could easily work with all my 3 monitors. After long consideration I eventually updated to 11.10 and now (of course) nothing works anymore. 

With ubuntu 10.10 the official amd catalyst driver was the only one that let me configure the two graphic cards so I figured its my best shot with 11.10. The newest version (11.12) installs fine but then when I try to make changes to the settings it just crashes always when I press 'Apply'. How do I get the driver working so that I can have all my monitors back in use. Anybody else experience these crashes?

Thank you

Did you try downgrading to cat 11.11?

---

