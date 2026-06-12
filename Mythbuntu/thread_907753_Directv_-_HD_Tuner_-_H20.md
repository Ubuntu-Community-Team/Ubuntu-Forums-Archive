---
title: "Directv - HD Tuner - H20"
date: 2008-09-01
forum: Mythbuntu
---

### Post by jleiss on 2008-09-01
So I have HD directv on a H20 box, and looking at getting a tuner card. From what I have read you cannot record HD from directv due to encryption is this correct, or is there tuners that get around this? If I cannot record HD will a tuner like the Hauppage 1250 be able to record non HD on this box?

---

### Post by newlinux on 2008-09-02
you are correct, unless you wan't to wait and use the hauppage HD-PVR which can capture Hidef from the analog component outputs of the H20. You can record HD and non HD (all will be converted to SD) via a capture card that has composite or s-video in that is supported in Linux. You'll need a serial connection or an IR blaster to have myth automatically change the channels on your H20

---

### Post by jleiss on 2008-09-02
And for the second part of my question. If I got a Hauppage 1250, could I use it to record non-HD channels? I tried using my 150, but i'm not getting any video.

---

### Post by jleiss on 2008-09-02
Can you also clarify this statement: You can record HD and non HD (all will be converted to SD) via a capture card that has composite or s-video in that is supported in Linux

what it sounds like your telling me is that it will recording HD & Non HD content, and it will convert the HD content to standard def, is that correct? If so why would I want to pay $200+ for that? I'd just get another directv box, leave it on standard def, and record through either my 150 or 500 hauppage cards...

---

### Post by newlinux on 2008-09-02
Sorry,  I wasn't explicit enough. In the US, you can only tune unencrypted cable and over the air signals with a tuner card. All other signals have to be captured from the video and audio outputs of the set top boxes (direcTV or cable). You can't tune the direcTV satellite signal with any tuner card. YOu can capture it with the  PVR-150 as I described above, but it will be downcoverted to SD, and the Hauppage 1250 won't help you anymore than the PVR-150 will. In fact, I don't think analog support is ready for the 1250 yet.

---

### Post by jleiss on 2008-09-02
And the HD PVR does the same conversion, therefore not really giving me any benefits over the 150 or 500?

---

### Post by newlinux on 2008-09-02
no, the HD-PVR takes in component (PVR-150/500 can do s-video/composite), so it can do true HD. But linux drivers aren't ready for it yet, last I checked

---

### Post by jleiss on 2008-09-02
Sounds like the best option is to wait until there are more players in the market versus paying $200+ for the Hauppage solution.

---

### Post by newlinux on 2008-09-02
I would definitely at least wait until the Hauppage HD-DVR is fully supported in Linux/Myth. There is no guarantee there will be more players in the market.

---

