---
title: "ATI drivers installation"
date: 2005-11-07
forum: Multimedia &amp; Video
---

### Post by core on 2005-11-07
I was trying to install 3D ATI Driver following the instructions from the FAQ Guide:

```
echo fglrx | sudo tee -a /etc/modules
sudo depmod -a ; sudo modprobe fglrx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

```

but an error came up right on instruction no. 2:

```
sudo depmod -a ; sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.12-9-386/volatile/fglrx.ko): Operation not permitted
```

any idea of how can I make this to work? Thanks.

---

### Post by mlomker on 2005-11-07
The wiki is out-of-date.  [Try this.]("http://ubuntuforums.org/showthread.php?p=408111")

---

### Post by Vorian on 2005-11-07
OOPs, I should refresh my tabs before posting.....




Try this how to, it is a great step by step.

[HERE]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=sudo+dpkg-reconfigure+xserver-xorg")

---

