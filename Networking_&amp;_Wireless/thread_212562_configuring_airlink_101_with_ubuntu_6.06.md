---
title: "configuring airlink 101 with ubuntu 6.06"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by karthikik on 2006-07-10
I have just installed ubuntu and trying to get it to work with wifi. 

I have an  AWLL3026 802.11g Ultra Slim USB 2.0 Adapter, after the install I noticed the wlan has been detected. I clicked on properties, in the ESSID selected the wifi connection, key type selected hexadecimal and then finally added the WEP Key. Configuration is set to DHCP. Default Gateway device is wlan0. 

I am using a Linksys WRTGC54 router and it works fine with other laptops with wifi. 

I tried - sudo ifdown wlan0

 and get the following 

Error for wireless request "Set ESSID" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument. 

so I now tried a 

sudo ifup wlan0

Listening on LPF/wlan0/00:11:a3:01:84:aa
Sending on   LPF/wlan0/00:11:a3:01:84:aa
Sending on   Socket/fallback/fallback-net
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database.
 
Sleeping.

I looked at many past threads but have not been able to make progress beyond this, any pointers or suggestions, would be very helpful.

Thanks
Karthik

---

### Post by windom on 2006-07-10
I use this card and I have it working. Finally. I had exactly the same problem as displayed.

I did two things to try and get the card working consistantly. I'll work backwards. The last thing I did was to get the card to get an IP address from the DHCP server. I turned off ipv6. Evidently my DHCP server does not work with ipv6. The software I am using is dnsmasq running on an unslung Linksys NSLU2 box. The newer versions of dnsmasq evidently support ipv6 now so I guess it's time for an upgrade. I makes me wonder about DHCP servers that are on the all the firewall/routers used in so many homes.

The second thing (actually the first thing I tried) was to use files that came with the Ralink linux driver. Besides the driver itself, the tarball also has 3 firmware files and a configuration file. I compiled the driver (very easy) and replaced the Ubuntu version with the newly compiled version. Then I installed the 4 files (3 firmware + 1 config) as documented in the tarball. The config file contains the info that usually would go in the /etc/network/interfaces file like essid, key, etc.

I don't think the new rt61.ko driver actually bought me anything but the config file (whose name escapes me) made things look right when I did an iwconfig. The firmware? Who knows? This is all a little short on details, but google can fill in the gaps.

  -w-

---

### Post by karthikik on 2006-07-10
I have switched off ipv6. 
Disable DHCP and replaced with a static ip. 
I added the windows drives using 

sudo ndiswrapper -i Driver.inf
sudo modprobe ndiswrapper 
sudo /etc/init.d/networking restart

ath0: Error while getting interface flags: No such device

Failed to bringup ath0

Error for wireless request "Set ESSID" (8B2A) :
SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device wlan0 ; Invalid argument.

---

### Post by windom on 2006-07-11
Where/how are you setting the wireless parameters like essid, key, etc? Sounds like they are not being set or not set correctly by whatever method you are using. You can use the linux driver rather than using the windows driver. And don't mix drivers. Remove rt61.ko if you are using ndiswrapper. You can find the Ralink linux driver package at 
[http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm")

The package has the firmware and config file I previously mentioned. I keep going back to this because I could not set various wireless settings (essid, etc) until I used the config file. For instance wireless-mode was rejected by the system (error mssg similar to your essid mssg) when I tried to set it in /etc/network/interfaces and when I used iwconfig, it was ignored. I also find that /etc/init.d/networking is not a reliable way to start wireless connections until after a stable connection has been achieved and the initialization kinks have been smoothed. I use ifconfig, iwconfig, modprobe, and dhclient (for dhcp situations). 

Also, I have forgotten more than once to add a new MAC address to the 'permit' list used by the access point. Just had to mention that.

Hope this helps.

    -w-

---

### Post by misfito on 2007-04-07
Where can I find the ubuntu driver for AWLL3026 802.11g Ultra Slim USB 2.0 Adapter?
Any ideas???
And how do I install it???

---

### Post by glcarteraz on 2007-08-29
I guess my newbie status is with a capital N.  I am trying to config this same wireless USB 2.0 adapter in Kubuntu 6.10 and am clueless.  Turning off IPv6?  I know what IPv6 but I have lived in the world of Windouse OS's and don't even know how to do that!

If there is a How To for this, that shows each detail, I would be grateful.  I could hook up the PC with a hard wired connection but I want to become a Linux guy and that is my "I have to start SOMEWHERE" moment in time.

---

