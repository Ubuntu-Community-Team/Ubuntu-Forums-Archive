---
title: "wpa_supplicant in 11.10"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by CryptAck on 2011-12-04
It appears wpa_supplicant under 11.10 doesn't use the /etc/wpa_supplicant.conf file anymore. In so, 
[list]
[*]what does wpa_suppliacnt use now to get it's SSID and wireless credentials,
[*]and is there a command to show what details wpa_supplicant is using (I didn't see any options under the typical command)?
[/list]

Thanks!

---

### Post by matt_symes on 2011-12-04
Hi

> **CryptAck said:**
> It appears wpa_supplicant under 11.10 doesn't use the /etc/wpa_supplicant.conf file anymore. In so, 
[LIST]
[*]what does wpa_suppliacnt use now to get it's SSID and wireless credentials,
[*]and is there a command to show what details wpa_supplicant is using (I didn't see any options under the typical command)?
[/LIST]

Thanks!

Are you taking about the desktop or a server. Network Manager (on the desktop) has used bdus for ages to give its settings to wpa_supplicant.

You can kill Network Manager and start wpa_supplicant with any configuration file you want. The same also applies to a Ubuntu server (apart from a cli server does not use NetwoprkManager).

You can also add the wpa_supplicant settings to /etc/network/interfaces.

Kind regards

---

### Post by CryptAck on 2011-12-04
> **matt_symes said:**
> 
Are you taking about the desktop or a server. Network Manager (on the desktop) has used bdus for ages to give its settings to wpa_supplicant.

I'm having some difficulty on another machine getting it to authenticate. I generated my own /etc/wpa_supplicant.conf file for the connection, verified that the passphrase is correct, but it still continues to have issues. I thought if I could review/copy the conf file from another machine, I could identify the cause of my issue.

> **matt_symes said:**
> 
You can kill Network Manager and start wpa_supplicant with any configuration file you want. The same also applies to a Ubuntu server (apart from a cli server does not use NetwoprkManager).

You can also add the wpa_supplicant settings to /etc/network/interfaces.

I'm actually not looking for a way to kill or use another config file. Just hoping to view what is currently used to connect in a wpa_supplicant.conf format. 

I hope that makes sense!

---

### Post by matt_symes on 2011-12-04
Hi

I am still not sure if you are trying to set this up from the command line from a server or on a desktop.

On my server this is what i do to connect to my wireless network. I do this all through the command line.

First i create my wpa_supplicant.conf file. I am using wpa2 personal. Here is an example.
```

matthew@server1:/var/www/php_work$ wpa_passphrase test_ssid test_passwd > ~/wpa_supplicant.conf
matthew@server1:/var/www/php_work$ sed -i '2ikey_mgmt=WPA-PSK' ~/wpa_supplicant.conf
matthew@server1:/var/www/php_work$ sed -i '2iscan_ssid=1' ~/wpa_supplicant.conf
matthew@server1:/var/www/php_work$ cat ~/wpa_supplicant.conf 
network={
scan_ssid=1
key_mgmt=WPA-PSK
        ssid="test_ssid"
        #psk="test_passwd"
        psk=2a1559fcf2d5a38c14a415afc6ae77f4646fd928bb208cdc00374a05e3739106
}
matthew@server1:/var/www/php_work$
```Make sure your wireless interface is up.

```
sudo ifconfig wlan0 up
```Then i start wpa_supplicant. Make sure no other instances of wpa_supplicant are running or you will have problems.

You can check for other instances with

```
ps aux | grep [w]pa
```and the kill them if required.

```
sudo kill <pid_of_wpa>
```Then i start up wpa_supplicant

```
sudo wpa_supplicant -Dwext -B -iwlan0 -c /home/matthew/wpa_supplicant.conf
```You can check you are connected to the access point with

```
iwconfig wlan0
```Lastly i get an IP address via dhcp.

```
sudo dhclient wlan0
```Xheck your ip address with

```
ifconfig wlan0
```The above is just an example. You will have to change values to fit your setup.

Does this help you ? :confused:

Kind regards

---

### Post by CryptAck on 2011-12-10
> **matt_symes said:**
> Hi

I am still not sure if you are trying to set this up from the command line from a server or on a desktop.

Not trying to set anything up. I'm just trying to identify HOW it works. :)

I've always used the /etc/wpa_supplicant.conf file, and would perform the same instructions you listed. However, there is no /etc/wpa_supplicant.conf file to browse, so I'm wondering if Ubuntu still is using wpa_supplicant, and if so, how it obtains it's "information". Needs to be a file somewhere I'd imagine.

I'm basically trying to understand how the Wireless (authentication) works in 11.10.

---

### Post by matt_symes on 2011-12-11
Hi

A far as i understand it, Network Manager uses DBUS to communicate with and control wpa_supplicant. The passwords are stored in Seahorse.

From [http://linuxwireless.org/en/users/Documentation/NetworkManager](http://linuxwireless.org/en/users/Documentation/NetworkManager)

> We now have a dbus-based control interface for  wpa_supplication. NM uses dbus to talk to wpa_supplicant, rather than  the old socket-based control interface which simply didn't have enough  flexibility. wpa_supplicant needs to be started as a system daemon, much  like dhcdbd and (optionally) bind are today. This should reduce  connection latency since we don't need to exec a copy of wpa_supplicant  for each connection. Scanning is also now handled through wpa_supplicant  for better coordination. 

wpa_supplicant  0.5 has basic dbus functionality, including the ability to add/remove  interfaces from its control, request scan results, and broadcast scan  result available signals. (updated 2006-06-26) Kind regards

---

### Post by CryptAck on 2011-12-11
> **matt_symes said:**
> Hi

A far as i understand it, Network Manager uses DBUS to communicate with and control wpa_supplicant. The passwords are stored in Seahorse.

From [http://linuxwireless.org/en/users/Documentation/NetworkManager](http://linuxwireless.org/en/users/Documentation/NetworkManager)

Kind regards

This is exactly what I was looking for!!! :)

Thanks!

---

