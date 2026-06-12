---
title: "Not able to enable wireless connection"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by lbjtemp on 2010-01-22
I am not able to enable wireless connection   ...

I am using a Linksys WMP11 V27 pci card that supposed to be talking to a Linksys BEFW11S4 wireless router (802.11B) ...

I am able to connect directly to internet (ethernet cable hooked to this wireless router) ... but for indepedence I need to go wireless.

I defined the configuration using the Network Connections ... also through ndisgtk .. can't seem to get this two to consolidate.

On /var/log syslog I see ....

an 22 14:27:10 ubucomputer NetworkManager: <info>  Sleeping...
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (wlan0): now unmanaged
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (wlan0): device state change: 2 -> 1 (reason 37)
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (wlan0): cleaning up...
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (eth0): now unmanaged
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (eth0): cleaning up...
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (eth0): taking down device.
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  Waking up...
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (wlan0): now managed
Jan 22 14:27:10 ubucomputer kernel: [  247.545137] eth0: link down
Jan 22 14:27:10 ubucomputer kernel: [  247.545244] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (wlan0): bringing up device.
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jan 22 14:27:10 ubucomputer NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jan 22 14



ubuadmin@ubucomputer:~$ uname -a
Linux ubucomputer 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux
ubuadmin@ubucomputer:~$ 

ubuadmin@ubucomputer:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuadmin@ubucomputer:~$ 
ubuadmin@ubucomputer:~$ iwlist wlan0 scanning
wlan0     Failed to read scan data : Network is down

ubuadmin@ubucomputer:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopbackiface wlan0 inet dhcp



So ... I need to guidance...  please help

---

### Post by lbjtemp on 2010-01-24
OK - I followed 

 Sticky: [all variants] Comprehensive ndiswrapper troubleshooting guide ( 1 2 3 ... Last Page)

And ... its very good ... now my PCI card is able to connect to wireless router ... but still not network connection .. pings do not ping and firefox no internet connection (no web surfing) ...

The "sticky" is very good ...

---

