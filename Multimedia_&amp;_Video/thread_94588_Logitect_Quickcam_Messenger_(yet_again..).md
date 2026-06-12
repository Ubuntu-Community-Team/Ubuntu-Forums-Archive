---
title: "Logitect Quickcam Messenger (yet again..)"
date: 2005-11-24
forum: Multimedia &amp; Video
---

### Post by Sanderfox on 2005-11-24
Hi !

A few months ago, I installed the qc-usb-messenger driver for my Logitech Quickcam Messenger and it worked all fine, but I've been trying to get the same driver working under Ubuntu for several weeks now, but it doesn't work the way it should.

I followed all the steps I could find in the topics available here and I succeeded to get it working with running ./quickcam.sh. But! after each reboot, I need to run the install script again to get it working. If I don't, I get the msg 'Could not connect to video device (/dev/video0)' with camorama or sort of the same msg with xawtv.

Does anyone have an idea on how to get it working without having to run the install script everytime ? I've tried everything afaik...

Just ask if you need more info :)

Thanks,

Sanderfox

---

### Post by ranf on 2005-11-24
[QUOTE=Sanderfox]
A few months ago, I installed the qc-usb-messenger driver for my Logitech Quickcam Messenger and it worked all fine, but I've been trying to get the same driver working under Ubuntu for several weeks now, but it doesn't work the way it should.

I followed all the steps I could find in the topics available here and I succeeded to get it working with running ./quickcam.sh. But! after each reboot, I need to run the install script again to get it working. If I don't, I get the msg 'Could not connect to video device (/dev/video0)' with camorama or sort of the same msg with xawtv.
[/QUOTE]
Just show us your quickcam.sh.

---

### Post by Sanderfox on 2005-11-24
See attachment for my quickcam.sh.

---

### Post by ranf on 2005-11-24
[QUOTE=Sanderfox]See attachment for my quickcam.sh.[/QUOTE]
At the very end it says something like this:
```
echo "Hopefully the driver is now installed and can be loaded"
echo "with command"
echo "	modprobe quickcam"
echo "as root. You can put this command into some startup"
echo "script to do it always automatically at boot."
echo "The exact location depends on distribution, and this"
echo "script is yet too dumb to do this automatically."

```

So does it work if you just run:
```
sudo modprobe quickcam
```

---

### Post by Sanderfox on 2005-11-24
Nope, it works only after I did the install script (without doing modprobe), but as soon as I do 'modprobe quickcam', it's over.

---

