---
title: "[SOLVED] VLC Korean subtitle problem"
date: 2008-12-13
forum: Multimedia Software
---

### Post by ryecomp on 2008-12-13
Env)
Ubuntu 8.04
VLC 0.8.6e

Symtoms)
1) Subtitle not displayed when launched from nautilus.
2) Subtitle displayed if VLC executed as follows. 
execute VLC > Open button > file selection > use a subtitle file ON > Advanced settings > Subtitle text encoding > EUC-KR 

Solution)
1) VLC > Preference > Input/Codecs > Other codecs > subtitles > Subtitle text encoding to EUC-KR
2) Nautilus > Right click > Open with Other application > use a custom command > vlc %m

---

