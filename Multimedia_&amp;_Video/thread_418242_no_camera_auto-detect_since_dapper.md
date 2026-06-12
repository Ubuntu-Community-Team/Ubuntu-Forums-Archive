---
title: "no camera auto-detect since dapper"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by HarmonicaGoldfish on 2007-04-22
I posted this in absolute beginner talk yesterday and have not received any answers, so I am reposting here since it is a multimedia issue and maybe I'll get some help :)

I had this problem with Edgy, and was hoping it would be resolved with an upgrade to Feisty, but it isn't...so here I am again.

I can import photos if I open up gthumbs and do a manual import, but my computer does not open the auto-import window when I plug the camera in, like it used to do with Dapper.

In System/Preferences/Removable Drives and Media/Camera - the import digital photos from camera option is ticked and the command is

gnome-volume-manager-gthumb %h

A friend of mine has suggested that I do a fresh install. That perhaps the code somehow got messed up during the original upgrade from dapper to edgy.

Any thoughts??

thanks!!

ps - I have tried to reinstall ubuntu-desktop, no changes.

---

### Post by aloshbennett on 2007-04-23
No luck at my end too. I did a fresh installation of Feisty. Auto detection used to work in dapper.
The camera is detected as a usb device but the importer is not launched.


[I]alosh@zion:~$ lsusb
**Bus 005 Device 010: ID 04a9:30f0 Canon, Inc. **
Bus 005 Device 003: ID 0ac8:c002 Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 0000:0000  [/I]


The import works if I launch gnome-volume-manager-thumb. I also tried hooking up my skip instead of it in System/Preferences/Removable Drives and Media/Camera, but that doesnt get called either :-(.

---

### Post by NickeM on 2007-04-24
I have the same problem. I can start gnome-volume-manager-gthumb and manually import photos from my canon powershot s410 but there is no automatic launch :-p Does anyone know how to debug or solve this?

---

### Post by NickeM on 2007-04-24
I found a solution by using ivman which is a daemon to auto-mount and manage media devices :)

```
sudo apt-get install ivman
```

and disabling the ivman system service, to be able to launch gnome-volume-manager-gthumb as a regular user
by using:

```
sudo sysv-rc-conf
```
and unchecking all runlevels for ivman.
	
lauch ivman in the terminal and it will create template config files in ~/.ivman

use the command:
```
lshal >hal.txt
```

and search for your equipment in the text file, after that i created a rule:

```
<ivm:Match name="hal.info.product" value="Canon Digital Camera">
        <ivm:Option name="exec" value="gnome-volume-manager-gthumb" />
</ivm:Match>
```

which i added to .ivman/IvmConfigActions.xml
start ivman by typing ivman & in the terminal, and for permanent use add it to System/Preferences/Sessions
	
Now you should be able to enjoy a auto-launched gnome-volume-manager-gthumb!

For more examples follow this link:
[Click here]("http://gentoo-wiki.com/HOWTO_ivman#A_Few_Example_Rules")

---

### Post by HarmonicaGoldfish on 2007-04-24
ok - I tried your fix, but didn't get past the 2nd step...

harmonicagoldfish@harmonicagoldfish:~$ sudo apt-get install ivman
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkexif1 libexif-dev libgphoto2-2-dev libusb-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ivman
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.1kB of archives.
After unpacking, 279kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe ivman 0.6.12-5ubuntu1 [59.1kB]
Fetched 59.1kB in 1s (36.4kB/s)
Selecting previously deselected package ivman.
(Reading database ... 147492 files and directories currently installed.)
Unpacking ivman (from .../ivman_0.6.12-5ubuntu1_i386.deb) ...
Setting up ivman (0.6.12-5ubuntu1) ...
Creating a user 'ivman'...
adduser: Warning: that home directory does not belong to the user you are currently creating.
Starting ivman: manager.c:1362 (do_startup_configure) Directory /etc/ivman/ will be used for configuration files.
ivman.

harmonicagoldfish@harmonicagoldfish:~$ sudo sysv-rc-conf
sudo: sysv-rc-conf: command not found
harmonicagoldfish@harmonicagoldfish:~$ sudo sysv-rc-conf
sudo: sysv-rc-conf: command not found
harmonicagoldfish@harmonicagoldfish:~$ 

So now what??

How do I undo this?

---

### Post by NickeM on 2007-04-25
It looks like you are missing the sysv-rc-conf, try:

```
sudo apt-get install sysv-rc-conf
```

and if you want to undo your changes:

```
sudo apt-get remove ivman
```

---

### Post by phogy on 2007-04-25
I've been struggeling with the same problem, editing the rules.d/45-libgphoto settings etc.
Here's what worked for me:

```
rm -rf ~/.gconf/desktop/gnome/volume_manager
```
For each user that has this problem.

---

### Post by HarmonicaGoldfish on 2007-04-26
thanks to NickeM and phogy. I'll give both a try when I get home :)

---

### Post by HarmonicaGoldfish on 2007-04-26
Phogy - it worked!!!!!

Thank you- very happy :)

---

### Post by laytek on 2007-05-12
About two weeks ago, I upgraded from Dapper to Feisty. I have been very pleased with the upgrade. This evening I tried to upload my pictures, and discovered that my automatic camera detection no longer works. I believe that this problem is a major bug. :oops: I am surprised that there hasn't been more attention given to this, and that a solution has come out already. Isn't this the famed Ubuntu that can fix a major security bug (root password written in the clear in logs) within 24 hours! I do not wish to become a linux guru, or have to remember a bunch of workarounds. I simply want a stable desktop system, especially if it used to work in a previous version. Plug in the camera and start moving pictures.

Sorry for the rant, but this should be fixed today!

LayTek

ps. Thanks HarmonicaGoldfish for the work around. I can now finish what I thought was going to a simple task.

---

### Post by dpgraves on 2007-07-04
Looks like problem fixed again in gutsy 
just plug in and turn on comes up with auto import :p

cheers

---

