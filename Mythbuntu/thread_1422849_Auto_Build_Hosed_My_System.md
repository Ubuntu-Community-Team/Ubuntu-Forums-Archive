---
title: "Auto Build Hosed My System"
date: 2010-03-05
forum: Mythbuntu
---

### Post by dsbw on 2010-03-05
I wanted to upgrade my mythtv from .21 to .22 (and my ubuntu as well) so I downloaded Auto-Build.

Auto-build upgraded parts of myth (partial upgrade) but in the process removed my front-end! (Or at least access to it from the menu. And the themes are the things that are showing as not being upgraded.)

It actually uninstalled mythfrontend? That doesn't seem helpful.

I try installing the frontend, and I get the "Some packages could not be installed" message. 

(I'd also like to upgrade from 9.04 -> 9.10, too, but I get the dreaded "No new release found" when I try.)

WTH?!?

---

### Post by tgm4883 on 2010-03-06
> **dsbw said:**
> I wanted to upgrade my mythtv from .21 to .22 (and my ubuntu as well) so I downloaded Auto-Build.

Auto-build upgraded parts of myth (partial upgrade) but in the process removed my front-end! (Or at least access to it from the menu. And the themes are the things that are showing as not being upgraded.)

It actually uninstalled mythfrontend? That doesn't seem helpful.

I try installing the frontend, and I get the "Some packages could not be installed" message. 

(I'd also like to upgrade from 9.04 -> 9.10, too, but I get the dreaded "No new release found" when I try.)

WTH?!?

Well without you posting any sort of log or terminal output. I can't really tell you what happened. I can speculate though. 

You probably ran into an issue with libvdpau and it being split from another package that it was in. I can't stress enough that people read the screen and not blindly hit yes without knowing what is happening to their own system. That is a huge security hole.

apt-get asked you if you wanted to do a partial upgrade and you hit told it yes (if you had read, it told you it was going to remove mythfrontend in the process). I think the only thing that 'hosed' your system was you.

---

### Post by dsbw on 2010-03-06
> **tgm4883 said:**
> Well without you posting any sort of log or terminal output. I can't really tell you what happened. I can speculate though. 

You probably ran into an issue with libvdpau and it being split from another package that it was in. I can't stress enough that people read the screen and not blindly hit yes without knowing what is happening to their own system. That is a huge security hole.

apt-get asked you if you wanted to do a partial upgrade and you hit told it yes (if you had read, it told you it was going to remove mythfrontend in the process). I think the only thing that 'hosed' your system was you.

Yep, that was it. I sure didn't see a "this will remove your frontend" message, but it's possible I just missed it. "Partial upgrade" is somewhat deceiving, though, don't you think, "Partial upgrade with removal of functional parts" would be a little more to the point? :razz:

---

### Post by tgm4883 on 2010-03-06
> **dsbw said:**
> Yep, that was it. I sure didn't see a "this will remove your frontend" message, but it's possible I just missed it. "Partial upgrade" is somewhat deceiving, though, don't you think, "Partial upgrade with removal of functional parts" would be a little more to the point? :razz:

Well that would be a bug you would have to file against apt. When you do an apt-get dist-upgrade, you should see something like this.

```
thomas@hermes:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  anacron apport apport-gtk at build-essential byobu capplets-data compizconfig-backend-gconf
  coreutils cpio cron dcraw diffstat ed empathy empathy-common f-spot findutils finger gdm gettext
  gettext-base gksu gnome-bluetooth gnome-control-center gnome-nettool gnome-power-manager
  gnome-terminal gnome-terminal-data grep gtk2-engines-pixbuf ibus ibus-gtk indicator-application
  indicator-messages initramfs-tools initramfs-tools-bin iptables libaa1 libanthy0 libappindicator0
  libbabl-0.0-0 libcairomm-1.0-1 libdevkit-power-gobject1 libexempi3 libflac8 libgail-common
  libgail18 libgegl-0.0-0 libglitz-glx1 libglitz1 libgnome-bluetooth7 libgnome-window-settings1
  libgoocanvas-common libgoocanvas3 libgpm2 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libibus1
  libido-0.1-0 libijs-0.35 libilmbase6 libupower-glib1 light-themes nautilus-sendto-empathy
  notify-osd nvidia-current-modaliases python-appindicator python-apport python-ibus
  python-problem-report python-ubuntuone-client python-ubuntuone-storageprotocol simple-scan
  ubuntu-artwork ubuntu-wallpapers ubuntuone-client ubuntuone-client-gnome ufw upower
  usb-creator-common usb-creator-gtk wpasupplicant xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom
86 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.1MB of archives.
After this operation, 356kB disk space will be freed.
Do you want to continue [Y/n]? 

```

If it is going to remove any packages, there will be a section like this

```
The following packages will be upgraded:
mythfrontend
```

By default, I don't think doing an apt-get upgrade removes packages. I think you need the dist-upgrade for that. 


Now all of that aside. What is the output when you try to do an apt-get install mythfrontend.

---

### Post by dsbw on 2010-03-06
It was something like "dpkg: error processing [some file] trying to overwrite '/usr/lib/libvdpau_trace.so', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9"

I did a lot of different things (upgraded to 9.10 and .22) including using the Avenard repos[1], but I'm not sure if the key thing I did was to uninstall  nvidia-185-libvdpau 0:185.18.36-0ubuntu9. It seemed like that removed the conflict. 

Now I'm not even sure if I have vdpau going, but the picture quality has dropped (tears and artifacts) with the 9.10/.22/185 Nvidia drivers.

[1] [http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html)

---

### Post by dsbw on 2010-03-07
OK, so here's the predicament I'm in:

In order to get around the libvdpau problem, I uninstalled the problem package, then manually installed the ones (I thought) I needed. But then the system had trouble booting; when it finally does boot, it's okay but the restricted NVidia drivers are not active.

When I activate it tells me it can't activate because the of the libvdpau conflict.

Crap!

---

