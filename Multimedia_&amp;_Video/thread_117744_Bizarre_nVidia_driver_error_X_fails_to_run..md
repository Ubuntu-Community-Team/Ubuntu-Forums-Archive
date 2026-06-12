---
title: "Bizarre nVidia driver error: X fails to run."
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by ghansel on 2006-01-15
For the past few days I've been attempting to install/ play Wolfenstein Enemy Territory, with varying degrees of success. I successfully got it installed, only to learn that it would be necessary to install the nVidia driver nvidia-glx and its accompaniment, nvidia-settings (presumably for OpenGL hardware acceleration) for my GeForce4. This I did. To enable nvidia-glx, it is necessary to run the command:

```
sudo nvidia-glx-config enable
```

That's easy enough. However, when I do that, I get the message that the X server must be restarted for the settings to take effect. So, ctrl-alt-backspace and we have what should be a successful X restart - except X fails to start. Terminal opens, I type ```
 sudo su 
``` and my password, and then run

```
apt-get remove xserver-xorg; apt-get install xserver-xorg x-window-system-core ubuntu-desktop 
```

I shutdown, reboot, and X is back to normal. However, I'm back at square one, because Enemy Territory isn't working. I then tried the tutorial at the top of this forum - and that gives me the identical result.


Any ideas?


George

---

### Post by SolidAndShade on 2006-01-15
Are you sure you need to install nvidia-settings as a package? I've run Enemy Territory with just the downloaded nvidia driver installed, and none of the nvidia packages in the Ubuntu repositories. On my system, installing the driver from the nvidia website also installed the nvidia settings program. After installing the driver, look at Applications > System Tools and see if there's an nvidia X server settings program there. ET never complained about a lack of nvidia packages to me, so if it does on your system you may want to post whatever message it gives you.

---

### Post by ghansel on 2006-01-15
Fixed it... though to be honest I have no idea how.

---

