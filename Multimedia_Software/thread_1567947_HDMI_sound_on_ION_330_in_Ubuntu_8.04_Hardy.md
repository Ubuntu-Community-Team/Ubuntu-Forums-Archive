---
title: "HDMI sound on ION 330 in Ubuntu 8.04 Hardy"
date: 2010-09-04
forum: Multimedia Software
---

### Post by MichiGreat on 2010-09-04
Meanwhile I have upgraded to Ubuntu 10.10 Maverick Meerkat and sound over HDMI works there without any problems so far after unmuting all channels.

Best regards

*Michael*

---

### Post by Matters1 on 2010-09-05
Is there any particular reason you are using Hardy instead of Lucid?

The XBMC forums will have a heap of info about getting the sound working on the Asrock ION 330 as it is one of their favourites.

I suggest updating to the latest Alsa version (there is a script for that somewhere on here).

First thing to check would be that the sounds isn't muted (as it can be by default).

Check that in 'alsamixer'

Failing that post your 'aplay -l' output here.

---

### Post by MichiGreat on 2010-09-18
> **Matters1 said:**
> Is there any particular reason you are using Hardy instead of Lucid?

Simply because I had no time upgrading yet.

> The XBMC forums will have a heap of info about getting the sound working on the Asrock ION 330 as it is one of their favourites.

Thanks for that hint. I searched the XBMC forums and found a link to the XBMC wiki:

[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_audio_over_HDMI_on_nVidia_GeForce/nForce_controller)

I exactly followed the suggested steps and neither it worked in Hardy, nor it did on my USB stick with Maverick Beta.

> I suggest updating to the latest Alsa version (there is a script for that somewhere on here).

Interestingly I read multiple times that upgrading ALSA isn't necessary as from Lucid, so if didn't work in Maverick, I assume that upgrading ALSA in Hardy wouldn't help either.

> First thing to check would be that the sounds isn't muted (as it can be by default).

That was one of the first things I checked. ;-)

> Failing that post your 'aplay -l' output here.

[http://michigreat.a.wiki-site.com/index.php/Speedy#aplay_-l](http://michigreat.a.wiki-site.com/index.php/Speedy#aplay_-l)

In Maverick Beta, it showed three devices for card 0, similar to the output in the Wiki article above, with an entry explicitly pointing to "HDMI".

However, yesterday I wasted another hour and gave up frustrated. From what I know right now I must assume that HDMI sound on my ION 330 currently doesn't work in Linux. I also found an unsolved forum entry here on Ubuntuforums from someone having exactly the same problem. This misfunction might be caused by a bug, so I think it's smart to open a bug report in Launchpad. Those stating that their ION 330 work with HDMI sound might have a slightly different version I found yesterday.

---

