---
title: "Fresh Mythbuntu 14.04.2 Install, Ceton PCIe 4 Tuner, Linux newbie, Stuck"
date: 2015-12-10
forum: Mythbuntu
---

### Post by 1bhfr1 on 2015-12-10
I have a working MythBuntu system running a HD Homerun Prime but want the ability to record more then 3 channels. I want to give my 12 year daughter the old old setup for Christmas and build myself a new one. My specs are as follows: Asus M5A97 plus motherboard, FX8350 Cpu, 16 gig DDR3 1866 ram, Antec 850 PSU, ScanDisk 120gig SSD for the current stable Mythbuntu 14.04.02, Samsung 2TB HDD for TV recordings and a GeForce GTX 960 GPU, HDMI hard wired to 4 HDTVs. All Hardware has been proven functional using win7 pro on a separate hdd. There are 3 webpages I'm trying to use to get the new system (Frontend/Backend combo) up and running, but they seem to have conflicting and/or out dated information causing failures. 

A. [https://www.mythtv.org/wiki/Ceton_InfiniTV_4](https://www.mythtv.org/wiki/Ceton_InfiniTV_4)

B. [http://www.bsmdevelopment.com/Reference/Sections/InstallNotes-MythTV_section-1.15.html](http://www.bsmdevelopment.com/Reference/Sections/InstallNotes-MythTV_section-1.15.html)

C. [http://chadarius.com/content/setup-dkms-ceton-infinitv-drivers-ubuntu](http://chadarius.com/content/setup-dkms-ceton-infinitv-drivers-ubuntu)

After downing the ISO and transferring to USB with rufus (under windows) the install woks great.Next I run the following commands, (I need gui's)
sudo apt-get install nautilus 
sudo apt-get install leafpad
sudo apt-get install Xarchiver
sudo apt-get install synaptic
sudo apt-get install DKMS

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

sudo /bin/sh -c "apt-get update && apt-get dist-upgrade && apt-get autoremove && apt-get autoclean"

(This leaves me with Kernel 3.16.55)

**[SIZE=3]Question #1:[/SIZE]** Would somebody please show me how to consolidate the above commands to the lowest number of clicks possible please?
[SIZE=3]**Question #2:**[/SIZE] Does the above satisfy all dependencies to compile drivers?
[SIZE=3]**Question #3:**[/SIZE] During update/upgrade I get a popup asking about Samba. The default choice below seems to be "Keep", show I select something else?

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Samba server and utilities &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474; A new version of configuration file /etc/samba/smb.conf is available, &#9474; 
&#9474; but the version installed currently has been locally modified. &#9474; 
&#9474; &#9474; 
&#9474; What do you want to do about modified configuration file smb.conf? &#9474; 
&#9474; &#9474; 
&#9474; install the package maintainer's version &#9474; 
&#9474; ***keep the local version currently installed*** &#9474; 
&#9474; show the differences between the versions &#9474; 
&#9474; show a side-by-side difference between the versions &#9474; 
&#9474; show a 3-way difference between available versions &#9474; 
&#9474; do a 3-way merge between available versions (experimental) &#9474; 
&#9474; start a new shell to examine the situation 

(Instead of compiling now, I open and follow instructions to set up auto DKMS) [http://chadarius.com/content/setup-dkms-ceton-infinitv-drivers-ubuntu](http://chadarius.com/content/setup-dkms-ceton-infinitv-drivers-ubuntu)

I run into problems compiling because "binaries are missing" I fix this by going to /usr/src/ctn91xx-2013_0326_2226. Inside that fold are 3 items, The tarball drivers fron ceton web site, the dkms.config file and a folder with the exracted drivers in it. I open the "drivers" folder and copy the continence then paste then outside the drivers so the they are in the "ctn91xx-2013_0326_2226" folder. 

I'm able to reboot without a problem but DMESG still doesn't show Ceton anywhere. I next edit the /etc/network/interfaces: file. I have tried the examples in both A and B above. Both leave me without internet working on the box. The frontend cant even connect to the backend on the same box.

**[SIZE=3]Question #4:[/SIZE]** Can somebody please show me what their working  /etc/network/interfaces: file looks like please?

I need to be able to cut and paste commands from chrome to terminal.[SIZE=3]
[/SIZE]

---

### Post by wpcprez on 2015-12-10
this doesn't answer your question but why 2 separate backends instead of one large backend+frontend and she just gets a frontend? (Unless this is a remote system)

Also, if you are trying to give easy instruction to configure, you can always turn on VNC for the install and have a port forwarded on a firewall to remote if it's not a local system.

---

### Post by 1bhfr1 on 2015-12-10
> **wpcprez said:**
> this doesn't answer your question but why 2 separate backends instead of one large backend+frontend and she just gets a frontend? (Unless this is a remote system)

Also, if you are trying to give easy instruction to configure, you can always turn on VNC for the install and have a port forwarded on a firewall to remote if it's not a local system.
1. Both computers have both front ends and backends. Right now my daughter doesn't have a desktop. The working system now will be her desktop, front end and back with parental controls to restrict what she can watch, in her room on her system.
 There are shows and movies on my system that I don't want her having access to.

2. I have port forwarding enabled on my router, my wife's family in the Philippines watch my recordings from a laptop hooked to a hdrv on win 8.1  and a windows mythtv frontend.

---

### Post by blm-ubunet on 2015-12-11
To cut & paste text in a terminal use <ctrl>+<shift>+<c> or <v>.

IMO this is a mistake.
> sudo apt-get install linux-headers-`uname -r`
The linux-headers-generic "meta" package would always give you the headers matching the installed kernel.

Did you actually test the DKMS build?
```
sudo dkms build -m ctn91xx -v 2013_0326_2226
```
You could post the terminal stdout warnings/errors..

---

### Post by deadflowr on 2015-12-11
[COLOR=#000000] > Would somebody please show me how to consolidate the above commands to the lowest number of clicks possible please?[/COLOR]
You can install all packages from within a single line, instead of individually.
So instead of:
```
sudo apt-get install nautilus 
sudo apt-get install leafpad
sudo apt-get install Xarchiver
sudo apt-get install synaptic
sudo apt-get install DKMS


sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
```
you can do:
```
sudo apt-get install nautilus leafpad Xarchiver synaptic DKMS build-essential linux-headers-`uname -r`
```
that'll cut down clicks a lot.

---

### Post by 1bhfr1 on 2015-12-12
> **blm-ubunet said:**
> To cut & paste text in a terminal use <ctrl>+<shift>+<c> or <v>.

IMO this is a mistake.

The linux-headers-generic "meta" package would always give you the headers matching the installed kernel.

Did you actually test the DKMS build?
```
sudo dkms build -m ctn91xx -v 2013_0326_2226
```
You could post the terminal stdout warnings/errors..

Everything seems to be working now. Everybody seemed to have luck with 14.04 and I did too!. After all updating/upgrading I had a working 14.04.3 system so I downloaded 14.04.3 and tried a different drive. That worked also! Not sure if it was me or the copy of 14.04.2 I stated with but one thing I know for sure is that trying to edit the [COLOR=#000000]/etc/network/interfaces: file caused nothing but problems and wasn't necessary to get a working system. DKMS  kept drivers working at all times going from 14.04 to 14.04.3 also. Thanks[/COLOR]

---

### Post by 1bhfr1 on 2015-12-13
> **deadflowr said:**
> [COLOR=#000000] 
You can install all packages from within a single line, instead of individually.
So instead of:
```
sudo apt-get install nautilus 
sudo apt-get install leafpad
sudo apt-get install Xarchiver
sudo apt-get install synaptic
sudo apt-get install DKMS


sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
```
you can do:
```
sudo apt-get install nautilus leafpad Xarchiver synaptic DKMS build-essential linux-headers-`uname -r`
```
that'll cut down clicks a lot.

WOW!!!! thanks so much.  Works like a charm.

---

