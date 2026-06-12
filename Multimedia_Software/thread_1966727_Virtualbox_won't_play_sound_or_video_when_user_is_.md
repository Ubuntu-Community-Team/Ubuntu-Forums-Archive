---
title: "Virtualbox won't play sound or video when user is logged off"
date: 2012-04-27
forum: Multimedia Software
---

### Post by stapper on 2012-04-27
Hi

I have set up 2 Virtualmachines with an administrator account on my ubuntu 12.04 3.2.0-24-generic. These two machines run headless. When I log out of the admin account and in with a standerd user account I cannot play media files on that VM via rdesktop. When I log out however and log back in with the admin account that "runs" the machines the sound starts playing. I tried to run it on boot with a startup script with username root but that didn't help, now the music and video play but there is still no sound.
Is there a way so that the sound will play when I rdesktop from a user account to the VM?

Kind Regards

ps: i'm using the most recent version of VBox

---

### Post by stapper on 2012-04-27
I solved it by changing the uid's so they are the same for the user running the VM and the user looking at the VM through rdesktop. I don't believe this is the best solution but it will do for now

---

### Post by SeijiSensei on 2012-04-27
Are all the users in the vboxusers group?  The simplest way to check is to edit /etc/group as root with sudo and look for the line that begins "vboxusers".  After the final colon there should be a list of usernames.  Make sure all the users who will be running VBox are in the list; separate the usernames with commas.  See if that helps.

---

### Post by stapper on 2012-04-28
Thanks for the reply but I already tried that, and it didn't help.
Now I just let the user for whom te VM is inteded also start the vm at first login, this way I have sound when the user is loged in local but not when he is connecting from a remote location, like another pc in the same network.

---

