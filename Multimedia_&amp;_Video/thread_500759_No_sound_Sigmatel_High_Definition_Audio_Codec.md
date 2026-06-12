---
title: "No sound: Sigmatel High Definition Audio Codec"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by Master_Z on 2007-07-14
I have been using feisty fawn for months, and I love it, but theres one problem: NO SOUND. I posted about this a while back, but no one helped me. My Sound card is a Sigmatel STAC 9200. Ubuntu detects it and I have unmuted on Alsamixer. I even did the snd_hda_intel thing to try to get it to work, but its just not working. Anyone else have this problem? If so, any way to fix it? I would love sound on my laptop.

---

### Post by dabl on 2007-07-14
Have you opened your little "Volume Control" panel, accessible by right-clicking the speaker icon that is in the upper-right corner of your panel?  The title "Volume Control" is misleading -- it's a lot more than that.  Open it, then click "Edit>Preferences", then on that list put a checkmark in every box. Close it, and on your "Playback" window make sure the sliders are up on "PCM" and "Front", and the others can probably be muted.  On the "Switches" tab, put a checkmark in the "IEC958" Box.

Now, shut down your browser first, then try Amarok or Audacity or whatever your player is, and see if there's any joy.  HTH  :)

---

### Post by Master_Z on 2007-07-14
Already tried that. No luck. :(

---

### Post by Master_Z on 2007-07-14
Bump.

---

### Post by theQmaster on 2007-12-02
Any news on this ? Is there a codec for SigmaTel High Definition ?

---

### Post by fenian on 2007-12-02
I think you need a newer version od ALSA.Follow the instructions[ here..]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

