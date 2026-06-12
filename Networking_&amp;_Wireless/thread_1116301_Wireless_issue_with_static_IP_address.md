---
title: "Wireless issue with static IP address"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Wug on 2009-04-04
*********Resolved?*****************

it turns out that the problem was my router.
In later tests with the nm app I tried to use 192.168.0.1 (to avoid the wierdness of starting at 192.168.1.2 because the router is ~.1), and the router only accepts 192.168.1.*, not ~*.*


******
I am trying to set my laptop to use a static IP over a wireless network.  My '/etc/network/interfaces' looks like this:
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	gateway 192.168.1.1
	broadcast 192.168.1.255

but theres a problem.
When I boot and login, nm-applet says that the wireless device is unmanaged.
Even if I try to repair it with 'sudo etc/init.d/networking restart', it still stays unmanaged.  The only way I can get it to work is if I comment out all of the wlan0 stuff in the interfaces, but then I dont get to choose my IP.  I tried setting 'managed=true' in '/etc/networkmanager/nm-system-settings.conf', and that did fix the device unmanaged problem, but overrided all of the static IP stuff.  The funny thing is, when I boot with the wlan0 stuff in interfaces commented out, then uncomment them and do a networking repair, the settings take effect and I can use them (although I get the error 'SIOCDELRT: process not found'), and apart from that, they work fine.

HELP!?

---

### Post by kreggz on 2009-04-04
I think you need to tell interfaces what ssid you want to connect to and password (using wpasupplicant). This thread might help

[http://ubuntuforums.org/archive/index.php/t-87730.html](http://ubuntuforums.org/archive/index.php/t-87730.html)

---

### Post by Wug on 2009-04-04
That doesn't explain how to set your wireless SSID and password in the interfaces file.  It just shows how to use scripts to change interface files.  Also, when I use the interfaces file above and reboot, It simply stops - it wont let me choose an SSID or pass, it just says its unmanaged.  I cant see anything wrong with the interfaces file, I read several other tutorials that show simply editing the interfaces file to include the static settings (although they only ever showed doing it with an eth# (wired) connection)
If that is the problem, how do you add those things to the interfaces file?

Hint: I am relatively new to linux and I dont know lots of the syntax involved (like how to do that).

---

### Post by kreggz on 2009-04-04
Is there some reason why you don't want to use Network Manager to set your static IP then?

---

### Post by Wug on 2009-04-04
edited: 
because that doesnt work either.  I entered all of my everything that was deduced from the other connections (gateway, ip, dns, etc) and it connected, but the internet stopped working.

---

### Post by kreggz on 2009-04-04
lol, I just don't want to offend you by assuming anything... :)

1. Go to System\Preferences\Network Connections
2. Click on the 'Wireless' tab
3. Click 'Add'
4. Type in your 'SSID'
5. Click on the 'Wireless Security' tab
6. Click 'Method' - Manual
7. Enter your details - make sure you add your DNS server, which you haven't listed. If you don't add it, you won't be able to use the Internet.

make sure there are no other entries under the Wireless tab against your SSID or it won't use the right one.

Cheers,

---

### Post by kreggz on 2009-04-04
- why are you using a static IP anyway?? :)

---

