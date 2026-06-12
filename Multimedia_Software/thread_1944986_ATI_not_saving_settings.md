---
title: "ATI not saving settings"
date: 2012-03-22
forum: Multimedia Software
---

### Post by mastermindg on 2012-03-22
I recently installed 11.10 from scratch and after looking around on the thread decided to install the binary ATI drivers following these instructions:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I manually installed Catalyst 12.2 and all is well besides. I'm not having any issues with the video....except:

The settings aren't saving on login!?

My xorg.conf looks good and I'm using the admin catalyst tool. I'm not sure why it's getting reset on every session.

Thanks.

---

### Post by mastermindg on 2012-03-22
I tried the following and rebooted...same:


sudo aticonfig --initial -f
sudo aticonfig --set-pcs-str="DDX,EnableRandR12,FALSE"
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1

xorg is not changing on reboot but the display is not matching.

---

### Post by mastermindg on 2012-03-29
I ended up re-installing from scratch.

This worked for me:

   Install packages:

    sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases

    Since I'm on 64-bit, I had to add to that:

    sudo apt-get install ia32-libs

    Download the latest Catalyst package:

    cd ~/; mkdir catalyst11.11; cd catalyst11.11
    wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-11-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-11-x86.x86_64.run)

    Create the deb packages

    sh ./ati-driver-installer-11-11-x86.x86_64.run --buildpkg Ubuntu/oneiric

    Install the deb packages
    sudo apt-get remove fglrx
    sudo dpkg -i fglrx*.deb

    Create basic aticonfig xorg file

    sudo aticonfig --initial -f

    Set PCS:

    sudo aticonfig --set-pcs-str="DDX,EnableRandR12,FALSE"

    Restart

    Opened amdcccle with sudo and configured to dual screen (proceeded to get kicked out and log back in).

    sudo service lightdm restart

    At this point, go to the Displays option in ubuntu (dropdown from top-right screen) and uncheck mirror and set the desktop to span the two monitors.

---

