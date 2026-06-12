---
title: "Kernel related IPV4 Wifi connection problem"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by Irv2 on 2010-04-02
I have several kernels remaining on my PC, from 2.6.18.13 up to 2.6.31.20 (but with several missing between).  I am using a Belkin FSD7050 Wifi USB Network Adapter connecting to a Netgear DGN2000 router.  I am using WPA/WPA2 encryption.

When I boot using kernel 2.6.18.13 I get immediate wifi connection.  When I boot with a kernel from 2.6.18.14 onwards, the router ESSID is shown in the Network Manager Applet, but it continually fails to connect.

After much browsing (I am a bit new to Linux/Ubuntu) I think I have identified that the .13 kernel starts IPv4 automatically but that later kernels are attempting to start IPv6 and do not start IPv4?  Of course neither my Wifi adpater nor my router support IPv6.  I have reached this conclusion (but realise I may still be mis-diagnosing the problem) through looking at the kernel ring-buffer using dmesg.  The output from dmesg is as follows:

                                 [COLOR=#000000]**root@Irv2:/home/keith# dmesg|grep wlan0 **[/COLOR] 
 [COLOR=#000000][   42.076990] ADDRCONF(NETDEV_UP): wlan0: link is not ready [/COLOR] 
 [COLOR=#000000]root@Irv2:/home/keith# dmesg|grep wlan0 [/COLOR] 
 [COLOR=#000000][   42.076990] ADDRCONF(NETDEV_UP): wlan0: link is not ready [/COLOR] 
 [COLOR=#000000][  161.516267] wlan0: authenticate with AP 00:22:3f:56:0e:16 [/COLOR] 
 [COLOR=#000000][  161.518273] wlan0: authenticated [/COLOR] 
 [COLOR=#000000][  161.518277] wlan0: associate with AP 00:22:3f:56:0e:16 [/COLOR] 
 [COLOR=#000000][  161.520508] wlan0: RX AssocResp from 00:22:3f:56:0e:16 (capab=0x411 status=0 aid=2) [/COLOR] 
 [COLOR=#000000][  161.520513] wlan0: associated [/COLOR] 
 [COLOR=#000000][  161.528800] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready [/COLOR] 
 [COLOR=#000000][  171.712017] wlan0: no IPv6 routers present [/COLOR] 
 [COLOR=#000000][  208.523931] wlan0: disassociating by local choice (reason=3)[/COLOR]
 
Did something change between the .13 kernel and the .14 kernel that leaves IPv4 out of the Network configs defaults?  Obviously between each boot I am not touching any of the /etc/network files - the only change is the kernel.....and I can boot backwards and forwards and the network will connect/fail accordingly.

If something did change, how do I re-enable IPv4?  I did read a post about IPv6 possibly causing problems and about disabling it in a network aliases file, but my system does not have such a file, so I assume that was referring to an earlier release - and I am only guessing that disabling IPv6 might have the effect of enabling IPv4, and that sounds to me like a long shot.

Any advice would be gratefully received.

---

### Post by chili555 on 2010-04-02
> I am not touching any of the /etc/network filesNetwork Manager has difficulty working with a populated (beyond loopback) */etc/network/interfaces* file. Recent kernels seem to want one or the other but not both. If you back up */etc/network/interfaces* and then amend it to just the loopback stanza and restart both NM and networking, does it connect?> wlan0: no IPv6 routers present  This is not relevant to the problem; it appears in every *dmesg*, if there are no IPv6 routers present. It may safely be ignored.

---

### Post by Irv2 on 2010-04-02
Under a working .13 kernel, ifconfig gives me:

  	 	 	 	 	 	  wlan0     Link encap:Ethernet  HWaddr 00:11:50:3e:99:91   
                [COLOR=#ff0000] inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0 [/COLOR] 
                 inet6 addr: fe80::211:50ff:fe3e:9991/64 Scope:Link  
                UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
                RX packets:344 errors:0 dropped:0 overruns:0 frame:0  
                TX packets:40 errors:0 dropped:0 overruns:0 carrier:0  
                collisions:0 txqueuelen:1000  
                RX bytes:114856 (114.8 KB)  TX bytes:6303 (6.3 KB)  
 
I colour coded the "inet"  line 'cause that is different from the non working .14 kernel ifconfig:

  	 	 	 	 	 	  wlan0     Link encap:Ethernet  HWaddr 00:11:50:3e:99:91   
                inet6 addr: fe80::211:50ff:fe3e:9991/64 Scope:Link  
                UP BROADCAST MULTICAST  MTU:1500  Metric:1  
                RX packets:42 errors:0 dropped:0 overruns:0 frame:0  
                TX packets:13 errors:0 dropped:0 overruns:0 carrier:0  
                collisions:0 txqueuelen:1000  
                RX bytes:11533 (11.5 KB)  TX bytes:2660 (2.6 KB)
 
which is what led me to look for why IPv4 wasn't starting?

---

### Post by chili555 on 2010-04-02
That simply means you didn't connect; that is, the system was not able to get an IP address. The IP address, indicative of a successful connection, is present in the first example and not in the second.

---

### Post by Irv2 on 2010-04-03
OK, I have now had a chance to check what is in my /etc/network/interfaces file and it looks top me like it only has the loopback stanza.  It only has 2 lines in it:

auto lo
iface lo inet loopback

....and that is the same interfaces file for the working .13 kernel and the non working more recent kernels.

---

### Post by chili555 on 2010-04-03
Perhaps the problem is in the wireless driver. I'm shocked, because wireless drivers just never cause any problems, har har har!

First, let's see what driver is being used. Please do:```
lshw -C network
```One part will relate to your ethernet and one to wireless. We need to know the wireless drivers name. Here is my example, trimmed:> *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
      --- snip ---
 [COLOR="Red"]driver=ipw2200[/COLOR] driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.105
 --- snip ---
You might also run:```
dmesg | grep <driver_you_found>
```Since Network Manager is managing your network connections, you could also check:```
sudo cat /var/log/syslog | grep -i network
```Be sure to run these tests in the latest kernel when you do *not* connect.

---

### Post by Irv2 on 2010-04-04
Thank you chili555, I think you have moved me forward a few stages with those comments.

Firstly I tried the "lshw -C network" option, but the driver did not show up in that listing.  I would guess that might be because my Wifi device is not a card but a usb dongle device.  So I browsed around the kernel ring buffer and from the lines:

[   35.496295] Registered led device: rt2500usb-phy0::radio 
[   35.496316] Registered led device: rt2500usb-phy0::quality 
[   35.496970] usbcore: registered new interface driver rt2500usb 

I would guess the driver in question is "rt2500usb".  However, it looks like the same driver is getting loaded in both my .13 kernel and in my .20 kernel (or are drivers like these built into the kernel?).

So, I tried your "syslog" file which had some interesting stuff in it, that I think moves me forward.  The .20 kernel (non-working) log entries show that the initial connection to the router is working, but when DHCP gets loaded with a 45 second timeout interval, the interval elapses without a successful DHCP capture if the various addresses and mask.  However, if I go back to the working .13 kernel, DHCP captures the addresses within 1 second.
_______________________________________
*Syslog extract from 2.6.31.20 kernel (non working):*
                                 Apr  4 12:05:13 Irv2 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)  
 Apr  4 12:05:14 Irv2 NetworkManager: <info>  dhclient started with pid 1602  
 Apr  4 12:05:14 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...  
 Apr  4 12:05:14 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.  
 Apr  4 12:05:14 Irv2 NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit  
 Apr  4 12:05:14 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...  
 Apr  4 12:05:14 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.  
 Apr  4 12:05:59 Irv2 NetworkManager: <info>  (wlan0): DHCP transaction took too long, stopping it.  
 [I]
....and the entries thereafter are about shutting down wlan0[/I]
_____________________________________
*Syslog extract from 2.6.28.13 kernel (working):*
                                 Apr  4 11:26:07 Irv2 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)  
 Apr  4 11:26:07 Irv2 NetworkManager: <info>  dhclient started with pid 1771  
 Apr  4 11:26:07 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...  
 Apr  4 11:26:07 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.  
 Apr  4 11:26:07 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...  
 Apr  4 11:26:07 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>    address 192.168.0.50  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>    prefix 24 (255.255.255.0)  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>    gateway 192.168.0.1  
 Apr  4 11:26:08 Irv2 NetworkManager: <info>    nameserver '192.168.0.1'  
 
*.....and the connection is made*
________________________________________________
Since there is a huge disparity in the wait times, I would not expect increasing the 45 second wait time would make any difference.  The problem must lie in the DHCP process or protocol?  What do you think?
As an aside, thank you for your assistance - I am finding this a really good learning curve as to how Linux/Ubuntu "ticks".

---

### Post by chili555 on 2010-04-04
> are drivers like these built into the kernel?Yes, indeed. As well, other, sometimes conflicting drivers get built-in, too. That may be the problem. 

You were quite right that USB devices won't show up in *lshw*. Hey, I took my best shot! It was either built in, USB or PCMCIA.

Let's take a look at 'list all my USB devices' and 'list all the loaded modules with rt2 in the name.' Please post:```
lsusb
lsmod | grep rt2
```If conflicting drivers are loading, we'll blacklist them and your device should work correctly.

---

### Post by Irv2 on 2010-04-04
Strangely, when I use "lsusb" on my working .13 kernel, I get a null response.  With the failing .20 kernel, I get:

                                 > [COLOR=#000000]**root@Irv2:/home/keith# lsusb **[/COLOR] 
 [COLOR=#000000]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/COLOR] 
 [COLOR=#000000]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/COLOR] 
 [COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/COLOR] 
 [COLOR=#000000]Bus 001 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi [/COLOR] 
 [COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/COLOR] 
 > [COLOR=#000000]**root@Irv2:/home/keith# lsmod|grep rt2 **[/COLOR] 
 [COLOR=#000000]rt2500usb                  21152     0 [/COLOR] 
 [COLOR=#000000]rt2x00usb                  11548     2    rt73usb,rt2500usb [/COLOR] 
 [COLOR=#000000]rt2x00lib                    29756      3    rt73usb,rt2500usb,rt2x00usb [/COLOR] 
 [COLOR=#000000]led_class                      4096     2    p54common,rt2x00lib [/COLOR] 
 [COLOR=#000000]input_polldev             3716     1    rt2x00lib [/COLOR] 
 [COLOR=#000000]mac80211                181140    4    p54usb,p54common,rt2x00usb,rt2x00lib [/COLOR] 
 [COLOR=#000000]cfg80211                     93052     3    p54common,rt2x00lib,mac80211 [/COLOR][COLOR=#000000][/COLOR]

---

### Post by chili555 on 2010-04-04
Ah, ha! Just for the intellectually curious:> Bus 001 Device 002: ID [COLOR="Blue"]050d:7050[/COLOR] Belkin Components F5D7050 ver 1000 WiFi  > $ modinfo p54usb | grep 7050
alias:          usb:v[COLOR="Blue"]050D[/COLOR]p[COLOR="Blue"]7050[/COLOR]d*dc*dsc*dp*ic*isc*ip*
$ modinfo rt2500usb | grep 7050
alias:          usb:v[COLOR="Blue"]050D[/COLOR]p[COLOR="Blue"]7050[/COLOR]d*dc*dsc*dp*ic*isc*ip*
$ modinfo rt73usb | grep 7050
alias:          usb:v[COLOR="Blue"]050D[/COLOR]p[COLOR="Blue"]7050[/COLOR]d*dc*dsc*dp*ic*isc*ip*So, indeed, *three* drivers claim this device and conflict. The trick is to determine which set, the rt2500 boys or otherwise, will do the best job and blacklist the others. I have googled a bit and found no concensus. Let's start out with the rt2500 suite and blacklist the others. We'll see how it works and adjust as needed. We are going to amend a file and remove un-needed drivers. Remove your little Belkin and open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a few lines:```
blacklist rt73usb
blacklist p54usb
blacklist p54common
```Proofread, save and close gedit. Now let's remove the offending drivers:```
sudo rmmod -f rt73usb
sudo rmmod -f p54usb
sudo rmmod -f p54common
```Now, reinsert the device. Is it working correctly? If not, we can tweak.

---

### Post by Irv2 on 2010-04-05
I am still in the process of trying out the various permutations of drivers and will continue to do so.  However, I had a couple of those "brain free running" thoughts as you wake up in the morning and that is - wouldn't a WiFi usb adapter have 3 drivers associated with it anyway?  One for the usb internal hub, one for the usb port and one for the usb device?....or am I just guessing wildly?

The other thought was that since my working .13 kernel gets a successful DHCP response in under a second (and it looks to me that the kernel ring buffer clock resolution is just to the nearest second - so 1 second may be a wild over estimate) and the non working kernels thereafter timeout after 45 seconds with not having received a response from DHCP.  Isn't it more likely that the non-working kernels fail to "listen" for the response quickly enough.  In other words, in the sequence of things in the driver, could it still be busy initialising itself after it has sent out the DHCP request and in so doing, miss the vital response?

I have had a few instances of the .13 kernel not establishing a connection - could it be that if the system is busy doing other initialisation things that the driver in the working kernel barely gets enough clock cycles to capture the DHCP response and due to enhancement in the non-working kernels does not get enough clock cycles?  I assume once it gets going properly, the handlers input and output streams are dealt with simultaneously, but could it be just during initialisation they are dealt with serially or the receive buffer is not made ready quickly enough...or something along those lines?

Anyway, having documented those thoughts I will get back to trying various combinations of driver blacklisting.  I certainly am only scratching the surface of Linux internals and am no where close enough to rule out driver clashes.  

Of the permutations I have tried, some of them stop wifi from initialising all together (eg. blacklisting rt2500usb but none of the others) and the Network Manager Applet has no wireless menu options yet the network definitions within Network Manager does have a wifi definition - I think that just means the software has not detected a wifi capability?  I am now trying to blacklist each permutation to see if, by observing what works and what doesn't work, I can work out how each driver contributes to a working system.

---

### Post by chili555 on 2010-04-05
> Of the permutations I have tried, some of them stop wifi from initialising all together (eg. blacklisting rt2500usb but none of the others) and the Network Manager Applet has no wireless menu options yet the network definitions within Network Manager does have a wifi definition - I think that just means the software has not detected a wifi capability? I am now trying to blacklist each permutation to see if, by observing what works and what doesn't work, I can work out how each driver contributes to a working system.Be sure you blacklist not just a single driver, but also it's dependencies; it's dependencies that are not also dependencies of the driver you want to keep.

Kinda complicated, isn't it! You can learn a lot from:```
modinfo <your_driver>
```We see that the following go or stay together:

rt2500usb with rt2x00usb and rt2x00lib

rt73usb with rt2x00usb and rt2x00lib

p54usb with p54common

As you can see, if you blacklist rt73usb and rt2x00usb and rt2x00lib, then rt2500usb will not work correctly. Since you have *three* drivers that claim your device, you must blacklist *two* in order to get wireless working correctly.

The question remains. Which of these suites, by experimentation and observation, will drive your device the best. The searchers and I will be interested to learn.

---

### Post by Irv2 on 2010-04-05
Ah! I see what you mean.  There will be a delay of a couple of days while I work that lot out.  Thank you for your help.  I will get back as soon as I have tried the combinations.

---

### Post by Irv2 on 2010-04-11
I have now had a chance to try all (I think) the options around those usb/WiFi drivers and the results are as follows:

All tests undertaken with kernel 2.6.31.20

1. Using rt2500usb, rt2x00usb and rt2x00lib, and blacklisting rt73usb, p54usb and p54common, I get a visible router and WiFi options in NetworkManager applet, but "syslog" shows DHCP timeout on attempted WiFi establishment.

2. Using rt73usb, rt2x00usb and rt2x00lib, and blacklisting rt2500usb, p54usb and p54common, I get NO wireless recognition or options in NetworkManager and "syslog" shows 
SCPlugin - Ifupdown ... get connections... gets an empty list returned

3. Using p54usb and p54common, and blacklisting rt2500usb, rt73usb, rt2x00usb and rt2x00lib, I get NO wireless recognition or options in NetworkManager and "syslog" shows
SCPlugin - Ifupdown ... get connections... gets an empty list returned

4. Using rt2500usb, rt73usb, rt2x00usb and rt2x00lib, and blacklisting p54usb and p54common, I get a visible router and WiFi options in NetworkManager applet, but "syslog" shows DHCP timeout on attempted WiFi establishment.

5. Using rt2500usb, rt2x00usb, rt2x00lib, p54usb and p54common, and blacklisting rt73usb, I get a visible router and WiFi options in NetworkManager applet, but "syslog" shows DHCP timeout on attempted WiFi establishment.

6. Using rt73usb, rt2x00usb, rt2x00lib, p54usb and p54common, and blacklisting rt2500usb, I get NO wireless recognition or options in NetworkManager and "syslog" shows
SCPlugin - Ifupdown ... get connections... gets an empty list returned

7. Using all drivers as stated originally, I get a visible router and WiFi options in NetworkManager applet, but "syslog" shows DHCP timeout on attempted WiFi establishment.....and when I revert to kernel 2.6.28.13 with all drivers, I get successful DHCP and the WiFi connection is established.

I think the synopsis of the above is that the rt2500usb driver (and its dependencies) has to be there for wifi hardware to be identified as present and for a PC / router dialogue to start, but that kernel .13 is the other necessary condition for full connection.  Having described the above, I have just realised I have one more test to try and that is using rt2500usb driver alone in a .13 kernel.......more to follow when I have done that.

---

### Post by Irv2 on 2010-04-11
.....and with only rt2500usb, rt2x00usb and rt2x00lib, and blacklisting rt73usb, p54usb and p54common, but this time using the 2.6.28.13 kernel, I still get successful Wifi connection.

I guess that proves the rt2500usb driver and its dependencies are the successful drivers, but that kernel .13 is the other necessary condition.  

It also suggests that while rt73usb and p54usb drivers probably are not required for this Belkin usb wifi dongle, I am leaning more to them being a red herring and more towards (as I was getting to in response 11 above) some change in the DHCP handling (or other code executing at the same time, robbing CPU cycles from DHCP handling) when the 2.6.28.14 kernel was introduced that means the DHCP client misses the DHCP router response and as a result times out whilst waiting for it.

---

### Post by Irv2 on 2010-04-25
Having now browsed around the internet for a resolution to my problem, it looks like there may be a ready made solution at:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29")

I will try it and post the results I get.

The link above explains a procedure related to an earlier version of Ubuntu and I note that it contains a link to an updated driver which is no longer a valid link.  The drivers are now located at:

[http://www.ralink.com.tw/support.php?s=2](http://www.ralink.com.tw/support.php?s=2)

Ooops - 9hrs later!  Looks like that posting is a rather old posting.  Following through the links, I guess the rt73usb driver and dependencies have been absorbed into the official Ubuntu release and I guess the drivers I have been blacklisting and unblacklisting are those from the rt2x00 project now in mainstream Ubuntu.  So not much point trying those drivers, they are the same ones.  However, anyone needing to insert new driver should read that "help.ubuntu.com" link. it gives a really clear step-by-step how-to for installing new wifi drivers.

---

