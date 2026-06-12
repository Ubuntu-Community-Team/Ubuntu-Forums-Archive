---
title: "Screen Resolution"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by dyde181 on 2006-10-22
Hi, i have been batteling with the screen resolution on my laptop on and off for years to no avail. I have read all the threads over this time but nothing has worked.

My laptop has a native resolution of 1024x768 but kde or gdm will only display at 800x600 or 640x480 (leaving a large black space around the screen) in my xorg config file it is set to 1024x768 (and it does run at that screen resolution when i turn off X)
it has done this with every realese and it is realy annoying (plus hard to use)

ubuntu runs fine on my desktop computers!

PS. this problem is the same with every linux distro (not just ubuntu) but it is fine when running under windows.

My laptop is and old (and slow) TOSHIBA Sadellite 4100XCDT

---

### Post by zek725 on 2006-10-22
yeah! how do you 'add' more resolutions? :confused: :-k

---

### Post by aznboi on 2006-10-22
i did this and it worked for me on my desktop:

```
sudo dpkg-reconfigure xserver-xorg
```

do that and it should autodetect some hardware for you and after a bit ask you the resolution modes u want available, after you finish it, press:

```
CTRL + ALT + BACKSPACE
``` to restart xorg

---

### Post by CatKiller on 2006-10-22
Have you set appropriate screen timings (refresh rates) in your xorg.conf?

---

### Post by zek725 on 2006-10-22
I don't know how to but I like the adapter default refresh rate of 60Hz.

---

### Post by CatKiller on 2006-10-22
> **zek725 said:**
> I don't know how to but I like the adapter default refresh rate of 60Hz.

If it's not set up for the appropriate horizontal sync rate, then you won't get the right resolutions available. Normally the graphics card gets this information from the monitor automatically and passes it to X. Sometimes that doesn't work, though, and you don't get all the resolutions the monitor can do available.

Look up the specifications of your monitor and then use those numbers to update your configuration. You can either use the command listed above, ```
sudo dpkg-reconfigure xserver-xorg
``` for an interactive configuration utility or you can use the commands ```
sudo cp /etc/X11/xorg.conf /etc/X11 xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``` to edit the file directly. Put the numbers you researched into the Monitor section like so: >         HorizSync       <some range of numbers>
        VertRefresh     <some other range of numbers>
There's plenty of information about it on this forum and in the man page.

---

### Post by zek725 on 2006-10-22
> **CatKiller said:**
> If it's not set up for the appropriate horizontal sync rate, then you won't get the right resolutions available. Normally the graphics card gets this information from the monitor automatically and passes it to X. Sometimes that doesn't work, though, and you don't get all the resolutions the monitor can do available.

Look up the specifications of your monitor and then use those numbers to update your configuration. You can either use the command listed above, ```
sudo dpkg-reconfigure xserver-xorg
``` for an interactive configuration utility or you can use the commands ```
sudo cp /etc/X11/xorg.conf /etc/X11 xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``` to edit the file directly. Put the numbers you researched into the Monitor section like so: There's plenty of information about it on this forum and in the man page.

Thanks! I've got it right. But how do you change the default resolution so that GDM uses that?

---

### Post by dyde181 on 2006-10-23
yes i beleive i have the right refresh rates but ill have to check i got sick of it not working so i switched to slackware! (noware as good) ill do a reinstall of 5.10 (too under-specd for 6.06)tonight and check back in the morning :)

---

### Post by dyde181 on 2006-10-24
ok well that diddnt go as planned!

my disk was scratched and everything installed except grub or lilo so i couldnt boot :(

will try again tonight with new disk

---

### Post by CatKiller on 2006-10-24
> **zek725 said:**
> Thanks! I've got it right. But how do you change the default resolution so that GDM uses that?

That's a different setting somewhere else, I believe. I don't know where, though. Sorry.

Glad you've got it working, though.

---

### Post by dyde181 on 2006-10-26
> **aznboi said:**
> i did this and it worked for me on my desktop:

```
sudo dpkg-reconfigure xserver-xorg
```

do that and it should autodetect some hardware for you and after a bit ask you the resolution modes u want available, after you finish it, press:

```
CTRL + ALT + BACKSPACE
``` to restart xorg

yes well..
i tried that and now my computer is running at 640X480 and just readable the screen is tiny :(

---

