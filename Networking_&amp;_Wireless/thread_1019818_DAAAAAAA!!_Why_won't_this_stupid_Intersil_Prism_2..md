---
title: "DAAAAAAA!! Why won't this stupid Intersil Prism 2.5 card work!!!!!!"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by jonsayer on 2008-12-23
First off, I'm using Hardy on a computer with an Intersil Prism 2.5 PCI wifi card in it. 

I downloaded and installed linux-wlan-ng. No dice

I installed the hostap drivers. No dice. 

I blacklisted orinoco, as per the instructions here: [https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan](https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan)

No dice. 

I've been scouring the internet for hours looking for a windows driver to plug into ndiswrapper to no avail. That probably won't work anyway because can't flash the card itself because this computer does not have a windows partition. 

I'm not sure what to try next to get this thing to work.

The symptoms: 

For some unknown reason I have two wireless networks available in Network settings: wifi0 and wlan0.

When I try to find a network on one of these two in Network Settings, they see nothing even though I know there are several networks in the area. 

When I run lsmod, I find that hostap and hostap-pci is indeed running. 

I know that this card does in fact work, too. I ran a Nimble-X liveCD in it and everything worked fine. 

I read somewhere that people had trouble with intersil prism cards after upgrading to 8.10, but I don't see how that could be my problem seeing as how this is strait up 8.04.1.

---

### Post by jonsayer on 2008-12-23
Commmme ooooon you guys! Throw me a bone here!

---

### Post by fvillars on 2008-12-27
Getting a Prism chipset card to work with the latest version of Ubuntu seems to be a common problem, as I have seen a smattering of posts on this forum as well as elsewhere that mention this problem. 

I have dealt with it as well and spent altogether too much time finding an answer...but finally did. Here are a couple of steps which I think will help:

1) Make sure you have updated to the latest kernel version and have the latest version of NetworkManager. Use a landline if you have no other means of connecting to an update repository.

2) Flash your chipset firmware with the latest primary and station firmware versions.Instructions on how to do this can be found at:

 [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

Read these instructions carefully, again very carefully, and apply them very, very carefully. Note: nothing will work unless your firmware is up to date. This step is very important. My chipset carries primary firmware v. 1.1.1 and station firmware v. 1.8.2

3) Examine /etc/networking/interfaces. It should have no references to any wireless interfaces. Any line containing "wifi0" or "wlan0" should be removed as well as anything else pointing to a wireless interface. NetworkManager will not work properly if these references are present. Wired interfaces can be safely ignored.

4) Prism cards will use the hostap driver preferentially. Make sure it is present - typing 'lsmod | grep hostap' on a command line should demonstrate this. Or else type 'lshw' - this should give you a list of all your hardware, associated chipsets,and associated drivers. 

5)In addition to hostap, you should have the 'hostap utilities' and the 'hostapd' packages on your system. Install them if they are not there.

6)There should be no conflicting drivers on your system. Hostap utilities takes care of the most common other driver 'orinoco' by  blacklisting it, however others may be present. Again, type 'lsmod' on a command line and scan the output for anything that looks like 'prism' 'pri' or combinations thereof. If present, remove them. That is to say, open /etc/modprobe.d/blacklist and add the appropriate lines to blacklist these drivers.

7)Also check /etc/modprobe.d/aliases and look for any reference to 'wlan0' or 'wifi0' These references, if present, should be removed as NetworkManager will not work properly if they are there.

8)Make sure 'wireless extensions' package is installed. It should be present by default but check anyway. Type 'iwconfig' on a command line. You should get some output. If you get 'command not found' then install this package.

9)This next step is important. On a command line type: 
'sudo hostap_crypt_conf -p wifi0 xx:xx:xx:xx:xx:xx none' where you replace the x's with MAC address of your wireless card. Having done that, do the same thing again, now with wlan0:
'sudo hostap_crypt_conf -p wlan0 xx:xx:xx:xx:xx:xx none '
We are disabling hostap's ability to negotiate encryption. It will be left instead to 'wireless extensions' This is where I think the problem lies for most people. If you allow hostap to negotiate encryption things will not go well.

10)Now make sure the encryption schemes agree between your wireless access point and your computer. Use whatever software to configure your access point. Use 'wpa_supplicant' to configure your computer. Reboot. You should now be able to connect to your access point using NetworkManager.

---

