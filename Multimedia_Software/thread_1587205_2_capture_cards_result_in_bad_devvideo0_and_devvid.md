---
title: "2 capture cards result in bad /dev/video0 and /dev/video1 output"
date: 2010-10-03
forum: Multimedia Software
---

### Post by dtbaker on 2010-10-03
So I have 3 old video capture cards which I would like to use for CCTV. Each card supports 1 camera. So I would like to have 3 cameras setup in the end and monitor them with zoneminder.

When each card is plugged in on it's own, it works fine. Video comes through clearly with xawtv and zoneminder. 

However as soon as I plug in a 2nd card (with or without a camera connected) the output in xawtv and zoneminder goes haywire. It looks like the 2nd card takes over the first card, resulting in majority of the picture coming from the 2nd card, and some (if any) from the 1st card. When viewing either of the two cards /dev/video0 or /dev/video1 in xawtv the output is identical.

I've tried this on a fresh 10.04 Ubuntu install, and on an older MythTV debian computer, the same results. 

Here are lspci -vv outputs with 2 combinations of cards (same fuzzy output):

[http://pastebin.com/Ri9RBipA](http://pastebin.com/Ri9RBipA)
[http://pastebin.com/RKupHYeg](http://pastebin.com/RKupHYeg)

My thoughts are because the capture cards are cheap (similar to winmodems), the problem may be in the software kernel modules not allowing room for other similar capture cards to run at the same time. 

Can anyone suggest me in the right direction? Do I need to setup some sort of memory allocation for each card manually? Something in the BIOS? An extra option when the card modules are loaded?

Or should I be posting this question towards some sort of v4l mailing list?

Thanks heaps!
Dave

---

### Post by dtbaker on 2010-10-03
A suggestion from the v4l irc channel was to blacklist the card modules, and then load each module manually after a timeout.

This seems to work :) yet to try all 3 cards together but 2 are working well with cameras connected.

:)

---

