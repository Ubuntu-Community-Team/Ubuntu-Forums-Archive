---
title: "Uninstalling Hauppage 1600-beta driver"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by Phantom87 on 2008-04-10
so Yeaa, its my 3rd time trying the beta driver out and i didnt get it to work and i dont want to go thru the whole deleting the partition and re-installing ubuntu again.

So was anyone able to uninstall the drivers properly? because now my video card Nvidia 8600GTS cannot be detected eventhough it says its active. and i keep getting this big X on my screen before i login after a restart.

I know  it can be uninstalled properly, i just dont know how to because i tried the instructions on linuxtv and nuthin worked.

---

### Post by warp99 on 2008-04-10
What instructions did you use? Please post a link if possible.

---

### Post by Phantom87 on 2008-04-10
> **warp99 said:**
> What instructions did you use? Please post a link if possible.

[http://linuxtv.org/repo/](http://linuxtv.org/repo/)

The instructions on that page, under where it says how to build the v4l-dvb kernel modules.

It says sumthin about removing the builds and modules and i tried that but it didnt work.

---

### Post by warp99 on 2008-04-10
Well what you did is try to make and install some new modules, so the best thing to do is re-install the standard kernel modules. So do the following:

```
sudo apt-get install --reinstall xserver-xorg-video-v4l linux-image-$(uname -r)
```

this should overwrite the modules. Then issue the following:

```
sudo apt-get install --reinstall nvidia-glx nvidia-glx-new linux-restricted-modules
```

and finally:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and choose 'nvidia' as your driver. Then issue a 'sudo reboot' to load the correct modules again. Hope this helps.

---

### Post by Phantom87 on 2008-04-10
> **warp99 said:**
> Well what you did is try to make and install some new modules, so the best thing to do is re-install the standard kernel modules. So do the following:

```
sudo apt-get install --reinstall xserver-xorg-video-v4l linux-image-$(uname -r)
```

this should overwrite the modules. Then issue the following:

```
sudo apt-get install --reinstall nvidia-glx nvidia-glx-new linux-restricted-modules
```

and finally:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and choose 'nvidia' as your driver. Then issue a 'sudo reboot' to load the correct modules again. Hope this helps.

Ah!, well it kinda worked because after re-installing the standard kernel modules, it worked fine. But when i try to enable my video card, its changed back to the 800x600 resolution.

I think i need to just uninstall completely the nvidia driver and re-install it again.

---

### Post by warp99 on 2008-04-10
> **Phantom87 said:**
> .I think i need to just uninstall completely the nvidia driver and re-install it again.

No you don't need to reinstall the drivers. Just do the following:

```
sudo dpkg-reconfigure xserver-xorg
```

This will build you a new xorg.conf with the correct resolutions for your monitor, just make sure that any resolutions **ABOVE** the resolution you want to use is removed from the list presented when you get to the monitor section.

Edit:

You already re-installed the drivers if you did all of the steps in my previous post.

---

### Post by Phantom87 on 2008-04-10
> **warp99 said:**
> No you don't need to reinstall the drivers. Just do the following:

```
sudo dpkg-reconfigure xserver-xorg
```

This will build you a new xorg.conf with the correct resolutions for your monitor, just make sure that any resolutions **ABOVE** the resolution you want to use is removed from the list presented when you get to the monitor section.

Edit:

You already re-installed the drivers if you did all of the steps in my previous post.

yeaa, i did follow the other steps and the new line  u just gave me and still now luck.

When i go to restricted driver and, it says that the nivdia card is not in use but i'm able to go to 1440 x 900 resolution and my compiz settings are still intact not just active because the video card is not active as well. And when i try to make the video card active and i restart, it goes back to the 800 x 600 res.

---

### Post by warp99 on 2008-04-10
> **Phantom87 said:**
> yeaa, i did follow the other steps and the new line  u just gave me and still now luck.

When i go to restricted driver and, it says that the nivdia card is not in use but i'm able to go to 1440 x 900 resolution and my compiz settings are still intact not just active because the video card is not active as well. And when i try to make the video card active and i restart, it goes back to the 800 x 600 res.

No the nvidia drivers are active when your did the 'sudo dpkg-reconfigure xserver-xorg' it just bypasses the restricted driver manager. The manager says they are not active, but they are.

When you make the drivers active in the restricted manager it just resets it to the default, so you then have to run the following to change the resolution:

```
sudo nvidia-settings
```

So it's basically the same thing. The drivers are active with either method, but with the restricted manager and nvidia you need to take some extra steps.

Edit:

When using the nvidia-settings application you can change the settings in the "X Server Display Configuration" and then click the "Save to X Configuration" button and save the file as /etc/X11/xorg.conf.

---

