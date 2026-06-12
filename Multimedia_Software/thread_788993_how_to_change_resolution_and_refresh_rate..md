---
title: "how to change resolution and refresh rate."
date: 2008-05-10
forum: Multimedia Software
---

### Post by Vegadark on 2008-05-10
Ok, I went into screens and graphics. My monitor is not listed as a manufacturer there. I have a Xerox XG-70D LCD panel. I have tried getting the resolution up to 1280x1024, but every time I have done that, the screen says "1280x1024 60Hz out of range" and I was forced to reinstall the OS. The specs for the screen are as follows:

```
Display

Diagonal Size: 17"

Viewable Size: 17"

Dot Pitch / Pixel Pitch: 0.264 mm

Max Resolution: 1280 x 1024 / 75 Hz

Max Sync Rate (V x H): 75 Hz

Response Time: 16 ms

Signal Input: DVI-D, VGA
```

So apparently i need it to be at 1280x1024@75 but the section in the xorg.conf where the resolutions can be changed is missing. In the screens and graphics panel, how do I do this with out the proper one being listed? I tried with generic LCD panel, but i cannot change the refresh rate from 60Hz - no other options are present.

All I want to do is set it to 1280x1024 from this 1024x768 that it is at now.

---

### Post by Vegadark on 2008-05-10
No ideas at all here?

---

### Post by janbockaert on 2008-05-10
hi, i was having the same problem. The nvidia driver did not believe my projector could handle a 800x600 resolution, and refused to give me more than 640 x480. There is a tool in /usr/share/applications/ called screen and graphics, you can use to change the monitorsettings. In my case, i changed my monitor to a generic 800x600 monitor. After logging out, and then logging back in, i had all my pixels back. 

Hope this helps.

---

