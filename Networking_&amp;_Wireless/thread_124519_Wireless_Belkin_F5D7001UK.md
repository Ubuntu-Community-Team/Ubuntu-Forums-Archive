---
title: "Wireless Belkin F5D7001UK"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by lexor on 2006-02-01
I need some help on checking how I have my Wireless Nic setup,I downloaded and installed all these after reading afew threads on the forum.

sudo apt-get install ndiswrapper-utils
sudo apt-get install ndisgtk
sudo apt-get install wireless-tools
sudo apt-get install wpasupplicant

I started up ndisgtk the gui for ndiswrapper and installed the bcmwl5.inf from dell.I then ran: "sudo gedit /etc/wpa_supplicant.conf" and put in all this.

> 
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

#eapol_version=1
#ap_scan=1
#fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
       ssid="mysid"
       psk=******************
}


Next I Did: "sudo gedit /etc/default/wpasupplicant" and put in all this.

> 
# /etc/default/wpasupplicant
# WARNING! Make sure you have a configuration file!
# Useful flags:
#  -D <driver>		Wireless drive, typically optional.
#  -i <ifname>		Interface
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up
# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-w"
ENABLED=1
OPTIONS="-iwlan0 -Dndiswrapper -c/etc/wpa_supplicant.conf"


Next I Did: "sudo gedit /etc/network/interfaces" and put in all this.I took out eth0 casue I dont need it anymore.

> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

auto wlan0
iface wlan0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1


On the wireless network icon I am getting 100% but I read thats a bug but the performance is good. The wireless card is 802.11g but acorrding to sudo iwlist rate its only doing 18Mb/s.

> 
***@***:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"******"
          Mode:Managed  Frequency:2.447 GHz  Access Point: ***************
          Bit Rate:18 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:********************************
          Power Management:off
          Link Quality:94/100  Signal level:-77 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:808  Invalid misc:5090   Missed beacon:0

sit0      no wireless extensions.




> 
***@***:~$ sudo iwlist wlan0 bitrate
wlan0     8 available bit-rates :
          6 Mb/s
          9 Mb/s
          12 Mb/s
          18 Mb/s
          42 Mb/s
          49.5 Mb/s
          25 Mb/s
          500 kb/s
          Current Bit Rate=18 Mb/s



Can I change the settings to 802.11g and not 802.11b to get a higher speed? I am in the UK and I  use channel 8, Can I set the card to use channel 8 as well.

Is there anything I need to change to config the card better, I cant get NTP on boot but I did with my Wired NIC.

---

