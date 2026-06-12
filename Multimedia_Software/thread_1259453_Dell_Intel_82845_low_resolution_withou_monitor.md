---
title: "Dell Intel 82845 low resolution withou monitor"
date: 2009-09-06
forum: Multimedia Software
---

### Post by MIKE SILVA on 2009-09-06
Hi all. 
Strange situation!
I install 9.04 on a Dell with motherboard Intel and graphic card 82845 and everything runs perfect. 
But I want to use this machine without monitor. And access using the remote option. When I boot without monitor, the system block, giving a message about low resolution mode.
Search and search everywhere and the unique solution I found is to change the xorg.conf and adding:

Section "Device"
Identifier "Configured Device"
Driver "vesa"
EndSection

Now the system starts well, but I have only 640 x 320 resolution. Try to add:

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Device"
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

But this part doesn’t change a thing. Still the same low resolution.
Any help Please?

---

