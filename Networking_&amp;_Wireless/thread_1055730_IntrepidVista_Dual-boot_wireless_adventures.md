---
title: "Intrepid/Vista Dual-boot wireless adventures"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by CodeLes on 2009-01-31
**The setting:**
- Toshiba Satellite (a205)
- RealTek wireless card (rtl8187b)
- dual boot: Windows Vista / Ubuntu Intrepid

**The issue:**
So I was using Hardy and had to patch an old Win98 (i think?) driver for this wireless card in order to get it to work, and it did for the most part. I recently upgraded to Intrepid (via the update manager) and to my joy it immediately recognized my card.  That was great... until after some use I noticed I'd be losing packets.  Then eventually I'd lose connectivity altogether.

I've done a lot of digging around on the internet (this forum included) and found a lot of tips and things to try, but I keep hitting this great big wall:  when I make some changes in ubuntu, whether or not they help my issue, those changes cause my wireless in Vista to not work... I feel insane on this, maybe I just don't understand.  Do hardware drivers and configurations have cross-partition relationships?

The last thing I tried was installing the linux-backport-modules-intrepid, seemed to help in ubuntu, but once I booted into Windows I was hit with a failing wireless connection... tried to mess with the Windows side of it with no luck... booted back into intrepid, did an apt-get remove of the module and then a clean, rebooted back to vista and here I am... on the net with a good connection... am I insane? is my computer possessed (besides the fact that it has windows installed on it)?

thanks for any info/tips/tricks or slaps to reality.
Les

---

