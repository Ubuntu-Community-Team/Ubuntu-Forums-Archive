---
title: "No sound after 16.04 fresh instal"
date: 2016-05-03
forum: Multimedia Software
---

### Post by malty on 2016-05-03
Xonar DG soundcard running in Gnome fallback (metacity) in 16.04, fresh install....no sound (nor with the onboard chip selected.) Everything checks out in both the sound settings and Alsamixer settings (Alsamixer is via terminal) both the Xonar card and the onboard sound chip are recognised, nothing is muted. The only discrepancy is in the 'mode' sound menu options, only two are shown.. 'Analogue surround 4.1' and 'Analogue surround 5.1'. In 14.04 (still used on another HD) the mode chooser has 3 more options '4.0,  '5.0' and 'Analogue stereo'....this is setting used. The sound in 14.04 works flawlessly (in 16.04 I have also tried Unity then Gnome fallback using compiz ...still no sound.) Any suggestions please.

---

### Post by danbuter on 2016-05-03
Try going into System - Preferences - Hardware - Sound. Then go to Output and make sure your speakers/headphones are selected.

---

### Post by malty on 2016-05-04
Thanks danbuter but as I said in the post, everything in settings checks out OK.

---

### Post by malty on 2016-05-04
Update....16.04 recognizes the onboard sound chip and plays thro' the headphone socket, it would appear not to recognize the Xonar card although, in sound settings it says it does?????

---

### Post by malty on 2016-05-10
Sorted......in alsamixer there is a sub menu, after highlighting with l/r arrow keys 'analogue output', up arrow selects sub menu....choose 'stereo headphones', now we have sound.

---

