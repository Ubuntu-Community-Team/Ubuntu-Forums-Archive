---
title: "[RANT] Screens and Graphics - I'm going nuts"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by DFreeze on 2008-02-26
I just tried to hook my TV on my laptop DVI port, to check if I could get a movie on the big screen. But I shouldn't have. I lost my whole evening trying to get my own laptop resolution back. These are the things that happened that I think are bugs (or I just don't get dual screens)

- editing the second screen resolution changed my laptop screen resolution too. I had to do a "dpkg-reconfigure xserver-xorg" to get it all back, but more on that later.
- I saw a window asking me to confirm the new resolution within 15 seconds. Since my laptop screen was messed up I did not confirm, but let the timer run out. Result: the new resolution stayed anyhow.
- having two screens, playing the movie only showed on the laptop - the TV stayed black
- after a reboot, the laptop couldn't get Xserver up. I was presented with the failsafe-xserver screen, but in a resolution that made the letters some three pixels big - unreadable.
- I did try to change some things with the failsafe X graphical tool, and a window was presented saying a reboot was needed, but the computer continued booting anyway.
-  In the end I had to reconfigure X the old way, to get graphics back.
- the generic screens in Screens and Graphics make no sense. If I select a generic LCD with 1366x900 (or something) - the resolution of my TV screen, the resolution options only contain 640x480, 800x600 and some others. NOT the one in the description.
- in 800x600 the system menu in the panel doesn't work right. Clicking 'System' activates some icon that was next to the System menu in normal resolution. Shrinking the panel made some icons disappear under the menu, but they did steal the mouseclicks.
- the shutdown icon in 800x600 was out of the viewable screen.

As you can understand, I did not have a pleasant night. Maybe I don't understand dual screens (or mirrored screens), but this smells an awful lot like bugs, right?

I'll check whether these bugs are already reported another day. I first had to let off some steam.

---

### Post by DFreeze on 2008-03-09
I posted the following bugs:

[200117]("https://bugs.launchpad.net/displayconfig-gtk/+bug/200117") "BulletProofX - restoring to my default resolution still doesn't get X back"
[200118]("https://bugs.launchpad.net/displayconfig-gtk/+bug/200118") "BulletProofX - "reboot needed" but computer doesn't reboot"
[197238]("https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/197238") "[Gutsy] displayconfig-gtk in BulletProof X - unreadable on 1440x900 laptop screen"
[196968]("https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/196968") "[Gutsy] screens and graphics resolution of screen 2 affects resolution of screen 1"

The other issues were already reported.

---

