---
title: "kismet - no capture"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by meastwood on 2009-01-29
using 8.04 LTS, RaLinK usb RT73

Kismet server starts, no complaints.

wireless interface in monitor mode, up and not associated. Wireless router on and therefore sending beacon frames - nothing is captured.

Kismet server causes segmentation fault when exiting...

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Disabling channel splitting.
Source 0 (addme): Enabling monitor mode for rt73 source interface wlan0 channel 6...
Source 0 (addme): Opening rt73 source interface wlan0...
Will attempt to put networkmanager to sleep...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
Logging networks to /var/log/kismet/Kismet-Jan-29-2009-6.network
Logging networks in CSV format to /var/log/kismet/Kismet-Jan-29-2009-6.csv
Logging networks in XML format to /var/log/kismet/Kismet-Jan-29-2009-6.xml
Logging cryptographically weak packets to /var/log/kismet/Kismet-Jan-29-2009-6.weak
Logging cisco product information to /var/log/kismet/Kismet-Jan-29-2009-6.cisco
Logging data to /var/log/kismet/Kismet-Jan-29-2009-6.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Using network-classifier based data encryption detection
Gathering packets...
Launching kismet_client: //usr/bin/kismet_client
Looking for startup info from localhost:2501....Launched client, pid 6252
. found.
Connected to Kismet server 2007.10.R1 on localhost:2501
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Segmentation fault

anyone any ideas?

*** have just been on the kismet forum - the advice there is to update my driver.  By this I take it they mean the RT73 driver however on this system I'm using the ubuntu generic wext driver.  

Does anyone have kismet working with wext? if so what version of the driver are they using and what <sourcetype> entry do you use in kismet.conf?

Does wext support monitor/rfmon mode for RaLink chips?
cheers.

*** sorted'ish
for my set up - kismet will not capture if using wext. A pity as I've had no problems with wext - but I also want to use Kismet.  If you are in a similar position the following has worked for me but is far from ideal ...... and for the more knowledgeable probably dodgy!!

1. used the latest rt73 driver (rt73-cvs-daily.tar.gz from the seamonkey project)
built it
installed it

2. build in support for rt73 into wpa_supplicant 
(a) Need to build openssl first. I used same version as on 8.0.4 LTS (openssl-0.9.8g.tar.gz). wpa_supplicant failed to build with the 'pre-installed' openssl along with  the source-dev package. So got the source from the openssl project and just built it. (I did NOT install it)  

(b) For wpa_supplicant - used same version as 8.0.4 LTS (wpa_supplicant-0.5.8.tar.gz)
Modified .config to point to newly built (but not installed) openssl libraries and source.

To build in support for rt73 need the driver source and header files - the seamonkey source did not come with instructions or code for modifying wpa_supplicant.

I used the link from ubuntu docs to get RT73_Linux_STA_Drv1.0.4.0.tar.gz (I did NOT build this driver). Followed the instructions in the archives WPA_Supplicant  subdirectory copying just the the driver_ralink.c and .h files to the wpa_supplicant build directory. Carried out all changes to wpa_supplicant build files manually (as opposed to copying RaLink supplied versions)
built it
installed it

3. using
(a) for normal connection/use to wpa2 enabled AP -
(i) manual
# ifconfig wlan0 up
# wpa_supplicant -i wlan0 -D ralink -c <conf file> -Bw
# dhclient wlan0

or 

(ii) automated (it does work!!)
in /etc/network/interfaces
================
iface wlan0 inet dhcp
	wpa-conf /etc/wpa_supplicant.conf
	wpa-driver ralink
auto wlan0
================
in /etc/wpa_supplicant.conf
================
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2      ### needed this else it will take an age when BSSID is hidden, with it set it is as good/quick as wext

network={
	ssid="MINE-KEEP-OUT"
	key_mgmt=WPA-PSK
	proto=WPA2
	scan_ssid=1		### need this for hidden BSSID
	pairwise=CCMP		
	group=CCMP			
	psk=<pass key>
}
================

(b) kismet
in /etc/kismet/kismet.conf
================
source=rt73,wlan0,RaLink
enablesources=RaLink
================
# ifconfig wlan0 up
# kismet

*** kismet still causes a segmentation fault on exit and fails to switch off monitoring mode =>
# ifconfig wlan0 -promisc 
# iwconfig wlan0 mode managed (especially after using kismet, if device is reported as busy, take it down and run this before bringing back up)
.......

---

