---
title: "need network access to get network access? 802.1x/WPA2 needed on Ubuntu Studio"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by malrost on 2009-07-26
Argh. I can't wrap my head around this problem.

The paradox: I need network access to get network access (via a more recent network manager). As it currently stands, I have no way to access either network from the Ubuntu Studio machine.

The network manager included with Ubuntu Studio 9.04 only supports WEP encryption (a protocal that I thought was quite obsolete). My building is completely wireless, so the only options I have for network access are either an 802.1x connection and or a WPA connection. 

My possible resources:

-I have a laptop that has network access.

-The network manager in the vanilla Ubuntu 9.04 install works in my building. I have a vanilla Ubuntu 9.04 install on another partition on this computer, and I am able to access its files from the Ubuntu Studio install.

Will I be able to utilize either of these to update the Ubuntu Studio network manager? If so, how?

---

### Post by martinbaselier on 2009-07-26
you can download the files here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

With synaptic you can generate a download script. You would need an updated version of the package list. Than you can choose to select all upgrades and create a download script. You can then run the script on the computer which is connected to the internet. 

The packagelist are in
/var/lib/apt/lists/
I believe. 

If you create a backup of the files on the unconnected machine and then copy the files of the connected machine to the unconnected machine, I think it will work.

---

### Post by RD1 on 2009-07-26
Add Ubuntu live CD as source in Synaptic and install NetworkManager. :)

---

### Post by malrost on 2009-07-26
Thanks for the help. I'm afraid that I've yet to get any of the below suggestions to work. After several failures I am now only getting more confused. 

I *thought* this would be a matter of identifying the package(s) I need, downloading them, and installing them. But now I am *very* confused about exactly which package(s) I need, which ones I am using, and how to install them.

**WHICH PACAKGE(S)?**
My (functional) network manager on my vanilla install seems to be called either "nm" or "networkmanager". The networkmanager-applet (as per the "about" right-click drop down menu) is what I've used to set up access. In /usr/bin, I have four packages: "nm", "nm-connection-editor", "nm-applet", and "nm-tool". And "network-manager" is a series of apps listed at packages.ubuntu.com.

But Synaptic will not locate any such named app. In Synaptic I searched for "nm", "network", "network manager", and "network-manager". The closest packages are "gnome-network-admin", "gnome-nettool", and "gnome-netstatus-applet".

Because I was unable to find the packages (I thought) I needed, I was unable create a download script from Synaptic -- I tried creating a download script from both installations.

**HOW TO INSTALL? Pt 1: package managers**
Since this didn't work, I downloaded and burned a 9.04 Live CD & added it as a source in Synaptic. Yet again, the apps I needed were not there. I double checked using apt-get intall (after apt-cdrom add); no dice.

Hookay. I should have checked the CD list file first (though for what exactly, I do not know.) Maybe I really needed the live DVD -- networkmanager & related apps ARE listed there ([http://cdimage.ubuntu.com/releases/jaunty/release/ubuntu-9.04-dvd-amd64.list](http://cdimage.ubuntu.com/releases/jaunty/release/ubuntu-9.04-dvd-amd64.list)). I'll try that as soon as it finishes downloading.

**HOW TO INSTALL? Pt 2: from source**
Since I couldn't get there via package managers, finally I tried installing from source. I downloaded the source tarball here: [http://projects.gnome.org/NetworkManager/]("http://projects.gnome.org/NetworkManager/")

I extracted this to a file, copied it to the Studio install, and am apparently now in an imaginary dependency hell. From the directory, ./configure runs for a bit until it returns this:

```

checking for xgettext... no
checking for msmerge... no
checking for msgfmt... no
configure: error: GNU gettext tools not found; required for intltool
```

I don't have GNU gettext tools? Synaptic indicates that I do indeed have the package named "gettext-base" installed ("This package includes the gettext and ngettext programs which allow other packages to internationalize the messages given by shell scripts.")

W.T.F.??? 	](*,)

---

### Post by malrost on 2009-07-27
I've now used the live DVD as a Synaptic source, and with it was able to add network-manager 0.7.1 and network-manager-gnome 0.7.1 from it. Yet I am still unable to get network access.

The networkmanager applet 0.7.0.100 allows me to set the proper SSID, Security, Authentication (PEAP, version 2), Inner Authentication MSCHAPv2, user name and password... but will still not connect.

So even thought I'm using the same settings --in the same version of the same application-- that work in vanilla 9.04, it won't work in Studio 9.04.

Is there a useful strategy for troubleshooting this issue that I've overlooked?

---

