---
title: "Pulse lists port as unplugged"
date: 2016-07-26
forum: Multimedia Software
---

### Post by childsey01 on 2016-07-26
Ok, a while back I mistakenly let Skype have control over my pulse audio settings. Bad move. To my defence it was enabled that way by default but then again I watched it progressively destroying my configuration each time it shut down with only a "huh?" in way of comment. By the time I changed it the damage was done. No more sound coming through. I investigated it and ended up giving up, blowing away pulse and living without skype (who have dropped alsa support).
Recently updated to 16.04 and it reinstalled it so I'm looking into the problem again.
I would have thought the config changes could be fixed by purging and reinstalling but somehow skype has found some really obscure file somewhere to spectacularly mess with.
ok the details:
my mobo has a 7.1 output fo which I am using 5.1 of them.
pacmd --list-cards gives 3 cards. One for the hdmi out, one for my webcam and the other for the motherboards inbuilt outputs (this latter should be the SPDIF and the 6x 3.5mm jacks comprising the 7.1 + mic). The active profile is for the SPDIF. Most looks ok with the exception of the ports. I'm guessing there's a reduced set w.r.t. the number at the output of the box analog-ouput-lineout being the only ouput port.
When I change the profile over to output:analog-surround-51, or similar, it will list the port as being unplugged.
Alsa on the other hand is having no problems seeing it (I did have to work at it a bit, but at least messing around with alsa is clear-cut).

Looks like it is only a problem with (Skyped) pulse, but I have no idea where

Any help greatly appreciated,

---

