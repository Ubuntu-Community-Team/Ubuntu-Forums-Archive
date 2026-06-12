---
title: "Wireless Hotspot"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by promach on 2013-03-13
Hi, I have followed the instructions on [http://thenewbieblog.wordpress.com/2012/05/01/wifi-hotspot-setup-on-ubuntu/](http://thenewbieblog.wordpress.com/2012/05/01/wifi-hotspot-setup-on-ubuntu/) 

But [COLOR=#404040][FONT=Helvetica Neue]I cannot even detect the hotspot from another laptop.[/FONT][/COLOR]
[COLOR=#404040][FONT=Helvetica Neue]WHY ?[/FONT][/COLOR]

the following is from "tail /var/log/syslog"
[COLOR=#404040][FONT=Helvetica Neue]Mar 13 15:09:13 dell rtkit-daemon[1585]: Supervising 6 threads of 2 processes of 2 users.
Mar 13 15:09:15 dell ntpdate[1669]: adjust time server 91.189.94.4 offset 0.340063 sec
Mar 13 15:09:24 dell NetworkManager[849]: (wlan0): IP6 addrconf timed out or failed.
Mar 13 15:09:24 dell NetworkManager[849]: Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled&#8230;
Mar 13 15:09:24 dell NetworkManager[849]: Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started&#8230;
Mar 13 15:09:24 dell NetworkManager[849]: Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 13 15:09:26 dell goa[1965]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Mar 13 15:09:27 dell kernel: [ 46.168993] audit_printk_skb: 39 callbacks suppressed
Mar 13 15:09:27 dell kernel: [ 46.169000] type=1400 audit(1363158567.011:25): apparmor=&#8221;DENIED&#8221; operation=&#8221;open&#8221; parent=1 profile=&#8221;/usr/lib/telepathy/mission-control-5&#8243; name=&#8221;/usr/share/gvfs/remote-volume-monitors/&#8221; pid=1960 comm=&#8221;mission-control&#8221; requested_mask=&#8221;r&#8221; denied_mask=&#8221;r&#8221; fsuid=1000 ouid=0
Mar 13 15:09:56 dell avahi-daemon[682]: Invalid response packet from host fe80::2a6a:baff:fe77:5460.[/FONT][/COLOR]
[COLOR=#404040][FONT=Helvetica Neue]

dell@dell:~$ sudo hostapd -dd /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
nl80211: Register Action command failed: ret=-114 (Operation already in progress)
nl80211: Register Action match &#8211; hexdump(len=1): 06
nl80211: Failed to register Action frame processing &#8211; ignore for now
nl80211: Add own interface ifindex 3
nl80211: Failed to set interface 3 to mode 3: -95 (Operation not supported)
nl80211: Failed to set interface 3 to mode 3: -95 (Operation not supported)
nl80211: Interface mode change to 3 from 0 failed
nl80211: Failed to set interface wlan0 into AP mode
nl80211 driver initialization failed.
ELOOP: remaining socket: sock=4 eloop_data=0x96cc900 user_data=0x96ccea0 handler=0x807c5e0
ELOOP: remaining socket: sock=6 eloop_data=0x96ceca8 user_data=(nil) handler=0×8086770
dell@dell:~$ cat /etc/hostapd/hostapd.conf
interface=wlan0
driver=nl80211
ssid=my_hotspot
channel=1
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

Any help?
[/FONT][/COLOR]

---

