---
title: "Streaming video over wireless?"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by brigzzy on 2008-12-21
Hey all,

I hope I'm posting this in the right forum.  I'm having trouble with my wireless when it comes to streaming video from my desktop (desktop running Ubuntu 8.10, laptop running 8.04.1).  I'll navigate to the network share, and load the video, which will play from anywhere from a few minutes to a few seconds, and then simply stop.  The audio and video will both freeze.  I can quit the application normally, and re-load it, with the same results.  

I'm streaming to an acer aspire one, using the madwifi drivers.  This is the method I used to set them up.

```
madwifi

Now we need to disable the hardware drivers that Ubuntu tries to use before the ones we make will function. So go to System -> Administration -> Hardware Drivers and uncheck everything. It should prompt us to reboot, so lets do it now.

We need to grab the wireless driver, and the things we need to build it, from a terminal:

mkdir source
cd source
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar -xzvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo apt-get install build-essential linux-headers-$(uname -r)

And we build and install:

make
sudo make install
sudo modprobe ath_pci

In order to have the wireless work after reboot, add the following line to /etc/modules ("sudo gedit /etc/modules") to automatically load the module when booting:

ath_pci

You should now have working wireless. However you may want to do the following to prevent problems (the symbol mismatch) when the module is loaded:

Add ath_hal to the DISABLED_MODULES= stanza in /etc/default/linux-restricted-modules-common

(i.e. 'DISABLED_MODULES="ath_hal"')

Every time there is a kernel update you will need to perform the following steps to make the wireless work. Go to the directory (madwifi-hal-0.10.5.6-r3835-20080801) and run:

make clean
make
sudo make install
```

Does anyone have any ideas what may be causing my problem?  I've tried everything I can think of (but that's not saying much, I'm kind of a Linux newbie...)

---

