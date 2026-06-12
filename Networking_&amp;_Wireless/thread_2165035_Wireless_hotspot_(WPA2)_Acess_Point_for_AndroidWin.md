---
title: "Wireless hotspot (WPA2)/ Acess Point for Android/Windows devices on Ubuntu Machines"
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by sbnwl on 2013-08-03
I am posting this because this functionality is not available in default Ubuntu 12.10/13.04 installations. Creating a wireless hotspot (infrastructure WPA2 Security) is required to share internet connection from a Ubuntu Machine to Android/Windows powered devices or iPhones.

Instructions:[INDENT]1. To Install the ap-hotspot script (GUI for this script is not available yet), add the following PPA:[/INDENT]
[INDENT]```
sudo add-apt-repository ppa:nilarimogard/webupd8
```
***The following command is required only if you have Ubuntu 12.04 or earlier releases:***
```
sudo add-apt-repository ppa:network-manager
```
Update the repository informations and install the "AccessPoint-Hotspot script":
```
sudo apt-get update
sudo apt-get install ap-hotspot
```
[/INDENT]
[INDENT]
2.  After the installation, either disable the firewall (if you are comfortable enough with no firewall) using gufw or firestarter, OR change the firewall rules to allow traffic for the following two services:
[/INDENT]
[INDENT=2]dnsmasq[/INDENT]
[INDENT=2]dhclient[/INDENT]
[INDENT]
3. A first time configuration can be done on Ubuntu machine by issuing the following command in the linux terminal:
```
sudo ap-hotspot configure
```
This configuration will ask for hotspot name you want to create, your LAN interface name, your WLAN interface name and the password (10 characters) etc. The interface names can be found by clicking network manager icon, and then clicking on 'information'.[/INDENT]
[INDENT]
4. Start the hotspot on Ubuntu machine:
```
sudo ap-hotspot start
```[/INDENT]
[INDENT]The hotspot is now active and ready to go. Turn the WiFi ON on your Android device/ Windows Phone/ Mac device and your device will show your 'hotspot name' that you had chosen during first time configuration (step 3). Tap on the name of hotspot to connect and enter the required password that you had set during configuration in step 3 above.[/INDENT]
[INDENT]
5. This hotspot can be stopped by using the command:
```
sudo ap-hotspot stop
```[/INDENT]

Please feel free to discuss/share your experiences/troubles....

This guide works with Ubuntu 12.10/13.04 and other derivatives of Ubuntu like Kubuntu 12.10/13.04, Xubuntu 12.10/13.04 or Zorin OS 7. Haven't checked yet on Linux Mint. 

References:
```
[http://www.ubuntuupdates.org/package/webupd8/raring/main/base/ap-hotspot](http://www.ubuntuupdates.org/package/webupd8/raring/main/base/ap-hotspot)
[http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html)
[http://forum.xda-developers.com/showthread.php?t=2009381](http://forum.xda-developers.com/showthread.php?t=2009381)
```

