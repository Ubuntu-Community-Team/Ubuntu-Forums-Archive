---
title: "The volume control doesn't control the volume"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by johlin on 2006-07-02
I'm having problems with the gnome volume control. In Ubuntu 5.10 for example, it used to control my master volume perfectly, but now with 6.06, it doesn't affect anything. I've tried opening the big volume control and switch between the 2 devices I can choose from, SBLive! Value [CT4780] (Alsa mixer) and TriTech TR28602 (OSS Mixer) but that doesn't seem to change anything (except for the sliders in the volume control).

I only have one soundcard installed, the Soundblaster Live! Value.

What do I do?

---

### Post by crispy_420 on 2006-07-02
Do you have an onboard sound card?

I found, for myself, to disable my onboard sound in bios solved most of my audio issues. Would not hurt to give it a try.

---

### Post by bogaboga on 2006-07-03
Right click the loud speaker icon and select preferences. In the window that will appear, you can choose what component you'd like to associate with the icon. Hope  you are using Dapper and this helps.

---

### Post by johlin on 2006-07-03
[QUOTE=crispy_420]Do you have an onboard sound card?

I found, for myself, to disable my onboard sound in bios solved most of my audio issues. Would not hurt to give it a try.[/QUOTE]

Nope. I thought of that also, but I don't.

[QUOTE=bogaboga]Right click the loud speaker icon and select preferences. In the window that will appear, you can choose what component you'd like to associate with the icon. Hope  you are using Dapper and this helps.[/QUOTE]

I've tried changing that but it makes no difference. If I change it to the OSS device, the PCM slider makes a difference in xmms, but that's all.
If I select the ALSA device, then I can set the PCM switcher to more than 50% to add a little echo and eventually feedback in Rhythmbox but Rhythmbox isn't quiet if I turn it down to 0%.

---

