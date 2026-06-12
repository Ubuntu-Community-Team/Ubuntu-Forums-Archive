---
title: "network questions"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by fkrogh on 2011-09-13
I've had a terrible time getting my wireless to work.  It appeared to be working at one point, but a reboot ended that.  I'm using gnome.  If I delete /etc/network/interfaces, the system boots up and if ifconfig shows both eth0 (wired) and eth1 (wireless) apparently all set up.  Also /etc/resolv.conf shows the dns servers as desired.  But the only thing I can ping is 192.168.1.1 which is the gateway for the wireless.  All others give "ping: sendmsg: Operation not permitted", even including a ping to the wired gateway, 192.168.0.3.

Of course with no interfaces file, I can not restart the network.  If I try to put what seems to me reasonable stuff into interfaces, then I can get the wired connection to work.  But ifconfig shows eth1 is not connected and resolv.conf does not get all the nameservers is should.

An alternative is to delete everything in the network manager gui, and create my own interfaces file.  If I do that and reboot the wired connection comes up, but no wireless.  Pings to the outside world work as long as I get the nameservers into resolv.conf.

I'm neutral as to whether this works using the network manager or with a hand created interfaces file.  The former just needs to allow pings (maybe), the latter needs to get the wireless going.

I'm at a loss.  Is there something magic to put in to interfaces that will not destroy what the gui network manager has done?

For the record, my interfaces file is (not using the network gui)

auto lo
auto eth0
auto eth1
iface lo inet loopback
iface eth0 inet static
  address 192.168.0.4
  network 192.168.0.0
  netmask 255.255.255.0
  gateway 192.168.0.3
  dns-nameservers 8.8.8.8, 8.8.4.4
iface eth1 inet dhcp
#  wpa-driver wext (I've tried this one as well nl80211 worked once)
  wpa-driver nl80211
  wpa-conf /etc/wpa_supplicant.conf
  network 192.168.1.0
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-nameservers 8.8.8.8, 8.8.4.4

/etc/wpa/supplicant.conf
network={
	ssid="crowsnest"
        scan_ssid=1
        key_mgmt=WPA-PSK
	#psk=
	psk=<Lots of characters as generated>
}
Many thanks, for any suggestions.
Fred

---

### Post by fkrogh on 2011-09-14
Installing wicd was the answer for me.  /etc/network/interfaces should only contain

auto lo
iface lo inet loopback

And remove any package that had network-manager in the name.  I missed doing the latter and trouble connecting.  Otherwise this is a very easy solution.

---

