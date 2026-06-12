---
title: "undoing nvidia symbolic linking (attempted fix gone wrong!)"
date: 2008-05-30
forum: Multimedia Software
---

### Post by mooglinux on 2008-05-30
it all started [Here]("http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white")i was having trouble with my dvd playback because the color was all off. so i came accross [This fix]("http://ubuntuforums.org/showthread.php?t=772408") but that completly rendered x unusable, so i have uninstalled and reinstalled the nvidia drivers several times after learning that many people were able to fix this problem by installing the driver direct from the nvidia website. so i did that and now i have the same probelm: x will not start. 

so i figure its the symbolic link the first fix had me do, and i want to undo it. ```
Instructions :

- Open a terminal window.

- Type: sudo rm /usr/lib/xorg/modules/libwfb.so

- Then type: sudo ln -s /usr/lib/nvidia/libwfb.so.xserver-xorg-core /usr/lib/xorg/modules/libwfb.so

- Restart X (either reboot or "Alt-Ctrl-Backspace")

```so how would i go about changing it back to the nvidia libwfb.so file?

---

### Post by ajmorris on 2008-05-31
hi there,
Remove the symbolic link you created, then re-install the nvidia drivers again, this will put it back to the default setting.

Also, if you just switch to the drivers from the nvidia site, you have to black list the open source ones first, you might like to see this how to on setting up the nvidia drivers:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
It is aimed at 7.10, but 8.04 uses the same principles. If some package names do not exist that you try to install, just post here, and we can figure out what they are called in hardy.

AJ

---

