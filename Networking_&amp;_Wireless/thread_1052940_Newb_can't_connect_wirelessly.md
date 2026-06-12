---
title: "Newb can't connect wirelessly"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by maidden on 2009-01-28
I'm very new to Ubuntu, so please bear with me. I installed Intrepid a few days ago. At first, it was able to connect to the Internet, even though it said the wireless signal strength was only 14-15%, while Windows on the same machine said it was "excellent".

Then, yesterday, it lost the connection entirely, kept asking for the encryption key, which I checked in the router admin page from another machine, and was correct. I tried rebooting and it reconnected for a while, but lost it again. Rebooting again sometimes worked for a few minutes, other times it just wouldn't detect any wireless networks at all. I tried changing the encryption from WEP to WPA and even no encryption, but it still couldn't connect.

I installed ndiswrapper and a win98 driver, and now it's consistently detecting networks and with better signals, but it went back to asking for the key.

Here's some output from the terminal that might have relevant information I missed:

lsusb
```
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
```

ndiswrapper -l
```
netrtuw : driver installed
device (0BDA:8187) present (alternate driver: rtl8187)
```

lshw -C Network
```
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:15:f2:2d:d0:cd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:13:bb:38:92:c9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:18:e7:1e:ba:56
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.53+OEM,04/04/2006,5.1221.0412. link=no multicast=yes wireless=IEEE 802.11g
```

iwconfig wlan
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

dmesg | grep -e ndis -e wlan
```
[   39.022246] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   39.931850] ndiswrapper: driver netrtuw (OEM,04/04/2006,5.1221.0412.2006) loaded
[   48.364880] wlan0: ethernet device 00:18:e7:1e:ba:56 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0BDA:8187.F.conf
[   48.364972] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   48.365161] usbcore: registered new interface driver ndiswrapper
[ 1922.425737] usbcore: deregistering interface driver ndiswrapper
[ 1922.493254] ndiswrapper: device wlan0 removed
[ 1922.669156] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 1923.029627] ndiswrapper: driver netrtuw (OEM,04/04/2006,5.1221.0412.2006) loaded
[ 1926.158082] wlan0: ethernet device 00:18:e7:1e:ba:56 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0BDA:8187.F.conf
[ 1926.159171] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1926.160322] usbcore: registered new interface driver ndiswrapper
```

---

### Post by renzokuken on 2009-01-28
ahh, the notorious rtl8187. my laptop has this chip and i could never get it working properly ..... with neither ndiswrapper or the kernel drivers.

in the end i gave up and bought a usb wireless dongle with a chipset known to work.

i realise this is probably not the answer you wanted but i've been trying to get the rtl8187 to work for years with no luck

EDIT: i did have it working on ndiswrapper with NO password/encryption, but obviously thats not ideal so i quickly binned that idea

---

### Post by maidden on 2009-01-28
At least you got it to work with no encryption. Here, even that doesn't. Your reply wasn't unexpected, actually. I've got a wireless USB adapter from Encore, which I've been told is, well, crappy. Right now I can't afford to get a new one, however. I was hoping I'd be able to at least get it to limping until I can...

---

### Post by maidden on 2009-01-29
Halp?

---

### Post by gstanden on 2009-05-19
Hi this thread is a little stale but since no solution was ever added I will add mine.  
This if for the rtl8187 with win98 driver and using ndiswrapper as the original poster described.

Note this only works right if you boot up with your ethernet wired connection plugged in to 
your laptop.  Once booted up you can switch back and forth between wired/wireless
but for some reason a bootup without wired connected isn't working.  So I'm trying to figure
this out - please take a look at the config and let me know if you know why.  I'd like to have
a config which can be booted up wired or wireless and work.

But anyway, here is the solution as it is:

gstanden@gstanden-laptop:/etc$ lsusb
Bus 007 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. 

There is a guide on how to set up the rtl8187 with ndiswrapper and wth win98 driver 
(and you can also download the driver from this same URL.  
After loading the URL scroll down to the bottom and click on the link 
"RTL8187B_driver_only.zip") at this URL:  

