---
title: "Dial up (DUN) via bluetooth and Network Manager."
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by frytek on 2013-03-12
I am not sure if this problem is present on Ubuntu... 
Anyway, I remember struggling with DUN via bluetooth on some older Ubuntu versions. On 12.04 it worked (gnome bluetooth applet plus Network Manager). Then I switched to Mint 13 and it worked as well. But recently I upgraded to Mint 14 and it didn't work again. 
Ubuntu users can have the same problem as the repos of Mint are based on newest Ubuntu. 

Anyway, if you cannot connect to the internet with bluetooth + mobile phone + network manager, this is the way to do it. 

This page:
[https://bbs.archlinux.org/viewtopic.php?id=147880](https://bbs.archlinux.org/viewtopic.php?id=147880)
iexplains why Network Manager doesn't want to work with Blueman. We have to compile Network Manager with bluetooth modem support.

Here's how to do it (Thanks to my friend Ethanak):

we need to add a sources repo:
sudo gedit /etc/apt/sources.list
add line: deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal main restricted
(replace quantal with your version name, e.g. precise and so on) 


sudo apt-get update
sudo apt-get install blueman build-essential dpkg-dev

sudo apt-get build-dep network-manager

mkdir -p ~/tmp
cd ~/tmp

with no sudo:
apt-get source network-manager
cd network-manager-versionnumber

(replace versionnumber with actual name of the folder)

now we edit the file inside network-manager-verionnumber

gedit src/nm-manager.c

as described in the page linked above. namely, we remove ! before strcmp in this location:

if (driver && strcmp (driver, "bluetooth")) {
nm_log_info (LOGD_MB, "ignoring modem '%s' (no associated Bluetooth device)", ip_iface);
return;
}


and we save the file

now:
dpkg-source --commit

it will ask for a name for the patch, we provide any, editor will be open - we save the file (if this is vi, type :wq)

dpkg-buildpackage -us -uc

a good idea now is to stop the current network manager:

sudo /etc/init.d/network-manager stop

cd ..

sudo dpkg -i network-manager-versionnumber.deb

and start new network manager:
/etc/init.d/network-manager start

now,
we stop the mate / gnome bluetooth applet:
killall mate-bluetooth-applet
(and remove it from startup programs in menu)

and start blueman:
blueman
(and add it to the startup programs if it's not there)

right click on blueman icon -> devices
search
add device -> pair, type PIN code and the same on the phone

now, our new network manager:
right click -> edit connections
broadband -> than the wizard for your country and operator plan.
new connection shows up in the network list (left click) where we used to have only LAN and wireless before. in the newly compiled network manager you can see e.g. T-mobile now. 

click on local services in blueman and in PAN and DUN support click on Network Manager. (This dialog is a little bit tricky because the Apply button is inactive as long as you disable, apply, and reenable the NAP option on the top.

Now click on Devices -> your phone -> select Serial ports -> DUN. confirm connection on your phone and observe the connection icon.
in my case the Network Manager connected automagically with the defined broadband connection. if yours doesn't - click it on the menu.

That's all. :)

---

### Post by gvlists on 2013-10-20
This has been a show stopper for me for a year. I was postponing my distribution upgrade because of this bug. Thanks very much for the detailed explanation. It worked for me in XUbuntu 13.10. I am surprised why this bug is not reported and not fixed in subsequent ubuntu versions. There might be many like me who use the internet from phone while travelling. Do you know of any bug reports?

A couple of improvements in the steps may be helpful for other ubuntu users. I applied this patch to XUbuntu 13.10 and observed these changes.

Adding the source may be done by (I hope you have synaptic package manager, else you will have to install it). 
System > Synaptic package manager > settings >           repocitories > Ubuntu software tab
          click "source code"
This will replace the following lines
> we need to add a sources repo:
> sudo gedit /etc/apt/sources.list
> add line: deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)           quantal main restricted

The following line may be incorrect although quite obvious to someone experienced.
> sudo dpkg -i network-versionnumber.deb
          It should be
sudo dpkg -i network-manager-versionnumber.deb
Just press tab to get the correct version number. It should usually autofill.

---

### Post by frytek on 2013-11-27
I have corrected the mistake in my original post (network-manager-versionnumber). Thanks. 

The whole story doesn't look like a bug to me. Somebody playing with the source code obviously wanted bluetooth interfaces not to be displayed. But of course I can't think of any good reason for doing so. :(

---

### Post by gvlists on 2014-10-03
Among the two wireless tethering options, WLAN has some disadvantage. The power consumption of WLAN modulation scheme, OFDM, is less efficient than Bluetooth FSK/QPSK. In the interest of battery life I prefer BT/GSM over WLAN/3G. BT/3G is still an option for speed. Anyway using WLAN to connect phone to mobile is not required. Afterall the max 3G bandwidth I got is well within what BT can handle. I am not sure of security of BT though.

---

### Post by gvlists on 2015-08-02
Are you still able to get Bluetooth tethering work? I recently tried and the above mentioned lines of code has changed. It is not possible to make the change now. I am using XUbuntu vivid.

---

