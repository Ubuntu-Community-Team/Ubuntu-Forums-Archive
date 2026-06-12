---
title: "envy Nvidia Drivers Xserver crash"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by jefisme03 on 2007-08-19
I get a xserver crash when I reboot 7.04 fiesty fawn after installing nvidia drivers useing envy. im useing an 8800 gts. This is a new install. im switching over from windows cause ill be going to college for an IT degree which includes linux. any help will be appreciated a lot. thx

---

### Post by tseliot on 2007-08-19
Boot in Recovery Mode (select it from the GRUB menu)

then restore the backup of your previous xorg.conf:
```
cd /etc/X11/
```
```
ls
```
you'll see xorg.conf and other backup files (e.g. xorg.conf_backup_200703022015)

replace xorg.conf with a backup:
```
cp name_of_your_backup_file xorg.conf
```

then reboot by typing:
```
reboot
```

Boot as usual and post your /var/log/envy-installer.log

---

### Post by jefisme03 on 2007-08-19
ok it looks like the xorg.conf and its backup were both deleted
i went ahead and re installed and i can now boot but i have far too low of a resolution

---

### Post by tseliot on 2007-08-19
> **jefisme03 said:**
> ok it looks like the xorg.conf and its backup were both deleted
i went ahead and re installed
Reinstalled what? the driver or Ubuntu?

---

### Post by jefisme03 on 2007-08-19
i reinstalled ubuntu completely it turns out that if you install the nvidia drivers then update ubuntu it will delete or corrupt any xorg.conf files you have but i tried updateing first this time and went off with out a hitch

---

### Post by tseliot on 2007-08-19
> **jefisme03 said:**
> i reinstalled ubuntu completely it turns out that if you install the nvidia drivers then update ubuntu it will delete or corrupt any xorg.conf files you have but i tried updateing first this time and went off with out a hitch
Now I know what you mean...

You will have to run Envy every time the kernel is updated (Boot in the new kernel and type: envy -t ).

---

