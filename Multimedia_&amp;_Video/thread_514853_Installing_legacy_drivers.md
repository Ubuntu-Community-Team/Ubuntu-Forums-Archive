---
title: "Installing legacy drivers"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by waqaskool on 2007-08-01
i want to install nvidia drivers, but only the ones on [www.nvidia.com](www.nvidia.com) not the ones in the restricted drives option & not with the automatix but the ones on [www.nvidia.com](www.nvidia.com)
i downloaded the the file ran it after killing the x server .........
like 'sh nvidia.....run' .
it installed ok !!!!
but when i restarted, my x server crashed like a wingless plane !!!!!


i cant find any actual guides to install legacy drivers in Ubuntu....!!
please help !!!

my experience with Linux is some where b/w a noob a rookie !!!

---

### Post by renzokuken on 2007-08-01
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

### Post by waqaskool on 2007-08-02
dude u just told me an other way how to install the drivers in the repositories !!!!
i already have them.        i need to install the ones available right now at [www.nvidia.com](www.nvidia.com)!!!

---

### Post by renzokuken on 2007-08-02
sorry dude, that guide use to explain how to do it from the official binaries, should have read it before i posted.

once they had been installed, did you use 

```
sudo nvidia-settings
```

to configure you're xorg.conf automatically. there is a guide round here i know but i cant find it.....i'll keep digging

EDIT: here it is [http://doc.gwos.org/index.php/Install_Nvidia_other_drivers](http://doc.gwos.org/index.php/Install_Nvidia_other_drivers)

---

### Post by RomeReactor on 2007-08-02
Hi. Just dropping by to note that **renzokuken**'s [first link]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html") **does** work for drivers downloaded from nVidia's website; just take a look at [Method 2]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2").

---

### Post by waqaskool on 2007-08-02
[http://doc.gwos.org/index.php/Instal..._other_drivers](http://doc.gwos.org/index.php/Instal..._other_drivers)

na man it ain't working ...!!!
it crashed ma x server niether is the first link and method 2 working !!!!
my xserver just crashes i followed it exactly !!!!

---

### Post by RomeReactor on 2007-08-02
Try this from the command line:
```
sudo dpkg-reconfigure xserver-xorg
```
when it asks you which driver to use, select **nvida**.

If it still won't work and you want to recover your display, run the command again and this time select **nv** as the driver to use.

---

### Post by renzokuken on 2007-08-02
> **waqaskool said:**
> [http://doc.gwos.org/index.php/Instal..._other_drivers](http://doc.gwos.org/index.php/Instal..._other_drivers)

na man it ain't working ...!!!
it crashed ma x server niether is the first link and method 2 working !!!!
my xserver just crashes i followed it exactly !!!!

are you absolutely sure you want the legacy driver and not the newer one? what card have you got?

---

