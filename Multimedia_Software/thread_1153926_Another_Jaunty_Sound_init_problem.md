---
title: "Another Jaunty Sound init problem"
date: 2009-05-09
forum: Multimedia Software
---

### Post by boba23 on 2009-05-09
Hey folks,

I recently upgraded to Jaunty and at first my sound was working fine as in Hardy.
Then after a few days I had the first "Sound blackout". After reboot, no sound nothing nada.
Logs didn't show anything, drivers loaded, soundcard detected etc. etc.
Anyway I played around, reinstalling sound packages etc. and eventually sound came back, don't ask me exactly why.
Now it seems that after every reboot my sound is gone. Though I can directly get it back working by doing a simple speaker test:

speaker-test -Dplug:spdif -c2

Speaker test works just fine and bang, all my sound is back and working fine. Seems to me like a sound init problem on bootup and that the speaker test then really initializes my sound somehow.

Here's my Hardware:

GA-73PVM-S2H
Intel E8400
Realtek ALC889A onboard sound

I am using the digital sound output from the motherboard and audio via HDMI from my Nvidia 9400GT passed through from mainboard to the 9400GT.

Can anyone point me to the right direction to get my sound back reliably also on bootup, without having to go through the speaker test thingy every time?

thanks

boba

---

