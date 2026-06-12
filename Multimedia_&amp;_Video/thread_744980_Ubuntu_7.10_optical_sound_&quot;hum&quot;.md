---
title: "Ubuntu 7.10 optical sound &quot;hum&quot;"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by curme on 2008-04-04
I just switched over to Linux for the first time last week, and this is the first problem Google didn't solve.

I have Ubuntu 7.10 with a Sound Blaster Audigy2 ZS Platinum Pro with some Logitech z-5500's and I have a "hum" on my optical input. For example, in the Alsa mixer:

[IMG]http://img.photobucket.com/albums/v73/curme/neowin/alsa.jpg[/IMG]

When I disable the IEC958 Optical Raw the hum goes away, but so does the sound from my tv, which is obviously on the optical cable.

Anyway to get rid of the hum? It doesn't happen in XP so it's not a ground loop. It's so annoying, it makes tv watching unbearable.

---

### Post by curme on 2008-04-04
Oddly enough, I just discovered, thanks to you, changing the volume for the IEC958 Optical doesn't effect the hum. I could mute the IEC958 Optical in the mixer with the volume controls, and the hum stays the same. Even stranger. If I mute the IEC958 Optical in the mixer with the volume controls, I can still hear my tv on the optical cable. The volume controls do nothing for the optical.

[IMG]http://img.photobucket.com/albums/v73/curme/neowin/Screenshot-VolumeControlAudigy2ZS20.png[/IMG]

It's only in the "Switches" tab that I lose my tv sound, and the hum.

---

### Post by curme on 2008-04-04
If I mute the center speaker of my 5.1 set-up, the hum goes away, but so does the sound from my tv.


[IMG]http://img.photobucket.com/albums/v73/curme/neowin/front.jpg[/IMG]

---

