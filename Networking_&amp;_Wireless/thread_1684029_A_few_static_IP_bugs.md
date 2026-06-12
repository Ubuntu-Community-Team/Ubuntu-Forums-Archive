---
title: "A few static IP bugs"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by eddierb on 2011-02-08
Hi all, I'm having a few issues with a static IP on a wireless network I set up for running a game server.  I edited /etc/network/interfaces in the following way:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

The server is working fine but I'm having two major problems:

1. If I reboot, the laptop no longer tries to connect to a network.  Current solution: Re-edit ~/interfaces back to default (remove the static bit), reboot again, add the static bit back and run '/etc/init.d/networking restart'.

2. If the network connection drops for some reason, I have to run '/etc/init.d/networking restart' manually to get the server back up.  Obviously I don't want to be worrying about dropping off the net when I'm absent.

Is there a simple way to avoid these two problems?

Cheers

---

### Post by chili555 on 2011-02-08
Your interfaces file is a bit busy in one respect and not busy enough in another. I assume, since the interface is wlan0, it's a wireless interface. Where is the essid and encryption key? It ought to look something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid your_router
wpa-psk your_key
```Assuming that Network Manager is not installed, and it shouldn't be on a server, this ought to work perfectly. 

Don't dare tell us you are running without encryption; don't!!!

---

### Post by eddierb on 2011-02-08
Thanks for your quick response Chili.  The laptop was used as a standard pc before I decided to run the server on it. It has network manager 0.8 - should I remove network manager and make the changes you've suggested?  And yes my network is encrypted :)

---

### Post by chili555 on 2011-02-08
> should I remove network manager and make the changes you've suggested?Yes and yes. It will probably require a reboot.> And yes my network is encrypted Excellent! Post back and let us know.

My suggested interfaces file is appropriate for WPA-PSK or WPA2-PSK. Let us know if that's not your encryption mode; or, even better, change it.

---

### Post by eddierb on 2011-02-08
Seems to have done the trick with regards to the server (though will post again tomorrow to confirm).

I've noticed that by removing network manager I've lost access to the internet through my browsers (FF/Chrome) - not the biggest problem but would like to have my cake and eat it too.  Have I pruned too much when using synaptic or is this to be expected?  Is there a solution?

---

### Post by chili555 on 2011-02-08
Oops! Network Manager grabs DNS nameservers from the router and fills in /etc/resolv.conf. Let's take care of that. Please do:```
sudo su
echo "nameserver 192.168.1.1" > /etc/resolv.conf
exit
ping -c3 www.google.com
```Did you get ping returns? If so, you're all set.

---

### Post by eddierb on 2011-02-09
That seems to have done the trick, cheers for you help.

---

