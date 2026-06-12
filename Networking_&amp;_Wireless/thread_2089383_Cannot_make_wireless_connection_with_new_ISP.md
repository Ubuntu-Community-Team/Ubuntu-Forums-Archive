---
title: "Cannot make wireless connection with new ISP"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by foursavages on 2012-11-29
I decided to write because I am having difficulty establishing a connection with one of my laptops. which is partitioned. The side that runs Ubuntu 10.04 does not connect with the wireless router. The other side, running Windows XP, connects fine. Two other laptops (running Windows) and two hard wired computers (one Mac and one running Ubuntu 10.04) are working with good speeds.

It was after switching my Internet Service Provider, that I noticed with this one laptop, the connection was not working. It still works on the Windows side and with Qwest, but I want to stop using Qwest and go with my new ISP (Comcast).

Nothing has changed on any of the settings on any computer, including the laptops. We ran an ethernet cable directly to the wireless router from the laptop with an immediate connection running the Linux side of that laptop. That tells me that the wireless router is functioning; well…the other laptops function also showing me that the router is not the issue.

Here again is my network/computer configuration:

One MacIntosh running OS 10.4 connected via ethernet - works fine

Two laptop PCs running windows wireless connections  - both connect just fine

One PC running Ubuntu 10.04 connected via ethernet - connecting perfectly

One laptop partitioned, one side running windows - wireless connection works. The other partition running Ubuntu 10.04, does NOT connect wireless, but does connect via ethernet.

This is all running through a netgear wireless router. Everything worked perfectly when our ISP was Qwest(now called Centurylink), but now that we are using Comcast the one partition on the laptop using Ubuntu does not connect. I have tried deleting all of the auto network connections and reconnecting, changing my router security settings from WPA/WPA2 to WEP and back, rebooting the router and modem and other stuff I can't remember. The only thing I haven't tried was trying to connect using terminal.All of the available neighborhood wireless networks show up. Sorry for any redundancy, I just wanted to make sure I got all the info. Any help anyone can give would be appreciated. Thanks!

---

### Post by Bucky Ball on 2012-11-29
*Thread moved to **Networking & Wireless***


Welcome to the forums. 
  
Do you know what security the router uses rather than guessing? The router IP address will be something like 192.168.0.1 (check the manual). Put that into the address bar of a browser and it will take you to the router config where you can check the security type and things. What security are the other computers using??? WEP, WPA? Stick with the correct type to avoid confusion. Then you have one other certainty.

You see your own network along with others? What exactly happens when you click and try to connect to your LAN?

Please open a terminal and paste in these two commands, one at a time: 

```
iwconfig
sudo lshw -C network
```Post the output back here and that will give us a better picture. Also, I figure you have opened Network Manager at the wireless tab on the 10.04 LTS boot on the other machine, which has wireless, and same on the laptop and made sure they are *identical*?

---

### Post by westie457 on 2012-11-29
Welcome to the Forums.

Go to here. [http://ubuntuforums.org/showpost.php?p=12377709&postcount=5](http://ubuntuforums.org/showpost.php?p=12377709&postcount=5)

Follow the directions please. They are self-explanatory on what information is gathered and what is removed for security reasons.

---

### Post by foursavages on 2012-11-29
The security setting on my router is WPA-PSK [TKIP] + WPA2-PSK [AES]. I have been using this setting for my router since I hooked it up about a year ago. I only tried changing it once yesterday to WEP just to see if I could hook up in any way through the Ubuntu partitioned laptop without success. When I try to connect I click on the widget to view available networks, then choose my network, for the wireless security, is set to WPA&WPA2, I type in the password. It tries to connect for approximately one minute then says "Wireless Network: you are now offline".

When I type in iwconfig this is the result:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

When I type in sudo lshw -C network this is the result(I have ommitted private info):

 *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:ef:f3:8e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5753m-v3.56 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f4100000-f410ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:1c:c6:41
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:f4000000-f4000fff

To clarify, I only have one laptop running Ubuntu 10.04. The other two laptops in the house are running Windows, and both connect. I do have a hardwired computer running Ubuntu 10.04 which also connects fine using ethernet. 

Hope this helps! 
Thanks for your post.

---

### Post by foursavages on 2012-11-29
> **westie457 said:**
> Welcome to the Forums.

Go to here. [http://ubuntuforums.org/showpost.php?p=12377709&postcount=5](http://ubuntuforums.org/showpost.php?p=12377709&postcount=5)

Follow the directions please. They are self-explanatory on what information is gathered and what is removed for security reasons.
[westie457]("http://ubuntuforums.org/member.php?u=970779") I followed your instructions, and here is the result:

#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt

Thanks for your post, I hope it helps you.

---

### Post by plucky on 2012-11-29
You need to post the **netinfo.txt** file not the **wireless_script** file.


Good Luck

---

### Post by Bucky Ball on 2012-11-29
Hmm, that is all looking good. I advise 'Edit Connections' and set it up there. Put the name of your access point/router/network in there and the security details directly. 

Yes, that card appears to be up and running but not associated with your access point.

---

### Post by foursavages on 2012-11-29
> **Bucky Ball said:**
> Hmm, that is all looking good. I advise 'Edit Connections' and set it up there. Put the name of your access point/router/network in there and the security details directly. 

Yes, that card appears to be up and running but not associated with your access point.


I am a newbie esp. at Ubuntu...having a really hard time.  I was trying  something--wicd and it didn't work. I uninstalled it, and then the wired  network applet went missing.  We plugged in the ethernet cable and it  reappeared, but it says, "Wireless network is unmanaged." lol! I made  the problem worse.  

As for the suggestion, I found "Edit  Connections."  I don't know where to find "access point/router/network  in there and the security details directly."  Someone told me upgrading  to 12 might solve the problem.  Do you have any suggestions?

---

### Post by Bucky Ball on 2012-11-30
Right click the network icon
Edit Connections
Wireless Tab

If your network is not there, add it with the correct details. When you add it:

* Make sure 'Connect Automatically' and 'Available to all users' are ticked;
* In the wireless tab at SSID make sure you have the name of your network and mode=infrastructure;
* IPv4 tab ... method=automatic (dhcp) ... probably, unless you are using a static IP address which changes things;
* IPv6 tab ... method=ignore ... this might actually be your problem;
* Wireless Security tab = make sure all the right security details are in there.

How'd that all go?

Another possibility is your wireless card has N capabilities. I've noticed that can be problematic but not really my area. Maybe those in the know might jump in here ...

---

### Post by foursavages on 2012-11-30
Thanks. I am going to look all of that stuff over again. I think it is set up like you said.  I might try reconfiguring the whole router.  I wonder if the mistake is there. This is really weird.  So glad someone is trouble shooting with me.

---

### Post by foursavages on 2012-12-02
After a long night and someone in Seattle giving step by step guidance, we were able to establish a connection. We upgraded to 12.04 with a thumbdrive.  It connected but Firefox wouldn't work.  Then, we set the router to default, lowered security, and it connected. Then, we changed to a secure setting...it worked.  It appeared to be the type of security chosen.  I could give a better explanation, but I am wiped.  Still likely might have questions, but I have to call it a night. Thanks for the input.

---

