---
title: "HD Channel Audio Low"
date: 2010-12-11
forum: Mythbuntu
---

### Post by lviperz on 2010-12-11
I'm building a new HD box using 10.10 with Mythtv 0.23.1 latest. I have both an HVR-1600 and HD Homerun. I have both configured and working with video and sound but the HD channels audio is much lower than the SD channels. By much lower I mean almost to the point it can't be heard. I have to triple the volume level when watching these channels.

Is there something I can do? I've been through all the settings many times and can't see a thing. I did notice, when watching a basketball game, the announcer was low as all sound in general was. But when the crowd cheered the audio seemed to pop a little and was almost normal for a split second.

Could the stream be passing a different audio and my audio card isn't decoding it correctly?

The box is a Dell Vostro 200 with onboard audio. I have myth set with alsa default.

---

### Post by Senkoboy on 2010-12-13
I have the same problem with HD channels, some worse than others. If I have my TV on 20 to hear a SD channel, I might have to turn up to 40 on some HD channels.  Sometimes the commercials will be twice as loud as the program.  I have a HDTV Wonder card.  Sorry I can't be of more help.

---

### Post by lviperz on 2010-12-13
I spent the day searching through the mythtv mailing list and discovered by using alsa mixer I needed to turn up the front mixer. This helped a lot. The volume is still less than SD but not by nearly as much. I can tolerate it now.

Now the only problem I have is one HD channel volume is still very low and out of sync. I did read where 0.24 may help some of the audio volume so I will try the upgrade and see what I get.

---

