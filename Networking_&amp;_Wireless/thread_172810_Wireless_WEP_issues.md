---
title: "Wireless WEP issues"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by ChristopherTeague on 2006-05-09
I've been trying to connect my dell PC running Ubuntu to the internet through my Netgear WG311t wireless card (madwifi driver).  When I disabled WEP on the router, I could connect, but after enabling it (128 bit) and entering the key in my Linux machine, I could no longer connect.

Now, I know what you're thinking, but I've checked the WEP key so many times that I know it can't be the problem.  I have the network set as DHCP on both router and wireless card, and the key type set as hexadecimal, which is what the router uses.

What might I need to do?

---

### Post by Danny Rafferty on 2006-05-09
I am having a simlar issue with Belkin F5D620 v3. Driving me nuts.
I have not tried turning off WEP completely (because that would knock out my wife's laptop and then she would shoot me) but I know my problem is WEP related.
Basically the card's LED dimly tries to turn on.
I changed the ESSID from 5234 9879 to 52349879.
Now the LED comes on and it's like it's trying to negotiate with the DHCP but nor receiving the DHCP offer.
I too have checked and double checked the key and the HEX/ASCII setting.
I have also tried manually making these entries into the /etc/network/interfaces file. No joy there.
I have also tried to give it a static address but this hasn't worked either.
Anyone any suggestions?

---

### Post by jml on 2006-05-09
I have read here on these forums that the graphical application to configure WEP is unreliable in its performance.  It seems that you need to configure WEP at the command line.  Here is a link to the Wireless Trougleshooting Guide.  It may help you.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by Danny Rafferty on 2006-05-10
Thanks for the tip. I tried this after posting but no joy. 
The Wireless Troubleshooting WIKI is excellent and I would advise anyone with a similar problem to download that page and the page on ndiswrapper.
Following the WIKI methodically I discovered that the driver was working and binding correctly.

I was not able to communicate with the AP although a scan showed that the card could see the router. The LED on the card was making feeble attempts to light up at this stage.

I turned off WEP and everything was fine. I turned WEP back on and I could not get an address from DHCP or communicate using a static address.

I am now basically stuck at this part of the WIKI:
--------------------------------------------------   
      If you can not connect to the router then try these.
         1. Change to an open signal (instead of wep or wpa). This may be an unattractive option but it's a short term one to make sure the card and ap can connect. Once you've verified this then you can add encryption back in.
[COLOR="Red"]This is what I am doing.[/COLOR]
               1. When using wep more people seem to have success using an open key instead of shared and a hexadecimal method instead of ascii. But there should be no reason any setting shouldn't work. Try the settings you want and consider adjusting if you have problems.[COLOR="Red"]Don't know what they mean by Open vs Shared. I am using HEX.[/COLOR]
               2. To get wpa working you will need to install the wpasupplicant from the repositories. There are instructions for various drivers on using wpa. See notes on wpa below.[COLOR="Red"]Don't want to start into WPA at this point -  could be just more headaches.[/COLOR]
         2. Download a scanner such as network manager, [WWW] gtk wifi, or [WWW] wifi radar. of course this is not an option if you can not connect to the internet without wireless[COLOR="Red"]Don't think this is applicable. Card works fine if WEP is off.[/COLOR]
         3.Try booting with kernel option pci=noacpi or acpi=off as acpi sometimes conflicts with network devices. The second option will affect power management.[COLOR="Red"]Don't know how to do this but am willing to try. Can't find documentation on how to do it. Real Newbie me![/COLOR]
         4. Check for firmware update on the router and update it if there is newer firmware available.[COLOR="Red"]Firmware is latest and the card and router work fine under XP.[/COLOR]

4.3.1. Notes on wep

     [WWW] ubuntu wep faq[COLOR="Red"]This is a broken link. So I'm stuck.[/COLOR]
    
      If you have a 10 digit wep key try entering it in this format xxxx-xxxx-xx (include dashes)[COLOR="Red"]Tried this, no luck.[/COLOR]

      Use an open setting instead of shared when using wep[COLOR="Red"]What is this? My router doesn't appear to have such an option.[/COLOR]

      When using wep, check driver files such as README as some drivers need a command to adjust the mode to work properly. Here are a couple examples.
[COLOR="Red"]This could well be significant, but can't find any such readme on the Belkin F5D6020 documentation or anywhere else on this site.[/COLOR]
----------------------------------------------------------

I have read posts that suggest ndiswrapper updates and kernal updates. 
I think I am on Breezy 5.10 (came on a CD I got at a trade show) but don't know what version of ndiswrapper I have.

Sorry for the long post, but I am desperate to get my hands even dirtier with the OS and would appreciate any input. The sooner I can get away from the evil OS the better.

Regards,

Danny.

---

### Post by ChristopherTeague on 2006-05-10
Solved:

I left my Linux wireless settings as they were (Hexadecimal WEP with DHCP) and changed the router WEP setting from "automatic" to "open" per the recomendations on this other forum on the madwifi website:

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

I did nothing in the command line on my computer, just changed the router settings.  There are some posts in the above link that talk about using "shared" WEP, but I haven't tried them.

I hope that helps the rest of you.  Danny, your problem sounds very similar to mine, so I'd suggest you look at your router's documentation to find out about changing the WEP setting from "Automatic" or "Shared" to "Open."


From my experience browsing around over the past few days, it seems like ubuntu has some issues that need to be ironed out regarding wifi ease-of-use.  Other than that, I love it!

---

### Post by ChristopherTeague on 2006-05-10
PS Danny, I enjoy your references to the "Evil OS."  I myself refer to it as the accursed OS, but its all in the same spirit.  I try to avoid using the terribly offensive M****soft obscenity as much as possible.

---

### Post by Danny Rafferty on 2006-05-11
There is a setting on my router for WEP - Automatic and WEP - Manual, but these look like settings for automatically or manually creating keys.
It's a Netopia, so I'll check out the site when I have a chance and report on my findings.

Will also do some investigation on this "open/shared" business.

Keep the faith people.

---

### Post by Danny Rafferty on 2006-05-12
Well my router only supports open wep, not shared. There is no option for shared and no place to configure the shared challenge password.
I looked through the inf of the driver and found a place that looked like I could put in the default key. I tried this in the xxxxxxxxxx format and the xxxx-xxxx-xx format in both the inf file and in the networking app with no success.
I decided I might try downloading network manager before I trap WPA. I have got 75% throught the install and my machine is not doing what the instructions say it should.

I am getting a bit tired of this. I have been at this for a couple of weeks and I am beginning to thing that there are more important things in my life than this problem.

More if I get it solved.

---

### Post by Danny Rafferty on 2006-05-14
Well I downloaded Network Manager and the install didn't go as described.
Apparently it is not loading up.
I also found that that none of the Totem decoders is working.
I have to admit that despite an honours degree in computer science and some light exposure to other Open OS's I am getting rather frustrated with this.
I am more than three weeks with this OS and not making much progress.
I have to reboot to the horrible proprietry OS if I want to do any work.

I note a lot of other posts similar to mine with no answers, or answers that don't arrive at a solution.

What now? Anyone found an easier distribution to work with?

Dubious is Dublin](*,)

