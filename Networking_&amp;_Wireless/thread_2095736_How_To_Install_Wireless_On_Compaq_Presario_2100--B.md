---
title: "How To Install Wireless On Compaq Presario 2100--Broadcom b4306 Rev 2, ndiswrapper"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by Ralph L on 2012-12-17
I spent an inordinate amount of time getting the b4306 rev 2 on my Compaq Presario 2100 to work.  There is a lot of mis-information out there about this chip, so I thought I would post how I got it to work.  First, the rev 2 seems to be different from the rev 3, so keep that in mind.  As far as I can tell the rev 2 will not work with b43 and b43legacy, so just use ndiswrapper.  At this point I have done the installation only on 10.04 Lucid Lynx, but I am going to install it on 12.04.1 Precise Pangolin.  I will update this post at that time.

This site tells how to get it working unencrypted:  [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) Post #1.  This site tells how to get it running encrypted [http://ubuntuforums.org/showthread.php?t=25683&page=59](http://ubuntuforums.org/showthread.php?t=25683&page=59)  Post #583.  I shortcutted things some by using Synaptic and found that some of the steps were unneeded.  The code shown below was what I executed in Terminal.  Note that I installed it in a clean lucid lynx system.  The b43 and b43legacy firmware was never installed.  Of course the b43 and b43legacy drivers were already installed as they are part of the standard live CD release of Ubuntu.

