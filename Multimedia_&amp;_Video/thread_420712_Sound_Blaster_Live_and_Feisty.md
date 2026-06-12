---
title: "Sound Blaster Live and Feisty"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by xtreme35967 on 2007-04-23
Ok for some reason my sound just stoped working on my SBL 24-bit. The sound works on my onboard Realtek but I have a 5.1 speaker setup on the SB. It was working this morning and now it is not. I am not sure what could have changed. How do I go about uninstalling the SB drivers and reinstalling them.

---

### Post by simonn on 2007-04-23
> **xtreme35967 said:**
> SB drivers and reinstalling them.

Gahhhsh, that is like soooo windows.

What is probably happening is that the kernel is assigning your onboard sound as the first sound card and the sound blaster as the second. Most applications are probably defaulting to the first sound card.

Sound possible?

See my posts on [http://ubuntuforums.org/showthread.php?t=410263](http://ubuntuforums.org/showthread.php?t=410263).

---

### Post by Neecapp on 2007-04-23
> **simonn said:**
> Gahhhsh, that is like soooo windows.

What is probably happening is that the kernel is assigning your onboard sound as the first sound card and the sound blaster as the second. Most applications are probably defaulting to the first sound card.

Sound possible?

See my posts on [http://ubuntuforums.org/showthread.php?t=410263](http://ubuntuforums.org/showthread.php?t=410263).


lol reinstall drivers..

It sounds like he hit the nail on the head. Also.. SBLive 24Bit is a problematic card for some reason. But your on-board mobo card is probably being set as the default and your kernel isn't utilizing your sb24bit.

Take care.

---

### Post by xtreme35967 on 2007-04-24
Yeah Yeah I know funny. I am a little bit of a noob so laugh all you want. Anyways Thanks for the help and I will try it when i get home.

---