---

### Post by hockeysk8 on 2007-03-03
> **ChristopherTeague said:**
> I've been trying to connect my dell PC running Ubuntu to the internet through my Netgear WG311t wireless card (madwifi driver).  When I disabled WEP on the router, I could connect, but after enabling it (128 bit) and entering the key in my Linux machine, I could no longer connect.

Now, I know what you're thinking, but I've checked the WEP key so many times that I know it can't be the problem.  I have the network set as DHCP on both router and wireless card, and the key type set as hexadecimal, which is what the router uses.

What might I need to do?

I experienced similar troubles and using all of diagnostic tools it really looked like I should have been connecting but just wasn't.  I finally noticed that in the output of "sudo iwconfig" a number of the settings were incorrect.  The BIG problem is that there is no way to manage these settings from System -> Administration -> Netwoking.  Therefore, you have to roll up your sleeves and set them with "iwconfig."  In my case (and probably in most people's) I had to set the channel as well as the security mode:

sudo iwconfig eth1 channel 7 enc restricted

By default it was setting the channel to 0 and the security mode as open.

You can probably set these values by putting them in /etc/network/interfaces but I have not tested this.

---

### Post by chili555 on 2007-03-03
**What we have here, is failure to communicate.**

In my experience, failure to connect with WEP is actually caused by two issues and, very rarely, a third.