1.Using synaptic I installed build-essential.
2.I got the version number of linux to find which headers to install for the build.
```
uname -r
```
The response was &#8220;2.6.32-21-generic&#8221;
3.Using synaptic I installed the version of linux-headers-xxxxx-generic.  In my case linux-headers-2.6.32-21-generic.
4.I made a symbolic link to it in /lib
```
sudo ln -s /usr/src/linux-2.6.32-21-generic /lib/modules/2.6.32-21-generic/build
```
5.Downloading ndiswrapper.  I used version 1.56, but the newest one is version 1.58.  I think that one will work also. Set up a folder for the ndiswrapper download and do the download.  In my case I just created a folder in my HOME directory.
```
cd  ~
mkdir ndiswrapper-1.56 (or you can just us nautilus to create a folder.)
cd ndiswrapper-1.56
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.56.tar.gz
```
7.Uncompress it.  I just selected &#8220;ndiswrapper-1.56.tar.gz&#8221; inside the download folder and double clicked.  This brought up the extraction utility File Roller.  I selected &#8220;extract&#8221; and extracted it to the same &#8220;ndiswrapper-1.56&#8221; folder.  Now the extracted files were in a sub-folder of &#8220;ndiswrapper-1.56&#8221; also named &#8220;ndiswrapper-1.56&#8221;.
8.Install ndiswrapper.
```
cd ~/ndiswrapper-1.56/ndiswrapper-1.56
sudo make (I don't know if the &#8220;sudo&#8221; is really needed here)
sudo make install
```
9.Install ndiswrapper utilities.  I just used synaptic to install &#8220;ndiswrapper-utils-1.9&#8221;. This may have brought ndiswrapper-common with it as I notice that it has been loaded into my system.  I don't know whether or not it is needed.
10.Download the 4306 rev 2 firmware from [http://ftp.us.dell.com/network/R90501.EXE](http://ftp.us.dell.com/network/R90501.EXE) into a folder, in my case &#8220;Dell firmware download&#8221; in my Home directory.  Double clicking it brings up the File Roller extraction utility.  I just extracted it to &#8220;Dell firmware download&#8221;.  Included in the extracted files was bcmwl5a.inf, which is what we will install with ndiswrapper.  Note that the Dell files worked great on my Presario.  Note also to use bcmwl5a.inf, not bcmwl5.inf, or encryption will not work.  These files may also be on the Windows XP that came with the Presario.  I don't know.
11.Install the firmware with ndiswrapper&#8212;actually I think it is ndiswrapper-utils that is doing it.  I think this could also have been done using the GUI front end ndisgtk, but I did it this way.
```
cd ~/&#8221;Dell firmware download&#8221;
sudo ndiswrapper -i bcmwl5a.inf
```
12.Find if it was installed.
```
sudo ndiswrapper -l
```
This should give an output like
bcmwl5a : driver installed
device (14E4:4320) present (alternate driver: ssb)
13.Set system to load ndiswrapper automatically when wlan0 interface is used.  This sets /etc/modprobe.d/ndiswrapper to  contain only &#8220;alias wlan0 ndiswrapper&#8221; (no quotes).
```
sudo ndiswrapper -m
```
14.Set to have ndiswrapper loaded at startup.  Puts &#8220;ndiswrapper&#8221; in /etc/modules.
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```
15.Set up a script to make sure correct modules are loaded into the kernel and in correct order.
```
sudo gedit /etc/init.d/wirelessfix.sh
```
16.Paste into the file:
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
17.Save the file and set to have execute permission
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
```
18.Set so that the file gets executed.  This will get warnings about not following Linux Standard Base (LSB) rules, but don't worry.  Go ahead: it works.
```
sudo update-rc.d wirelessfix.sh defaults
```
19.I am not sure what this does, but it was on the web site I followed so I did it.  It may be just a status in which case the &#8220;sudo&#8221; isn't needed.
```
sudo iwconfig wlan0
```
20.Wait 30 seconds or so and check the Net Manager icon on the top panel to see if any wireless networks show.  Also, check that networks are enabled, and that wireless is enabled.  If you are running under lucid, the network/wireless enable is under the right-click menu.  If nothing shows, reboot the computer.  Note that I had to reboot mine twice before any wireless networks showed.  No idea of why.
21.Because bcmwl5a.inf was used in the installation you should have the capability to run unencrypted, wep,wp, or wp2.  Note that the instructions for installing an encryption capability that are in [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) didn't work, because the 4306 rev 2 needs bcmwl5a.inf.  Using bcmwl5a.inf causes several more firmware files (I guess they are firmware, but could be something else) needed for encryption to be loaded than bcmwl5.inf causes to be loaded.  These files appeared in /etc/ndiswrapper.
22.Right after I did the wireless installation I did a system update using Update Manager.  For some reason it wiped out ndiswrapper, but not ndiswrapper-utils.  When I did &#8220;ndiswrapper -l&#8221;, it showed everything was fine, but it wasn't .  Also, when I did &#8220;lsmod&#8221;, it showed ndiswrapper as being loaded into the kernel, but it didn't work.  Finally I reinstalled ndiswrapper using the &#8220;-i&#8221; option (as shown above), and ran /etc/init.d/wirelessfix.sh.  Then I had to re-enable wireless networks by clicking (or right-clicking) the network manager icon on the top panel.  I don't know what caused this wipe out to happen, but I am going to experiment some.  I guess I could do the re-install each time I do an update, but that is a nuisance. 
23.If you have problems send me a private message and I will try to help by updating this thread.  Hopefully I haven't left anything out.

---

### Post by Ralph L on 2013-01-12
I also did this installation on Ubuntu 12.04.1 Precise Pangolin.  However, I found a much easier way.  Skip the first 13 steps, which just install ndiswrapper from scratch, and use ndiswrapper (and its utilities) to install bcmwl5a firmware.  

1.  Instead go to synaptic and install ndisgtk, ndiswrapper.dkms,ndiswrapper-common, and ndiswrapper-utils-1.9.  Among other things this will install ndiswrapper on your computer, but you still need to configure it to use bcmwl5a firmware.
This will create Windows Wireless Drivers (ndisgtk) in your dash. 
2.  As described in my post above, download the Dell Firmware (or get the bcmwl5a firmware from someplace else) and use Windows Wireless Drivers to install it.  
3.  While Windows Wireless Drivers will create the file /etc/modprobe.d/nidiswapper, there is a bug that puts the wrong stuff in the file.  I just added "alias wlan0 ndiswrapper" (no quotes) to the file (using "sudo gedit /etc/modprobe.d/ndiswrapper"), but I think you can delete everything else if you want to.
4.  Follow Step 14 onward in the original post to create and instatiate the "wirelessfix.sh" file, and to get ndiswrapper to load on startup.
5.  You will probably have to reboot twice to get your wireless to work.  You may also have to "enable wireless" in the network manager icon on your task panel.

Note:  I tried to blacklist b43legacy in /etc/modprobe.d/blacklist, because I thought it wasn't needed and it might speed the boot process. However, it disabled wireless.  So unless you are smarter than me about ubuntu (and most people are), don't blacklist b43legacy, even though wirelessfix.sh removes it later.

---

### Post by Ralph L on 2013-03-18
Mistake in the above:
Where I say to add "alias wlan0 ndiswrapper", it should be to file /etc/modprobe.d/ndiswrapper.conf.

Also, I said that blacklisting b43legacy caused problems.  However, when installing ndiswrapper in Xubuntu 12.04.2, I added "blacklist b43legacy" to the end of /etc/modprobe.d/blacklist.conf and my wireless worked better than before.  Also it didn't get any errors in the dmesg output that I ran immediately after startup.  Without blacklisting b43legacy I got some errors.

---

