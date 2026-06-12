---
title: "Alas, my sound has died."
date: 2014-11-01
forum: Multimedia Software
---

### Post by IanKoro on 2014-11-01
I tried posting this in the stickied sound troubleshooting thread, but didn't get any replies, so hopefully someone will see this here:

My audio recently stopped working. I upgraded from 13.04 to 14.04 about a week ago, and everything was working fine.
Yesterday I was using Rhythmbox (which I don't normally use) to listen to some music. I was adding a bunch of files to Rhythmbox's library, and the audio suddenly stopped working. Rhythmbox froze, so I closed it, (I think I may have gotten an error message related to Pulseaudio around this time, but didn't think to take note), and when I reopened it the sound still didn't work. Sound also stopped working in VLC. I figured I had just crashed Pulseaudio, and that a reboot would fix it, but still nothing.

I went through the troubleshooting steps posted above with no luck.

Here's the output of running the alsa information script, if that helps: 
[http://www.alsa-project.org/db/?f=3b98f5c8ab0f5076c661e486c2656798562de125](http://www.alsa-project.org/db/?f=3b98f5c8ab0f5076c661e486c2656798562de125)

---

### Post by whereismymindat2 on 2014-11-01
@Ian...Just curious, did this start after installing 14.10?  I have same issue and started with 14.10. will monitor thread for hopeful solution.

---

### Post by IanKoro on 2014-11-01
Well, shortly after upgrading to 14.04 from 13.04, so it's possible that we're experiencing the same issue. 
I had no issues for several days until something happened while listening to music in Rhythmbox, so it wasn't immediate after the upgrade.

---

### Post by IanKoro on 2014-11-05
Bump...?
Any suggestions?

---

### Post by SeijiSensei on 2014-11-06
Install and run the package **pavucontrol** and see what devices it reports.  Do you have multiple audio outputs like HDMI as well as an analog jack?  If so, the upgrade might have chosen the wrong output.  You can fix that with pavucontrol.

---

### Post by IanKoro on 2014-11-14
Nice! That actually worked!

Just in case anyone else has the same issue, here's a screenshot:
[IMG]http://i.imgur.com/LCDZyMS.jpg[/IMG]

The green checkmark button (I pointed to the one I needed to press with the red arrow) is to select the active output device. I'm not entirely sure what caused it to switch around, but that's the way to fix it... (and I think swapping it back should allow me to use the audio through an HDMI monitor, which I was wondering about as well, so two birds.)

---

