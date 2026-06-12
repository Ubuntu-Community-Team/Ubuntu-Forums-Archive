---
title: "Amarok won't play ogg files"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by Stochastic on 2007-11-30
So I'm running UbuntuStudio Gustsy64 and amarok is giving me errors when it tries to play some of my ripped (through sound juicer) cds that are ogg files.  I don't think I have any other ogg files on my computer so I can't tell where this issue is stemming from but totem is able to play the files just fine.  It's Amarok 1.4.7 (using KDE 3.5.8 ).  Any suggestions?

---

### Post by Stochastic on 2007-12-05
bump.

---

### Post by koleoptero on 2007-12-05
Amarok uses xine so you need plugins for xine. try installing libxine1-plugins and libxine1-ffmpeg and it should then be able to play everything.

---

### Post by Stochastic on 2007-12-05
hmm apt-get says I have those installed.

---

### Post by koleoptero on 2007-12-06
Hmmm, then it must be a bug or something. Does amarok play everything else?

---

### Post by Stochastic on 2007-12-07
well it plays mp3 files fine.  bahh, whatever, I'll just sit with a bug up my a** until April.  no use pulling my hair out over one particular player.

---

### Post by Stochastic on 2007-12-07
Actually, how do I go about checking which version of xine I have installed?

---

### Post by prince_niceguy on 2008-01-10
I had some problem earlier in the not able to play ogg files. The problem was traced out to ntfs-3g. I have my entire collection on ntfs so it is shared between windows and linux. some how ntfs was not able to write to ogg file, amarok was playing ogg fine but when i used to change the tag detail it used to crib that there were no demux found to play it. So, to avoid this i copied all the files from external drive to my laptop again and it started playing the songs even after editing the tags.

---

