---
title: "Problem with graphics configuration after installing XBMC"
date: 2011-01-16
forum: Multimedia Software
---

### Post by harishkushwaha on 2011-01-16
Hi All,

I recently installed XBMC on ubuntu 10.10 thereafter I am unable to login in to my default ubuntu. While booting, ubuntu displays the popup message saying that my graphics configuration does not match my hardware. It give me option to reconfigure my graphics configuration but I don't know how to do that. I have uninstalled the XBMC using the command:

apt-get purge xbmc xbmc-standalone

But the proble, still persists. Please help!!!

My graphics card is "ATI Mobility Radeon HD 4500 Series".

Please help me in resolving this issue.

Thanks
Harish Kumar

---

### Post by tjones00 on 2011-01-16
Probably didn't install ati propretary drivers and xbmc stand alone tried setting up an ati/fglrx xorg.conf

Without going into why try this.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo aticonfig --initial
```

If you recieve an error that says the command aticonfig doesn't exist don't worry, then reboot.

```
sudo reboot
```

---

### Post by harishkushwaha on 2011-01-17
Thanks for the reply.

I tried your solution but the problem still persist. There is one more thing I want to add when I start X manually using "startx" it tries to start xbmc and not gdm.

Please help...I don't want to reinstall ubuntu again :(.

---

### Post by tjones00 on 2011-01-17
```
rm ~/.bash_profile ~/.bashrc ~/.xesssion

sudo reboot
```Hopefully that works or things are going to get more complicated.

Edit: you should also check this file.
```

sudo nano /etc/init/tty1.conf
```Make sure it looks like this:

```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 tty1
```If not edit it in nano Ctrl-O to save Ctrl-X to exit then:

```
sudo update-initramfs -u

sudo reboot
```

---

### Post by iraiam on 2011-08-07
I think this is an old post but it sounds like you installed the wrong kind of XBMC and it un-installed gdm (gnome) or kde.

Re-install gdm or kde and you will likely see an XBMC package that will be removed to install gdm. There is an XBMC package that is for dedicated xbmc, in which case XBMC is your GUI, and will remove a GDM when installed.

try this:
sudo apt-get update
sudo apt-get -d install --reinstall gdm
sudo apt-get remove --purge gdm
sudo apt-get install gdm
reboot

If you are using kde I can't help much I haven't used KDE in several years.

---

