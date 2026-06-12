---
title: "Ubuntu 14.04 no right channel sound on Creative Xtreme Audio (CA0106)"
date: 2014-04-20
forum: Multimedia Software
---

### Post by mladenovicp on 2014-04-20
There is no sound on right channel on my desktop after installation of Ubuntu 14.04, no sound on right channel even with liveCD. But it works perfectly in other OS (no gnu/linux), and it worked perfectly on Ubuntu 12.04 before I've installed 14.04. My sound card is Creative Xtreme Audio (PCI CA0106).

---

### Post by GN_ on 2014-04-20
I have the same problem (CA0106, 14.04) :(

---

### Post by xtopherbv on 2014-04-20
The same, also happens with Xubuntu and Lubuntu - (14.04) (PCI CA0106)

---

### Post by mladenovicp on 2014-04-21
I found a solution whitch solved this problem:

[https://forums.mageia.org/en/viewtopic.php?f=15&t=6420](https://forums.mageia.org/en/viewtopic.php?f=15&t=6420)

---

### Post by mladenovicp on 2014-04-21
[COLOR=#333333][FONT=Lucida Grande]1. launch alsamixer (from console).[/FONT][/COLOR] I've started with "sudo alsamixer".
[COLOR=#333333][FONT=Lucida Grande]2. Select your soundcard (press F6), mine was CA0106.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]3. Look for stereo items with one channel muted (text beneath bars looks like "63<>0").[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]4. Make volumes equal (63<>63) using keyboard controls (UP/DOWN, Q/Z, E/C).[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]5. Exit (ESC), no need to save manually.[/FONT][/COLOR]

---

### Post by GN_ on 2014-04-21
mladenovicp, big big thanks dude!

---

### Post by xtopherbv on 2014-04-22
thank you very much, it worked for me!!! :guitar:

---

### Post by pablosquared on 2014-04-22
I had the same problem - both RHS channels on a 5.1 rig with this sound card were muted, and the same fix worked for me. How does a bug like this get past testing?

---

