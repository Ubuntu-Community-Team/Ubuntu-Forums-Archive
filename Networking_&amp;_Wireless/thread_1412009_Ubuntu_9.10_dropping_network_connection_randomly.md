---
title: "Ubuntu 9.10 dropping network connection randomly"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by slowman_x on 2010-02-20
Hi, I am a total Linux newbie, and I have just installed Ubuntu 9.10 on my laptop. I have a windows installation (partition) but have installed into freespace on the same drive using the auto-partition manager, etc, and everything is fine. I got my network going fairly easily by going Preferences > Wireless and inputting SSID and WPA encryption key (PSK). My router issues an WLAN IP,  I can get on the net, I can see my other Windows PCs on the network, I can reach my router, and all is good.

So after several hours of mooching about and looking at things, I have updated all the Linux packages via Synaptics (following a prompt to update everything) including GRUB. My dual boot now shows two versions of the OS:

GRUB 1.7~Beta4
Ubuntu, Linux 2.6.31-19 - generic (I am booting this one)
Ubuntu, Linux 2.6.31-14 - generic

I also set up my HP F4580 printer over wifi on the network though with slightly incorrect drivers (for the F4400 series as this was recommended at the closest match). It works, and I can print a test page no problem.

The only thing is that now (since doing all that) Ubuntu seems to periodically drop my connection to the network and then request the network PSK again, but when I enter it, it spends time trying to renegotiate but fails, and then re-requests the PSK, over and over and it never reconnects. I have to reboot and then I can connect again (automatically), until it drops at some random point (like 5 or 10 mins later). My windows pcs are not losing their connections when this happens on the Linux OS, and the router is fine..

Can anyone suggest why this might be or what I can check? 

Thanks very much...

---

### Post by 2hot6ft2 on 2010-02-20
I upgraded network-manager from the PPA to see if it would help to stop the disconnects and it's working good 3 days so far without a single one. So it may help.
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
To undo it the lines added earlier would have to be removed or commented out.
Apt would have to be updated again.
And apt-get reinstall would have to be used to revert back to the previous version. May even need to use a wired connection to do it.
:guitar:

---

### Post by 2hot6ft2 on 2010-02-20
> **slowman_x said:**
> My dual boot now shows two versions of the OS:

GRUB 1.7~Beta4
Ubuntu, Linux 2.6.31-19 - generic (I am booting this one)
Ubuntu, Linux 2.6.31-14 - generic

It's not 2 versions of the OS it's 2 kernel versions.
It's a good idea to keep 2 because if the new one doesn't work for some reason you still have one that works to boot to.

---

### Post by slowman_x on 2010-02-20
Hi 2hot6ft2, thanks for your fast advice. I'm not sure exactly what I've done but I've just done all that, so thanks...! My connection dropped after the file edit in step one and I had to reboot to get a connection to complete the remaining steps, but it all seemed to work ok and I have rebooted agaom and auto-connected to my network... 5 minutes uptime and counting... as I said I am a total newbie and I don't have any experience of Linux before this afternoon when I decided to take the plunge and give it a go. So I am just wondering if having done these mods and now having 'non-standard' files (?) am I creating any future problems for myself re updates to the packages that will come later? Do I need to watch out for that with regard to what I've changed here?

Thanks again for your help so far, much appreciated

---

### Post by northd_tech on 2010-02-20
> **2hot6ft2 said:**
> It's not 2 versions of the OS it's 2 kernel versions.
It's a good idea to keep 2 because if the new one doesn't work for some reason you still have one that works to boot to.

I like to keep at least 3, so that if you want to "tweak" or test something, you've still got one and a backup to fall back on.  One or two of the kernels had seemed buggy to me, so I kept one of the much older ones as my "backup" copy.

I recently uninstalled Gnome's Network Manager and have been running wicd for a while now.  I like it better, and my connection has been somewhat faster (but still lags FAR behind Vi$ta, and it really sucks at work).

I've disabled IPv6 with a kernel option in /boot/grub/menu.lst and have recently gone to static OpenDNS server IP addresses- still evaluating whether it's better.

edit:  I'm getting 25913 kbps just now according to Firefox's Bandwidth Tester plugin- so the static OpenDNS thing is nearly twice as fast on the download side.  Uploads are still in the DSL neighborhood at 471 kbps.

---

### Post by slowman_x on 2010-02-20
:-( damn, connection dropped again, just like before, except now the PSK password field in the Authentication window is populated where before it was blank. Still it can't seem to get a second successful connection without rebooting... 

I tried booting the older kernal version to see if it was ok but same problem. Should I roll back to where I was before I updated all the packages earlier? I don't even know how to do that...

---

### Post by northd_tech on 2010-02-20
If you have a working cabled ethernet connection, I'd consider trying wicd instead of the default [Gnome] Network Manager- it has worked better for me.

If you want to try that, just search for "wicd" in the Synaptic Package Manager.

ONE WORD OF CAUTION:  Wicd will **require** you to uninstall the Network Manager, so you might want to gather the appropriate wicd and Network Manager ".deb" Debian package files onto a USB stick (or search your LiveCD) before you try any of that.

Here are tutorials on wicd:

[http://ubuntu-tutorials.com/2009/09/14/replace-network-manager-with-wicd-ubuntu-9-04/](http://ubuntu-tutorials.com/2009/09/14/replace-network-manager-with-wicd-ubuntu-9-04/)

[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

Downloads are here:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

[http://linux.softpedia.com/get/System/Networking/Wicd-40130.shtml](http://linux.softpedia.com/get/System/Networking/Wicd-40130.shtml)

The Karmic 9.10 version is here:

[http://packages.ubuntu.com/karmic/wicd](http://packages.ubuntu.com/karmic/wicd)

or else search for "wicd" here for older versions:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

(You should also be able to find the network manager applet by searching the above link)

[http://packages.ubuntu.com/search?keywords=Network+Manager&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=Network+Manager&searchon=names&suite=karmic&section=all)

---

### Post by slowman_x on 2010-02-22
In the time I've had for testing, it seems that if I disable the printer I installed (WIFI connection) then the Network Manager doesn't drop the connection... it stayed up for an hour or more in the last session I did like this... previously it's only managed a few minutes... will have to investigate more later.. thanks for your advice so far folks

---

### Post by ajitwarrier on 2010-02-25
@Slowman_x, Did that work for you? I have the same problem except I do not have a printer connected to the PC? My desktop has an ralink usb wireless card and it works for a few hours till it drops just like yours (asks for PSK etc). It only reconnects after a reboot. Anyone has any ideas? Maybe even a way to reinitialize the card? I take the card out and system shows it has gone. I plug it back in and the system gets that too. But does not reconnect. ifup on the card does not work either. I was running XP on this box before and the card worked flawlessly. 

Please help.

Ajit

---

### Post by slowman_x on 2010-02-27
Hi - no unfortunately my problem is not solved. I'm not sure how much it has to do with the printer in the end. But with the printer disabled in Ubuntu and not switched on (so basically out of the equation) my connection usually stays up for probably about 20 or 30 mins maybe a bit more, and then it drops and nothing but nothing will re-establish connection other than a reboot. This is longer than it was staying up with the wifi printer on... Anyway it always auto connects first time after boot without issue, so it has to be something about the network manager I think. I have no problem under windows with the same configuration. Anyone have any other ideas?

---

