---
title: "PCM and Front volume on Acer 5044"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by karhulitos on 2007-02-22
Hello,

I wonder if anyone could help me get this sorted out. My laptop is an 6.10/Acer 5044 with
```
aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: SB [HDA ATI SB], laite 0: ALC883 Analog [ALC883 Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0

```

Sound works superbly but one thing annoys me a lot. By pressing the  Fn + <vol up/up button> key I guess I set PCM volume, pressing the button brings the little 'volume window' with speaker icon in it. So far so ood.

Now the speaker icon on the panel has channel called "Front" set, which also seems to set whole system volume.

Now, this wouldn't be a problem but for some reason Firefox won't obey the Fn+VolUp/PCM setting at all but only the Front control on the panel.
[edit] actually it perhaps is Flash player that plays the sound which goes through 'Front' channel only and not Firefox. 

Can anyone help?
1. how to set 'Front' as the channel the Acer's Fn+VolUp controls? or
2. how to set Flash (or Firefox) to obey PCM channel volume

Confused I am..

---

### Post by karhulitos on 2007-02-25
For this problem the solution was the [firefox_dsp="aoss"]("http://ubuntuforums.org/showthread.php?t=364313")

---

### Post by karhulitos on 2007-03-02
Phuuh... get one part fixed, break another.

firefox_dsp="aoss" did make my audible flash pages to obey PCM sound control but then.. long working Skype got pissed off. Now if I have Firefox open, no mic in Skype!

Can't believe this is happening but it is. After reboot Skype is OK, I can hear and others can hear me, but if I happen to open firefox (have homepage with flash+sound) -> mic gone in Skype.

Dippaduidaa..

---

