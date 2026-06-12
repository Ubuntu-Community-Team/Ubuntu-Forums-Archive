---
title: "How does one enable 4.1 sound on an Intel HDA card?"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by cookevillain on 2006-01-19
Hi everybody!

I have an Intel D945PSNLK motherboard. I am using Ubuntu 5.10 and am trying to get the sound to work. I can play 2 channel sound without any  problem but how do I enable all 4 channels (well, I only need 4)? When I run

speaker-test -Dplug:surround40 -c4

I can only hear the sound when I plug the speakers into the `line out' jack. No other jack produces sound even though the motherboard is supposed to be able to switch the mic and line-in jack to output . Playing with the mixer did not get me anywhere. Does anyone have any idea of what is going on?

If it helps, here is the output of

aplay -L 2>&1 | egrep surround

:
surround40 'cards.pcm.surround40'
surround41 'cards.pcm.surround41'
surround50 'cards.pcm.surround50'
surround51 'cards.pcm.surround51'
surround71 'cards.pcm.surround71'

Please help. Thanks in advance.

---

