---
title: "Resoultion won't stay ATI"
date: 2008-08-27
forum: Multimedia Software
---

### Post by musta78 on 2008-08-27
Hi

Does anyone know how to fix the resoltuion?  Everytime I reboot the resoultion goes back.  Very annoying!

On NVIDIA I could just open the display manager in terminal as root user.  I've tried the same with the Catalyst control center but no luck.

Anyone?

---

### Post by tuxxy on 2008-08-27
It should save the settings if run as root, are you saving it to the  xorg efore you quit it

---

### Post by musta78 on 2008-08-27
I'm not in the xorg file.

I'm trying to solve how I can get changes done with Catalyst control center.

Manual editing the xorg.file will be an emergancy solution

---

### Post by tuxxy on 2008-08-27
You catalyst control centre is saving the configurations to your xorg, save your changes in the program before quitting it.

---

### Post by musta78 on 2008-08-27
Well, that is the problem.  The Catalyst center is NOT saving the change of resolution.  

I change resolution, push apply and the ok.  The Catalyst center closes.

Had the same issue when I had NVIDIA.  There I opened the control center with terminal in root so the changes would save.

---

### Post by markbuntu on 2008-08-27
You should save your session when you get it setup the way you want or change it so it remembers when you log out. Otherwise you will end up back where you were every time you login

---

### Post by musta78 on 2008-08-27
This will maybe sound stupid to you, but from where can I save it?

---

### Post by markbuntu on 2008-08-27
Oh sorry, System/Preferences/Session. There are tabs, you will figure ot out from there.

---

