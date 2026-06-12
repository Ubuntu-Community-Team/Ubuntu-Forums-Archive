---
title: "uninstall driver from live cd?"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by kyle.k on 2008-02-02
Hi, first time posting in the forums, been checking the site out as ive been figuring ubuntu out by trial and error lol. Well anyways, my question is, is it possible to uninstall drivers via the live cd, i installed the ati drivers for my awi 9800 pro and now when ever i boot into ubuntu i just get a blank screen.

---

### Post by RomeReactor on 2008-02-02
Hi. If you get dumped to the command line after the system boots, try this:
```
sudo dpkg-reconfigure xserver-xorg
```
Follosw the instructions and accept the defaults, except when asked which video driver to use select **fglrx**. If your display doesn't start immediately after finishing, enter:
```
sudo /etc/init.d/gdm start
```
or:
```
startx
```

If you keep getting this problem, try the dpkg-reconfigure command again and this time select **ati** as the dirver.

---

### Post by kyle.k on 2008-02-02
it just goes black, no command line unfortunately

---

### Post by RomeReactor on 2008-02-02
Try booting in Safe Mode/Recovery Mode, then run the commands. To boot in Safe/Recovery Mode, press ESC when Grub begins to load.

---

### Post by kyle.k on 2008-02-02
still just a blank screen, is there maybe a boot command that i could use to stop it from loading the ati drivers?

---

### Post by RomeReactor on 2008-02-03
> **kyle.k said:**
> still just a blank screen, is there maybe a boot command that i could use to stop it from loading the ati drivers?

Does your system show any display after turning it on--such as BIOS version, motherboard/video card datails, etc.? after those, there should be a screen telling you that you have 3 seconds to "Press ESC to load the Grub menu" or something similar. Also:
> **RomeReactor said:**
> Try booting in Safe Mode/Recovery Mode, then run the commands. To boot in Safe/Recovery Mode, press ESC when Grub begins to load.
That should have read "To boot in Safe/Recovery Mode, press ESC **before** Grub begins to load".

---

### Post by kyle.k on 2008-02-03
yup, i can see all the way up until its supposed to load into the os. and when i tried to boot into recovery mode, it did the same thing.

---

### Post by RomeReactor on 2008-02-03
That's odd. In any case, you could load the Live CD, open a terminal and mount the HD:
```
sudo mkdir /media/harddrive
```
then:
```
sudo fdisk -l
```
to see if your root partition is **/dev/hda1** or something else; if *it is* **/dev/hda1**:
```
sudo mount /dev/hda1 /media/harddrive
```
if not, change as appropriate; then edit the xorg.conf file in the HD:
```
sudo nano /media/harddrive/etc/X11/xorg.conf
```
Scroll down to **Section "Device"**, and change the driver from **fglrx** to **ati**. To save the file press CTRL+O, then CTRL+X to exit the text editor. To unmount the HD:
```
sudo umount /dev/hda1
```

---

### Post by kyle.k on 2008-02-03
i was able to edit the xorg.conf, but i still get the blank screen at startup. what else could be causing this?

---

