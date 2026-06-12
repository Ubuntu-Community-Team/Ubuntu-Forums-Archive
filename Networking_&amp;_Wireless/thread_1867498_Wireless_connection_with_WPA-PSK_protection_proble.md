---
title: "Wireless connection with WPA-PSK protection problem"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by mr.champagne on 2011-10-23
I just got a new PC from FREE GEEK Running Lucid Lynx. I am trying to get connected to my wireless access point that has WPA-PSK protection. My wireless card is a PCI D-link airplusG DWL-G510 (A1 chipset). The driver i am using is a windows driver through ndiswrapper.

I have tried doing this my self and i got as far as getting the wpa_supplicant gui to throw an error when i try to add the network:

wpa_gui
Failed to enable network in wpa_supplicant configuration.

I am posting this from a dying windows laptop and i am now an expert at finding packages and transferring them to my Ubox (read Ubuntu PC)so i cant do anything that required the $sudu get apt... command

any and all help would be appreciated and as an incentive there will be cake. ;)

---

### Post by praseodym on 2011-10-23
Hi, add the following lines to your /etc/network/interfaces:

```
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]YourESSID[/COLOR] 
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
auto wlan0
```
And a wpa_supplicant.conf:

```
sudo touch /etc/wpa_supplicant/wpa_supplicant.conf
sudo chmod 600 /etc/wpa_supplicant/wpa_supplicant.conf
gksudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```
Insert:
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1

network={
ssid="[COLOR="Red"]YourESSID[/COLOR]"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=TKIP
group=TKIP
psk="[COLOR="Red"]YourKey[/COLOR]"
}
```
Restart the Network:

```
sudo /etc/init.d/networking restart
```
If it doesnt work, change "false" to "true" in this file:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
if you are using the NM, otherwise the "interfaces" is ignored

---

### Post by mr.champagne on 2011-10-24
ok i followed your steps to the letter and I cannot connect to my access point. I lost the password yesterday and i have it now but it will not work. I have heard that ndiswrapper as a driver will not always work with WPA/psk encription, could this be the problem?

---

### Post by mr.champagne on 2011-10-26
still looking for help on this

when i try to connect to the wireless network in network manager it 
keeps trying to connect and then asks for the password for the connection without ever connecting when i enter it. It does this for about 3 attempts and then stops trying to connect.
 I know its the right password because its the password i use to connect on this POS laptop.

---

### Post by yan_sukran on 2011-10-26
Hi
after applying tutorial above, trying to setting manual your interface, something like this:

sudo ifconfig  down
sudo dhclient -r
sudo wpa_supplicant -w -D wext -i wlan0 -c /etc/wpa_supplicant.conf -dd
sudo ifconfig  up
sudo iwconfig  mode Managed
sudo dhclient

work for me, with both driver rtl8187 and ndiswrapper.:)

---

### Post by mr.champagne on 2011-10-27
> **yan_sukran said:**
> Hi
after applying tutorial above, trying to setting manual your interface, something like this:

sudo ifconfig  down
sudo dhclient -r
sudo wpa_supplicant -w -D ***_wext_*** -i wlan0 -c /etc/wpa_supplicant.conf -dd
sudo ifconfig  up
sudo iwconfig  mode Managed
sudo dhclient

work for me, with both driver rtl8187 and ndiswrapper.:)

first command throws this at me:
```
down: error fetching interface information: Device not found
```

thanks for the input.

---

