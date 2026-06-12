---
title: "nvidia-glx-legacy installed instead of nvidia-glx"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by pretentioushobo on 2007-09-20
Hi, I'm running the 64 bit version of Feisty (Xubuntu), and I used the Restricted Drivers Manager to install the drivers for my video card (nVidia GeForce 6800 GT PCIe 256MB).  The graphics are fine, but my problem is that the driver it lists is "NVIDIA accelerated graphics driver (legacy cards)".  I confirmed in Synaptic that nvidia-glx-legacy is installed and not nvidia-glx.  Unless I'm mistaken, nvidia-glx should be the one there, plus I think I need it for Compiz.
        My question is, what is the *correct* way of fixing this?  Should I go into Synaptic, mark nvidia-glx-legacy for uninstallation and mark nvidia-glx for installation and apply, and then run "sudo nvidia-glx-config enable"?  That's what I can tell from online sources and the message board, so I guess I'm just asking for explicit confirmation; I just don't really know what the Restricted Drivers Manager does behind the scenes.

---

### Post by pretentioushobo on 2007-09-21
Can anyone help me out here?  Will it cause any problems if I try this, or is there a better way?

---

### Post by RomeReactor on 2007-09-21
Hi. While I can't assure you that the change won't cause problems, I've had a somewhat similar situation where, upon enabling Desktop Effects, the driver that gets installed is **nvidia-glx** for my 6200, an I often change it through Synaptic to the **nvidia-glx-new** without any issues. So you *could* probably change the legacy driver for nvidia-glx in Synaptic without expecting any breakage.

It would be a good idea, however, to backup your current xorg before the change, just in case:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
That way, if nvidia-glx causes you trouble, you could reinstall the legacy driver and restore the xorg file:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by Poet with a Gun on 2007-09-21
I installed my 6100 drivers with a program called Envy. It gets you the right driver automagically and downloads it from nvidia and installs it.

It'll even remove the old one you have installed. It is in your synaptic manager it's been a while so I don't recall if I had to add it to my repositories, or what, but if it's not there by default a trip to google will turn it up.

Good luck.

---

