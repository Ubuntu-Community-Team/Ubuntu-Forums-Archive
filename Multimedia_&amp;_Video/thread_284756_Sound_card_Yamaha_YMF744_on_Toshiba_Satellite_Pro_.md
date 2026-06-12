---
title: "Sound card: Yamaha YMF744 on Toshiba Satellite Pro 4200"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by Pitt Stains on 2006-10-26
Hello,

I installed Ubuntu 5.10 and then immediately upgraded to the version I was prompted to install (6.06?  6.10? -- sorry, my Ubuntu machine is off).  Never tested the sound in 5.10, so I don't know if the problem is related to the upgrade.

The laptop is a Toshiba Satellite Pro 4200 with a Yamaha YMF744 sound card.  The module/driver for this card is called snd-ymfpci.  I tried the "Comprehensive Sound Problem Solutions Guide" ([http://www.ubuntuforums.org/showthread.php?t=205449]("http://www.ubuntuforums.org/showthread.php?t=205449")), but after purging and reinstalling the packages I still couldn't get sound.  Ubuntu is seeing the card, but no sound.

I also tried following the technique at [http://www.ubuntuforums.org/showthread.php?t=131157]("http://www.ubuntuforums.org/showthread.php?t=131157") - "How i got yamaha sound card in Ubuntu breezy."  This basically involves creating a file called sound in /etc/modprobe.d.  The Yamaha card in the above post is a slightly different model than mine, so I had to make up values for many of the parameters... so that approach may have worked if I knew more.

I'm not very comfortable in Linux yet, so it's certainly possible that I'm overlooking something.

Thanks for your help,
-Pitt Stains

---

### Post by Pitt Stains on 2006-10-26
Strange, but most excellent!  It may have been unclear from my previous post, but the order of my attempts to get the sound card working was:

1) Try to create file "sound" in "/etc/modprobe.d"

...then...

2) Use the "Comprehensive Sound Problem Solutions Guide," which wiped out tinkering from step one.

Frustrated with the apparent failure of steps one and two, I turned off the laptop and went to sleep.  When I booted it up the next morning, as I was telling the intern who will be using the laptop that the sound card would not work, the start-up sound came pouring out of the speakers!

The only explanation I can come up with is that rebooting the computer is somehow different from turning it all the way off and back on again, and that one of the steps I took in the above-mentioned Guide required a complete shut-off in order for the changes to take effect.  Or I could be completely wrong... but, hey, I've got sound!

---

