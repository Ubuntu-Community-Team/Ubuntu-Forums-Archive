---
title: "Can't install Wicd Please help"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by newbby on 2009-04-07
I have been trying Ubuntu 8.10 over the past couple of weeks in a dual boot system and am pretty pleased with it. Have successfully done most things with online help but can't seem to get Wicd to install.

Tried this method from Wicd site

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

and always get this error

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828"


also tried this method

Open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type:
(if the system ask you for a password give your user password, you will not see nothing when you type it, then press enter)

wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O - | sudo apt-key add -

Add the wicd repository row to your /etc/apt/sources.list, type:

sudo gedit /etc/apt/sources.list

and add this row:

deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

save close and exit. Then type:

sudo apt-get update
sudo apt-get install wicd
sudo killall nm-applet

and always get this error 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What am I doing wrong? Any help would be much appreciated.

Thanks

---

