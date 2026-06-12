---
title: "Wits' End with ATI Drivers"
date: 2009-01-01
forum: Multimedia Software
---

### Post by zzantozz on 2009-01-01
At one time, I had the proprietary drivers for my ATI Radeon X1900 installed (through Ubunutu's own installer) and working great. Then I updated and couldn't get to my desktop because of what turned out to be video driver issues. I ended up downloading the driver directly from ATI and reinstalling it manually from the command line. Again, everything was great. Then I made the mistake of updating again. Now my fglrx driver has disappeared again, and I'm stuck on the mesa driver, which I thought I uninstalled. My resolution won't go higher than 800x600, and compiz doesn't work. I'm tired of jacking around with these things! Why does it seem so fragile? Am I doing something wrong? Is it too much to ask for the latest video driver to work consistently? More importantly, where do I go from here? Do I go back and re-reinstall the driver that I downloaded? How would I go about reenabling Ubuntu's proprietary drivers, since they seemed to work well until they caused my desktop to be inaccessible?

---

### Post by Melcar on 2009-01-01
Did you update the kernel?  You probably did and that is why the drivers don't work anymore.  I would first uninstall the old driver; if you used the Ubuntu "restricted drivers" thing or generated packages with ATI's installer then search Synaptic for "fglrx" and uninstall it (it should be 3 packages); if you installed it straight from the install script then you need to launch the uninstaller script:

```
cd /usr/share/ati
sudo sh fglrx-uninstall.sh

```


Immediately after uninstalling I would rebuild X just to be safe:

```
sudo dpkg-reconfigure xserver-xorg
```

Reboot, or simply restart X, and then proceed to install the driver.

- Download the latest [driver]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html") and copy it somewhere you will remember

- Open a terminal and move to wherever you copied the driver to:
```

cd <location of driver>
```

- Run the installer:

```
sudo sh ati*.run
```

- Follow the automatic method and wait for the installer to finish

- Once you are dropped back to the terminal (make sure it did not throw out any errors) initialize the driver:

```
sudo aticonfig --initial

```
- Reboot

---

