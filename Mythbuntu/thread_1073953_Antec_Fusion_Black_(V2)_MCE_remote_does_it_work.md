---
title: "Antec Fusion Black (V2) MCE remote does it work??"
date: 2009-02-18
forum: Mythbuntu
---

### Post by Cuppa-Chino on 2009-02-18
Hi 
I have an Antec Fusion Black with the VFD & Remote>
**lsusb**
Bus 001 Device 004: ID 15c2:0038 SoundGraph Inc. 

The display now works fine and I can get feedback from my RM200 supplied remote using IRW and also it does operate Mythtv a bit (I struggle to get anything sensible in myth tv down works, up does not it always jumps several lines..... - hints on that welcome!)

The box claims this works with the MCE - has anyone got that combo working under Linux?
The reason I ask is that my box is now nearly tip top, I still needed to get auto wakeup and sleep working but not much else.
Any helps really appreciated...

---

### Post by Jimwah on 2009-03-12
I've got the same device, on Mythbuntu 8.04, but when I tried to set it up I couldn't get it working. What did you do to get as far as you did?

---

### Post by Cuppa-Chino on 2009-03-12
you mean the rm200 remote? 

I used this info:

[http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452]("http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452")

---

### Post by Cuppa-Chino on 2009-03-21
bump

---

### Post by tkoopa on 2009-03-24
I followed this guide and got the LCD + Button + MCE Remote working with Mythbuntu 8.10

[http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD](http://wiki.foxmediasystems.com/index.php/Antec_Fusion_v2_Black_LCD)

---

### Post by Cuppa-Chino on 2009-03-24
thanks tkoopa, i have ID 15c2:**_0038_** SoundGraph Inc
so not sure if works but will try!

will feedback;)

---

### Post by pcooley on 2009-03-28
I found this post worked for me on 8.10 for Antec Fusion 15c2:0038 with RM200 remote:
[http://ubuntuforums.org/showthread.php?t=1103474](http://ubuntuforums.org/showthread.php?t=1103474)

---

### Post by Cuppa-Chino on 2009-03-28
Also a great place to look is Avenard's blog:

[JYA's media page]("http://avenard.com/media/Home.html")

For what its worth, I gave up on the MCE remote and bought a Logitech Harmony which works a treat with Fusion, just choose Soundgraph Imon Pad Remote et voila.

---

### Post by jyavenard on 2009-03-28
I've detailed how to get this case working (LCD and remote) as well as how to use it with a logitech remote.

[http://avenard.com/media/Patches_%26_Add-Ons/Archive.html](http://avenard.com/media/Patches_%26_Add-Ons/Archive.html)

Start from this post.
[http://avenard.com/media/Patches_%26_Add-Ons/Entries/2008/10/8_LIRC_to_work_with_Antec_Fusion_Remote_Black.html](http://avenard.com/media/Patches_%26_Add-Ons/Entries/2008/10/8_LIRC_to_work_with_Antec_Fusion_Remote_Black.html)

then use next to see my other entries...

BTW, this case isn't a VFD but a LCD ...

---

