---
title: "nvidia drivers for ubuntu 9.10"
date: 2010-03-16
forum: Multimedia Software
---

### Post by jackaloper on 2010-03-16
I have ubuntu 9.10. I have nvidia graphics motherboard 7050(nvidia 610i). Recently i reset the desktop (removed gnome conf files because it had
become messly i mean my panels). The problem is that my resolution is fixed at 800x600 which i dont want. Even if i save to the xorg.conf, after i restart it does not change. I know the problem is with nvidia drivers which even if i change to the 185 one in the repositories my resolution is still 800x600 and desktop effects cannot be enabled. But in 9.04 i had no problem.

I have googled this problem but i cannot get the keyring from keyserver.ubuntu.com to use when i add the ppa to my repositories to get the 190.xx or 195.xx.

help me pliz i am about to downgrade to 9.04.

---

### Post by sikander3786 on 2010-03-16
I think you should remove your old NVIDIA Drivers before installing new ones. Use Envy to remove old drivers (Envy is found in repositories).

Then again install the drivers.

Hope that helps.

Sikander.

---

### Post by jackaloper on 2010-03-16
[sikander3786]("http://ubuntuforums.org/member.php?u=806649"):

i have done that -EnvyNG shows that i must install, when i try it i get: p, li { white-space: pre-wrap; }  installArchives() failed


i also did: sudo add-apt-repository ppa:nvidia-vdpau/ppa 

to download from ppa but cannot get keyring.

---

### Post by sikander3786 on 2010-03-17
Try un-installing from the command line.

```

sudo sh NVIDIA* --uninstall

```

Have you followed the following page. It states a lot about resolutions.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

