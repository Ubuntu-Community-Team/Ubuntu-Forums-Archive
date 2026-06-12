---
title: "install wireless &amp; graphic(nvi) driver without Internet connection"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by amahi on 2011-07-01
We have 2 ways to install the drivers in Ubuntu 

 I :installation of the synaptic (access internet)

II: [COLOR=Blue]Installation Manual (I'd recommend the second method.)[/COLOR]

You do not need to download the file. You should install the following packages.
[COLOR=Red]dkms[/COLOR] package prerequisites that must be installed. ,install dkms form  Ubuntu 11.4 cd-dvd :

path:
>  /pool/main/d/dkms                        install it.

then:
[COLOR=Red]for Wireless Driver:Go to this track 

[/COLOR]>  /pool/restricted/b/bcmwl  install it.

You do not need to download and install another package.!!!

[COLOR=Red]for Graphic Driver(nvidia):Go to this track [/COLOR]

>  /pool/restricted/n/nvidia-graphics-drivers  install it.

[COLOR=Red]for Graphic Driver(ATI):Go to this track [/COLOR]

>  /pool/restricted/f/fglrx-installer install 2 files.

[COLOR=RoyalBlue]Notes[/COLOR]:

1-
[LEFT][COLOR=RoyalBlue]If your network manager is not working, and says unmanaged, or Networking disabled or Wireless disabled , open your terminal and enter[/COLOR]

>  
[LEFT][LEFT]sudo rm /var/lib/NetworkManager/NetworkManager.state[/LEFT]
[/LEFT]
 then in terminal: init 6

2-[COLOR=RoyalBlue]if  network manager not appear[/COLOR] ;

in ubuntu 11.4,in terminal:

>   
[LEFT]sudo gedit  /etc/NetworkManager/NetworkManager.conf [/LEFT]
  [/LEFT]

then change managed=[COLOR=Red]false[/COLOR] to managed=[COLOR=YellowGreen]true[/COLOR].


in other ubuntu version.(10,9,8...) in terminal:

>   
[LEFT]gksu gedit /etc/NetworkManager/nm-system-settings.conf[/LEFT]
 then change managed=[COLOR=Red]false[/COLOR] to managed=[COLOR=YellowGreen]true[/COLOR].

then reboot.

3-use this command to show Enable/Disable network:

>  sudo lshw -C network  sample output:


>   
[LEFT]network [COLOR=red]DISABLED[/COLOR]
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7e:5d:78:70
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=b43  driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes  wireless=IEEE 802.11bg[/LEFT]

 shows wireless is disable.

---

