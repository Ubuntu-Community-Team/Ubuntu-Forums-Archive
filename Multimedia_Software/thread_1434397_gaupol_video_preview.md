---
title: "gaupol video preview"
date: 2010-03-20
forum: Multimedia Software
---

### Post by dazle on 2010-03-20
i use gaupol subtitle editor and i want to change the video player it uses for subs' preview
it has vlc and mplayer to choose between but i want to use totem

so i will need the third option which is "custom" but i don't know what to set as command
(for MPlayer it is:
mplayer -identify -osdlevel 2 -ss $SECONDS -slang -noautosub -sub $SUBFILE $VIDEOFILE
and for VLC:
vlc $VIDEOFILE :start-time=$SECONDS :sub-file=$SUBFILE)
but i can't figure out what would it be for totem (yeah dummy:p)
 
any help?

---

