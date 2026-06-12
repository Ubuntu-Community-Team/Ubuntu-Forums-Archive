---
title: "Can not Obtain IP address on wireless network"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by SteelGuy21 on 2010-02-19
Need a little help here.  I believe I have the wireless card installed properly and wicd sees the router.  When I try to connect I get an error "can not obtain IP address"  Output from iwcongif and lspci is....  Thanks

dillan@dillan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:43/70  Signal level:-57 dBm  Noise level:-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dillan@dillan-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 12)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 12)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 12)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage 128 Pro Ultra TF [1002:5446]
02:08.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
02:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
dillan@dillan-desktop:~$

---

### Post by Julita on 2010-02-19
Sometimes you have to disable wired connection for the wireless to work. To do that, go to System->Administration->Networking, properties for eth0, uncheck the box and reboot. Later, you will be able to check the box again.

---

### Post by SteelGuy21 on 2010-02-19
The box is unchecked.  It there a different way to disable the card?

---

### Post by Julita on 2010-02-19
Then try this:
ifconfig eth0 down

EDIT:
to enable it,
ifconfig eth0 up

---

### Post by Julita on 2010-02-19
You can also look at /etc/wicd/wireless-settings.conf if everything is as it should be.

---

### Post by SteelGuy21 on 2010-02-19
Still the same....Rebooted and unplug the cable, still not able to obtain IP address

---

### Post by Julita on 2010-02-19
Then post please
lshw -class network

---

### Post by SteelGuy21 on 2010-02-19
Ok here you go....



dillan@dillan-desktop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: wifi0
       version: 01
       serial: 00:05:5d:da:af:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=hostap firmware=1.3.5 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11-DS
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:76:74:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.50.11 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
dillan@dillan-desktop:~$ 
dillan@dillan-desktop:~$

---

### Post by SteelGuy21 on 2010-02-19
of course right now I have the wire connection so that I can access the internet.

---

### Post by Julita on 2010-02-19
gksu gedit /etc/modprobe.d/blacklist
Add those to the file
blacklist hostap
blacklist hostap_cs
blacklist hostap_pci
gksu gedit /etc/modules and add the line
orinoco_pci

---

### Post by Julita on 2010-02-19
You have wireless network disabled. If you are using laptop, have you switched on the wireless card? 
To enable wireless, try
iwconfig wifi0 up

---

### Post by SteelGuy21 on 2010-02-19
Julita when I try these commands in terminal I get nothing.  When I try to modify the file with file manager it tells me I can't open the file to write, although it actually opens the file so I can see the contents of it.  What am I doing wrong?

---

### Post by Julita on 2010-02-19
OK then try with
sudo gedit /etc/modprobe.d/blacklist
Add those to the file
blacklist hostap
blacklist hostap_cs
blacklist hostap_pci
sudo gedit /etc/modules and add the line
orinoco_pci

---

### Post by SteelGuy21 on 2010-02-19
This is what I get when that is put into terminal....

dillan@dillan-desktop:~$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for dillan: 
sudo: gedit: command not found
dillan@dillan-desktop:~$ 


I did not tell you that I am running 8.04...it that matters...

---

### Post by Julita on 2010-02-19
Oh, I see... You have no gedit. For kubuntu, I think it's kate default "notepad," right? So you just replace gedit with kate.

---

### Post by SteelGuy21 on 2010-02-19
Julita

I apologize again I believe I am running xubuntu instead of k

---

### Post by Julita on 2010-02-19
OK, then replace gedit with mousepad and sudo with gksu :) By the way, wicd does not work for my wireless in Xubuntu, only Network Manager.

---

### Post by SteelGuy21 on 2010-02-19
Julita,

Ok I've made all the changes you recommended.  Went back to network manager and now I can't even see the router.  Here's the lastest lshw

dillan@dillan-desktop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:76:74:b7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.50.11 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes
dillan@dillan-desktop:~$ 

Now the card seems to be unclaimed?

---

### Post by Julita on 2010-02-19
Network unclaimed because the network is not recognized. OK, now you have to undo the changes, remove the blacklisted modules and remove the line orinoco_pci from modules as well. Reboot and try using network manager. If it doesn't help, try again
iwconfig eth0 down
iwconfig wifi0 up
If it doesn't help, try
iwconfig wlan0 up (it seems the only one with the "available" wireless extension, but the wireless card is linked to wifi0 still)

---

### Post by SteelGuy21 on 2010-02-19
Julita,

It doesn't recognize the down command...

dillan@dillan-desktop:~$ iwconfig eth0 down
iwconfig: unknown command "down"
dillan@dillan-desktop:~$ 

I appreciate the time your taking to help me with this....

---

### Post by Julita on 2010-02-19
OH my, OK, there is another set of commands
sudo ifconfig eth0 down
sudo ifconfig wifi0 down
dhclient -r wifi0
ifconfig wifi0 up
iwconfig essid your_essid (do you know it?)
iwconfig wifi0 mode Managed
sudo dhclient wifi0
Do you have any errors after the aforementioned commands? When I connect to my wireless, I press network-manager icon and choose the name of my network (there are many on the list). Which errors does Network Manager post? wicd does not work with my wireless, the same error as you have.

---

### Post by SteelGuy21 on 2010-02-19
ALl kinds of bad stuff ;)

dillan@dillan-desktop:~$ sudo ifconfig eth0 down
[sudo] password for dillan: 
dillan@dillan-desktop:~$ sudo ifconfig wifi down
wifi: ERROR while getting interface flags: No such device
dillan@dillan-desktop:~$ sudo ifconfig wifi0 down
dillan@dillan-desktop:~$ dhclient -r wifi0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
dillan@dillan-desktop:~$ ifconfig wifi0 up
SIOCSIFFLAGS: Permission denied
dillan@dillan-desktop:~$ iwconfig essid jerrysbelkin54g
iwconfig: unknown command "jerrysbelkin54g"
dillan@dillan-desktop:~$ iwconfig wifi0 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wifi0 ; Operation not permitted.
dillan@dillan-desktop:~$ sudo dhclient wifi0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
receive_packet failed on wifi0: Network is down
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dillan@dillan-desktop:~$ 

I need to leave for a few hours but I'll check on your response when I get back.

Thanks Again !

Jerry

---

### Post by Julita on 2010-02-19
You will say "thank you" when we have your wireless :) The errors that you have is largely because you have typed it as a user, not as a root.
sudo ifconfig wifi0 up
iwlist wifi0 scanning
sudo iwconfig wifi0 essid your_essid (for correct name see iwlist)
sudo iwconfig wifi0 key your_key (if you have WPA or WEP)
sudo dhclient
ping ubuntuforums.org (to see if everything goes flawlessly)

---

### Post by Julita on 2010-02-19
Truth to be told, when I saw this - [http://ubuntuforums.org/archive/index.php/t-1019818.html](http://ubuntuforums.org/archive/index.php/t-1019818.html) (go to the last post, where the solution is provided for your card configuration for Ubuntu) - I understood why it was very hard to set up your wireless. If my previous post won't help, you should look at this topic. Oh my... I also had problems with wireless - my card was not supported until recently, and I had to install the driver; it was quite a challenge because I didn't have a wired network...

---