1. **Router and computer don't have the same key.**

Get the WEP key from your router and check it twice. We do not want the passphrase, we want the alphanumeric key, something like this: 93c8530b2df51711bad5596f91.

Then, sudo gedit /etc/network/interfaces to make the relevant interface entry look like this:
```

auto wlan0 
iface wlan0 inet dhcp
wireless-key 93c8530b2df51711bad5596f91
```

Your interface may be eth1, ath0 or ra0, etc.

Check your work twice. Then restart networking sudo /etc/init.d/networking restart and you should be all good.

2. **Router and computer don't share the same ESSID**

Run sudo iwlist wlan0 scan. See your router? Write down it's essid. Let's say it's chili, for example. Now run sudo iwconfig wlan0. Is the essid chili? Good! If it is Chili or CHILI or anything else, you will never connect. 

sudo gedit /etc/network/interfaces and now further amend your relevant interface, in my example wlan0 to match the essid you saw in scanning:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91
```

Restart networking (see above) and *now* you should be all good.

3. **Restricted vs. Open**

Some routers, sometimes under Advanced Wireless Settings, have a setting for Authentication Type: Auto or Shared Key. Here is what the explanation says from Linksys:
> The default is set to Auto, which allows either Open System or Shared Key authentication to be used. For Open System authentication, the sender and the recipient do NOT use a WEP key for authentication. For Shared Key authentication, the sender and recipient use a WEP key for authentication. If you want to use only Shared Key authentication, then select Shared Key.

Seems kind of silly, to me, to set up your computer to use WEP and allow your router to accept non-WEP traffic, if I read that correctly. So, I use Shared Key. I then must further amend /etc/network/interfaces as follows:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91 restricted
```
For some reason, some of us will only connect if "open" is explicitly called: ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91 open
```

Now restart networking...you know the rest.

Hope this helps.

---

### Post by tetobear on 2007-03-04
I have the same issues...

I am using really Kubuntu 6.10
I have a Netgear card pci see as ath0
too bad i cant turn off the WEP to check if it works like u did...

so the AP access point set for WEP is:
Wireless LAN 
 Network Authentication:   Shared Key
 Data Encryption:  128 bits WEP    
 Passphrase:      
( ) Key 1: 6653xxxxxxxxxxxxxxxxxxxxxx	    
( ) Key 2: 6653xxxxxxxxxxxxxxxxxxxxxx   
(o) Key 3: 6653xxxxxxxxxxxxxxxxxxxxxx     
( ) Key 4: 6653xxxxxxxxxxxxxxxxxxxxxx

as u see it is the key n. 3

so my /etc/networks/interfaces is:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Nestor_bridge
wireless-key 3 6653xxxxxxxxxxxxxxxxxxxxxx

auto wlan0
iface wlan0 inet dhcp 

the gateway 192.168.0.1 is the DNS server too

comand iwconfig say access point not asscociated... 

I dont understand i tried everything...

on winxp on the netgear drive i just select key 3 and the password and it works...

dont know what to do...

please help : - )

---

### Post by chili555 on 2007-03-04
tetobear-

> Network Authentication: Shared Key
The post right above yours suggests you add restricted to your wireless-key line. Try it and let us know. For example: ```
auto ath0
iface ath0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Nestor_bridge
wireless-key 3 6653xxxxxxxxxxxxxxxxxxxxxx **restricted**

