---
title: "Lost all sound configurations"
date: 2008-05-19
forum: Multimedia Software
---

### Post by iomesus on 2008-05-19
Under Preferences > Sound, I had all my sound set up correctly using Alsa. I was trying Vendetta Online, and it requires OSS, so I attempted to get OSS working (messed around installing OSS based app's from synaptic, ended one or two processes to see if they were interfering...etc). Somehow I've ended up with no sound icon in notification area on taskbar, and even worse, under Preferences > Sound I now have no options for Default Mixer Tracks, and only 3 options for each of the Sound Events, Music and Movies etc. None of these options work, so I have no sound.. :( why do I always try to fix things I don't understand.

I was hoping you could tell me a way to get Ubuntu to rescan all my hardware and set it up like it did at installation. If that's not possible then any other suggestion would be appreciated.

I'm using Ubuntu 8.04 x86_64.

~peter

---

### Post by Royke on 2008-05-19
Hello iomesus, i hope this helps and is correct: In your profilefolder you can delete(move to thash) the folder gnome-volume-control. It will reset the mixer and a new folder with settings will be created automatically. /home/yourname/.gconf/apps/gnome-volume-control

I'm sorry to say i haven't tested it but it worked before when i used gamix. You can also try to move everything but documents to the thash and test it.
Good luck :guitar:

---

### Post by iomesus on 2008-05-19
Thanks for the quick reply, unfortunatly this doesnt seem to have worked though :( no change after reboot.

I've also just tried the 'Getting the ALSA drivers from a *fresh* kernel' on [here]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound"), but this had no effect either :(

Not looking too good. I really don't want to have to do a fresh install.

---

### Post by iomesus on 2008-05-20
Spent so much time trying to fix this that I'm just going to give in and do a fresh install. Thanks for trying Royke.

---

