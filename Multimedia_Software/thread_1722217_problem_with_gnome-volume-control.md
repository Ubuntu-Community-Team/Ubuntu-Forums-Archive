---
title: "problem with gnome-volume-control"
date: 2011-04-05
forum: Multimedia Software
---

### Post by brizou on 2011-04-05
Hi everybody,
First of all excuse me for my english, I'm french so it's not perfect.
I recently changed from alsa to oss4 for a better support of my audiocard (aaudiotrak prodigy hd2)
I can't control the sound volume via gnome-volume-control anymore, and my keyboard's volume keys are now useless.
However when I go in, i have this
[[img]http://uppix.net/5/f/d/cbda33e8e8e3ad4196873ab1ad895tt.jpg[/img]](http://uppix.net/5/f/d/cbda33e8e8e3ad4196873ab1ad895.html)

And there I can control the volume. 

How can I do to force vmix0-ouvol to be the default volume outpout on my computer ?

Thank you, I hope I have been clear in my request

---

### Post by brizou on 2011-04-06
up ?

---

### Post by lidex on 2011-04-06
Add this ppa and use those packages instead of default:
[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by brizou on 2011-04-06
it's strange, I added the repo to my sources.list, i did an apt-get update but an apt-get upgrade didn't upgrade thse packages and it would'nt find libcanderra, as if there was nothing on the repo.

---

### Post by lidex on 2011-04-07
What ubuntu release are you on? Apt/Synaptic may not see those packages as an upgrade and therefore doesn't offer to install.
If you open synaptic, click on the 'Origin' button on left then select that ppa above it. On the right select those packages for install and see what happens. Have you uninstalled the default packages? Did you follow this procedure to install OSS:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by brizou on 2011-04-07
I'm on maverick, when i go on the origin button everything is installed, it consider it as the xurretn pakage. I followed the french version of the procedure 
[http://doc.ubuntu-fr.org/oss4](http://doc.ubuntu-fr.org/oss4)

I did resolve partially the problem by launching ossxmix, now by keyboard is working, not gnome-volume-control but I don't really mind.

---

