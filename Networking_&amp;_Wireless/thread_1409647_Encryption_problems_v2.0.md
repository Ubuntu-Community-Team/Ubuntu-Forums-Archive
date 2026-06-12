---
title: "Encryption problems v2.0"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by MrDead on 2010-02-17
A while back I posted ( [http://ubuntuforums.org/showthread.php?t=1342574]("http://ubuntuforums.org/showthread.php?t=1342574") ) a question about Ubuntu 9.10 not recognizing my WEP encryption key. The problem that I had is still essentially the same:> After upgrading to 9.10 beta, then trying to upgrade using the alternate install disc for the full version (because of the same problem) I ended up having to do a completely new installation. Anyhow the problem still stands: my internet card works and it detects available wireless networks, the only thing is that after entering the key in, it will attempt to connect, then after a min or so, it will ask for the key again, ad infinitum. The upshot is that I can't connect to the internet at all. Right now I'm on Windows 7 RC. If anyone has any suggestions, that would be great.
The only thing that has changed is that I tried disabling encryption entirely, and Ubuntu was still not able to connect (I think the connection just timed out after a few minutes). I should add that I have Verizon FiOS, an Actiontec router, and my computer (since it is far away from the router) connects through a Hawking_300N extender. Right now I am using Windows 7 RC (which unfortunately expires in a little over a week), so I can access the internet through Windows, and check for any posts, but I can't immediately provide any command outputs, I'd have to restart, and that would take a few minutes. Further, I have tried both Network Manager and WICD, both of which produced the same results. I have not tried any WPA encryption mainly because the router is shared, and I don't to mess with everyone using the router unnecessarily.    

As always any and all replies are appreciated.

---

### Post by chili555 on 2010-02-18
My suspicion, based on my own experience with extenders, is that your computer can't decide which device, the extender or the router, to associate with. When you are connected in Windows, can you see the MAC address of the device you are connected to? In Linux, it is available in *iwconfig*. For example:> $ iwconfig eth1
eth1      IEEE 802.11abg  ESSID:"mylilrouter"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: [COLOR="Red"]99:24:56:2A:D7:99 [/COLOR]Do the extender and the router have the same ESSID? Is it required? Can you see which device has which MAC address in:```
sudo iwlist wlan0 scan
```

We might get some clues in:```
sudo cat /var/log/messages | grep wlan0
```Substitute your wireless interface, if it's not* wlan0*.

Is this a desktop machine that isn't going down to the coffee shop? If so, may we do away with Network Manager and Wicd and manually specify to which MAC address and ESSID we wish to connect?

---

### Post by MrDead on 2010-02-19
The thing is, both Windows and Ubuntu can see both networks: the extender (Hawking_300N) and the router (6ECL2). However Ubuntu can't connect to either of them. When I ran```
iwconfig wlan0
``` for the Access point I got "not associated"; however, I looked on wicd, and the MAC address for 6ECL2 is 00:1F:90:EE:E1:28 and for Hawking_300N 00:0E:3B:0F:0D:08.

```
sudo iwlist wlan0 scan
``` returned "network is down", and nothing else

```
sudo cat /var/log/message | grep wlan0
``` returned "/var/log/message is not a valid directory" and ```
sudo cat /var/log | grep wlan0
``` returned "/var/log is a directory".

One more thing, in the past I have tried manually connecting w/o wicd or network manager, but to no avail; however, I'd be willing to see if I had done something wrong before.

Thanks so much.

---

### Post by chili555 on 2010-02-19
> "/var/log/message is not a valid directory" Please try:```
sudo cat /var/log/message[COLOR="Red"]s[/COLOR] | grep wlan0
```Thanks.

---

### Post by MrDead on 2010-02-19
Here's what I got:
Feb 18 22:24:14 Maimon kernel: [  339.269140] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:24:22 Maimon kernel: [  347.859833] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:25:42 Maimon kernel: [  427.749143] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:29:12 Maimon kernel: [  636.929250] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:29:24 Maimon kernel: [  649.811976] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:29:36 Maimon kernel: [  661.369433] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:31:01 Maimon kernel: [  746.189462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:32:14 Maimon kernel: [  819.889498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:32:18 Maimon kernel: [  823.729215] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:32:22 Maimon kernel: [  826.971788] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:32:31 Maimon kernel: [  836.889442] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:32:38 Maimon kernel: [  843.541936] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:33:44 Maimon kernel: [  909.159548] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:35:18 Maimon kernel: [ 1003.779500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:35:22 Maimon kernel: [ 1007.119426] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:35:27 Maimon kernel: [ 1012.840023] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:35:34 Maimon kernel: [ 1019.392016] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:35:38 Maimon kernel: [ 1023.535818] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 18 22:36:25 Maimon kernel: [ 1070.439361] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 18 22:36:29 Maimon kernel: [ 1074.599652] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 19 15:07:08 Maimon kernel: [   14.305338] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:07:18 Maimon kernel: [   24.429017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:07:20 Maimon kernel: [   26.302294] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 19 15:08:48 Maimon kernel: [  114.439483] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:08:57 Maimon kernel: [  123.267047] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 19 15:10:44 Maimon kernel: [  230.109462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:10:54 Maimon kernel: [  240.021886] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:10:55 Maimon kernel: [  241.123719] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 19 15:12:00 Maimon kernel: [  306.469260] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:12:01 Maimon kernel: [  307.424481] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 19 15:12:43 Maimon kernel: [  349.789214] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:12:44 Maimon kernel: [  350.040063] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb 19 15:39:47 Maimon kernel: [   12.863136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:39:52 Maimon kernel: [   17.711741] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb 19 15:39:55 Maimon kernel: [   20.142310] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

### Post by chili555 on 2010-02-20
Unfortunately, that doesn't tell us anything useful.

I have some problems with Wicd myself, however, it can connect  automatically in my WEP encrypted network reliably on boot. The settings that work for me are as follows. First, I check off 'Automatically connect to this network' as per attached. Next, I select 'Properties' and enter all my details; see my second attachment. Finally, my */etc/network/interfaces* file is:```
auto lo
iface lo inet loopback
```My computer is connected at boot.

If you try the steps and it still doesn't work, you might have a look at */var/log/wicd/wicd.log*. Post any suspicious entries and we will be glad to help you.

---

### Post by northd_tech on 2010-02-20
Have you tried cabling into the router and checking its settings, MrDead?  Usually you just open a web browser and type something like 192.168.0.1 and then a username and password.  The procedure should be in the documentation for your router- maybe you can download a .PDF from their website if you don't still have the manual.

I know that at my university, we customized our Linux to only allow connections from select few MAC addresses for security reasons.  Some routers can "learn" or have a list of preferred MAC addresses to accept or reject.

I'm not sure this is your problem, but it might be a possibility.  Also are you sure you have wireless-tools installed completely?

[https://launchpad.net/ubuntu/+source/wireless-tools](https://launchpad.net/ubuntu/+source/wireless-tools)

You might want to search for "wireless-tools" in Synaptic Package Manager so that it can configure everything for you.

---

### Post by MrDead on 2010-02-21
Attached is the content of /var/log/wicd/wicd.log. I doubt it will be terribly helpful. I had my settings as you described them above. Also I checked, and my wireless-tools package is up to date.

---

### Post by MrDead on 2010-02-23
If there is anybody who was any ideas, help would be much appreciated. My Windows 7 RC is about to run out, and I would be loathe to buy a whole new Windows operating system just because of some glitch that I can't figure out.

---

### Post by MrDead on 2010-02-25
Update: I tried connecting manually by changing /etc/network/interfaces to:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid mylilrouter
wireless-key 1234567890 

#auto eth0
iface eth0 inet dhcp
```When I used the network 6ECL2 (the original router network) I got some network activity on the system monitor, but I could still not connect to Google on Firefox, and I couldn't ping Google.com. However, when I used Hawking_300N_Extender (the range extender network) I got no activity and no connection.

---

### Post by chili555 on 2010-02-25
Please try this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid Hawking_300N    <--double-check the essid!
wireless-ap 00:0E:3B:0F:0D:08
wireless-key <your_WEP_key>

#auto eth0
iface eth0 inet dhcp
```You might have to amend /etc/resolv.conf to add:```
nameserver 192.168.ip.of.your.gateway
```Now restart networking:```
sudo /etc/init.d/networking restart
```

---

### Post by MrDead on 2010-02-25
I did what you instructed above for both networks as best as I could, but to no avail. I just wanted to make sure I understood what you meant by a few things. First for the "Wireless-ap" line, was I supposed to change anything? Second, for the /etc/resolv.conf amendation, did you want the local ip adress of the network device I was connecting to (i.e. the Hawking_300N is 192.168.1.8 and the 6ECL2 is 192.168.1.1)? Finally, did you want me to reboot my machine completely, or just enter in the code you posted?

Everytime I tried that code the dhcp timed out, and I only saw a flicker of network activity once.

---

### Post by chili555 on 2010-02-25
The wireless-ap line should be the MAC address of the Hawking device; you gave that to me in post #3. Please double-check it. Also, the wireless-essid should be the ESSID of the Hawking device. In post #3, you said it was Hawking_300N, but later (post #10 ), it was evidently Hawking_300N_Extender. Your *interfaces* file needs the exact wording.

Last, the *resolv.conf* file should show the IP address of the gateway of the one device in the mix that is the DHCP server, I hope, the 6ECL2. 

We are attempting to force your machine to go through the extender to the gateway (6ECL2) to get both a DHCP IP address and domain name service (DNS) resolution.

---

### Post by MrDead on 2010-02-25
OK I tried all that, and different combinations of networks/gateway addresses/MAC addresses, but still nothing happened. However, I looked up one thing which might be irrelevant, but I noticed the command ```
iwlist channel
``` gives me this:
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

But I looked on my extender's config page, and it says it's broadcasting on channel 11. I don't know if this means anything, but I thought I'd post it anyway.

---

### Post by chili555 on 2010-02-25
Does:```
sudo iwlist wlan0 scan
```tell us that *both* the router and the extender are on channel 11? Substitute your interface, if it's not wlan0. Your computer should figure the correct channel out automatically without human intervention.

---

### Post by MrDead on 2010-02-25
Yeah, both networks are on channel 11.

---

### Post by chili555 on 2010-02-25
With the double-checked ESSID, MAC address and WEP key in */etc/network/interfaces, * what happens at:```
sudo dhclient wlan0
```

Is Network Manager removed? Is Wicd removed?

---

### Post by MrDead on 2010-02-25
Here's what I get:
sudo dhclient wlan0

maimon@Maimon:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:e7:4a:48:b6
Sending on   LPF/wlan0/00:18:e7:4a:48:b6
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

As far as WICD and NM go, I opted for the "remove" option in synaptic manager as opposed to the "remove completely." I hope that doesn't make too much of a difference. Either way, they don't show up on the process list in the system monitor.

---

### Post by MrDead on 2010-02-28
Does anyone have any further ideas, I only have one day left, before I have buy Windows 7. I hope someone can help.

---

