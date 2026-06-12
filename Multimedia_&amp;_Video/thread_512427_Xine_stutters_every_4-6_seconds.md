---
title: "Xine stutters every 4-6 seconds"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by edbyford on 2007-07-29
Hello all.

I've just installed Ubuntu 7.04 Feisty on my computer. I'm using the integrated soundcard on my Intel DG965RY motherboard. All the sound architecture settings are on 'autodetect' in the Ubuntu control panel.

At first, there was no problem when playing movies or music using xine. But now (and I haven't done anything that I can think of to the computer to affect it) every 4-6 seconds the sound of whatever I'm playing (music, movies etc) drops out for about half a second or so. And this happens in every program that uses xine as a backend (Amarok etc).

Now, Gstreamer works fine, and I just can't work out why!

If you're wondering why I don't just use Gstreamer, there are two reasons:
1. I hate to have something suddenly stop working for no reason and not be able to work out why!
2. Amarok uses Xine and I can't work out how to get it to use Gstreamer instead. In fact, if someone could tell me how to do that, I'd be very grateful.

Thanks for your time!

---

### Post by edbyford on 2007-07-29
If it helps, I just ran Xine in verbose mode and in the log I've highlighted the line that occurs just after the sound drops out:

fixing sound card drift by -3311 pts
fixing sound card drift by -3540 pts
fixing sound card drift by -3714 pts
[COLOR="Red"]fixing sound card drift by -1250 pts[/COLOR]
fixing sound card drift by -1996 pts
fixing sound card drift by -2555 pts
200 frames delivered, 0 frames skipped, 2 frames discarded
fixing sound card drift by -2982 pts
fixing sound card drift by -3308 pts
fixing sound card drift by -3539 pts
fixing sound card drift by -3712 pts
[COLOR="Red"]fixing sound card drift by -1253 pts[/COLOR]
fixing sound card drift by -1998 pts
fixing sound card drift by -2545 pts
fixing sound card drift by -2999 pts
fixing sound card drift by -3306 pts
fixing sound card drift by -3538 pts
fixing sound card drift by -3709 pts
[COLOR="Red"]fixing sound card drift by -1253 pts[/COLOR]

---