```

---

### Post by tetobear on 2007-03-04
hi thanks to help geeee getting crazy to trying to connect with wireless

yes i did add restricted and add other setting

this the whole interfaces file, still access point not associated

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.0.9
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet static
address 192.168.0.3
netmask 255.255.255.224
gateway 192.168.0.1
wireless-essid Nestor_bridge
wireless-channel 1
wireless-mode managed
wireless-key 1 66533EA73867XXXXXXXXXXXXX restricted
wireless-key 2 66533EA73867XXXXXXXXXXXXX restricted
wireless-key 3 66533EA73867XXXXXXXXXXXXX restricted
wireless-key 4 66533EA73867XXXXXXXXXXXXX restricted
wireless-defaultkey 3

auto wlan0
iface wlan0 inet dhcp


i have a question about wifi0 as i saw it associte to the card when i do the lspci command
so for now i just add the ifconfig and iwconfig

i have to reboot every time between kubuntu and winxp to be able to be in this forum for now... hope i can fix it geeeee

ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:85:85:BF
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe85:85bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20696 (20.2 KiB)  TX bytes:20696 (20.2 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-85-85-BF-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10315 errors: 0 dropped: 0 overruns:0 frame:19428
          TX packets:44781 errors:3 dropped: 0 overruns: 0 carrier: 0
          collisions:0 txqueuelen:199
          RX bytes:1203010 (1.1 MiB)  TX bytes:2317906 (2.2 MiB)
          Interrupt:201 Memory:e0a60000-e0a70000

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Nestor_bridge"
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

sit0      no wireless extensions.


geeeeee i wanna it runninggggggg :mad: 

thanks so much to bother

---

### Post by tetobear on 2007-03-04
so here what the lshw show...

tefano@tetobearpc:~$  sudo lshw -businfo
Bus info      Device     Class       Description
================================================
                         system      A7N8X-X
                         bus         A7N8X-X
                         memory      BIOS
cpu@0                    processor   AMD Athlon(tm) XP 2600+
.
.
.
pci@01:0a.0   wifi0      network     AR5212 802.11abg NIC
.
.
.

stefano@tetobearpc:~$ sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:0c:6e:fb:b6:26
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=half link=yes multicast=yes port=MII speed=10MB/s
       resources: iomemory:e7000000-e7000fff ioport:e400-e407 irq:177
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: a
       bus info: pci@01:0a.0
       logical name: wifi0
       version: 01
       serial: 00:14:6c:85:85:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.2.1) ip=192.168.0.3 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e6000000-e600ffff irq:201
stefano@tetobearpc:~$ 


stefano@tetobearpc:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Nestor_bridge"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:6653-3EA7-3867-XXXX-XXXX-XXXX-XX   Security mode:restricted
          Power Management:off
          Link Quality=27/94  Signal level=-68 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

stefano@tetobearpc:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:14:6C:CF:ED:32
                    ESSID:"Nestor_bridge"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/94  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00

stefano@tetobearpc:~$

stefano@tetobearpc:~$ sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:85:85:BF
          inet addr:192.168.0.3  Bcast:192.168.0.31  Mask:255.255.255.224
          inet6 addr: fe80::214:6cff:fe85:85bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-85-85-BF-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3821 errors:0 dropped:0 overruns:0 frame:1370
          TX packets:4949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:452248 (441.6 KiB)  TX bytes:256141 (250.1 KiB)
          Interrupt:201 Memory:e0ae0000-e0af0000


I had to change my etc/network/interfaces, as it doesnt start that card with more then one wireless-key and it doest accept the line wireless-defaultkey, i found out it with sudo ifdown ath0 and sudo ifup ath0 after making the changes...  and i notice with sudo iwconfig  i can see the key setting and resticted mode 

well if i get out of this mess i will be sooooooooooooooo happy! :) 


Thanks a lot guys for your help

---

### Post by tetobear on 2007-03-11
GRRRRRRRRRR yes baby now it works finalllllllllllllllly 
 
maybe this post will help someone :-)

so the story...
Thanks to you all to understand the wep key

so i set the etc/network/interfaces...
auto ath0
iface ath0 inet static
address 192.168.0.3
netmask 255.255.255.224
gateway 192.168.0.1
wireless-essid Nestor_bridge
wireless-channel 1
wireless-mode Managed
wireless-key [3] 66533EA73XXXXXXXXXXXXXXX6D7B restricted

as u see i set the key n. 3 couse that was set on the access point (i couldnt make any change) I notice that i coundnt use any other wireless-key line or the interfaces will not go up ( i tried to set a key for each of the 4 keys)

so after this i could check the interface key with
sudo iwlist ath0 k

root@tetobearpc:/home/stefano# sudo iwlist ath0 k
ath0      3 key sizes : 40, 104, 128bits
          4 keys available :
                [1]: off
                [2]: off
                [3]: 6653-3EA7-xxxx-xxxx-xxxx-xxxx-xx (104 bits)
                [4]: off
          Current Transmit Key: [3]
          Security mode:restricted
          Authentication capabilities :
                WPA
                WPA2
                CIPHER TKIP
                CIPHER CCMP
          Current key_mgmt:0x3
          Current cipher_pairwise:0x10
          Current cipher_group:0x4

and the channel with 
sudo iwlist ath0 c

root@tetobearpc:/home/stefano# sudo iwlist ath0 c
ath0      23 channels in total; available frequencies :
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
          Current Frequency=2.412 GHz (Channel 1)

Setting is ok, but still access point NOT ASSOCIATED!!!

so i read the info for madwifi drivers more carefull
AND I FOUND IT!!! (after a month of working GRRRRRRRRRR on this wireless insue!!!)

 here the code!!!

If you get a message such as: 
ath0      Failed to read scan data : Resource temporarily unavailable

 instead of actual scan results, and you are in an environment that requires a shared encryption key, try running: 
iwconfig ath0 key <yourkey>
iwpriv ath0 authmode 2

This will tell the card that it is operating in a restricted, shared-key environment, and thus it needs to use the key you supply with iwconfig. To use an open system key (which is often considered more secure) use iwpriv authmode 1: 
iwconfig ath0 key <yourkey>
iwpriv ath0 authmode 1

 Once this is done, re-run the scan, and you may see proper results.


so the iwpriv ath0 authmode 2 MADE IT!!! my card now CONNECT TO THE ACCESSO POINT!!!

so i am going to add a line on the interfaces file...

WELL almost there!
now where i can type the iwpriv aht0 authmode 2 so it will be loaded on the boot?

thanks to all!!!

---

### Post by m47h3us on 2007-04-05
ace, i had too uninstall ubuntu cos i could not get the wireless working this is gr8 help thanks alot i can use ubuntu again yay :D

---

### Post by thebluejay on 2007-04-12
Incredible! Did anybody ever actually get a wireless connection to work after going through all of that. I may go back to Windows! That looks like sheer torture. Can somebody please sum up the correct way to get it going without all of the by-ways, blind roads and dead ends? Do I have have to re-write 85 files, install 16 packages, write 600 lines of code and then find it doesn't work because /etc/resol.config could not be opened for writing....

confused and discouraged

---

### Post by chili555 on 2007-04-13
thebluejay-
If I've told you once, I've told you a million times: don't exaggerate!

To connect, at a minimum, you need to tell your computer which network you want to connect to and, if there is any, input your encryption details. In Linux, you can do so with a variety of graphical interfaces, NetworkManager, Wifi-radar, Wireless Assistant or Wicd. Some on these forums swear by them and some swear *at* them!

But there are also some people who like to roll up their sleeves and get their hands dirty in the .config files. They'd like to understand how things work and why. They appreciate that they can control literally *every* aspect of the way their computer works. 

You don't like the way that software RAID is implemented? Super! You are perfectly free to implement a better way. You can examine and improve the current code and publish it for anybody to use. Try that in Windows. Write to Mr. Gates and ask for the Vista source code. Good luck to you on that one! But the source code for the Linux kernel? Absolutely free and available to all; I have a copy on this computer now.

You asked:> Did anybody ever actually get a wireless connection to work after going through all of that.Absolutely. I just bought a new laptop two weeks ago, and installed Edgy within 20 minutes of the UPS man leaving my door. I changed my /etc/network/interfaces file from:```
auto eth1
iface eth1 inet dhcp
```to this:```
auto eth1
iface eth1 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91
```I then issued a command:```
sudo dhclient eth1
```and I connected. I have connected on boot ever since.

There is no perfect operating system; not Windows, not OSX and not Linux. If you are a hard-core gamer, you want Photoshop, viruses and malware, then Windows is for you!

For me and my 60-something wife, we want to surf the web, email, instant message, rip mp3's, rip...er, back up DVD's, write and print documents, etc. and we want to do so blissfully free of viruses and malware. And we want all this free. Linux is for us.

---

### Post by thebluejay on 2007-04-13
still discouraged, chili!

I have tried EVERYTHING! Network Manager, Wifi-Radar, Wireless assistant, command line, static versus DHCP, modifying /etc/network interfaces and so on and so forth. I have installed ndiswrapper and God knows what else. I don't give up easily but one would hope that eventually a solution could be found. I set up my system exactly as in your model, using the correct parameters, and got this:

no DHCP offers received.
No working lease in persistent database - sleeping.

So.....

---

### Post by thebluejay on 2007-04-13
... and one more thing: why can't I access /etc/resolv.config to edit it? When I try to edit it, I am told I cannot access it. the various network managers also tell me that they cannot connect because they cannot write to this file and so cannot change nameserver and domain.

---

### Post by chili555 on 2007-04-13
There is no file '/etc/resolv.config' unless you have accidentally created one. The relevent file is /etc/resolv.conf. You should be able to edit it easily with:```
sudo gedit /etc/resolv.conf
```You need sudo because the file is an internal configuration file which is only 'writable' by the superuser. 

Did you follow the instructions for setting up NetworkManager here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

Especially this part:> Any already configured devices that you want to be available in Network Manager will need to *de-configured,* as otherwise they will be ignored.

The easiest way to do this is by going to System -> Administration -> Networking and then going to "Properties" of each connection. In Properties, just untick the "Enable this connection" checkbox. Logout then log back in again. These connections should now be available in Network Manager. I would also check that you have the ESSID absolutely correct. belkin is not the same as Belkin is not the same as belkin54g. You can check with:```
sudo iwlist eth1 scan
```Substitute your wireless interface for eth1 here.

Post back. Old Chili has heard the challenge!

---

### Post by thebluejay on 2007-04-13
Well, Chili, guess what! Solved! Just pure luck maybe, since I've been working on this for a loooooong time. But it may be that your advice did the trick. I disabled the card as you suggested and then tried to set up the network again using both Wifi-Radar and Wireless Assistant which seemed to provide more options. Both failed. Then I did the same procedure with Network Manager and BINGO - to my great surprise and delight it actually connected for me. May your name be written in heaven in the book of the blessed - or in other words - thanks loads.

I am sooooo happy. :)

Now on to new adventures in Linux...

---

### Post by chili555 on 2007-04-13
Thank you for your kind comments. May your Linux journey be enjoyable.

---

### Post by kaginken on 2007-04-18
Chili555, thank you thank you and thank you!  Your first post (#1) solved my problem, and I've been trying to get my linksys wpc11 v. 4 wireless adapter working for weeks now!  I just installed ubuntu dapper drake, the wireless card was recognized after the first bootup - but I could only get one reply each four pings.  

What I noticed in your post, was the encryption key was all LOWERCASE, and I had put in all UPPERCASE letters (which is what my router showed).  So, I modified my key to all lowercase and WHAM!  Instant success.  I've never heard anyone mention the key being case sensitive - SSID yes, but never the key.  So I wanted to mention that here for all you fellow ubuntairians.

Chili, you ROCK man!  Thanks again,

Ken  :guitar:

---

### Post by thebluejay on 2007-04-18
It is very strange that wireless keys are indeed case sensitive and yet when the key shows up in the router configuration it shows as all caps (at least in my Linksys system). Pretty dumb. :))

Are you listening router manufacturers?

---

### Post by Peter Parley on 2007-04-20
Chili,

Just wanted to echo thanks! Hunted around the forum for a way to get my Belkin F5D6020 working in Xubuntu, and your suggestions provided the answer.

---

### Post by Michael Matthews on 2007-06-21
put this is /etc/rc.local

iwpriv ath0 authmode 2

Interface will work at boot.

---

### Post by McSnide on 2008-03-02
Chili555,

Thanks for Post 11.  I'm a Linux newbie and had spent about 4 hours fighting my wireless card.  After reading your post, specifically the "restricted" and "open" settings, I was online in 15 seconds.

---

### Post by chili555 on 2008-03-05
Thank you all for your kind comments! Glad it's working now.

---

