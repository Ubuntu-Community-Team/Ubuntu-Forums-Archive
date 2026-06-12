---
title: "How To MSI DIGI VOX II v.3 USB TV tuner"
date: 2009-09-21
forum: Multimedia Software
---

### Post by ayenack on 2009-09-21
Hello all.

Has anyone got an MSI DIGI VOX II v.3 USB TV tuner working on Ubuntu 8.04.1 or does anyone know of a tutorial on how to get it working.

Thanks for any help.

---

### Post by babarosa on 2009-09-21
Hello ayenack,

in a terminal:

sudo apt-get install mercurial linux-headers-$(uname -r) build-essential subversion gcc make 

wget [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw) 

sudo cp dvb-usb-af9015.fw  /lib/firmware/ 

hg clone [http://linuxtv.org/hg/~anttip/af9015](http://linuxtv.org/hg/~anttip/af9015) 

cd af9015 

make 

sudo make install 

echo dvb-usb-af9015  | sudo tee -a /etc/modules 

sudo reboot 

remove the stick and push it in again ...



Now get me-tv from [www.getdeb.net](www.getdeb.net) (v0.5.3).
After installation (dvb-utils will be installed too) a scan starts automatically.

Manual scan:

wget [http://wirbel.htpc-forum.de/w_scan/w_scan-20081106.tar.bz2](http://wirbel.htpc-forum.de/w_scan/w_scan-20081106.tar.bz2) 

tar -xjvf w_scan-20081106.tar.bz2 

sudo mv w_scan-20081106 /opt/w_scan 

sudo ln -s /opt/w_scan/w_scan /usr/local/bin/w_scan 
 
w_scan -X >~/.me-tv/channels.conf

Hope that helps, there was a change in the stick's chip recently.
Michael

---

### Post by ayenack on 2009-09-22
Hello babarosa. Thanks for the help.

Getting a 404 error on the

wget [http://www.otit.fi/~crope/v4l-dvb/af...-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af...-usb-af9015.fw)

So the file has either been removed or put somewhere else.

Managed to get the firmware from.

sudo wget [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/)

Which I think is compatible with the stick but after install there's no /dev/dvb. Bit stuck on this one any ideas?

The card is listed under lsusb as:-

Bus 005 Device 006: ID 15a4:9015

So it's there just not working for some reason.

---

### Post by babarosa on 2009-09-22
Hi!

I am not happy to hear that so I tested the reported link just now. It works well for me as does the installation.

Please try once more downloading the firmware from that link (although your link is exactly the same place, isn't it?).

Do not enter **sudo** wget ... but wget ...

I read in a german speaking forum that recently the stick's chip was changed and people could not get it to work properly :-(

Greetings,
Michael

---

### Post by ayenack on 2009-09-22
Ok I've finally got it working. Not entirely sure how I did it (had a few hurdles to overcome). But know that putting the firmware dvb-usb-af9015.fw in /lib/firmware as you said made it work.

Ok I got the firmware from the site you listed. Was entering it wrong.

babarosa I could not have done it with out you. Thank you.

ayenack.

---

