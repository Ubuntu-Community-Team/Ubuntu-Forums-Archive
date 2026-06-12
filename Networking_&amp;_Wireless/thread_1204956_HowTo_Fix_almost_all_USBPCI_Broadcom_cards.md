---
title: "HowTo: Fix almost all USB/PCI Broadcom cards"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Questioneer on 2009-07-05
Hello-
Perhaps your card doesn't work with 9.04 out of the box, or you are having some security issues or something.
However, if your broadcom card doesn't work, there is a VERY easy way that I have tested with many usb and pci broadcom devices to get the adapters up and working quickly.
These works especially well with linksys adapters.

You will need:
1. Your ubuntu install CD/flashdrive
2. Your wireless card's CD, OR access to internet on another computer.

Steps:
1. Get your wireless card's drivers. These can either be found on the CD, or online.
The drivers will be in a folder by themselves. There will probably be a ".inf" file(this is the "driver" file), and 2-3 system(.sys) files.

2. Copy all of these to a folder in your home folder.("/home/you/wdrivers", or something like that.)

****ONLY DO THIS PART IF YOU DON'T HAVE YOUR CD****
3. If you cannot get these files in a .zip online, and you don't have your card's CD, it is possible to get the drivers from the .exe driver.

So, go to your card's manufacturer, and download the exe driver they provide.
Download the program, 7zip, install it, and right click on the exe driver, and click extract with 7zip. In the extracted folder, you will find the "inf" and "sys" files.
****************************

4. Insert your ubuntu cd and run the following command:
```
sudo aptitude remove b43-fwcutter
```

5. Now, on your ubuntu CD, navigate to the folder "/pool/main/n/ndiswrapper/". Install the .DEB files called "ndiswrapper-utils" and "ndiswrapper-common" by double clicking.

Now, navigate to the folder: "/pool/main/n/ndisgtk/". Install the DEB file in this folder.

Now, go to System-Administration, and click on "Windows wireless drivers". In the program, click "select inf", and browse to select your inf file. Hit ok. It should say: "Driver Installed: Yes, and Hardware Present: Yes". Exit windows wireless drivers.

6. Now, run the following command:
```
sudo gedit /etc/init.d/wirelessfix.sh
```

In the empty file that pops up, type:

```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

```

7. Save the file, exit the text editor, and run the command:
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
```

8. Run:
```
sudo update-rc.d wirelessfix.sh defaults
```

9. Reboot, and you should have working wireless!

This is, in my own experience, the only satisfactory way to install broadcom cards in ubuntu. It works especially well with linksys cards.


Edit: Additionally, this has worked for me from 8.04 to 9.04.

---

