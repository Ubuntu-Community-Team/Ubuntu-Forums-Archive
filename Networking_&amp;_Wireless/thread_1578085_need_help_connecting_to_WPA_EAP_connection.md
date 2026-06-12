---
title: "need help connecting to WPA EAP connection"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by kyo_udon on 2010-09-19
Its my first time using Ubuntu. I'm using Ubuntu 10.04 currently.
Using Network Manager thats preinstalled i'm able to connect both my home wlan and my universitat wlan. But there is a stability problem when connecting to uni wlan which is using WPA EAP security, under the guide on how to connect to uni wlan, they mention there will be stability problem when i'm using Network Manager and yeah i keep disconnected every 2-5 min.

the guide state that using wpa_supplicant will be stable. but i'm havin problem on how to install them.
the following are all the steps in the guide :
1.install wpasupplicant with
   a. apt-get wpasupplicant
   b. rpm wpa_supplicant.rpm or
   c. download the tar file, extract and ./configure, make and make install
2. look for wpa_supplicant.conf (usually in /etc)
    and paste this
ctrl_interface=/var/run/wpa_supplicant 
fast_reauth=0 network={
	ssid="Uni-ID"
	key_mgmt=WPA-EAP
	proto=RSN
	pairwise=CCMP
	group=TKIP
	eap=PEAP
	phase2="auth=MSCHAPV2"
	identity="Username"
	password="Password"
	ca_cert="/etc/ssl/certs/deutsche-telekom-root-ca-2.pem"
}
start wpa_supplicant with

wpa_supplicant -BW -c/etc/wpa_supplicant.conf -i<WLAN-Interface-Name>
Done

just to clear things up, what is my wlan interface name? is it wlan0 (first question)
but i when i tried to install them :
xxxxxxxxxxlaptop:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wpasupplicant is already the newest version.
The following packages were automatically installed and are no longer required:
  python-psyco python-gtkmozembed python-pysqlite2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

am i to understand that wpa_supplicant is also preinstalled? i can certainly find wpa_supplicant folder under /etc, when i look in Software Centre wpa_supplicant 0.6.9 is indeed already installed.
but wpa_supplicant.conf is nowhere to be found inside /etc and inside /etc/wpa_supplicant there is only 3 file which r : action_wpa.sh  function.sh  ifupdown.sh

I then download [wpa_supplicant-0.7.3.tar.gz]("http://hostap.epitest.fi/releases/wpa_supplicant-0.7.3.tar.gz") but i cant seem to install them either
i manage to extract it to home directory but when i type ./configure this is what i get:

xxxxxxxxxxxxxxlaptop:~$ ./configure
bash: ./configure: No such file or directory

well i'm pretty stuck right now. So i thought i might mention it here.
Any help is appreciated. Hope its easy to understand

---

