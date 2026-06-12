---
title: "Port forwarding/static IP setup help..."
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by bertles86 on 2008-12-26
Hi folks I've got the following:

Ubuntu 8.04
Belkin F5D7632-4 Modem Router
CNET Wireless PCI Card

I'm connecting to the net just fine, but I would like to setup a static IP address in order to forward a port to use Azureus properly.

Could someone help me setup a static IP and I can do the rest!

If you need any more data pulled off shell just ask.

Cheers!

---

### Post by caleb12 on 2008-12-26
Are you using Network Manager? If so, you can configure a static IP through NM's interface. There are other Network Utilities on Ubuntu as well, under System -> Adminstration that would allow for configuration. 

Worse case scenario, you'd have to edit the /etc/network/interfaces file to set a static IP. So, open your favorite terminal or just ALT+F2 and type gnome-terminal. 

Then sudo pico /etc/network/interfaces 

The file should look something like this for a static setup:

```
# The loopback interface
auto lo
iface lo inet loopback

# The first network card 
# (network, broadcast and gateway are optional)
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

If you run into any problems, typing _man interfaces_ will give you a detailed manual to the syntax available for that file...

---

### Post by bertles86 on 2008-12-26
I gave that a crack mate and I think that is if you are using a wired ethernet connection. I'm on wireless and think it's a bit different. In NM, I have manually set the wifi configuration but it's not working:

SSID: My network appears briefly then disappears in the list, but I can type it in manually but that does not work.

I think type in mask and IP from ifconfig under the 'lo' set of data but it won't connect.

Any ideas?

---

### Post by bertles86 on 2008-12-26
Right no I tried this code in interfaces:

```
mapping hotplug
        script grep

# The primary network interface
iface wlan0 inet static
wireless-essid McGaughey
wireless-key s:susan
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.255

auto wlan0

```

And after doing sudo /etc/init.d/networking restart - all I got was:

"Failed to bring up wlan0" and my connection dropped out.

On running iwconfig I get this:

```
wlan0     IEEE 802.11g  ESSID:"XXX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:81:03:48   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=71/100  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

So what's up with it?

P.S. XXX for ESSID is me blanking out my networks name!

---

### Post by caleb12 on 2008-12-26
So, for a wireless interface in Network Manager - using a static IP is a little different. 

Any entries in the interfaces file will conflict with NM, so return it to the original state you had... For instance mine looks like this: 
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
```

Check the version of Network Manager that you are using, I believe 8.04 came with 0.6 - however in 8.10 NM 0.7 is the standard. This makes a huge difference because static IPs for wireless was not supported until 0.7. Besides upgrading to 0.7 would only be a bonus, they have done so much work since 0.6. 

I'm using a static IP at my house as well, with 8.10 and NM 0.7 and it works flawlessly.

---

### Post by superprash2003 on 2008-12-26
you could setup static ip like this [http://www.prash-babu.com/2008/10/wifi-tip-always-better-to-disable.html](http://www.prash-babu.com/2008/10/wifi-tip-always-better-to-disable.html) .. chose static ip instead of DHCP in step 6

---

### Post by bertles86 on 2008-12-27
Right well I think I have NM 0.6 so how do I update to 0.7?

---

### Post by caleb12 on 2008-12-27
Hopefully you're familiar with apt... If not we can try another approach... 

Edit the file /etc/apt/sources.list

add these lines:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

sudo apt-get update
sudo apt-get install network-manager

That should do it... 0.7, IMHO, was a major improvement from 0.6.6. It's pretty self explanatory on setting up a static IP after that...

---

### Post by bertles86 on 2008-12-28
Righto mate I've added those lines and got the updates. Now which app am I looking to use:

System > Preferences > Network Config
System > Administration > Network
System > Administration > Network Tools?

A step by step would be great mate, I know my networking but only under windoze really!

---

### Post by caleb12 on 2008-12-28
If you're using Synaptic, just hit the Reload button at top - that will refresh your package information and Network Manager should show up as needing to be upgraded. Technically, this should all happen automagically... You can also try the Search function as well - Network Manager are the key words. 

If you're not using Synaptic, then you can always use a terminal and type the commands: 

sudo apt-get update
sudo apt-get install network-manager

If you click the Add/Remove Applications, on the Main menu... Just highlight all and do a search for Network Manager. 

The only thing to really remember here is that after editing the sources.list file, the apt-cache needs to be updated. Which you can do by hitting Reload in Synaptic or the command sudo apt-get update. 

Once it's installed, it's pretty much like Windows... Right click the icon in the System Tray, and edit connections.

---

### Post by bertles86 on 2008-12-28
Phew right think I've done it, I'll let you know if it holds! Cheers for all the help.

---

