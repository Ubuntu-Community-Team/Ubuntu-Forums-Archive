---
title: "VLC and A2DPD; Setting gets deleted"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by Rinzwind on 2006-12-07
I use a bluetooth headset with VLC when I am in a train/bus/etc. The headset works when I add 'alsadev=a2dpd' in ~/.vlc/vlc under the section '# ALSA Device Name (string)'

From:
# ALSA Device Name (string)
# alsadev=default

To:
# ALSA Device Name (string)
# alsadev=default
alsadev=a2dpd

BUT when I switch to 'default' (at home I use the normal speakers) this line is deleted from this file and it's back to standard. 

Is there a way to tell vlc to have both 'default' and 'a2dpd' as a setting?

---

