---
title: "No background images on frontend"
date: 2010-09-26
forum: Mythbuntu
---

### Post by xykevinr on 2010-09-26
Hi all,

I'm a bit lost as to where to look....everything but this is working, and I don't really need it, but this is mythtv, so i MUST keep going, even if I wreck everything and have to start again :-)

When I look at tv recordings on the backend pc, many programs have the an image in the menu background - presumably an image that's been downloaded by jamu.

On the seperate frontend pc, the same tv programs do NOT have the background. 

So, I guess jamu is working, but the frontend doesn't know to look - or does not have permission to access where the images are. But, I don't think that this is part of storage groups.

Any ideas ?

Thanks, Kev

---

### Post by ian dobson on 2010-09-26
Hi,

Are the images your talking about from recorded programs or videos you've copied onto the system?

Have a look in the frontend log file (/var/log/mythfrontend.log) to see if there are any error messages listed.

Regards
Ian Dobson

---

### Post by LowSky on 2010-09-27
Just to point out, Some themes of MythtV, like Mythcenter, do not use the media art as a background.

---

### Post by tgm4883 on 2010-09-27
You say that you don't think this is part of storage groups. Are you referring that you don't think the issue is related to storage groups, or that you don't have storage groups set up? The background art is definitly done via storage groups.

---

### Post by xykevinr on 2010-09-27
All fixed, thanks. 

Ian - thanks, no errors. I meant recorded tv programs, not videos
LowSky - thanks, feeling stupid now. Backend was working. Frontend was using mythcentre. Changing this fixed it !
Tgm - I meant that I didn't have storage groups set up for videos, for the moment I am using smb shares. I didn't see why that would be related for new recordings using myth.

Thanks all for your time


Kev

---

### Post by LowSky on 2010-09-27
I had a feeling the theme you picked was the issue, glad to help

---

