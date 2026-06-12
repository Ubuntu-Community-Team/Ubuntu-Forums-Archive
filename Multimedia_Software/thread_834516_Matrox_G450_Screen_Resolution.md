---
title: "Matrox G450 Screen Resolution"
date: 2008-06-19
forum: Multimedia Software
---

### Post by JDA on 2008-06-19
To start with I am a "Newbie" so please forgive me.

I have a Matrox G450 video card in my machine. I loaded Ubuntu 8.04 Server the added the ubuntu desktop GUI. I can not get the resolution greater than 800x600. 

I tried editing the xorg.cong file to add:

SubSection "Display"
              Depth 24
              Modes "1280x140" "1040x768" "800x600"
EndSubSection

when I rebooted the system I got a screen that was barely readable and showed 2 or 3 desktops on about 2/3 of the monitor screen (CRT monitor).

Can anyone please help a "Newbie" resolve this issue

Thanks

---

### Post by JDA on 2008-06-19
excuse the typo in the previous post - the Mode was set as "1280x1040"   not "1280x140" 

need to find a keyboard that can spell - that or tighten the nut between the chair and the keyboard

---

