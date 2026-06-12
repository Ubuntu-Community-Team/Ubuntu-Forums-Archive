---
title: "ra0 ra3070sta works with NetworkManager but not with iwconfig"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by linuxculo on 2010-06-02
I have a tenda W311u wireless with a ra3070sta chipset, i read a lot of tutorials to get it working. I recently had my wireless working but just in NetworkManager. I need to get working in console mode,
for example when i make a:

**sudo iwconfig** ra0 essid azcor key XXX3240251 
**sudo iwconfig**
ra0       Ralink STA  ESSID:"ryt"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=100/100  Signal level:-33 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
note: The Essid the same i added in the RT2870sta.dat file.

And therefore if i try a **dhclient3 ra0 **no dhcp offers received.
Listening on LPF/ra0/c8:3a:35:c3:3f:88
Sending on   LPF/ra0/c8:3a:35:c3:3f:88
Sending on   Socket/fallback
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPREQUEST on ra0 to 255.255.255.255 port 67
...
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.

Rare, but if i start NetworkManager connected to azcor, and i make a **dhclient3 ra0** i get an ip very fast.

i try with cnetworkmanager but is complicated and isn´t working for me! =(

---

### Post by chili555 on 2010-06-02
Network Manager is to tightly entwined in our systems that it's very difficult, and sometimes impossible to get manual methods to work. You might try:```
sudo /etc/init.d/network-manager stop
```If that doesn't work, you may need to remove NM entirely and populate /etc/network/interfaces.

---

### Post by linuxculo on 2010-06-02
I dont belive that NetworkManager is the problem because i hava another pc without NetworkManager (just console) and the results are the same i cant configure the wireless with [B]iwconfig
Nor [/B]/etc/network/interfaces work i give me a no dhcp offers

---

### Post by chili555 on 2010-06-02
> i hava another pc without NetworkManager (just console) and the results are the same i cant configure the wireless with iwconfig
Nor /etc/network/interfaces work i give me a no dhcp offers
If you'd care to troubleshoot, please post:```
ps aux | grep -i network
cat /etc/network/interfaces
```Thanks.

---

### Post by linuxculo on 2010-06-02
jlmunix@Tecolote:~$ ps aux | grep -i network
root      2117  0.0  0.1  82552  4488 ?        Ssl  12:18   0:00 /usr/sbin/NetworkManager
root      2130  0.0  0.0   6304   956 ?        S    12:18   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-681b428f-beaf-8932-dce4-687ed5bae28e-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0

allow-hotplug eth0
iface eth0 inet dhcp
#auto ra0
#iface ra0 inet dhcp

---

### Post by chili555 on 2010-06-02
> $ ps aux | grep -i network
root 2117 0.0 0.1 82552 4488 ? Ssl 12:18 0:00 /usr/sbin/[COLOR="Red"]NetworkManager[/COLOR]As you can see, Network Manager is running and your entries in /etc/network/interfaces are commented out, making them ineffective.

Can you confirm that these are from the PC that you described as console only and *no* Network Manager?

---

### Post by linuxculo on 2010-06-04
Sorry i have 2 computers 1 without NetworkManager and other with it. I test the same driver in both computers but don´t work. My partner Nilda discover an error in my configuration. Here how we solved this problem. Not with iwconfig but with wpa_supplicant... console mode too

**First add this lines in /etc/network/interfaces**
```
auto ra0
iface ra0 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant.conf
```**create if you don´t have the file*** /etc/wpa_supplicant.conf*  [B]and add this lines

[/B]```

ctrl_interface=/var/run/wpa_supplicant
network={
     ssid="internet"
     key_mgmt=NONE
     wep_key0=652458795
                }

```**Note**: Here was my problem i was thinking that **key_mgmt** must be WEP as my router is configured with WEP but wpa supplicant has not a WEP parameter. If you use WEP in your router you must set **key_mgmt**=NONE, with the key wpa_supplicant know is a WEP.

reboot your network => 
**sudo /etc/init.d/networking restart**

and its all.

---

