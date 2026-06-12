---
title: "Problem with Wireless hotspot selection"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by hatitye on 2011-12-08
I have been working on a Linux box with ubuntu 9.10 desktop. I am having a problem with my wireless connection. 
I am working in an environment with a CLI side with now graphical interface only only shell based. 
In the environment there are 3 different wifi hotspots and I only want to have one working only. I am working with a WPA network, and I edited the /etc/network/interfaces file to accommodate the wireless network I want. The machines reboots every midnight and runs dhclient on the wireless drive.

So the problems comes in that the machine chooses the network with the strongest signal first, which is not the one that I want it to connect to.
So I need lock one of the network provider to the machine, if it fails to connect via that provider, I need it to fail to connect.

Remember I am working on a xterm side with no Graphical interface

---

### Post by chili555 on 2011-12-08
May we peruse your interfaces file?```
cat /etc/network/interfaces
```If your interfaces file references an /etc/wpa_supplicant.conf file, please let us see that as well:```
cat /etc/wpa_supplicant.conf
```Of course, please disguise any WPA passwords and MAC addresses.

Are all the networks named the same?

---

### Post by hatitye on 2011-12-08
/cat/etc/interfaces

auto lo
iface ra0 inet dhcp
wpa-ssid "My Home Longer"
wpa-psk "PASSWORD"

cat /etc/wpa_supplicant.conf

wpa_passphrase name s:knockknock
wpa_passphrase name s:knockknock
wpa_passphrase name s:knockknock

[FONT=monospace]The networks are named differently[/FONT]

---

### Post by chili555 on 2011-12-08
> auto lo
iface ra0 inet dhcp
wpa-ssid "My Home Longer"
wpa-psk "PASSWORD"This ought to be:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
wpa-ssid "My Home Longer"
wpa-psk "PASSWORD"
```Since /etc/wpa_supplicant.conf isn't called here, it really isn't needed but probably doesn't actually hurt in any way. > the machine chooses the network with the strongest signal first, which is not the one that I want it to connect to.So you find it has connected to "MY NICE NEIGHBOR" instead of "My Home Longer"?? In a properly configured interfaces file, the machine ought to steadfastly decline to connect to anyone but "My Home Longer."

After you correct the interfaces file as I outlined, if it still occurs, let us see if there are clues here:```
sudo cat /var/log/syslog | grep -e etwork -e wpa -e ra0
```Thanks.

---

### Post by hatitye on 2011-12-09
This is what I get from the results. Taking the tail

Dec 08 15:20:14 allabout dhclient: DHCPREQUEST of 10.5.50.68 on ra0 ro 10.5.50.1 port 67
Dec 08 15:23:15 allabout dhclient: Listening on LPF/ra0/XX:XX:XX:xx:XX:XX
Dec 08 15:28:14 allabout dhclient: Sending on LPF/ra0/XX:XX:XX:xx:XX:XX
Dec 08 15:34:14 allabout dhclient:  DHCPREQUEST of 10.5.50.68 on ra0 ro 10.5.50.1 port 67
Dec 08 15:36:14 allabout kernel: [ 9.307938] type=1505 audit(1322015656.697:3): operation="profile_load" pid=418 name=/usr/lib/NetworkManager/nm-dhcp-client.

---

### Post by chili555 on 2011-12-09
This statement:> I am working in an environment with a CLI side with now graphical interface only only shell based. Is not consistent with this:> pid=418 name=/usr/lib/NetworkManager/nm-dhcp-client. How is Network Manager running and mis-managing your network connections in a command line shell environment. Maybe I don't fully understand.

---

### Post by hatitye on 2011-12-10
Let me be more specific, this Ubuntu version was tweeted to be dedicated to its function. With this I use x-windows system. Specifically I use a browser and I have my php application sand boxed to the browser. So compared to the traditional approach I would take to select the network of preference:confused: I have used wicd-curses to try and configure the network selected at boot time.

Is there anything else you want me to specify.

---

### Post by chili555 on 2011-12-11
> With this I use x-windows system. Specifically I use a browser So this statement is in error?> only only shell based. ???> Is there anything else you want me to specify.Yes. Are you using /etc/network/interfaces or Network Manager or Wicd? Or are you trying to use them all? 

Maybe I'm too confused to figure this out.

If you want to use /etc/network/interfaces properly, you must remove Wicd and Network Manager.

---

### Post by hatitye on 2011-12-13
Yes the statement is false that is only shell based is false. Only that I can do my configurations in a terminal.
I tried wicd and /etc/network/interfaces. My focus then was laid to /etc/network/interfaces but still the problem is failing to be solved that way. wicd-curses is also not resolving the problem sorely.

So are you suggesting I purge wicd and Network Manager?

---

### Post by chili555 on 2011-12-16
You have three conflicting methods installed simultaneously. Your system doesn't perform as expected. I'm pretty sure Network Manager will, depending on your wireless driver, typically try to roam to the perhaps stronger network. That's exactly what you *don't* want. The first step I'd try is to comment out the wireless lines in /etc/network/interfaces, thus:```
auto lo
iface lo inet loopback

**#**auto ra0
**#**iface ra0 inet dhcp
**#**wpa-ssid "My Home Longer"
**#**wpa-psk "PASSWORD"
```Now remove Network Manager:```
sudo apt-get remove --purge network-manage*
```Now see if Wicd will do the job. If not, we'll remove it, too and use manual methods solely.

---

