---
title: "nvidia hdmi edid_disable_exts...tgz?"
date: 2010-09-29
forum: Multimedia Software
---

### Post by odsus1 on 2010-09-29
I have seen several posts on various message boards that touch on the no sound over hdmi on nvidia cards issue (mine is an 8400 gs) and the general consensus seems to be create a custom edid and tell x to use it. So here is the heart of the post: I downloaded [**http://analogbit.com/sites/default/files/edid_disable_exts_v1.2.tgz**]("http://analogbit.com/sites/default/files/edid_disable_exts_v1.2.tgz") to modify my edid but I don't know what to do with it. I extracted it and tried **$ make** and **$ sudo make install** But that wasn't the ticket, could someone please educate me, thanks;
Odie

---

### Post by odsus1 on 2010-10-17
Well I fixed the hdmi audio stream problem simply by updating the nvidia driver to 260.19.12. Now I can hear sound through my TV using my soundcard bypassing the hdmi audio. If it will help anyone here is what I did (note: this is for 10.04/10.10);

Add the PPA to the repository:
```
$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Install the current nvidia drivers:
```
$ sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```Go to hardware drivers (sys/admin/hardware drivers) and enable the current version

Restart

Thanks to webupd8 for the walkthrough ([http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html")

---

