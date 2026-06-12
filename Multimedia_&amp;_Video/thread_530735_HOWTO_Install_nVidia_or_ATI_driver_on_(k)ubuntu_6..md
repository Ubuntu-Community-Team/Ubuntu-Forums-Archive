---
title: "HOWTO Install nVidia or ATI driver on (k)ubuntu 6.06 or +, if official method fails"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by Hyssar on 2007-08-20
**[SIZE="3"]HOWTO Install nVidia or ATI driver on Ubuntu (or Kubuntu) dapper, edgy or feisty, if the official method fails[/SIZE]**

This method will install the non-free official latest nVidia or ATI drivers on your system easily.
Read everything carefully before doing anything

I wrote this due to the number of posts about drivers, I hope it could be a 'sticky' post
First of all, french version : [http://doc.ubuntu-fr.org/envy](http://doc.ubuntu-fr.org/envy)

This is an unofficial method, so make a backup (don't worry, it works good!)
You got to have both the universe and multiverse repositories activated (default : activated)

**First**, you need the .deb package for the current stable version of Envy (20/08/08 : 0.9.7)
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)

or

Open a Terminal and type
```
sudo wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
```
Don't double-click on it!

**Second**, run the package

In Terminal, of course
```
sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
```

It will show many error messages, don't worry, it's normal

**Third**, install the dependencies

```
sudo apt-get install -f
```

It takes some time

**Fourth**, reboot (yes, it rarely useful on Linux, but here you got to do it)

By the menu,

or

```
sudo reboot
```

**Fifth**, open Envy

System menu -> Envy

or

```
sudo envy -g
```
The -g option means 'graphic' or you can use '-t' if you prefer text method
However, I wrote this tutorial for graphical mode.

**Sixth**, install the driver.

Choose either 'Install nVidia driver' or 'Install ATI driver' (you got to know the brand of your video card)

Envy will do EVERYTHING for you, it is a bit long but it works.
It automatically detects your card's GPU and your system (32 or 64-bit) and downloads the right driver.
You got to be connected to the Internet because Envy will download the driver before installing it.

**Seventh**, it asks you if you wish to automatically reconfigure xorg.conf, accept
Then, if you wish to reboot, accept

**Finally**, read this :

- If everything worked, you will be able to run 3D things normally and the nVidia (if you got nVidia)
    logo will appear at boot
-To update the driver version, unistall the driver (with Envy) before installing it again (with Envy)
-Before unistalling Envy, unistall any driver installed with it
-Before a major upgrade (ex :edgy to feisty), _**unistall any drivers installed with Envy**_
-If you want to use Beryl (desktop animation), your terminal may send you this error :
    "No composite extension", just edit xorg.conf and modify the 'Composite' line, change Disable by
    Enable. save, then restart Xorg (or simply reboot)
-Envy doesn't remove the 'restricted' modules of Ubuntu (or Kubuntu), wich is a good thing.

useful links :
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
[http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

Please tell me if it helped you!

Thanks,
Hyssar

---

