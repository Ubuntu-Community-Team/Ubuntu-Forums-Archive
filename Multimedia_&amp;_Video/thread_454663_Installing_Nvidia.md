---
title: "Installing Nvidia"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by phoenix23 on 2007-05-25
I tried to install my new Nvidia Geforce FX 5200 with the Restricted Driver Manager. I put the card in the box, ran Ubuntu and downloaded the driver (with my old card), then restarted the computer.

Upon restart, the system "failed to x server graphic interface". Here are the reports:

[[IMG]http://img525.imageshack.us/img525/9753/img2264it2.th.jpg[/IMG]](http://img525.imageshack.us/my.php?image=img2264it2.jpg) [[IMG]http://img182.imageshack.us/img182/9875/img2266eb6.th.jpg[/IMG]](http://img182.imageshack.us/my.php?image=img2266eb6.jpg)

I'm following along with the sticky

[http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1)

But I can't figure out how to > sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

In the text thing. It won't open a text editor to let me change the settings.

How do you do it in the command linething?

---

### Post by ethos101 on 2007-05-25
Text mode:

```
sudo nano /usr/share/applications/NVIDIA-Settings.desktop
```

I wish I could help more, I'm new too.  Hopefully karma will help with my own problems.  :D

---

### Post by phoenix23 on 2007-05-25
> **ethos101 said:**
> Text mode:

```
sudo nano /usr/share/applications/NVIDIA-Settings.desktop
```

I wish I could help more, I'm new too.  Hopefully karma will help with my own problems.  :D

Thanks Ethos

I used nano to finish the method, and it's still not working.

I can't get to my GUI.

---

