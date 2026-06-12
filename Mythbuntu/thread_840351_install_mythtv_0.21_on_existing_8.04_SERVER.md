---
title: "install mythtv 0.21 on existing 8.04 SERVER"
date: 2008-06-25
forum: Mythbuntu
---

### Post by ballersupg on 2008-06-25
Hello,

I am not new to Ubuntu, but i'm also not a power user so I need some help.
I'd like to install mythtv on my existing ubuntu 8.04 server box.  Do I have to install a desktop before I can set up a backend?  I really do not want to reinstall mythbuntu from disk, because of the things i already have running.  Any way I can use SSH to just go in there and download, install, setup a mythtv backend only?  Or will this require a desktop to be install (and can I uninstall that after setup?)

Thanks for any help.

current setup:
VPR matrix box with ubuntu 8.04 server.
(reason I do not want to reinstall from disk is because the 8.04 disks do not boot my computer(or if they do, it will run into errors on the install, and yes i've checked the disks on other machines). To install server, I have to start from 6.06, then run upgrades)
I have SSH, NFS, twonky, and a few other things running that I do not want to start from scratch.
I use a mac to ssh into it, and have a completely mac house with a windows virtual machine if needed.

I really like the concept of ripping all of my DVDs into one place to watch from any computer in the house with mythVideo.  While we're on the topic,  does anyone have any success with mythvideo and saving DVDs to hard drive?  Any tips?

Thanks so much.

---

### Post by uopjohnson on 2008-06-26
In order for mythbuntu to be useful for you you will want to install a desktop.  The number one benefit of mythbuntu is the mythbuntu-control-center.  It will make the rest of yoru setup a piece of cake. Unless you are extremely space limited there is no reason not to install a desktop, once you are done setting up you can even setup your machine to not start up x windows and you won't loose any resources.  However, in my experience you should just install the desktop and leave it running with a vnc server on it so that you can easily make changes and manage updates. I use chicken of the VNC on my macs to manage all of my mythbuntu boxes.  
I'm pretty sure that if you just run apt-get install mythbuntu-desktop you will get a desktop environment and then the MCC you can then choose to install just a backend and you will be good to go.

---

### Post by duckville on 2008-06-26
the bulk of mythbuntu is not required, the control centre is nice; however you already have ssh, nfs (rather than samba) etc... installed. you do need the X server as it's the only way to configure mythtv.

you can use ssh and -X to forward the x traffic to your mac and configure everything remotely.

---

### Post by uopjohnson on 2008-06-26
The question is what do you save by not installing the full mythbuntu-desktop?  A few MB of disk space?  In return you end up with a non-standard installation that is much mroe difficult to troubleshoot.

---

### Post by fosheezy on 2008-07-02
how would I go about setting up SSH -X?  I've played around with this, but it was on an Ubuntu gnome Desktop.  WIll I need to install a desktop on my server and have it forward X to SSH?  I will be able to leave the server up without running the desktop though, correct?

As to what I'll save without installing mythbuntu, I only need a backend running, which can be setup then left alone and configured with mythweb and webmin.  I'd like as little as possible running on the thing, and im trying to force myself to learn the command line (which i'm really enjoying running the server over SSH).  This thing is going to sit in a closet as a huge file server for DVDs, movie files from 6 summers of month long family vacations, photos, and music.  I'd like mythtv to use the mythvideo dvd archiving feature and in the future to use to record tv.


EDIT:  Nevermind, I found how to install X server.

---

### Post by ian dobson on 2008-07-02
Hi,

I'm running a "desktop" less backend. I'll try and dig up the notes I used to just install the packages required.

I actually run mythtv-setup through a remote X session from a windows XP pc using cygwin. It's not that quick but it's enough to setup the box.

Regards
Ian Dobson

edit: Found the links [https://help.ubuntu.com/community/MythTV/Install/Server/Backend](https://help.ubuntu.com/community/MythTV/Install/Server/Backend) &
[https://help.ubuntu.com/community/MythTV/Install](https://help.ubuntu.com/community/MythTV/Install)

---

