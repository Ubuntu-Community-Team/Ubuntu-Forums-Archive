---
title: "XOrg Help"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by ditoa on 2006-10-13
Hey all. I have Ubuntu 6.06.1 installed in VMware Workstation (5.5.2, the lastest version as of this date) but I have 1 small problem.

I want to be able to use two resolutions in Ubuntu. 1024x768 and 1280x1024. The reason for this is that my monitors res is 1280x1024 so when I run the VM full screen I want it to use the full screen resolution, however 90% of the time I run it in the VMware Workstation window at 1024x768.

Now I have edited my xorg.conf to include this ...


```
Modes    "1024x768" "1280x1024"
```


However this causes the VM to boot up to 1280x1024 (at the login screen). I changed the resolution (and checked make it system default) to 1024x768 and when I am logged in it runs at this resolution however at the login screen it is still 1280x1024.

Now I am guessing that either a) XOrg uses the highest resolution as the default/boot resolution or b) I need to set the default resolution somewhere else.

Could someone with some XOrg knowledge lend a hand?

Many thanks.

---

### Post by CatKiller on 2006-10-14
Everything to do with the graphical login is handled by GDM. There is a file of configuration options at /etc/X11/gdm/gdm.conf-custom.

That's about all I know.

---

