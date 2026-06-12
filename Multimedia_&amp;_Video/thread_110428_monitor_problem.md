---
title: "monitor problem"
date: 2005-12-30
forum: Multimedia &amp; Video
---

### Post by Roger Hunter on 2005-12-30
Hi all;

My problem with the monitor is that ubuntu insists it is 640x480 ONLY.

As a result, everything is too big for my screen. Buttons are hidden, for example.

So what application do I need to fix it? I have a voodoo 3 card and a Phillips 107S monitor capable of very high resolution but ubuntu doesn't seem to know it.

Roger

---

### Post by jannol on 2005-12-30
my guess is that you need to install nvidia-glx-legacy

fastest method is to open up a terminal window and type

```
sudo apt-get install nvidia-glx-legacy
```
and follow the instructions

and if it asks you about modifing xorg.conf let it do so, if it does not, then type

```
sudo gedit /etc/X11/xorg.conf
```

find Section "Device"
and a few lines below you should have
```
Driver		 "nv"
```
or it might be
```
Driver		 "vesa"
```
for you

change it to look
```
Driver		 "nvidia"
```

reboot

then from the menu, find System > Preferences > Screen Resolution

and choose your resolution

---

