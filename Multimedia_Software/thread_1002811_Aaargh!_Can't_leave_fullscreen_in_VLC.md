---
title: "Aaargh! Can't leave fullscreen in VLC"
date: 2008-12-05
forum: Multimedia Software
---

### Post by Donalb on 2008-12-05
Hey all, I know the shortcuts, f for fullscreen on/off. F11 for fullscreen controls etc, but no matter what I do I can't get out of fullscreen oin VLC. stopping and starting a different vid file starts fullscreen immediately.

I'm SURE it's something dumb I've done/missed but a clue would help...


Regards

---

### Post by miniyak on 2008-12-05
obvious would be not right clicking for options but im sure you've done that. if your really stuck, it might be a bug, a re instillation of vlc might do the trick (move to  screen left, to control ubuntu agian) sorry for the laymen answer.

---

### Post by mc4man on 2008-12-05
Your best bet would be to delete the vlcrc file.
 
What you could try first is open vlc -> tools and enable the fullscreen interface checkbox which will actually disable it.(when in fullscreen interface
 Then go media -> exit and reopen.

The 0.9.x rc is in home -> .config -> vlc
The 0.8.6 is in home -> .vlc

---

### Post by Donalb on 2008-12-05
Thanks guys.
I had already tried the "set fullscreen" option and quit, in the hope it might kick something loose on a restart, but that didn't work either. It's not a big deal but I would have preferred to know if there was something i was doing wrong before going the uninstall/reinstall route...
I tried deleting vlcrc but that didn't do it so I've done a reinstall. But....it's still fullscreen!

---

### Post by mc4man on 2008-12-05
Are you using vlc 0.9.x or vlc 0.8.6 and are you using 8.10 (intrepid) or 8.04 (hardy) ?


Edit; don't think it matters which

Go in to home folder -> (view -> show hidden files) and **totally delete** .vlc if found.
Open .config and **totally delete** the vlc folder if found.

Now restart vlc
If using 0.8.6 it should start normally
If using 0.9.x you should first get the 'privacy and network warning' pop up, then vlc.

---

### Post by Donalb on 2008-12-06
You're a star! That worked. Thanks very much.
BTW for anyone else searching, it was 0.9 VLC on Intrepid.

Thanks again!

Regards

---

### Post by InspirationDate on 2009-04-07
I had this same problem and finally figured out I needed to click Tools > Fullscreen Interface.  It's kinda dumb that pressing F11 will enable fullscreen but won't disable it.

---

### Post by qamelian on 2009-04-07
> **InspirationDate said:**
> I had this same problem and finally figured out I needed to click Tools > Fullscreen Interface.  It's kinda dumb that pressing F11 will enable fullscreen but won't disable it.
The 'F' key also toggles fullscreen on and off.

---

