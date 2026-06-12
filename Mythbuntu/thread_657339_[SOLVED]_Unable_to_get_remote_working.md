---
title: "[SOLVED] Unable to get remote working"
date: 2008-01-03
forum: Mythbuntu
---

### Post by murbanci on 2008-01-03
I have been trying to get my ATI Wonder remote working with my mythbuntu system (v 7.10).  I have tried uninstalling and reinstalling lirc and even reinstalling the whole OS and setting the remote up in the initial setup but nothing has worked.  When i try to run irw i get "connect: Connection refused".  At one point I had irw working and all the buttons were mapped right so I know that the remote is working, but I have never gotten it to control the mythfrontend.  I am a complete n00b so any help would be greatly appreciated.  Thanks!

---

### Post by volkswagner on 2008-01-03
In mythbuntu-control-centre what remote is selected under remote configuration?  Try to change it to another ati IR remote if the proper one is selected.  I have noticed irw refuses connections when an RF remote is selected.  You can always change it back.

---

### Post by murbanci on 2008-01-03
> **volkswagner said:**
> In mythbuntu-control-centre what remote is selected under remote configuration?  Try to change it to another ati IR remote if the proper one is selected.  I have noticed irw refuses connections when an RF remote is selected.  You can always change it back.

Ok so i tried that and nothing.  But when i disabled the remote in the control-centre and rebooted the system, irw worked and the remote would sorta function.  Some of the buttons are mapped wrong or not at all.  When i press buttons while running irw it says the remote is Snapstream.  So i guess the next step would be to remap the buttons but im not sure how to do that.  Thanks

---

### Post by murbanci on 2008-01-03
Ok i have it figured out! The config files were for the new ATI remote and I have the old one.  I fount the correct config files and put them in the correct files and everything works.  For some reasion, I dont need to have a remote enabled in the mythbuntu-control-centre.

---

