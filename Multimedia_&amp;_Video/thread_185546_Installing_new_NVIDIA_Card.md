---
title: "Installing new NVIDIA Card"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by zeppelin06 on 2006-05-31
I just upgraded my ati 9000 to a nvidia 6200, however after installation X crashes.  I'm assuming it is because ubuntu is looking for the ati card and the xorg needs to be reconfigured.  However I don't know how to get to the xorg without GDM, or what to change in it, if this is in fact the problem. Secondly will the upgrade to dapper tommorow look for my hardware and reconfigure without losing my home folder and installed programs?  Thanks in advance.

---

### Post by tonyr on 2006-05-31
I assume that you are getting a console login prompt (black screen, white characters) and that you can login.  At that point you can
```

sudo dpkg-reconfigure xserver-xorg

```

After that, you can simply reboot, or you can
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

Nvidia controllers need some special handling to get the full benefit.  See
[URL="http://doc.gwos.org/index.php/Latest_Nvidia_Dapper"]
http://doc.gwos.org/index.php/Latest_Nvidia_Dapper[/URL]

---

### Post by zeppelin06 on 2006-06-01
Thank you, after three attempts GDM and xserver are working again.  However after installing the nvidia drivers using the linked instructions the performance of the geforce 6200 is worse than the ati 9000.  Maybe dapper will correct this during upgrade.



Thanks problem solved

---

### Post by fuuma_monou on 2006-06-03
Did you also install glx, nvidia-glx, and nvidia-settings?

---