[http://www.thecomingstorm.us/smf3/index.php?topic=198.0](http://www.thecomingstorm.us/smf3/index.php?topic=198.0) 

Once you have finished with that post on setting up ndiswrapper for this card, 
you now need to configure a few more things.

This is the config I use and it works great.  
My hardware is a Toshiba A205-S5800 laptop.  
There are probably variations on my config files that will work also;  
this is just one way to do it.  
My network setup is a Westell DSL modem at 192.168.1.1 
and a linksys WRT54G Wireless G router at 192.168.200.1 
connected to the Westell DSL modem.  
My wired connections use the 192.168.200.xxx ip addresses 
and my wireless connections use the 192.168.1.x ip addresses.

I also use WICD instead of gnome-network-manager.  
I found that ubuntu updates were breaking my 
gnome-network-manager pretty frequently so I 
replaced it with WICD which as been robust and 
reliable for over a year through thick and thin and 
many ubuntu update sycles.  I recommend you also rip out 
gnome-network-manager and switch to WICD.  Get WICD as follows:

sudo apt-get install wicd

I think the above apt-get will work for wicd with the 
base-install repositories but you might have to add a 
respository possibly.

Once you have WICD do the following file steps.

cd /etc/network
cp -p interfaces interfaces.bak

Then replace your interfaces with this interfaces file shown below.  
Before you can do that however, you need to identify your psk key.  
You do this with this command:

 wpa_passphrase <ssid> [passphrase]

For example is your ssid was MyHomeNet and your 
plaintext passphrase for your router was OpenSesame you would run this command:

wpa_passphrase MyHomeNet OpenSesame

which gives this output:

gstanden@gstanden-laptop:/etc/network$ wpa_passphrase MyHomeNet OpenSesame
network={
	ssid="MyHomeNet"
	#psk="OpenSesame"
	psk=6d3da2b9c1b04b81af42544ae3778652e0e1604ad5c54f246188030557dbcc2c
}

So we will assume these are the actual names of your systems 
values but of course when you actually do this yourself substitute your 
own ssid and plaintext passphrase and use the long encrypted value you get.

So then starting with a fresh blank /etc/network/interfaces file 
(you backed up the original one in the above step) paste this 
into the new interfaces file just as shown you don't need any " " 
around any of the values but you do have to change things 
like the "xxx" to your network values.

---New /etc/network/interfaces File---

auto lo
iface lo inet loopback

iface eth0 inet static
        address 192.168.200.xxx
        netmask 255.255.255.0
        network 192.168.200.0
        broadcast 192.168.200.255
        gateway 192.168.200.1

auto wlan0
iface wlan0 inet dhcp
	wpa-driver ndiswrapper
        wpa-ssid MyHomeNet
	wpa-ap-scan 1
	wpa-proto WPA RSN
	wpa-pairwise TKIP CCMP
	wpa-group TKIP CCMP
	wpa-key-mgmt WPA-PSK
        wpa-psk 6d3da2b9c1b04b81af42544ae3778652e0e1604ad5c54f246188030557dbcc2c

---End /etc/network/interfaces File---

Of course substitute your own ip address where you 
see the "xxx" and/or also change the subnet values 
in the first stanza for the eth0 settings which is to say 
you could 192.168.201.xxx etc. instead of 192.168.200.xxx for example.

Now do this next:

cd /etc/wpa_supplicant

If there is an existing wpa_supplicant.conf file in 
that directory, back it up:

sudo cp -p wpa_supplicant.conf wpa_supplicant.conf.bak

Now create a new wpa_supplicant.conf file and 
paste this into it:

---New /etc/wpa_supplicant/wpa_supplicant.conf File---

network={
	ssid="MyHomeNet"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
	psk=6d3da2b9c1b04b81af42544ae3778652e0e1604ad5c54f246188030557dbcc2c
}

---End /etc/wpa_supplicant/wpa_supplicant.conf File---

One other edit you will need to make is at rc.local.  
This edit is kind of weird in that it's just a workaround that works.  
There is probably a better way to accomplish the same thing 
that this rc.local fix does, but I don't know it.  
Basically, I found that this networking setup didn't 
load and startup right unless I did a

sudo /etc/init.d/networking restart

after bootup.  So I added this command to /etc/rc.local 
to do it automatically:

---Add this code to /etc/rc.local File---

sleep 20
sudo /etc/init.d/networking restart

---End of additions---

Now you have got all the config files setup.  
You should also check your file:

/etc/resolv.conf

and make sure it has a valid value in it for nameserver.  
This will usually be the ipaddress of your modem.  
In my case this is what is in my /etc/resolv.conf

---/etc/resolv.conf File---

nameserver 192.168.1.1

---/etc/resolv.conf File---

Now you have got all the files in place.  
Now I also have WICD configurations that I 
set up with the WICD gui.  Here are screenshots of how to do that:

Find the WICD icon in the task bar at the very top 
right area of the screen usually next to the battery icon 
(if you have a laptop) and to the left of the date information.  
Click on the WICD icon which is two overlapping 
computer screens.  It gives you the main WICD page.  
Along the top of the page click on "preferences" as shown below.

[IMG]http://www.thecomingstorm.us/images/wicd-1.jpg[/IMG]

On this preferences page be sure you have set
WPA Supplicant Driver field to ndiswrapper

Your DNS 1 may be different.

Be sure to check under General Settings:
x Use global DNS servers
x Always show wired interface
x Automatically reconnect on connection loss
x Use default profile on wired autoconnect

click on "OK" to save the preferences.

Now go to the main WICD screen again and 
expand the entry for your wireless and edit 
the advanced setting as shown. 

[IMG]http://www.thecomingstorm.us/images/wicd-2.jpg[/IMG]

x Use these settings for all networks sharing this essid
x Use Encryption

Then choose WPA 1/2 (Preshared Key) from the drop
 down box and then paste in that long string again into the field

6d3da2b9c1b04b81af42544ae3778652e0e1604ad5c54f246188030557dbcc2c

click ok and close up all the WICD screens.  

Ok you should be done ready for showtime. 
 You can try just doing this at the ubuntu command line:

/etc/init.d/networking restart

You should see something like this if all goes successfully:

---

gstanden@gstanden-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for gstanden: 
 * Reconfiguring network interfaces...                                                                                                                       RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5793
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:44:9d:44:e4
Sending on   LPF/wlan0/00:16:44:9d:44:e4
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:44:9d:44:e4
Sending on   LPF/wlan0/00:16:44:9d:44:e4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.42 from 192.168.1.1
DHCPREQUEST of 192.168.1.42 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.42 from 192.168.1.1
bound to 192.168.1.42 -- renewal in 41436 seconds.

---

If it worked, you will find that if you reboot your laptop 
network setup will autodetect if you are on wired or wireless.  
If you bootup wired, and then after bootup switch to wireless 
(unplug your network cable from the laptop) you will see WICD 
immediately switch to the wirless icon (little green signal bar) 
and then if you plug the wired back in it will switch back to wired. 
 WICD uses wired preferentially: if it detects it it will use wired; otherwise wireless.

Now one interesting thing I noticed with this.  The wlan0 in this 
setup gets an ip assigned from the subnet of the MODEM.  So on my 
network the wlan0 wireless gets a dhcp assigned ip on the 192.168.1.xxx range.  
On the other hand, the ip of the ethernet wired card gets an ip on the 192.168.200.xxx range.  

It's 1:17 AM eastern standard time here and I'm sure if you try 
different configs you will find ways to get the wireless card to 
be on the same subnet as the wired and vice versa.  I did do a bit 
of tests and I could not get the wireless card to come up when
 I tried to get it to come up on the 192.168.200.xxx range 
with a static ip;  only dhcp would work for me.

Another thing:  Here is the wpa_supplicant command that 
ubuntu networking runs for you in the background when you run 

/etc/init.d/networking restart

it's an interesting wpa_supplicant command string - 
not sure what it means but ubuntu seems to know:

/sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D ndiswrapper -C /var/run/wpa_supplicant

You will find that if you try to run

 /etc/init.d/networking restart 

again after running it once it's going to complain 
about the wlan0.pid already existing.  I tried rm'g 
the wlan0.pid but still seemed to be hitting this each 
time, so once this network setup is up, after boot, leave it all up.  
The system automatically switches you back and forth between 
wired/wireless as needed so it should work ok I think without 
any further steps.

Hope this helps.  I learned most of this from 
various posts on the net and then some really long trial-and-error.  
Here are some of them:

References

Centos-&-Ubuntu-Wireless-on-Toshiba
[http://forums.fedoraforum.org/showthread.php?t=152598](http://forums.fedoraforum.org/showthread.php?t=152598)
[http://wiki.zenwalk.org/index.php?title=Wpa_supplicant](http://wiki.zenwalk.org/index.php?title=Wpa_supplicant)
[https://www.centos.org/modules/newbb/viewtopic.php?viewmode=flat&order=DESC&topic_id=11749&forum=40&move=prev&topic_time=1197965854](https://www.centos.org/modules/newbb/viewtopic.php?viewmode=flat&order=DESC&topic_id=11749&forum=40&move=prev&topic_time=1197965854)
[http://www.redhat.com/archives/fedora-list/2006-June/msg00344.html](http://www.redhat.com/archives/fedora-list/2006-June/msg00344.html)
[http://www.pantz.org/software/wpa_supplicant/wirelesswpa2andlinux.html](http://www.pantz.org/software/wpa_supplicant/wirelesswpa2andlinux.html)
[http://www.jms1.net/ifcfg.shtml](http://www.jms1.net/ifcfg.shtml)
[http://nst.sourceforge.net/nst/docs/faq/ch07s03.html](http://nst.sourceforge.net/nst/docs/faq/ch07s03.html)
[http://madwifi-project.org/attachment/wiki/UserDocs/Distro/RedHat/ifcfg-ath0](http://madwifi-project.org/attachment/wiki/UserDocs/Distro/RedHat/ifcfg-ath0)
[http://forums.fedoraforum.org/showthread.php?t=112037](http://forums.fedoraforum.org/showthread.php?t=112037)
[http://www.howtoforge.com/how-to-install-intel-pro-wireless-3945-on-centos-linux](http://www.howtoforge.com/how-to-install-intel-pro-wireless-3945-on-centos-linux)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4935302](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=4935302)
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)
[http://wiki.openzaurus.org/HowTos/roaming_with_wpa_supplicant](http://wiki.openzaurus.org/HowTos/roaming_with_wpa_supplicant)
[http://wiki.archlinux.org/index.php/Wpa_supplicant](http://wiki.archlinux.org/index.php/Wpa_supplicant)
[http://www.enterprisenetworkingplanet.com/netsecur/article.php/3594946](http://www.enterprisenetworkingplanet.com/netsecur/article.php/3594946)
[http://hostap.epitest.fi/wpa_supplicant/conf/configure.html](http://hostap.epitest.fi/wpa_supplicant/conf/configure.html)
[http://ubuntuforums.org/archive/index.php/t-156516.html](http://ubuntuforums.org/archive/index.php/t-156516.html)
[http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/](http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/)
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by renzokuken on 2009-05-20
excellent post gstanden. i will give it a go this weekend and let you know how it went.

thank you

---

### Post by gstanden on 2009-05-21
Hi renzokuken well there is a problem with this though which I discovered after getting a few hours of sleep.  This only works when I boot up with the wired ethernet connected as well because the dhcp lease for wlan0 is coming from the dslrouter/modem behind my linksys router.  Apparently wlan0 dhcp request gets routed right through the linksys to the www-facing dsl router which allocates an ip on the 192.168.1.0 network.  I have a feeling this is not so good because I guess this puts my wireless card outside of my WPA2 encryption which I'm trying to get to work.  The other problem is that while nslookup works with only wlan0 up, internet page rendering does not because apparently there is no route from 192.168.1.0 network to my internal LAN of 192.168.200.0 (the linksys router).  I don't know much about routing and I was playing around with this to see if internet traffic in from the web could be routed from 192.168.1.0 to 192.168.200.x addresses with some additional routing table entry, but even if it could, I'm really looking for the dhcp lease to be issued by the linksys router on 192.168.200.x network and also for the dhcp lease to be issued whether or not wired ethernet is connected, so this post is incomplete still as a solution.  (However the ndiswrapper part is thoroughly tested and should work perfectly).

---

### Post by gstanden on 2009-05-21
Update.  Ok I have got a lease as usual from the dslrouter (www-facing) and I can both run nslookup and load internet pages from the www and I am using only the wireless card (wired ethernet is disconnected).  I went to some websites I have never loaded just to make sure I wasn't seeing cached pages.  Here is my ifconfig and route info:

wlan0     Link encap:Ethernet  HWaddr 00:16:44:9d:44:e4  
          inet addr:192.168.1.41  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe9d:44e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:773896 (755.7 KB)  TX bytes:115133 (112.4 KB)

gstanden@gstanden-laptop:/etc/wpa_supplicant$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.103.0   *               255.255.255.0   U     0      0        0 vmnet8
192.168.182.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         dslrouter       0.0.0.0         UG    0      0        0 wlan0

Here is my /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
        address 192.168.200.101
        netmask 255.255.255.0
        network 192.168.200.0
        broadcast 192.168.200.255
        gateway 192.168.200.1

auto wlan0
iface wlan0 inet dhcp
	wpa-driver ndiswrapper
	wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf


Here is my wpa_supplicant.conf:

crtl_interface=/var/run/wpa_supplicant
network={
	ssid="SomeSSID"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
	psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
}

However I cannot ssh to hosts on my internal 192.168.200.x network because there is no route to these hosts.

---

### Post by gstanden on 2009-05-25
RTL8187 WPA2 UBUNTU 8.04 9.04 TOSHIBA A205 S5800

Ok I claim this is "solved" although it's not "truly solved" because I could not get WPA2 encryption to work with the 8.04 LTS Ubuntu version.  In the end I "threw in the towel" and upgraded to 9.04 Jaunty Jackalope with which this RTL8187B card plays pretty nicely.

(There are reasons why I stubbornly did not want to go to 9,04 the biggest reason being that vmware server 1.0.x will not install right on 9.0.4 even with the any-any-patches etc. etc. etc.).  But as all my other equipment is on WPA2 now, well, I'll just have to solve the vmware problems separately :popcorn: )

Here is one recipe to get this working if you are on 8.04 LTS and your wireless card is a Realtek RTL8187 and your hardware is a Toshiba A205-S5800 laptop (This procedure may also work if you are on other hardware with this same RTL8187 but I can only guarantee this hardware/software pair because it has been proven).  Also, this was tested on a Linksys WRT54G wireless/wired router so it is possible other routers could have different results (but should work).  The DSL modem on this setup is a WESTELL Model 6100F.

First, you must upgrade your 8.04 LTS to 9.04 Jaunty Jackalope.  I did this by first upgrading to 8.10 then another hop up to 9.04.  I'm not sure if there is a direct route.  Follow the instructions here to do this upgrade:

[http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibix.html)

Then just do a similar step to go to 9.04.

Once you are upgraded to 9.04 you need to put these files in for your network.  Change the address information for eth0 to fit your own network first. 

_1.  /etc/network/interfaces:_ 

auto lo
iface lo inet loopback

iface eth0 inet static
        address 192.168.200.101
        netmask 255.255.255.0
        network 192.168.200.0
        broadcast 192.168.200.255
        gateway 192.168.200.1

auto wlan0
iface wlan0 inet dhcp
 	wpa-driver wext
 	wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

_2.  /etc/wpa_supplicant/wpa_supplicant.conf:_

ctrl_interface=/var/run/wpa_supplicant
network={
	ssid="YourWirelessNetworkName"
	scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
	psk=dc44d7b6c2f8cfe45109d44d86ec2221ff8a237a862e90d60b31c9edec4f57ad
}

Next you have to be sure ndiswrapper is uninstalled (if you were previously using it on 8.04 according to the recipe I provided above for ndiswrapper).

First do:

sudo apt-get purge ndiswrapper-common ndiswrapper-utils

Then do:

sudo modprobe rtl8187

You can see your loaded modules this way:

laptop:/etc/wpa_supplicant$ lsmod | grep rtl8187
rtl8187                53376  0 
mac80211              217208  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               38032  2 rtl8187,mac80211

laptop:/etc/wpa_supplicant$ lsmod | grep ndiswrapper
ndiswrapper           193436  0 

Now you can reboot and wlan0 should come up working on boot!  I can load pages from www and I can ssh to other servers on my network using wlan0 now and the connection is WPA2 encrypted.  I live in a cooperative apartment and I'm just a bit pleased to say that of the 3 to 12 wireless networks I can see at any given time, mine is the only one secured with WPA2 so I guess any wifi hackers would probably pick on the easy networks and leave mine alone and I guess it is an indication that WPA2 is a pain to configure!  

Note also that the ndiswrapper module is still there.  I could have gotten it out with sudo modprobe -r ndiswrapper, but since things are working fine with it living in the kernel, I don't care, and moreover, I don't want to f anything up so I'm leaving well enough alone.  This adventure of getting WPA2 to work on my Ubuntu desktop has been a memorable frustrating experience.

Please let me know here if run into any snags with the above, and update with additional steps, quirks, scenarios.

Thanks, Gil

ps however I still cannot get it to work with MAC address filtering on the Router...aaaargh this will never end welcome to h*** mortal....

---

