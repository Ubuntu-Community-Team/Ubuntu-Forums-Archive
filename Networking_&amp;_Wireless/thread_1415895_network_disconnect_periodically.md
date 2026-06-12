---
title: "network disconnect periodically"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by u_kapaley256 on 2010-02-25
Hi all,

I use kubuntu 9.10 64-bit on AMD Turion M500 machine.
The network keeps disconnecting periodically or on some heavy activity 
The connection is totally stable on windows 7 though.
My doubts point to network manager and so my next step is to switch to command line wpa_supplicant 
Any suggestions ?

Thanks

---

### Post by 2hot6ft2 on 2010-02-25
I upgraded network-manager from the PPA to see if it would help to stop the disconnects and it's working good 14 days so far without a single one.

So it may help. Adjust the commands for Kubuntu like sudo instead of gksu. And you probably wont want the "network-manager-gnome" in the commands.
I got it by adding the karmic PPA from here:
[Karmic network-manager PPA]("https://launchpad.net/~network-manager/+archive/trunk/")

These are bleeding edge with the very latest bug fixes so do so at your own risk!!!
If you want to give it a try you can do it like this:
Open a terminal
Applications > Accessories > Terminal
and follow this:
(when asked for your password in the terminal it wont display what you type, you just type it in and hit Enter)
```
gksu gedit /etc/apt/sources.list
```
Add these 2 lines to the bottom
> deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
Save and close it then use this to add the key (shouldn't really need sudo in the rest but I included it just in case you take more than 15 minutes to complete it all).
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8
```
Then update apt
```
sudo apt-get update
```
Install the new network manager
Here you have some choices

If you just want to **just update network manager** use this first one (this is what I used)
```
sudo apt-get upgrade network-manager network-manager-gnome
```
If you're using **pptp** use this to update it as well otherwise it's not needed.
```
sudo apt-get upgrade network-manager network-manager-gnome network-manager-pptp-gnome
```
If you're using **VPN** use this to update it as well otherwise it's not needed.
```
sudo apt-get upgrade network-manager network-manager-gnome  network-manager-vpnc-gnome
```
If you want to **update it all** use this one
```
sudo apt-get upgrade network-manager network-manager-gnome network-manager-pptp-gnome network-manager-vpnc-gnome
```
To undo it the lines added earlier would have to be removed or commented out in /etc/apt/sources.list.
Apt would have to be updated again.
And apt-get reinstall would have to be used to revert back to the previous version. May even need to use a wired connection to do it.
:guitar:

---

