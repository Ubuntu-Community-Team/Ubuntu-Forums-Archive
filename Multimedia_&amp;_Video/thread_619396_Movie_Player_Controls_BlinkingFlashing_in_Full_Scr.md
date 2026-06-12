---
title: "Movie Player Controls Blinking/Flashing in Full Screen Mode"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by Devi 710 on 2007-11-21
Hey guys, hope you can help.

When I switch to full screen mode in the default video player "movie player" the "Leave Fullscreen" box in the top right and the control bar on the bottom start flashing rapidly when I move the mouse to display them. It is really annoying and often won't stop. If I click on the bar with the mouse it seems to display properly after.

I had this problem back in Feisty towards the end before I upgraded to Gutsy. I am running a fresh install in Gutsy now. Same problem. I tried making the VLC  Player the default for avi files and such, but the full screen option isn't working. Like if it is widescreen, the parts of the screen that should be black still show my desktop.

Any ideas or similar problems??

Thanks

Nvidia GeForce 6200 LE card

---

### Post by Devi 710 on 2007-11-21
Actually the whole screen flashes as soon as my mouse moves. umm....

---

### Post by Devi 710 on 2007-11-21
Ok, now movie player won't write to the screen properly sometimes as well. Like I said with the VLC Player, the part of the screen that should be black shows the desktop or a gray mess of graphics.

These problems are happening about 70% of the time with movie player.

---

### Post by davec64 on 2007-11-23
I had a similar problem with viewing video clips emailed to me by a friend, I'd get a flash of the clip, then it would go to black whilst the sound was fine. This was while I had Compiz running.

To fix it I opened gstreamer-properties from the terminal, and on the video tab set the output to "X Windows System (No Xv)".

This did the trick for me! Might be worth a go!

Here's the page I got the info from:

[http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/2]("http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/2")

(it about half way down)

Best of luck!:)

---

### Post by Devi 710 on 2008-01-08
Thanks for the response! I couldn't find this post again, forgot to set email notifications. I just started using Mplayer instead of Totem. But I'll try your fix for the Totem player.

---

