---
title: "Installing a Philips 300NC webcam in Ubuntu Breezy"
date: 2006-04-29
forum: Multimedia &amp; Video
---

### Post by cypresstwist on 2006-04-29
First things first - download the latest spca5xx drivers from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html).
wget [http://mxhaard.free.fr/spca50x/Download/sp...20060202.tar.gz](http://mxhaard.free.fr/spca50x/Download/sp...20060202.tar.gz)
Download the headers matching your kernel, GCC 3.4 and the buid tools using apt-get
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4
Make a link to the headers in /usr/src:
ln -s /usr/src/linux-headers-2.6.12-9-386 /usr/src/linux
Untar the drivers you just downloaded and compile them using GCC 3.4 (NOT the default 4.0 that comes with Breezy)
tar xvfz spca5xx-20060202.tar.gz
cd spca5xx-20060202
sudo make CC=gcc-3.4
sudo modprobe -r spca5xx
Then do a
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
Install Video4Linux if you haven't done so already
sudo apt-get install libpt-plugins-v4l
Edit /etc/X11/xorg.conf and add the following to 'Section "Module'
Load "v4l"
Now let's make an init script that loads the webcam:
sudo touch /etc/init.d/webcam
sudo chmod +x /etc/init.d/webcam
sudo nano /etc/init.d/webcam
and add the following two lines:

!#/bin/sh
for i in 0 1 ;do if [ ! -f /dev/video$i ]; then echo "Creating /dev/video$i" && mknod /dev/video$i c 81 $i && chown :adm /dev/video$i && chmod 660 /dev/video$i; else echo "/dev/video$i already exists";fi;done

Save the file, do a

sudo update-rc.d webcam defaults

Reboot and there you have it. Plug in your Philips 300NC webcam and check if Ubuntu "sees" it:

cypress@malacka:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0471:0326 Philips
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

Launch xawtv or gnomemeeting and enjoy

---

### Post by Anae on 2006-05-15
First: I am sorry for my bad english. 

I use Breezy Badger with Gnome and  i tried this HowTo for the Philips 300 NC.

This is my lusb:

anae@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0471:0326 Philips
Bus 001 Device 001: ID 0000:0000

Edit: 

This is my xawtv output, sometimes this output comes, sometimes it is frozen

anaee@ubuntu:~$ xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.12-10-386)
can't open /dev/video0: No such device
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Kein passendes Gerät gefunden
v4l2: open /dev/video0: Kein passendes Gerät gefunden
v4l: open /dev/video0: Kein passendes Gerät gefunden
no video grabber device available


All programs (gnomemeeting, xawtv, camorama, camstream) don't go.
If i open them, the whole system is frozen and i must restart over the On/Out Button.

Can you help me perhaps?

And again, sorry for my bad english :-(

Greetings
Anae

---

