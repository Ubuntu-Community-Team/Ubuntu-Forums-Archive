---
title: "lost! netgear wg311v2 breeze 5.10"
date: 2006-03-06
forum: Networking &amp; Wireless
---

### Post by tempo500 on 2006-03-06
i have been using this system now for a month and i really like it (coming from windows) the last unresolved thing is the wireless.... the wireless icon showed up in the network tool(for time being i am also conected to the router with a cable) but dissapeard after fiddling around because i could not connect to the router. so... where should i start?
1- right now there is no wireless icon in the network gui
2- ndiswrapper -l sayeswg311v2 is invalid.
3- sudo iwconfig doesnt find the wlan0 device any more

i really could use some help... my time is running out because i have to finish some graphics and i would really like to spare me and my office pc a windows system just because of the wlan!

---

### Post by mavr on 2006-03-06
I've been having trouble with this sorta stuff too. First of all check that your ndiswrapper-utyls packet is installed. If u are on Gnome there is a graphical tool as well. Then i will try to remove the driver e install it again. When your ndiswrapper is telling you that hardware and drivrer are working, you'd better have a look at your /etc/network/interfaces and take everything about the wlan0 off. You'd better config it from the gui.

---

### Post by tempo500 on 2006-03-06
ok, so i should go with the ndiswrapper driver?
ndiswrapper utils 1.1-4 and gtk 0.5-1 are installed. 
1- shouldnt my wireless be showing up in the network settings dialog? i rebooted and the entry came up again - activated and turned the wep off for now.
2- which wg311ver2.inf should i install? i have the origcd + downloaded 1.00.10 and 2.0 windows zip files -i just managed to install the drivers from the original cd. the downloaded 1.0 and 2.0 dont install. ndiswrapper -l tells me that the drivers are invalid
so... if i say sudo ndiswrapper -i wg311v2.inf it tells me that they are allready installed
if i say sudo ndiswrapper -e wg311v2.inf it tells me that they are not installed...

i tryed this [guide]("http://www.ubuntuforums.org/showthread.php?t=45876&highlight=wg311+v2") but unfortunally i get stuck installing the inf files. trying this through the gui lets me install the orig drivers but says: hardware preset no

im now really stuck, dont let me switch to windows again! ahh

---

### Post by tempo500 on 2006-03-10
hi, back again.
got the ndiswrapper with the netgear wg311v2 working tryed all driver versions - all seem to work-driver present, hardware present (info from ndiswrapper -l)
iw config
wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:58/100  Signal level:42/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

so i guess my problem is the acces point?
is this still the native ubuntu driver acx? tryed this [guide]("http://www.ubuntuforums.org/showthread.php?t=45876&highlight=wg311+v2") when i execute this: sudo rmmod acx-pci ubuntu deletes my wlan0 device and iwconfig fails to get the cards info.
i checked with a windows machine if my static ip, mask and gateway are correct.i am using wep, 64bit

iwlist encryption
wlan0     3 key sizes : 40, 104, 232bits
          4 keys available :
                [1]: off
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [0]

that doesnt look good?! i could use any help! please, p

ps: my interfaces file

auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map eth0

iface wlan0 inet static
wireless-mode managed
wireless-essid wirework
wireless-channel 1
wireless-key 59A5D20D4B
wireless-defaultkey 1
wireless-keymode open
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.255

iface eth1 inet static
address 192.168.0.2
netmask 255.255.255.0

auto eth1
iface eth0 inet dhcp
auto wlan0
auto eth0

---

