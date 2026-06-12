---
title: "error:symbol not found: &quot;grub_env_export&quot; on boot up"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sprogmeister on 2011-04-10
I tried updating to Natty Narwhal from the previous version of Ubuntu on rebooting receive the error message "error:symbol not found: "grub_env_export". I have tried to make changes to the grub via the live cd but am told it cannot find grub. Please help.

---

### Post by Rowanmf on 2011-04-11
PLEASE help i am having the same problem .

Thanks

---

### Post by sprogmeister on 2011-04-18
Anyone?

---

### Post by dino99 on 2011-04-18
goes to synaptic to remove/purge then reinstall grub-pc & grub-common

---

### Post by sprogmeister on 2011-04-18
Thanks dino99, but the OS won't even boot ti stops at the line given in the title. Any ideas?

---

### Post by FEGuy on 2011-04-18
For anyone who can't seem to log into their PC because of this issue, get some distro with a live session and use it to re-install grub completely. Doesn't seem to stop GRUB from breaking every time a new version hits the Natty repos, though, or at least for me.

---

### Post by drs305 on 2011-04-18
Often this type of message indicates grub wasn't fully installed. You can do as *dino99* suggests from the LiveCD using the 'chroot' procedure so it alters your real installation.

Visit the "Chroot" link in my signature line for instructions on how to purge and then reinstall grub-pc. Make sure you are using a Natty CD, as previous releases used Grub 1.98 and Natty uses 1.99. (1.98 will work with Natty, but it would be better to use the version shipped with it).

Edit: My Grub2 broke yesterday after an update but, as I was playing with themes, assumed the theme broke it. Perhaps not...

---

### Post by s3MA00RRNY on 2011-04-27
I'm having the same problem on Mint Debian (based on Testing). Must be an upstream issue. I'll try reinstalling :/

---

