---
title: "[SOLVED] Monitor goes black on bootup."
date: 2008-07-15
forum: Multimedia Software
---

### Post by johnnyhop on 2008-07-15
Xubuntu installed on a slopoke. 233mHz CPU with 512mb RAM. While booting all looks well until the login screen is expected, then monitor goes black. The display adapter is integrated lshw identifies it as: Trio 64V2/DX, vendor: S3 Inc, driver=s3fb. Tried dpkg-reconfigure xserver-org but no conf support for monitor was offered, only keyboard. I'd like to try lowering the resolution but don't know how in terminal mode.

---

### Post by aeiah on 2008-07-15
you can alter it by editing your xorg.conf file and setting a lower maximum resolution. that'd probably be your best bet. you could copy and paste your xorg.conf here too for someone to have a look at if you have the patience to do that :p

on the command line, use nano to edit documents and use w3m or lynx to view websites. to edit your xorg.conf do

```
sudo nano /etc/X11/xorg.conf
```

normally id suggest backing up your xorg.conf but i guess there's not much point if its broke :p

---

### Post by johnnyhop on 2008-07-18
Thank you, that pointed me in the right direction. Not knowing how to properly instruct xorg.conf to load screen resolution my two attempts at modifying the file failed.  Then found on my Kubuntu machine an xorg.conf.failsafe which made a reference to screen resolution.  Copying that file to the new Xubuntu install (by way of the old legacy diskette) ultimately got to the GUI.

---

