---
title: "Wireless Netgear WG511 Marvell Chipset - How To"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by philrosenberg on 2010-08-13
I recently bought the above PCMCIA because it was the only wireless card available in a popular electronics store here in the UK. It took me a long time to get it installed and I saw a large number of other people asking about this card with no real answer. I was installing on Jaunty Server and there was no native driver so I needed the windows driver. Unfortunately the files required were not available from the CD or the netgear website - they were encapsulated in the installation files. I couldn't extract them by installing on a windows machine because I don't have a Windows laptop with a PCMCIA. The breakthrough came when I realised the WG311 had an identical chipset so I used the driver for this card available from the Netgear webpage. Anyway a full How-to is below. Hope it is of use to someone else
 
1) Install wireless-tools, ndiswrapper and dhcpcd if you don't already have them
```
sudo apt-get install wireless-tools
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9
sudo apt-get install dhcpcd
```
2) Check your card chipset
```
lspci | grep wireless
```
It should say it is an ethernet controller by Marvell Technology Group Ltd
3) Use the number at the start of this line to check the chipset id. In my case the number was 06:00.0. 
```
lspci -n | grep 06:00.0
```
This line should include the chipset id 11ab:1faa. If not then you haven't got the card being described in this tutorial so you need to find a driver for your card, you can stop reading now, or read on for your own interest.
4) Download the WG311 driver. This card uses the 11ab:1faa chipset also. The driver can be found at [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)
5) open the zip file and extract the files from driver/windows xp to any folder.
6) cd to the folders with the drivers in
```
cd /folder/with/extracted/drivers
```
8) install the driver using ndiswrapper
```
sudo ndiswrapper -i WG311v3.INF
```
9) Check driver was installed
```
ndiswrapper -l
```
You should get an output which states that the driver is installed. If you get a warning about the blacklist then you seem to be able to ignore this.
10) Start ndiswrapper
```
sudo modprobe ndiswrapper
```
11) You should now be able to run iwconfig and see the default connection setup for your card. Note down the connection name. In my case wlan1.
```
sudo iwconfig
```
12)search for available networks
```
sudo iwlist scan
```
13)Use iwconfig to set up your connection. The details below assume a WEP encrypted open network using managed mode and a connection id of wlan1. Change as needed. Search for iwconfig for more details
```

sudo /etc/init.d/networking stop
sudo ifconfig wlan1 down
sudo iwconfig wlan1 key open s:abcdefghijklm
sudo iwconfig wlan1 mode Managed
sudo iwconfig wlan1 essid "My network name"

```
14) Check the details are correct
```
sudo iwconfig
```
15) Connect to the network. If you are using dhcp then you can do (changing wlan1 for you connection id)
```
sudo ifconfig wlan1 up
sudo dhcpcd wlan1
```
16) if all has gone well then you will probably want the wireless card to load on startup. Use your favourite text editor to open /etc/modules and append 
```
ndiswrapper
```
17) Usually you would edit /etc/network/interfaces file to connect to your preferred network on startup - search the web for details. I found that this did not work for me (problem with dhcp client?). So I wrote a script to do this (many thanks to Axel for this) using dhcpcd. The script simply included the code from steps 13 and 15. Put the script in /ect/init.d I will assume it is called wirelessconnect.sh. Ensure the script is executable and set it to run on startup
```
chmod +x /etc/init.d/wirelessconnect.sh
sudo update-rc.d wirelessconnect.sh defaults
```
18) Reboot to check the script is working as expected.
 
That's it. Hope this has been useful
 
Phil

---

### Post by darrask on 2011-05-22
Thank you so much!

---

