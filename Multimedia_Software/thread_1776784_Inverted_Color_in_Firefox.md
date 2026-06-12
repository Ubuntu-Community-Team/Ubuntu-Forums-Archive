---
title: "Inverted Color in Firefox"
date: 2011-06-06
forum: Multimedia Software
---

### Post by Wildcarded on 2011-06-06
This is a strange issue I've been having that seems to affect some pictures and not others (even in the same album). I'm not sure if it has to do with my video drivers or what, but basically some pictures seem to be arbitrarily inverted colors (or something else equally bizzare, if not truly inverted). It seems to be happening in Firefox only, as I haven't noticed it either offline or in chromium. 

Specs:
Ubuntu 11.04
Firefox 4.0.1
GC: ATI Mobility Radeon HD 3650

If anyone has had this problem or knows a solution I'd be very grateful. I could just switch to chromium, but I prefer the fox. I can provide more specs if necessary, or even a screenshot of an example of the arbitrary color inversion (though I'm not sure if it would show up for you if it's a graphics card issue). Thanks!

---

### Post by bastienqueste on 2011-06-21
Same issue here, Ubuntu 11.04. FF4.0.1 and 01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series. Proprietary fglrx drivers. Again not observed anywhere else. Investigating now, hopefully post a solution now...

---

### Post by bastienqueste on 2011-06-21
Solution by cor-el ([http://support.mozilla.com/en-US/questions/831778#answer-198511):](http://support.mozilla.com/en-US/questions/831778#answer-198511):)


This can be caused by a problem with the color profile for your display monitor or color profiles embedded in images.
You can disable color management to test that.
You can set the pref gfx.color_management.mode to 0 on the about:config page to disable Color Management.
You need to close and restart Firefox to make the change effective. 
See: 
 
[LIST]
[*] [http://kb.mozillazine.org/gfx.color_management.mode](http://kb.mozillazine.org/gfx.color_management.mode)
[/LIST]

---

### Post by charisz on 2011-06-30
Same issue by me. Ubuntu 11.04. Firefox 5.0. ATI Mobility Radeon HD 2400 XT.
I've changed about:config gfx.color_management.mode; from 2 to 0.And it's working now.

---

