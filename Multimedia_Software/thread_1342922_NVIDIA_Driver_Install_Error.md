---
title: "NVIDIA Driver Install Error"
date: 2009-12-01
forum: Multimedia Software
---

### Post by Non.Cents on 2009-12-01
To start I will tell you that I am still pretty much a newbie on Ubuntu.

I just installed 9.10 64 bit on my Laptop. I did all of the necessary updates once it was installed. When I went to get the proprietary NVIDIA driver through the Hardware Drivers utility, the first time it blacked out my screen and I could not get any response back from the computer. I did a hard shutdown, now when I try to install the driver i get an error every time

SystemError: installArchives() failed

I am not sure where to go from here.

---

### Post by efflandt on 2009-12-02
I had that problem too trying to enable nVidia driver in Qimo for kids (based on Xubuntu 8.10).  When I booted after enabling the driver, total blackness.  If you are not sure of the package name from console or xterm do **sudo less /var/log/apt/term.log** and scroll down to the bottom (PgDn or down cursor key) and check the name of last related package.

In my case it was dkms so I did **sudo apt-get purge dkms**.  Then I was able to reboot and get into X.  That package had some files related to the original, instead of updated linux kernel, maybe because I enabled that after doing updates before rebooting.

I upgraded that laptop to 9.04 and it is now using default nvidiafb, rivafb modules.

---

