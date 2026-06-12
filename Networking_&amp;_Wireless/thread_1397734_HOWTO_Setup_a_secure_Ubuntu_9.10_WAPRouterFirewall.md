---
title: "HOWTO: Setup a secure Ubuntu 9.10 WAP/Router/Firewall"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by imrazor on 2010-02-03
HOWTO: Setup a secure Ubuntu 9.10 WAP/Router/Firewall

My wireless router wasn't cutting it, so I decided to build my own Linux WAP/DSL router out of spare parts. I went down many dead ends, and hope to save others the trouble.

For hardware, we'll need the following:

1) PC with Intel/AMD x86 processor
2) Standard Ethernet card supported natively by Ubuntu 9.10
3) Wireless NIC supported by the mac80211 network stack (bcm4318 in my case)
4) At least a 10GB hard drive

Notes: iwconfig is not your friend for this job. It will not work properly with the new b43 driver. Instead, use the 'iw' command if you want to verify something.

Software installation and configuration goes as follows:

1) Install Ubuntu 9.10 32-bit Desktop (Server may be a better choice)

2) Enable optional Ubuntu repositories from Administration>Software Sources
    (I enabled everything but the Source CODE repo)

3) (Broadcom WLAN NIC only) Install b43-fwcutter for Broadcom firmware cutter. Most cards will be supported by the included firmware, but you may need to manually extract the firmware from the Broadcom Windows driver for legal or compatibility reasons. ```
bash> sudo apt-get install b43-fwcutter
```4) (Broadcom WLAN NIC only) Disable QoS support for the b43 kernel module by adding the following line to the end of /etc/modules:```
b43 qos=0
```This step may not be necessary with chipsets other than bcm4318, but I couldn't get a stable connection without that setting.

5) Uninstall NetworkManager. ```
bash> sudo apt-get remove NetworkManager
``` NetworkManager is a handy tool for a laptop, but will interfere with a running access point.

6) Set static IP addresses for the Ethernet and wireless adapters in /etc/network/interfaces. The snippet below assumes that the Ethernet adapter we will be connecting to our DSL modem/router is eth0, and the wireless adapter is wlan0.```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    broadcast 192.168.0.255

auto eth0
iface eth0 inet static
    address 192.168.1.1
    netmask 255.255.255.0
    broadcast 192.168.1.255
``` Reboot once the changes are made, and check that the adapters are up with ifconfig. The parameters for eth0 will change once we set up the DSL connection.

7) Install hostapd.```
bash> sudo apt-get install hostapd
```8) Configure hostapd. This can be complicated, but the main idea at this point is to set the SSID (ie, network name) for our wireless network and to tell hostapd which interface, IP address and driver to use. Look for the lines below and set them as follows.```
driver=nl80211
ssid=<your network name>
hw_mode=g
channel=6
``` The Broadcom and optionally Atheros adapters use the nl80211 driver. For other drivers/devices, see the comments in hostapd.conf. hw_mode can be either g or b for older adapters. 802.11n configuration is beyond the scope of this HOWTO. Channel 6 is a standard wireless channel that should be valid in most countries.

9) Reboot your PC and test with a laptop or other wireless device to see if you can associate with your SSID and ping the access point. Always reboot after changing hostapd.conf or your results may be unpredictable.

10) Enable WPA1/2 in hostapd.conf. Look for the following lines in /etc/hostapd/hostapd.conf, uncomment if necessary and set as follows:```
wpa=3
wpa_passphrase=<your network password>
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
auth_algs=1
eapol_version=1
``` This enables WPA & WPA 2 and turns on WPA-PSK (personal shared key) authentication. eapol_version=1 I found to be necessary if connecting OS X clients.

11) Reboot and test your new config with a wireless device. Make sure that it accepts your WPA passphrase and you can ping the access point.

12) Now that wireless is working, we need to set up the DSL connection. First we need to install and enable ufw. ```
bash> sudo install apt-get ufw
bash> sudo ufw enable
``` If it's already installed and enabled, that's fine.

13) Now we need to turn on packet forwarding. Edit the following line in /etc/default/ufw:```
DEFAULT_FORWARD_POLICY="ACCEPT"
``` You then need to edit /etc/ufw/sysctl.conf as follows:```
net.ipv4.ip_forward=1
```Finally we need add these lines to the top of /etc/ufw/before.rules, just after the header comments:```
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from wlan0 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT
```Then disable and re-enable ufw:```
bash> sudo ufw disable
bash> sudo ufw enable
``` Important note: We'll need to come back in a few steps and change "eth0" above to "ppp0".

14) Next, we'll need to install pppoeconf. ```
bash> sudo apt-get install pppoeconf
```15) Next you'll need to plug in your Ethernet card into the DSL modem/router and actually run pppoeconf. For this step, you'll need to know your DSL PPPoE username and password. Contact your ISP if you don't have this info. Run ```
bash> sudo pppoeconf
``` pppoeconf will try to autodetect your network config. Make sure to point it at eth0 (or whatever device name your Ethernet NIC has), NOT wlan0. Once complete, your /etc/network/interfaces file should look something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
    address 192.168.0.1
    netmask 255.255.255.0
    broadcast 192.168.0.255

auto eth0
iface eth0 inet manual
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
``` Verify that your PPPoE connection is up by checking ifconfig ppp0; you should see a number other than 192.xx.xx.xx or 169.xx.xx.xx. Finally, launch a web browser to make sure you can get on the Internet. You may have to set your DNS servers manually in /etc/resolv.conf.

16) Now we need to change /etc/ufw/before.rules to match our new ppp0 interface. Edit the following lines:```
# Forward traffic from wlan0 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
``` to read as follows:```
# Forward traffic from wlan0 through ppp0.
-A POSTROUTING -s 192.168.0.0/24 -o ppp0 -j MASQUERADE
```

That should do it. If you're running network games or torrent clients behind your firewall, you'll want to set up some rules for ufw. However, that's beyond the scope of this HOWTO.

---

### Post by laluz on 2010-04-29
Hi there, 
just to let people about my experience: I have bought a D-Link DWL 520 card with AR5001X+ Atheros Chipset. The only thing I had to do to set up an access point was to click on the network icon in the Ubuntu(Gnome) desktop panel and "create new wireless network"
The routing to the existing dsl(eth0) connection was also set up automatically. So I could immediately start surfing on the windows laptop connected to the new wireless network.
Karmic is working better than I expected. I am really happy so far.

---

