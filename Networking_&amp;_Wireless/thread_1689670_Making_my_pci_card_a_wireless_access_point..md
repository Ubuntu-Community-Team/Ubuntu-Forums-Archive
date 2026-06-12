---
title: "Making my pci card a wireless access point."
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by jogi.nayak on 2011-02-17
I am trying to make my D-Link DWA-525 wireless 150 card an access point. The** lspci -k** command gives the following information :-

Network controller: RaLink Device 3060
    Kernel driver in use: **rt3060**
    Kernel modules: rt3562sta

I'm using this link to set up the wireless access point :

[http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto](http://rt2x00.serialmonkey.com/wiki/index.php/AP-mode_Howto)

Everything went smooth until the last step where i have to run : ```
./hostapd -dd hostapd.conf.

```
It gives me the following error :-
> 
Configuration file: hostapd.conf
nl80211: 'nl80211' generic netlink not found
nl80211 driver initialization failed.
rmdir[ctrl_interface]: No such file or directory


Could someone please tell me where I am going wrong? I searched a lot on Google but couldn't find an answer

---

### Post by amsterdamharu on 2011-02-17
I am not sure what they mean by rt2x00 chips but is it the one you have?

If you want other wireless to connect to your card can't you just click on the network applet and choose "create new wireless network". Then use squid to proxy connections to the Internet

I do see that hostapd has a routing to traffic option. Maybe it is something in the hostapd.conf you need to change.

---

### Post by amsterdamharu on 2011-02-17
I just see that squid is not needed, Ubuntu can share the Internet as easily as changing a select box
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
Right click, edit connections, edit the connection you made with "create new wireless network", under ipv4 method choose "shared to other computers"

You can install hostapd with apt-get if you need to use that:
```
sudo apt-get install hostapd
```There isn't much info on Ubuntu help:
[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)
bottom of the page

---

### Post by jogi.nayak on 2011-02-17
I have tried all that but choosing an option in network manager does not create an access point. ( I cannot view the network on android phones since android does not support ad hoc networking) It just creates an ad hoc network. I am trying to configure my wireless card to behave like a router. and my card is rt3060 a newer version of rt2x00 so im guessing they are compatible. Does anyone know where exactly i am going wrong here?

---

### Post by jogi.nayak on 2011-02-17
Creating an access point through network only creates an ad hoc network. I need to configure my card to behave like a wifi router. Some one please help!

---

### Post by amsterdamharu on 2011-02-18
Ok, that clears something up so we have to go with the complicated solution. I was thinking you might run it as a server and don't have gnome.

First: according to the tutorial you check out stuff from git and compile, maybe installing hostapd from ubuntu will work better. I think you can do make uninstall if you installed it and then install the ubuntu package:
```
sudo apt-get install hostapd
```

Now check out the hostapd.conf according to the tutorial and make the changes you need. I don't have too much time now to look into it but try again later.
The man page for hostapd:
[http://www.openbsd.org/cgi-bin/man.cgi?query=hostapd&sektion=8](http://www.openbsd.org/cgi-bin/man.cgi?query=hostapd&sektion=8)
hostapd.conf:
[http://www.openbsd.org/cgi-bin/man.cgi?query=hostapd.conf&sektion=5&arch=&apropos=0&manpath=OpenBSD+Current](http://www.openbsd.org/cgi-bin/man.cgi?query=hostapd.conf&sektion=5&arch=&apropos=0&manpath=OpenBSD+Current)

---

### Post by amsterdamharu on 2011-02-18
Could you check your driver to see if it's compatible with hostapd?

```
sudo apt-get install hostap-utils
sudo hostap_diag -a wlan0
```

I gave it a shot here but don't have the drivers for my wifi that'll work with my wireless. Maybe I'll try madwifi but will have to wait since I don't have the time for it right now.

---

### Post by jogi.nayak on 2011-02-20
Thank you so much ! I'll try tomorrow and let you know what i get..Do you have any idea what nl80211 is? And im guessing madwifi is not compatible with my card since its not atheros family. I tried installing it anyway and it didnt even install. So i tried running hostapd with driver=nl80211 in hostapd.conf. I also installed libnl because i read somewhere that its required for nl80211 to work. Am i going wrong somewhere here?

---

### Post by amsterdamharu on 2011-02-20
According to this page:
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)
It looks like madwifi is only atheros.

On that page your card is (somewhat) listed
[https://help.ubuntu.com/community/WifiDocs/MasterMode#Texas%20Instruments%20ACX100/ACX111](https://help.ubuntu.com/community/WifiDocs/MasterMode#Texas%20Instruments%20ACX100/ACX111)
> In cards based on this chip (ex. D-Link DWL-520+) master mode is not  fully implemented (as of 2007-01-01 driver) and there are some different  problems like sometimes no beacons are broadcasted and card can't be  properly initiated. Supports 1/2/5.5/11M(b) and 22M(b+) modes.

Looks like only b mode is supported by driver but this doesn't mention DWL-525 card that you have.

You could just use the driver you have and check with hostap_diag what the outcome is. The page also mentiones some commands you could try to see if the hardware supports master mode. If hostap_diag fails as it did with me it doesn't mean the card doesn't support it, my card supports master mode but the driver doesn't.
> sudo aptitude install iw
iw list | grep IBSS #should have some output
iw list | grep managed #should have some output
iw list | grep AP #should have double output AP and AP/VLAN
iw list | grep monitor #should have some output
iw list | grep mesh point #should have some output
Quote from the page:
> If there is 'AP' in the list of "Supported interface modes" your device will support the Access Point mode with hostapd. 

nl80211 seems to be for  softmac
[http://linuxwireless.org/en/developers/Documentation/mac80211](http://linuxwireless.org/en/developers/Documentation/mac80211)
On this page:
[http://linuxwireless.org/en/developers/Documentation/Glossary#SoftMAC](http://linuxwireless.org/en/developers/Documentation/Glossary#SoftMAC)
> *SoftMAC* is a term used to describe a type of wireless card where the MLME is expected to be managed in software. [mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211") is a driver API for SoftMAC wireless cards, for example. 
Browsed through the pages but all I can figure out is that it is a layer upon the driver, but what drivers and hardware are supported I can't figure out.

---

### Post by jogi.nayak on 2011-02-22
I dont know how to thank you amsterdamnharu. 

I tried hostap_diag -a ra0 and this is what it said :-

Host AP driver diagnostics information for 'ra0'
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Could not communicate with the kernel driver.

This means my driver does not support hostapd right? how do i get a driver or a utility like hostapd for my card?. I am quite sure my card supports master mode because in windows7 using a program called 'Connectify' i can convert it into an access point very easily which means it must support AP mode. Could you please go about configuring my card to work as an ACCESS POINT?

Thank you once again for all your replies.

---

### Post by jogi.nayak on 2011-02-22
And the output of all of the following command is the same

iw list | grep IBSS #should have some output
iw list | grep managed #should have some output
iw list | grep AP #should have double output AP and AP/VLAN
iw list | grep monitor #should have some output
iw list | grep mesh point #should have some output 			 		

Output: nl80211 not found

---

### Post by jogi.nayak on 2011-02-22
Also like you said i installed hostapd with : sudo apt-get install hostapd.

So where is it installed? and where can i find the .config file and the make file?

---

### Post by amsterdamharu on 2011-02-22
So all the iw list commands have some output, if you execute without grep you get a long list and have to check yourself if IBSS, managed, AP etc.. is in there.

If the output was nl80211 not found then it returned an error. Does the card work connecting to a wireless network?


I am not at my laptop now but remember some files in /etc/default/hostapd and /etc/hostapd. Starting hostapd with service start hostapd and or /etc/init.d/hostapd start does not give an error but would not really start hostapd therefore you'd better give the hostapd command yourself.

---

### Post by jogi.nayak on 2011-02-22
Yes the card can connect to a wireless network. How do i get nl80211 driver for my card?

---

### Post by jogi.nayak on 2011-02-22
Yes the card can connect to a wireless network. How do i get nl80211 driver for my card?

---

### Post by amsterdamharu on 2011-02-22
I have something in usr/include
/usr/include/linux/nl80211.h 

A search on google shows me that that file came from linux-libc-dev
[http://packages.ubuntu.com/lucid/i386/linux-libc-dev/filelist](http://packages.ubuntu.com/lucid/i386/linux-libc-dev/filelist)
[http://packages.ubuntu.com/maverick/i386/linux-libc-dev/filelist](http://packages.ubuntu.com/maverick/i386/linux-libc-dev/filelist)

I have no idea how executing iw list on your machine ends up complaining about it and not on my machine.

---

### Post by jogi.nayak on 2011-02-22
I do not have nl80211.h in the same directory. May be that is why i am getting the error :
nl80211: 'nl80211' generic netlink not found
nl80211 driver initialization failed.
 when i try to run hostapd. you have any idea how i can enable nl80211 for rt3060 wireless card? I guess my hostapd will run if i get this to work!

---

### Post by jogi.nayak on 2011-02-22
Hey sorry i just checked /usr/include/linux properly...Even i have a netlink.h file. My default driver does not respond to hostapd_diag so how do i get a driver for my rt3060 that will enable hostapd to work with it?

---

### Post by flash63 on 2011-02-22
Hello,
you can use rt2800pci/rt2800usb with hostapd and nl80211 (if it works with your card).

The Ralink Driver supports only Infrastructur- an Ad-Hoc Modes. Blacklist rt3562sta/rt2870sta/rt2860sta.

Supported Drivers and Modes:
[http://www.linuxwireless.org/en/users/Drivers](http://www.linuxwireless.org/en/users/Drivers)

---

