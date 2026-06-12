---
title: "Multimedia player not working"
date: 2008-12-11
forum: Multimedia Software
---

### Post by deneth on 2008-12-11
Im having a nightmare with ubuntu. Since i have installed Vlc player which i have used with other linux distribution its not functioning in Ubuntu. When ever i try to play a vedio file i get this green screen. I installed M-player to check whether the issue is with VLC. but it gives me the same problem. 

From my expereince i think the problem is with a codec. So i tried installing libxine1-all-plugins. But still i get the same error

Any suggestions

---

### Post by kpkeerthi on 2008-12-11
[http://ubuntuforums.org/showthread.php?t=671994&highlight=green+totem](http://ubuntuforums.org/showthread.php?t=671994&highlight=green+totem)

---

### Post by deneth on 2008-12-11
I have solved the matter with Vlc by changing the settings of the output. I have changed the output to X11 vedio output/

the change was done 
as 
Settings > Preferences > Video > Output Modules > Advanced Options > Videod output module > X11 video output 

Mplayer the problem still exists. output mode change did not help

---

