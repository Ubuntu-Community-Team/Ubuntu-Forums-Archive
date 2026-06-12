---
title: "&quot;Artifact&quot; Trouble with Dell P1130 and ATI Radeon 9500"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by Lockjaw on 2007-03-18
I hope someone can give me some good direction.

I installed Edgy on my Dell and, for awhile, everything was peachy. I'm running a Dell 8250 with a P1130 monitor and an ATI Radeon 9500 video card.

Recently, my monitor has begun to display "artifacts" when I first boot my machine in the morning, or after it has been running for some time. After a few boots I can usually get my system to display everything correctly, but when left on for awhile these artifacts begin to appear -- streaks, random blocks of inverse characters, occasionally blinking characters. When they begin to appear, things deteriorate quickly -- more and more characters show up and I need to reboot.

Sometimes this doesn't happen at all, but usually only after a number of reboots.

Things seemed okay up until the time I installed Beryl, which worked well for one session and then wouldn't work at all after that. So I uninstalled Beryl, uninstalled the fglrx driver, experiemented with reconfiguring my xorg.conf, tried the vesa driver, went back to ati -- all to no avail.

I tried upgrading to Feisty in the hope that things would improve. They did, actually, and a nasty keyboard problem I'd been having disappeared completely -- usually I'd need to reboot a few times before my keyboard would be "recognized" and I'd be able to log in. That problem is gone, but the display problem remains.

Suspecting a hardware problem, I've tried booting into Windows XP on another partition, but whenever I do that my display seems to work perfectly. ARGH!

Suggestions? Similar problems? If anyone has any insights I'd be very grateful. My productivity goes *way* up over Windows when Ubuntu is working, so I really don't want to go back to Windows, but this is getting pretty rough.

---

### Post by Erlander on 2007-03-18
The P1130 is a nice monitor.  I recently got one and am impressed with it.

Having said that it is unlikely to be the monitor but more a display card or display card driver issue.  ATI and Linux may be the issue however the fact it occurs after a while may indicate that it is an overheating issue for the display card.  Worth taking the side off the case and directing a small fan at the display card to see if that is the issue.  You could also feel the display card and see how hot it is.

Good luck.

Rob

---

### Post by Lockjaw on 2007-03-18
Thanks for the help.

Unfortunately, I don't think it's an overheating issue. If so, then it seems that the problem would occur under XP, which it doesn't. Also, my system has one of Dell's characteristically overenthusiastic fans, so that when any processing requires any significant power at all the fan begins to turn crazily. But the monitor problem occurs when the system is running quietly in a cool room.

It's the strangest problem I've run across under Linux, by far, one which, I suppose, may be unsolvable.

---

