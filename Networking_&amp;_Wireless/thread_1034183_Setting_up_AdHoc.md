---
title: "Setting up AdHoc"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by Rolcol on 2009-01-08
I've read and tried both the Network Manager and Terminal approach mentioned here:  [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc).  I could not get my laptop to create and connect to a new AdHoc connection.  I tried connecting to one created in a Windows Laptop and that didn't work.  I'm running Ubuntu 8.10 Intrepid Ibex.

My Network Card:  02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

I really need this to work for tomorrow.

---

### Post by mag_dex on 2009-01-08
what's a problem? Give more information.
Give result of commands: ifconfig and iwconfig.

You can try install WICD [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/).
It has a nice feature to do Ad-hoc network. 
It's graphical program and it can really help you in easy way to set up ad-hoc network.

for me following code works:

sudo modprobe -r ath_pci
sudo modprobe ath_pci autocreate=adhoc
sudo iwconfig ath0 essid eXtremeNet channel 11 key off mode ad-hoc
sudo ifconfig ath0 192.168.0.1

I don't set any key!

---

### Post by Rolcol on 2009-01-08
> **mag_dex said:**
> what's a problem? Give more information.
Give result of commands: ifconfig and iwconfig.

You can try install WICD [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/).
It has a nice feature to do Ad-hoc network. 
It's graphical program and it can really help you in easy way to set up ad-hoc network.

for me following code works:

sudo modprobe -r ath_pci
sudo modprobe ath_pci autocreate=adhoc
sudo iwconfig ath0 essid eXtremeNet channel 11 key off mode ad-hoc
sudo ifconfig ath0 192.168.0.1

I don't set any key!

I installed WICD and it didn't help much.  I'm actually trying to get a windows computer to connect to my ad-hoc network so windows can connect to an IRC server on my laptop.  I ran your command and windows can see the adhoc network but cannot connect.  WICD "creates" the adhoc connection but windows can never see it.

Edit:  It'd be ok to create the ad-hoc network on windows and then allow me to connect to it but WICD just gets stuck at "Obtaining IP Address".

Edit2:  The AdHoc connection to Windows eventually dies and doesn't connect any more.  It's just like it was with the network-manager.  Am I missing any packages?

---

### Post by mag_dex on 2009-01-08
WICD is trying to get IP (and so on) from Windows. I guess you don't have installed DHCP server on this windows machine.

Run ifconfig and iwcofing and paste outputs here
It should help.

run:
sudo iwlist scan
find you ad-hoc network from your windows, like:
                    ESSID:"dlink"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
and then in terminal run:
sudo iwconfig essid YOUR_NETWORK channel YOUR_CHANEL
and set up you ip on ubuntu:
sudo ifconfig ath0 192.169.0.2

---

### Post by Rolcol on 2009-01-08
> **mag_dex said:**
> WICD is trying to get IP (and so on) from Windows. I guess you don't have installed DHCP server on this windows machine.

Run ifconfig and iwcofing and paste outputs here
It should help.

run:
sudo iwlist scan
find you ad-hoc network from your windows, like:
                    ESSID:"dlink"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
and then in terminal run:
sudo iwconfig essid YOUR_NETWORK channel YOUR_CHANEL
and set up you ip on ubuntu:
sudo ifconfig ath0 192.169.0.2
[noparse]
Thanks for your help but it's not working for me.

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:39:6a:7c  
          inet addr:10.0.10.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::219:d2ff:fe39:6a7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:284972 (284.9 KB)  TX bytes:114124 (114.1 KB)

iwconfig:
wlan0     IEEE 802.11abg  ESSID:"gash"  
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: 02:16:EA:01:B0:44   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


gash was the test network I tried connecting to.  Ubuntu shows that it's connected but Windows keeps going from one to another saying that I am connected but then that I disconnect.[/noparse]

---

### Post by mag_dex on 2009-01-09
You have to set up the ip for wlan0

sudo ifconfig wlan0 192.168.0.1
sudo ifconfig wlan0 up

on windows machine you should set up following settings:
ip: 192.168.0.2
netmask: 255.255.255.0

It should work :)

---

### Post by Rolcol on 2009-01-09
I'll try again.  Thanks for putting up with me.  I wanted it for yesterday but the guy I planned the activity with ended up forgetting.  He'll be bringing his computer on Monday.  I'll get it to work over the weekend.

---

