---
title: "Problems with wireless on Ubuntu 8.10"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by dthorstein on 2009-03-02
I am a new user to ubuntu...a new linux user to be exact. I'm having an issue with my Acer Aspire 5310 laptop - it is not able to connect to the Internet wirelessly. 

I don't mean to sound like a complete noob, but i have tried copying several help suggestions in this and other forums to no avail. My wireless card is an atheros device which i have determined as the problem (...duh). 

What I need is someone to run me through how to correct this issue as soon as possible and help out however you guys can.

---

### Post by x1101 on 2009-03-02
First, welcome aboard. Now, open a terminal window, (Applications -> accessories->terminal) and post the output of the following commands
ifconfig
iwconfig

also can you please describe the kind of wireless network you are trying to connect to? (open/wep/wpa)

---

### Post by dthorstein on 2009-03-03
ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1d:d9:2a:4d:37  
          inet6 addr: fe80::21d:d9ff:fe2a:4d37/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1b:38:5e:df:32  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe5e:df32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:738770 (738.7 KB)  TX bytes:56412 (56.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1D-D9-2A-4D-37-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47926 errors:0 dropped:0 overruns:0 frame:3315
          TX packets:4386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:4333080 (4.3 MB)  TX bytes:204437 (204.4 KB)
          Interrupt:19 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:47027  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

I'm currently having problems connecting to any type of inernet configuration. I know it is operational because I have used another laptop with ubuntu 8.10 on the same router with no problems.

pretty much I'm to the point where I know where the problem is and I know enough to fix it if this were windows (pc repair tech xd), but I haven't had enough experience to know how to handle this issue.

---

### Post by Joren on 2009-03-03
I have the same problem with my artheros wireless internet. Recently got a laptop and installed 8.10 on it. I can use only wired internet and not wireless. Just like you I tried numerous things and tutorials on the internet but it just didn't work (and I am using Ubuntu for a couple of years now!!)
At some point I just gave up (since I have mild RSI and digging and digging for answers on the internet adds fuel to the fire)

So I'will follow this thread closely. :)

---

### Post by x1101 on 2009-03-03
So from this
> **dthorstein said:**
> 
ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1d:d9:2a:4d:37  
          inet6 addr: fe80::21d:d9ff:fe2a:4d37/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and this
> **dthorstein said:**
> 
iwconfig
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:47027  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

We can see that the interface (in this case ath0) is up, we just need to associate it with the network. What kind of network is it? Open?WPA?WEP?
Regardless the first step is the same, try this
```

iwconfig ath0 essid <ssid of your wireless network>

```
for an open network you would be all set, after running this
```

dhclient

```
If  your network has WEP or WPA things get a little trickier, but nothing we cant deal with...

Let me know if that helps

---

### Post by dthorstein on 2009-03-03
This is a little strange, but that worked. I'm going to post the results of those here just so they're on record...I have a feeling from this that it's not the first issue I'm going to have...


 iwconfig ath0 essid linksys
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.

dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
wifi0: unknown hardware address type 801
Open a socket for LPF: Operation not permitted


Just going by that gives me a bad feeling. I'm not sure exactly why its working since it lists everything as permission denied...maybe it decided to not make me kill it xd. If you maybe have some suggestion about this it would be appreciated and if I have any more issues out of this I'll try to keep this up to date so I can get more help xd.

---

### Post by mixtri on 2009-03-03
Hey Guys!
I am experiencing similar problems using an Atheros based Network adapter.
I currently use Ndiswrapper which has enabled a wireless network i can see and select my own network from via the Network manager applet.

The only problem i have is that i can never seem to connect to the blasted thing!
I have configured my router with WPA2 encryption using a password which I am prompted for whenever I attempt to connect to wireless.

I keep getting the message "Attempting to join the wireless network" and thats all it seems to do before giving up without a connection. On the odd occasions i will get another message: "Obtaining an IP address from the wireless network - blah!" But not much   happens after that.
I have on 3 previous occasions got a connection but upon disconnecting i face the same problems getting a connection again, as previous.

It's so frustrating, as the network is there yet i am unable to connect to it.
I also noticed that upon each failed attempt to connect  - the wireless network login applet appears prompting me to log on again and again yet it always fails to connect.
I have checked and double checked to make sure router configurations, encryption, password settings etc are all correct.
Someone please help, I've spent 3 months on this laptop trying to get this to work and completely at my wits end.

---

### Post by x1101 on 2009-03-03
> **dthorstein said:**
> This is a little strange, but that worked. I'm going to post the results of those here just so they're on record...I have a feeling from this that it's not the first issue I'm going to have...


 iwconfig ath0 essid linksys
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.

dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
wifi0: unknown hardware address type 801
Open a socket for LPF: Operation not permitted


Just going by that gives me a bad feeling. I'm not sure exactly why its working since it lists everything as permission denied...maybe it decided to not make me kill it xd. If you maybe have some suggestion about this it would be appreciated and if I have any more issues out of this I'll try to keep this up to date so I can get more help xd.

I apologize, you need to run both of those commands with sudo. To do that simply type
```

sudo <command>

```
This allows you to run the commands as root (the admin) simply by putting in your password. It is similar to a windows 'run as'.

Hope that helps a bit

---

### Post by dthorstein on 2009-03-03
Lol xd....should have known that from the other self-helps i tried..

Anyway, the wireless seems to be functioning without those lines and I know it didn't resolve itself. It even works on encrypted networks with no further configuration. If anyone is interested I'll link the last self help blog I tried, I have a feeling it works better than I thought and just took a little time to function properly. 

I'll say this: this little fiasco has taught me more about this OS than I probably could have learned in a few weeks of tinkering. It only makes me feel better that I switched from "winblows" to Ubuntu. Thanks for your assistance and I hope someday i can return the favor ;)

---

### Post by rira on 2009-03-03
i experienced the same problem. I use emachines D720, atheros 802.11 wireless LAN cards.

when i tried to type ifconfig, here is the result:
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:da:f9:8c  
          inet addr:167.205.3.55  Bcast:167.205.3.63  Mask:255.255.255.192
          inet6 addr: 2002:a7cd:310:7:21e:ecff:feda:f98c/64 Scope:Global
          inet6 addr: fec0::7:21e:ecff:feda:f98c/64 Scope:Site
          inet6 addr: 2002:a7cd:339:7:21e:ecff:feda:f98c/64 Scope:Global
          inet6 addr: 2403:8000:1:1880:21e:ecff:feda:f98c/64 Scope:Global
          inet6 addr: fe80::21e:ecff:feda:f98c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24886655 (24.8 MB)  TX bytes:3227896 (3.2 MB)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

pan0      Link encap:Ethernet  HWaddr ae:e7:d0:9e:78:e9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


anyone can help me? thanks

---

### Post by x1101 on 2009-03-03
what do you get when you type
```

iwconfig

```

that will tell you what wireless interfaces you have, and we can work from there.

---

### Post by mixtri on 2009-03-03
Hey Guys!
I am experiencing similar problems using an Atheros based Network adapter.
I currently use Ndiswrapper which has enabled a wireless network i can see and select my own network from via the Network manager applet.

The only problem i have is that i can never seem to connect to the blasted thing!
I have configured my router with WPA2 encryption using a password which I am prompted for whenever I attempt to connect to wireless.

I keep getting the message "Attempting to join the wireless network" and thats all it seems to do before giving up without a connection. On the odd occasions i will get another message: "Obtaining an IP address from the wireless network - blah!" But not much happens after that.
I have on 3 previous occasions got a connection but upon disconnecting i face the same problems getting a connection again, as previous.

It's so frustrating, as the network is there yet i am unable to connect to it.
I also noticed that upon each failed attempt to connect - the wireless network login applet appears prompting me to log on again and again yet it always fails to connect.
I have checked and double checked to make sure router configurations, encryption, password settings etc are all correct.
Someone please help, I've spent 3 months on this laptop trying to get this to work and completely at my wits end.

---

### Post by Simyager on 2009-03-03
Hi I am having problems with my atheros as well. I have installed Ubuntu 8.10 64bit and I can´t connect with wifi. And sadly that´s the only way I can connect to the internet. These are the things that I get on the terminal:

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:cd:80:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f6:5b:71:16:e4:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
-----------------------------------------------------------------

And I can't activate the wireless card (in Ubuntu on vista it works) it always stays unactive. I have tried many tutorials without any succes. I can only connect to the internet through wifi and sadly no cable :(

---

### Post by Scunnered on 2009-03-03
mixtri

I sometimes have a problem where the wireless connection does not work. I am asked for a password like you and what I do is to enter my details and press connect. Often this does not work immediately but comes back repeating the password request. I totally ignore this and shut down the system completely.  Do not use restart but completely shut down.  Give it a little time to settle and then reboot.  This usually works immediately for me.

Give it a try and see if this helps

---

### Post by dthorstein on 2009-03-03
Not really sure if it's the same problem I had, but check out this help guide and lemme know if you still have problems or if it fixes yours too:

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

Keep in mind the guide was written for the 2008 11/01 package and instructs you to use that as part of it, however the actual file that they instruct you to download is dated 2009 05/02 I believe. If thats not the right date just watch the terminal and use the version info that is unpacked in terminal.

---

### Post by Masterflex on 2009-03-03
I am having a similar problem connecting to my campus wireless ( WPA2 Enterprise PEAP) on Ubuntu 8.10, except that after I enter my credentials, the wireless connection animation goes for about 3 seconds and then the entire system freezes! I can't do anything at that point besides hold down the power button and do a hard reset. This thread ([http://ubuntuforums.org/showthread.php?t=1071291](http://ubuntuforums.org/showthread.php?t=1071291)) talks about people with similar problems. I am not able to get my logs or do an iwconfig or ifconfig right now, but if anyone could offer some help I'll gladly post them. Thanks in advance.

---

### Post by Simyager on 2009-03-04
Unfortunatly it still doesn´t work as I said my only connection is through wifi. Therefore I can´t get the essentials through terminal. I tried to do it before on another tutorial but because I lack the cabled connection I can´t come any further.

I mostly don´t get stressed but I am using Ubuntu for a week or so. And the only thing that bothers me is the freakin´ internet connection. So please help me.

---

### Post by crokett on 2009-03-04
Install the wicd network manager.  It helped me a lot. I could not connec to my LEAP network at work with the default Ubuntu network manager. Once I installed wicd I could.  

I also have an atheros wireless on my laptop.  I upgraded the driver from ath_pci to ath5x but I don't remember exactly how and can't find the tutorial.  Basically you insall the ath5x driver, load it as a module and then blacklist the old driver to keep it from loading. 

getting wicd:

```

# add the repository to your sources
echo "deb http://apt.wicd.net intrepid extras" | sudo tee -a /etc/apt/sources.list

#get the key
wget q http://apt.wicd.net/wicd.gpg -O | sudo apt-key add -

#install the package
sudo apt-get install wicd

```

---

### Post by Simyager on 2009-03-04
unfortunatly it didn´t work for me perhaps it can work for others. I can´t download it under ubuntu because my only connection is wifi, which is the biggest problem, but please help me I am really getting stressed. So please help me :(

---

### Post by Simyager on 2009-03-08
3 days later and still no internet. As I said I only have internet acces via wifi so please help me I am getting really stressed, please help me :(

---

### Post by nicors.net on 2009-11-01
Ich habe das gleiche Problem.
Habe Quad CPU und ubuntu erkennt das Netzwerk nicht. Habe nun die Treiber seperat gezogen und versucht diese mittels Stick zu laden (dachte es liegt an einem Lesefehler vom ROM).
 
Leider alles ohne Erfolg. Liegt bestimmt an der Config, kann das Problem allerdings nicht finden. Muss auch gestehen, dass ich nicht wirklich soviel Ahnung habe von der Config und als newbie mich erst einarbeiten muss.
 
Kann mir hier jemand auf deutsch Hilfe geben zum Thema?
 
viele grüße
nicors

---

### Post by nicors.net on 2009-11-01
Habe das Problem gefunden ;)
hat sich somit erledigt. war ein simpler Fehler in der Config und den konnte ich hier in einem anderen Thread finden.
nochmals vielen Dank!

---

### Post by DJ . on 2009-11-07
Hello, I have signed up in this forum because i have the same problem. I have a Verizon Network with a wep key and Network Manager won't connect. Everytime I try to connecct a message comes up saying that I have been disconnected. I am very used to windows but I need to switch to Ubuntu.
 
Here is what I get when I type iwconfig:
 
[EMAIL="dj@ubuntu:~$"]dj@ubuntu:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:"nr8p2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.
 
 
nr8p2 is what my wireless connection is called. I have been trieng to figure out how to get connected for 3 days but nothing is working. So... Help please. I don't want to go back to windows xp.

---

### Post by DJ . on 2009-11-08
> **DJ . said:**
> Hello, I have signed up in this forum because i have the same problem. I have a Verizon Network with a wep key and Network Manager won't connect. Every time I try to connect a message comes up saying that I have been disconnected. I am very used to windows but I need to switch to Ubuntu.
 
Here is what I get when I type iwconfig:
 
dj@ubuntu:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:"nr8p2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions. 
 
 
nr8p2 is what my wireless connection is called. I have been trieng to figure out how to get connected for 3 days but nothing is working. So... Help please. I don't want to go back to windows xp.

Still looking through the forums and nothing is working.
```
sudo iwconfig wlan0 essid nr8p2
sudo dhclient
```
The code above isn't working because it is password protected. Can anyone help?

---

