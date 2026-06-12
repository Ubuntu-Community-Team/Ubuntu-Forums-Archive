---
title: "VLC crackling sound"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by mlucian72 on 2007-06-22
I have VLC 0.8.6 with Ubuntu Feisty and the sound in VLC is very bad (crackling).
 I've tried to change the plugin from to OSS but I can't find it under "Advanced" in the "Audio" preferences.
 How do I fix this?
 I've updated the VLC with the latest plugins, but I still have the same crackling sound.
XMMS and everything else is fine.
 Does anyone know know to fix this?

 Thanks!

---

### Post by greeneggsnsam on 2007-06-24
If i'm not mistaken you need to turn the volume on VLC itself (the little bar) down until it stops crackling- and turn your speakers up (actually turn them up, like with your hand or remote or whatever you use, or just turn up the ubuntu system volume) so you can actually hear it ;) To set the deafault sound low enough to stop the crackles, go to settings>preferences and lower it to whatever volume your speakers can handle.

---

### Post by mlind on 2007-06-26
this is a known issue in feisty with certain sound cards. Current suspect is alsa-lib instead of vlc.
There's few bugreports about this on launchpad.

---

### Post by tie_dyed_sox on 2007-06-30
I also had  a problem with crackling sounds in VLC but was able to fix it by configuring the ALSA device name in the VLC settings.

Settings -> Preferences -> Audio -> Output modules -> ALSA -> ALSA Device Name

Click 'Refresh list' and select something other than the default.

Hope this helps.

---

### Post by ubu-for on 2007-06-30
> **tie_dyed_sox said:**
> Settings -> Preferences -> Audio -> Output modules -> ALSA -> ALSA Device Name

Click 'Refresh list' and select something other than the default.

That's right! Click on refresh.

[Bug #103025](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025)

---

### Post by RTrev on 2007-06-30
One way I've minimized the problem is to click on Settings in VLC, then select Extended GUI.  Click on the Equalizer tab, and if it's enabled turn down the Preamp a bit.  On my last install it was always enabled by default, but now having reinstalled Feisty 64-bit I find that it's now disabled by default.  Go figure.  But if it's enabled, turn it down or turn it off.. something is being badly over-driven by this component.

---

### Post by mocha on 2007-07-02
> **tie_dyed_sox said:**
> I also had  a problem with crackling sounds in VLC but was able to fix it by configuring the ALSA device name in the VLC settings.

Settings -> Preferences -> Audio -> Output modules -> ALSA -> ALSA Device Name

Click 'Refresh list' and select something other than the default.

Hope this helps.

Hey!  That worked great!  thanks!

---

### Post by bailunrui on 2007-09-21
That worked for me too. Thank you very much!

---

### Post by tie_dyed_sox on 2007-09-22
Glad I could help :)

---

### Post by GatorBait3 on 2007-09-30
Worked for me too! Thanks for the helpful tip!

---