AN UPDATE (#1)```
**The network manager in default Kubuntu 13.10 installation has inbuilt support for Access Point mode. **
Just go to "Edit Connections" on the tray icon in the plasma desktop,
Select "Add"  then select "WiFi(Shared)" connection,
Select "WiFi tab, mode = AccessPoint",
Select "WiFi-Security tab,  Security = WPA & WPA2 Personal and give any password" and save the  connection. 
That is all, you should be done!
```

---

### Post by praseodym on 2013-08-03
If someone uses 12.04 or earlier, it should read additionally:
```

sudo apt-get upgrade
sudo apt-get dist-upgrade
```
to update the NWM

---

### Post by sbnwl on 2013-08-03
[COLOR=#DD4814][COLOR=#000000]@[praseodym]("http://ubuntuforums.org/member.php?u=1411497")[/COLOR][/COLOR][COLOR=#000000] 
Thanks for the additional info.[/COLOR]

---

### Post by robjoski on 2013-08-10
NetworkManager already supports AP mode for hotspots, however wpa_supplicant needs to built with this support as well, which Ubuntu hasn't enabled yet.
It's a very simple config change, and rebuilding wpa_supplicant is almost easier than setting up extra tools like dnsmasq, so even GUI frontends for these tools are unnecessary IMHO.

 [http://pkgs.fedoraproject.org/cgit/wpa_supplicant.git/commit/?id=16eae335b8b710abef21dcf9df4294533f2b42a1](http://pkgs.fedoraproject.org/cgit/wpa_supplicant.git/commit/?id=16eae335b8b710abef21dcf9df4294533f2b42a1)

---

### Post by sbnwl on 2013-08-12
@[**[COLOR=#000000] robjoski[/COLOR]**]("http://ubuntuforums.org/member.php?u=392321") 	 
It would be great if you share/explain the wpa_supplicant configuration a bit in detail...

---

### Post by djibrilcoulibaly on 2013-09-12
what's to do if this happen? I'm on 13.10 but I didn't tried this at 13.04
> /home/psy/Desktop# ap-hotspot configure
**Your wireless card does not support Access Point mode**

>  description: Wireless interface
 product: Centrino Ultimate-N 6300
 vendor: Intel Corporation
 physical id: 0
 bus info: pci@0000:44:00.0
 logical name: wlan0
 version: 35
 serial: 00:24:d7:79:df:3c
 width: 64 bits
 clock: 33MHz
 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
 configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-4-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn


---

### Post by sbnwl on 2013-09-14
@[**[COLOR=#000000]djibrilcoulibaly[/COLOR]**]("http://ubuntuforums.org/member.php?u=1735028")
```
/home/psy/Desktop# ap-hotspot configure
**Your wireless card does not support Access Point mode**
```
I have also experienced the same on a three year old Dell M1330 netbook.

Probably your wireless card is too old to support this feature.

---

### Post by childintime on 2013-11-28
I was using this hot spot, and wonder is it possible to check who is connected to this network?

---

### Post by sbnwl on 2013-12-16
**@**[**[COLOR=#000000]sladeinflame7[/COLOR]**]("http://ubuntuforums.org/member.php?u=1880342")
It is possible. All you have to do is a ping search on your subnet.

First find the ipv4 IP address of your shared internet connection, which you can look into network-manager icon. If not there then look into the output of following command
```
user@mylappy:~$ifconfig

wlan0     Link encap:Ethernet  HWaddr 23:2f:32:d8:4a:d1  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::762f:68ff:fed8:8ad1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:905 errors:0 dropped:2 overruns:0 frame:0
          TX packets:3109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160202 (160.2 KB)  TX bytes:1248214 (1.2 MB)
```
So you now have 10.42.0.1 as the IP address of your broadcasting device named "wlan0".
Now you open a terminal and go like this:
```
user@mylappy:~$nmap -sn 10.42.0.1/24

Starting Nmap 6.40 ( http://nmap.org ) at 2013-12-16 22:57 GMT
Nmap scan report for 10.42.0.1
Host is up (0.00079s latency).
Nmap scan report for 10.42.0.70
Host is up (0.045s latency).
Nmap done: 256 IP addresses (2 hosts up) scanned in 2.82 seconds


```
You see in the output that the IP 10.42.0.70 is what you are looking for.

---

### Post by childintime on 2013-12-16
Worked perfectly, thank you sir! :)

One thing though, I typed ifconfig, and there is this field:

```
mon.wlan0 Link encap:UNSPEC  HWaddr 6C-71-D9-91-64-CD-3A-30-00-00-00-00-00-00-00-00            
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12146013 (12.1 MB)  TX bytes:0 (0.0 B)

```

which is not my hotspot, but do you know what it is exactly?

---

### Post by asus-user on 2013-12-23
I'm on ubuntu 12.04, and it works fine, but I had to make static IPs for each device, is it possible to use DHCP?

---

### Post by sisternotes2 on 2014-01-25
Thanks for this. It seemed to work great: I'm trying to use my USB mobile broadband connection to turn my laptop into a hotspot. I tested the connection using my Android phone. I was able to connect to the broadcasted wifi, but then my mobile broadband connection would disconnect. It reconnected, and I was able to restart the hotspot. Except now my phone says I'm connected but with "limited connectivity" and I can't access any web pages. I've tried restarting/reconnecting and get the same thing. Any ideas?

---

### Post by sbnwl on 2014-01-26
@[**[COLOR=#000000]sisternotes2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1877488")

```
Except now my phone says I'm connected but with "limited connectivity" and I can't access any web pages.
```

Well! It seems like your phone is now connected but not able to communicate to your broadband connection's Gateway/DNS. Check if you find any Gateway IP in Android phone connection, while it is having "limited connectivity". Or look into your "broadband connection settings" and find if it uses any proxy server? (Though it is highly Unlikely for a USB broadband to have a connection through proxy server). If yes, then you need to put that 'proxy server address' also into your 'Android phone connection'.
I can't guess anything more at the moment.

---

### Post by grrrbob on 2014-01-27
i used the original post to configure on my os which is ubuntu 12.04.It seemed to go smoothly and my ipad air can see the hotspot from ubuntu but fails to connect with a simple message of unable to join the network :-( any ideas of what is wrong?



> **sbnwl said:**
> I am posting this because this functionality is not available in default Ubuntu 12.10/13.04 installations. Creating a wireless hotspot (infrastructure WPA2 Security) is required to share internet connection from a Ubuntu Machine to Android/Windows powered devices or iPhones.

Instructions:[INDENT]1. To Install the ap-hotspot script (GUI for this script is not available yet), add the following PPA:[/INDENT]
[INDENT]```
sudo add-apt-repository ppa:nilarimogard/webupd8
```
***The following command is required only if you have Ubuntu 12.04 or earlier releases:***
```
sudo add-apt-repository ppa:network-manager
```
Update the repository informations and install the "AccessPoint-Hotspot script":
```
sudo apt-get update
sudo apt-get install ap-hotspot
```
[/INDENT]
[INDENT]
2.  After the installation, either disable the firewall (if you are comfortable enough with no firewall) using gufw or firestarter, OR change the firewall rules to allow traffic for the following two services:
[/INDENT]
[INDENT=2]dnsmasq[/INDENT]
[INDENT=2]dhclient[/INDENT]
[INDENT]
3. A first time configuration can be done on Ubuntu machine by issuing the following command in the linux terminal:
```
sudo ap-hotspot configure
```
This configuration will ask for hotspot name you want to create, your LAN interface name, your WLAN interface name and the password (10 characters) etc. The interface names can be found by clicking network manager icon, and then clicking on 'information'.[/INDENT]
[INDENT]
4. Start the hotspot on Ubuntu machine:
```
sudo ap-hotspot start
```[/INDENT]
[INDENT]The hotspot is now active and ready to go. Turn the WiFi ON on your Android device/ Windows Phone/ Mac device and your device will show your 'hotspot name' that you had chosen during first time configuration (step 3). Tap on the name of hotspot to connect and enter the required password that you had set during configuration in step 3 above.[/INDENT]
[INDENT]
5. This hotspot can be stopped by using the command:
```
sudo ap-hotspot stop
```[/INDENT]

Please feel free to discuss/share your experiences/troubles....

This guide works with Ubuntu 12.10/13.04 and other derivatives of Ubuntu like Kubuntu 12.10/13.04, Xubuntu 12.10/13.04 or Zorin OS 7. Haven't checked yet on Linux Mint. 

References:
```
[http://www.ubuntuupdates.org/package/webupd8/raring/main/base/ap-hotspot](http://www.ubuntuupdates.org/package/webupd8/raring/main/base/ap-hotspot)
[http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html)
[http://forum.xda-developers.com/showthread.php?t=2009381](http://forum.xda-developers.com/showthread.php?t=2009381)
```

AN UPDATE (#1)```
**The network manager in default Kubuntu 13.10 installation has inbuilt support for Access Point mode. **
Just go to "Edit Connections" on the tray icon in the plasma desktop,
Select "Add"  then select "WiFi(Shared)" connection,
Select "WiFi tab, mode = AccessPoint",
Select "WiFi-Security tab,  Security = WPA & WPA2 Personal and give any password" and save the  connection. 
That is all, you should be done!
```

---

### Post by UrbenLegend on 2014-01-29
@sbnwl

You mentioned that Kubuntu 13.10 now has built-in support for AP mode in Network Manager. Is that also available for regular Ubuntu? I can't see the option in my Ubuntu 13.10 install.

---

### Post by sbnwl on 2014-02-10
[**[COLOR=#000000]@UrbenLegend[/COLOR]**]("http://ubuntuforums.org/member.php?u=160491")
You are right, it's not seen in Ubuntu 13.10, but Kubuntu 13.10 has this feature.

---

### Post by Adfc on 2014-02-10
Hi!
I have just followed what you wrote in this thread, but I cannot have my hotspot working. It runs but my device (smartphone with Android 4.4.2) cannot connect to the wi-fi network: it does not see it.
I have the same problem if I activate the Wireless Hotspot in Network setting, but also if I activate ap-hotspot (as described here).
Have you other suggestions?

---

### Post by sbnwl on 2014-02-16
@[**[COLOR=#000000]Adfc[/COLOR]**]("http://ubuntuforums.org/member.php?u=149471")

Your OS is Ubuntu? (12.04.x or 12.10?) I have seen some problems on Ubuntu 12.04.x LTS.

May be the hint by[**[COLOR=#000000] asus-user[/COLOR]**]("http://ubuntuforums.org/member.php?u=1347753") (see #11, on top of this page) can help.

---

### Post by markos_bravo on 2014-03-26
> I am posting this because this functionality is not available in default Ubuntu 12.10/13.04 installations. Creating a wireless hotspot (infrastructure WPA2 Security) is required to share internet connection from a Ubuntu Machine to Android/Windows powered devices or iPhones.

Instructions:[INDENT]1. To Install the ap-hotspot script (GUI for this script is not available yet), add the following PPA:[/INDENT]
[INDENT]```
sudo add-apt-repository ppa:nilarimogard/webupd8
```
***The following command is required only if you have Ubuntu 12.04 or earlier releases:***
```
sudo add-apt-repository ppa:network-manager
```
Update the repository informations and install the "AccessPoint-Hotspot script":
```
sudo apt-get update
sudo apt-get install ap-hotspot
```
[[COLOR=#ffffff]hotspot shield[/COLOR]]("http://www.hotspotshielddownloadfree.com/") 
[/INDENT]


 i'm fine tell this but the rest i can not do does there is any screen shots that help do the rest of instruction i'm not good in english 
any way thanks for your help

---

### Post by BobSands on 2014-04-02
Hi there!,
A few days ago I configured my hotspot and worked fine until a yesterday. 
Trying to connect using my Nexus 4 i just receive the message "Authentication problem", but in ubuntu, everything looks like charm: no errors.

The OS in my computer is Ubuntu 13.10, and in the phone is Android 4.4.2.

If anyone knows about some update or workaround that i can follow to see what could happen, i will really appreciate the help.
Thanks in advance.

---

### Post by gnrdeepak on 2014-04-08
Hi all,


I configured ap-hotspot as per the post. However, my android phone while connecting to the hotspot gets stuck at "Obtaining IP address". Please help!!!!!!!!!!

---

### Post by nithin-ramu on 2014-06-26
Bear with me; I am a rookie. 

How do I enable traffic for dnsmasq and dhclient using ufw? (I am running Ubuntu 14.04 LTS).

---

### Post by sbnwl on 2014-07-05
@ [**[COLOR=#000000]nithin-ramu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1931220")
Why do you need to disable them? I suppose you instead want them to be allowed through the ufw firewall. right?

---

### Post by nithin-ramu on 2014-07-17
Sorry, my bad. I meant to say how do I allow their traffic.

---

### Post by hrvojet on 2014-08-21
I can't install hotspot-app.
Lubuntu 12.10, Atheros AR9271 wifi usb adapter.
I want to share my wifi connection via same wifi card, like on win 7.
I've purchased this adapter and try several linux versions... it has been two months trying to deal with problem.
If anybody has suggestion I'll appreciate it.

```
kipa@kipa-laptop:~$ sudo add-apt-repository ppa:nilarimogard/webupd8[sudo] password for kipa: 
You are about to add the following PPA to your system:
 The main Web Upd8 PPA maintained by: http://www.webupd8.org/


To add this PPA, simply paste this in a terminal:
sudo add-apt-repository ppa:nilarimogard/webupd8


Packages in this PPA: audacious, ap-hotspot, awn-applet-radio, awn-applet-wm, calise, cmus, dockbarx, dockbarx-themes-extra, dropbox-share, emerald, exaile, fbmessenger, gnome-subtitles, gnome-window-applets, grsync, grive, gthumb, launchpad-getkeys, mc, mdm (Mint Display Manager), minitunes, minitube, musique, notifyosdconfig, nautilus-columns, powertop, ppa-purge, rosa-media-player, fixed pulseaudio-equalizer, subtitleeditor, syncwall, umplayer, unity-reboot, wimlib, youtube-dl, xfce4-dockbarx-plugin, xournal, yad and others. Almost all packages are updated to their latest version.


For other (specialized) PPAs we maintain, see: https://launchpad.net/~webupd8team
 More info: https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpgsuln4/secring.gpg' created
gpg: keyring `/tmp/tmpgsuln4/pubring.gpg' created
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpgsuln4/trustdb.gpg: trustdb created
gpg: key 4C9D234C: public key "Launchpad webupd8" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
kipa@kipa-laptop:~$ sudo apt-get update
Ign http://hr.archive.ubuntu.com quantal InRelease
Ign http://hr.archive.ubuntu.com quantal-updates InRelease                     
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://hr.archive.ubuntu.com quantal-backports InRelease                   
Ign http://ppa.launchpad.net quantal InRelease                       
Ign http://hr.archive.ubuntu.com quantal Release.gpg                 
Hit http://extras.ubuntu.com quantal Release.gpg                     
Ign http://hr.archive.ubuntu.com quantal-updates Release.gpg         
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://hr.archive.ubuntu.com quantal-backports Release.gpg                 
Hit http://extras.ubuntu.com quantal Release                                   
Ign http://hr.archive.ubuntu.com quantal Release                               
Ign http://hr.archive.ubuntu.com quantal-updates Release             
Ign http://security.ubuntu.com quantal-security InRelease            
Hit http://ppa.launchpad.net quantal Release                         
Ign http://hr.archive.ubuntu.com quantal-backports Release           
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main Sources                    
Ign http://security.ubuntu.com quantal-security Release.gpg          
Hit http://extras.ubuntu.com quantal/main i386 Packages              
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Ign http://security.ubuntu.com quantal-security Release                        
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://extras.ubuntu.com quantal/main Translation-en             
Ign http://ppa.launchpad.net quantal/main Translation-en_US          
Ign http://ppa.launchpad.net quantal/main Translation-en             
Err http://hr.archive.ubuntu.com quantal/main Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal/restricted Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal/universe Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal/multiverse Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal/main i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal/restricted i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal/universe i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal/multiverse i386 Packages
  404  Not Found
Ign http://hr.archive.ubuntu.com quantal/main Translation-en_US
Ign http://hr.archive.ubuntu.com quantal/main Translation-en
Ign http://hr.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://hr.archive.ubuntu.com quantal/multiverse Translation-en
Ign http://hr.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://hr.archive.ubuntu.com quantal/restricted Translation-en
Ign http://hr.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://hr.archive.ubuntu.com quantal/universe Translation-en
Err http://hr.archive.ubuntu.com quantal-updates/main Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-updates/restricted Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-updates/universe Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-updates/multiverse Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-updates/main i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-updates/restricted i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-updates/universe i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-updates/multiverse i386 Packages
  404  Not Found
Ign http://hr.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-updates/main Translation-en
Ign http://hr.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://hr.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://hr.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-updates/universe Translation-en
Err http://hr.archive.ubuntu.com quantal-backports/main Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-backports/restricted Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-backports/universe Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-backports/multiverse Sources
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-backports/main i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-backports/restricted i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-backports/universe i386 Packages
  404  Not Found
Err http://hr.archive.ubuntu.com quantal-backports/multiverse i386 Packages
  404  Not Found
Ign http://hr.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-backports/main Translation-en
Ign http://hr.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-backports/multiverse Translation-en
Ign http://hr.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://hr.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://hr.archive.ubuntu.com quantal-backports/universe Translation-en
Err http://security.ubuntu.com quantal-security/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com quantal-security/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com quantal-security/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err http://security.ubuntu.com quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Ign http://security.ubuntu.com quantal-security/main Translation-en
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en
W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://hr.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
kipa@kipa-laptop:~$ sudo apt-get install ap-hotspot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ap-hotspot : Depends: hostapd but it is not installable
              Depends: dnsmasq but it is not installable
              Depends: iw but it is not installable
E: Unable to correct problems, you have held broken packages.
kipa@kipa-laptop:~$ 



```

---

### Post by sbnwl on 2014-08-23
@[**[COLOR=#000000]hrvojet[/COLOR]**]("http://ubuntuforums.org/member.php?u=1937028")You are struggling with an unsupported Ubuntu release (12.10) which is nearly 2 years old. Starting from Ubuntu 13.04, sharing internet connection over WIFI is very well supported.
Could you upgrade to Ubuntu/Lubuntu 14.04? If it is not possible, then try installing Ubuntu/Lubuntu 14.04 and you will be easy going with WIFI sharing...

---

### Post by hrvojet on 2014-08-23
Are You shoure about Lubuntu 14.04?
I had 14.04 which has some issues with hostapd and moved to 12.10.
On Ubuntu (tried 12.04, 14.04) versions my laptop is to slow.
I can try with 13.10 if thats gone solve problem, but I want to know first why do I get errors above.

---

### Post by sbnwl on 2014-08-24
@[**[COLOR=#000000]hrvojet[/COLOR]**]("http://ubuntuforums.org/member.php?u=1937028")
```
I can try with 13.10 if thats gone solve problem, but I want to know first why do I get errors above.
```

Unsupported distributions' repositiories are no longer maintained. So the package you are looking for might be removed from that repository.


I insist you go for Kubuntu 14.04 (if your machine could afford it), where you are no longer required to do this ap-hotspot installation thing. The sharing facility is inbuilt in the distro. Check the first revision of this post..

---

### Post by hrvojet on 2014-08-24
I have IBM ThinkPad R40e celeron 1.8 upgraded to 1gb ram. It's really slow and unusable on Ubuntu 14.04. (12.04 little better but still slow).
My intention was to use this laptop only as hotspot, no other purpose.

---

### Post by praseodym on 2014-08-24
Chose Lubuntu instead or install the package "lxde"

---

### Post by hrvojet on 2014-08-24
OK. I've just installed lubuntu 14.04.
What next?

---

### Post by sbnwl on 2014-08-30
@[**[COLOR=#000000]hrvojet[/COLOR]**]("http://ubuntuforums.org/member.php?u=1937028")

```
If you installed Lubuntu 14.04 then follow instructions on the very first page of this post.
``` It should be easy...

You plan to install Kubuntu 14.04 ? Then what to wait for? Follow the instructions to make a hotspot....
For your convenience:

```
Just click on "Network icon" in the tray in the plasma desktop,
Click on the "gear button" on the top right corner in the popup window,
A new window will open now. 

In the new window:
Select "Add"  then select "Wireless(Shared)" connection,
Select "WiFi tab, mode = AccessPoint",
Select "WiFi-Security tab,  Security = WPA & WPA2 Personal and give any password" and save the  connection. 
That is all, you should be done!
```

---

### Post by hrvojet on 2014-09-03
I 've done that. 
I have create hotspot and my Samsung S3 can connect to it but with no traffic.
I am trying to share my WiFi access because I dont bave wired internet.

edit:
Solved the issue. I've cloned MAC from second addapter...

---

### Post by kajsa2 on 2015-02-15
I am using Xubuntu 14.10 and have followed the original post.
Every thing seams to be working as it should but when I type
```
sudo ap-hotspot start
```
I get this
```
Starting Wireless Hotspot...

```
Then nothing happens. The hotspot does not start and the terminal is busy with this and never finishes.

The post by @sbnwl does not apply since the option "wireless(shared)" is not present.

What am I doing wrong?

[B]Edit:
[/B]Found a solution on this link: [http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html)

---

### Post by Tiwo on 2015-04-14
've easy other tutorial to share internet from Linux to Android. Here the tutorial [http://unixsquad.blogspot.com/2015/04/create-hotspot-on-linux-and-share.html](http://unixsquad.blogspot.com/2015/04/create-hotspot-on-linux-and-share.html)

---

### Post by vasa1 on 2016-04-08
Just bumping this to keep it from being automatically closed. I hope [sbnwl]("http://ubuntuforums.org/member.php?u=1425968") will revisit this thread once 16.04 is released.

---

