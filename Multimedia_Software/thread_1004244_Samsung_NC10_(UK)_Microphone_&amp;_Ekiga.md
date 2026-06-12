---
title: "Samsung NC10 (UK) Microphone &amp; Ekiga"
date: 2008-12-07
forum: Multimedia Software
---

### Post by jaseanton on 2008-12-07
1) Updating ALSA driver

I updated the Alsa drivers as stated here.
[https://help.ubuntu.com/community/NC10#Audio%20-%20Alsa%20Driver](https://help.ubuntu.com/community/NC10#Audio%20-%20Alsa%20Driver)

2) Enabling Microphone

Then double-click on volume icon near clock, 
Preferences > Input Source (tick)
Preferences > Microphone (tick)
Preferences > Front Mic (tick)
Close preferences

Options Tab
Choose Front Mic

3) Installing latest Ekiga (3.0.1)
System > Administration > Synaptic Package Manager
Settings > Repositories > Third Party Software > Add
Paste:
```
deb http://ppa.launchpad.net/tlbdk/ubuntu intrepid main
```
Click 'Add Source'

Reload > Mark All Upgrades > Apply

Ekiga 3.0.1!

Still to test: Speaker in Ekiga

---

