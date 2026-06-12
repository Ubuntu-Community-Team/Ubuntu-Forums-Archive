---
title: "Restore audio function in (now) Xubuntu 18.04 LTS"
date: 2019-06-08
forum: Multimedia Software
---

### Post by derek-lawrence on 2019-06-08
Hi, I had an audio problem with my Acer netbook when I was running Xubuntu 16.04, I tried to fix it using internet posts and ended up with no sound output at all.

 Everything else works, and I didn't need sound then, so I gave up and left it the way it was. Then the update came along for 18.04, so I installed that, thinking it might put it right - it didn't. Now I have some time and I want to use the netbook for usb voice chat while gaming so it would be useful to have sound if possible. I know there's the "Nuclear option" to re-install from scratch, but I've personalised this install so much that I'd really rather not do that unless I absolutely have to.

 I started with this thread [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting), and it seemed promising until I pasted in the command "[COLOR=#333333][FONT=UbuntuMono]sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2[/FONT][/COLOR]" to refresh/reinstall the drivers, at which time the terminal gave me the error "sudo: aptitude: command not found" and having no idea what to do next, I decided to post here.

 Many thanks in advance for any suggestions/help you can provide, I look forward to voice chat soon - Derek

---

### Post by CatKiller on 2019-06-08
aptitude is a command-line package manager, but it's not installed by default. You can install it with ```
sudo apt install aptitude
``` or use apt instead.

---

### Post by derek-lawrence on 2019-06-14
Thanks for that, I installed Aptitude and ran the command again, that gave me a different collection of errors.
Fortunately I have a backup, so I've re-installed - Problem solved.

---

