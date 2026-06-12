---
title: "Nvidia has trouble loading module - x broken"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by gavintlgold on 2007-10-21
Hi, a while ago I started the envy script, stopped it after it installed the  dependencies, and then installed the nvidia drivers using the .run file.

Then I upgraded to the gutsy beta, without any problems. However, one day I updated, and nvidia fails to load the module now, with an error about that. When i'm back on my failsafe x i'll post the error, but it's very vague.

In gutsy I am using the restricted drivers manager for  my nvidia install.

card: NVIDIA GeForce 7600

nvidia-glx is not installed, nvidia-glx-new is, the kernel modules are installed... but it doesn't work. Can anyone help?

---

### Post by pbcartwright on 2007-10-21
after any upgrade that installs a new kernel module, you need to rerun the envy/NVIDIA install script..
to get into X you can edit /etc/X11/xorg.conf and change the driver line from:
nvidia
to nv
then you can at least run X and rerun envy OR stay at the command prompt and run the .run install script again.

---

### Post by gavintlgold on 2007-10-21
But i thought Ubuntu was supposed to fix that automatically. I did not run the install script while updating gutsy, and it worked. This time updating, it did NOT.

---

