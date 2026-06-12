---
title: "Unique Audigy Problem (ALSA)"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by leetsauce on 2007-07-14
Hi,

Perhaps it's the combination of my speakers and the Audigy card, but my setup has this unique problem where the sound from my speakers is nearly bassless and low on volume upon boot. In Windows, this is easily fixed by running the Creative Audio Console, flipping over to the Speakers setting, and change selection from whatever it is (usually 4.1) to 2.1, and back (though it is optional since, at this point, the difference between leaving it at 2.1 and changing it back to 4.1 or higher is subtle). This would, for reasons beyond me, fully activate my speakers, bringing them to full volume (bass is most noticeable). This setting is synchronized with the Control Panel sound setting, as indicated by a checkbox option on the page.

**Edit**: After some researching, I realized that I'm not alone with this problem. The problem seems to the inability to play from channels other than my front left and right speakers. I've tried changing the content of my .asoundrc, different settings for speaker-test in terminal (only front left and front right channels have sound, all others are mute despite being full blown on alsamixer), none which seemed to have worked.

Is there no hope for us Audigy users?

---

