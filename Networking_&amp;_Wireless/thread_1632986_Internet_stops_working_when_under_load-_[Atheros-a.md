---
title: "Internet stops working when under load- [Atheros-ar9285 driver]"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by Davste on 2010-11-28
[COLOR="Red"]Note: When the internet disconnects, the WiFi remains connected, with a strong signal. However iwconfig shows that the Bit Rate goes down to 1Mb/s when this happens.[/COLOR]


I just installed ubuntu 10.1 on my netbook, connected to my wireless network, and the internet worked fine. Then I tried to download netbeans with firefox (about 100 mb), and it only downloaded 80mb of the file. After that, internet stopped working completely. I tried rebooting - same result. 

The netbook can also dual boot windows 7, and wireless internet works fine with windows 7 :(

** 
Update: This does not only happen when downloading large files, it seems to be happening after using the WiFi for a certain period of time. (5-10min)

---

### Post by Davste on 2010-11-28
I can't ping the router, nor any sites like [www.google.com](www.google.com) now :S

---

### Post by drdos2006 on 2010-11-28
From a terminal type :
ifconfig

If you do not see 192.168.0.20 or 10.10.0.0 type IP addresses then you may have IPv6 instead of IPv4.
Please post the result of ifconfig here.

regards

---

### Post by Davste on 2010-11-29
```
mario@mario-ubuntu:~$ sudo ifconfig
[sudo] password for mario: 
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:53:11:f3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:78:fe:9a  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe78:fe9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3325 (3.3 KB)  TX bytes:13082 (13.0 KB)

mario@mario-ubuntu:~$ 

```

Thank you for your reply :)

---

### Post by Davste on 2010-11-29
When I ping 192.168.1.254 (my router), I now get a reply.

Firefox still says "Server not found" when I type in [www.google.com](www.google.com) in the address bar.

---

### Post by Davste on 2010-11-29
I think this screenshot may be of interest to you:

---

### Post by Davste on 2010-11-29
I restarted my router and internet started working again, but it's erratic.

---

### Post by Davste on 2010-11-29
*Update

Randomly, the internet just disconnects, and I usually have to reboot the rooter to get it working again :(

Sometimes, though, when I just disconnect and reconnect it works again... for a short time. Remember, the WiFi network always stays connected, and at a decent strength - it's just the internet that stops working.

It might be useful to mention that my netbook has an atheros-ar9285 driver, I'm not sure if it's a driver problem or network configuration problem. Can anyone help please? :(

---

### Post by Davste on 2010-11-29
Bump :(

I really need help with this - it's really appreciated. Thanks folks.

**

I reinstalled ubuntu, and still get the same result. It's really frustrating.

---

### Post by drdos2006 on 2010-11-29
Are you able to plug in an Ethernet cable from your computer to your modem ?

What brand is your modem, is it a USB modem ?
How old is the modem ?

How far away from the exchange are you ?
Have you tried another phone line filter ?
Are you on ADSL2 or ADSL1 ?

I got your PM, my ISP has been up and down for two days now, so I was not able to respond earlier.

regards

---

### Post by Davste on 2010-11-30
> **drdos2006 said:**
> Are you able to plug in an Ethernet cable from your computer to your modem ? 

It's a netbook and unfortunately, no ethernet. However if I need to download a file, I would be able to through the wifi, I keep retrying until it works.   ( Internet works 40% of the time )

> **drdos2006 said:**
> 
What brand is your modem, is it a USB modem ?
How old is the modem ?


It's a very new modem, about 1 month old, and it's a normal one, not USB. I have 4 computers connecting to it, and a total of 3 smartphones, they all connect and download large files, without any problems whatsoever. In fact, one of the computers that connects to it has ubuntu installed, and it also has no problems. I am starting to suspect this is a driver problem.


> **drdos2006 said:**
> 
How far away from the exchange are you ?
 

Just about 6 metres. I tried varying the range (going further, or closer), but the problem was still there. The icon on the top right indicates I have a very strong WiFi signal. Coming to think of it, I'll try viewing the router's homepage next time it happens.

> **drdos2006 said:**
> 
Have you tried another phone line filter ?
Are you on ADSL2 or ADSL1 ?
 

Nope. I don't know if I am on ADSL1 or ADSL2, but then again, if all the computers(including an Ubuntu one) connect successfully, I would assume it is a problem with the netbook's settings.


I just thought about it now: my router's IP is **_192.168.1.254._**
Looking at the output of ifconfig, there is this line: **_Bcast:192.168.1.255_**

On a windows pc that is successfully connected to my network, the output of ipconfig is:
> Ethernet adapter Wireless Network Connection 2:

        Connection-specific DNS Suffix  . : lan
        IP Address. . . . . . . . . . . . : 192.168.1.66
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : [COLOR="Red"]192.168.1.254[/COLOR]

This is strange.... Shoudln't the 255 be a 254, and if yes, why did it happen in the first place, and how do I even manage to connect?

Thank you for your help, it is very much appreciated.

---

### Post by Davste on 2010-11-30
[SIZE="3"][FONT="Arial"]It's a driver problem. 
When the internet disconnects,  iwconfig shows > (wlan0) Bit Rate = 1 Mb/s
When internet is working, iwconfig shows > Bit Rate = 81 Mb/s I have an Atheros AR9285 chipset, and I haven't managed to find the right drivers.[/FONT][/SIZE]

---

### Post by Davste on 2010-11-30
Yep. Definitely driver problem, I can't view the router's homepage when the internet cuts off. I have tried downloading the atheros-ar9285 driver, but no success :(

The instructions at this thread
      [http://lovinglinux.ubuntuforums.org/showthread.php?t=1286503](http://lovinglinux.ubuntuforums.org/showthread.php?t=1286503)
will not work.

---

### Post by Davste on 2010-11-30
I'm Sorry, my netbook does have ethernet, the port was a bit hidden though and I did not see it =/ Didn't have it for very long :P

Anyway, I connected my laptop to the router, and internet worked - instantly. It doesn't stop working when I download a large file, and it's really fast. I really wish I could get WiFi working the same way ethernet does...

---

### Post by cybergnome on 2010-11-30
You need to set the rate of your device with IWCONFIG wlan0 rate 54M, etc., so the the rate doesn't revert to a lower setting that you want (use the highest that your router can handle).  The other issues is DNS servers.  If your network configuration doesn't know your DNS servers addresses, it can't resolve host names.  Numerical entries will still work.  You can manually enter the DNS addresses, which should be visible on your router's status page.

---

### Post by Davste on 2010-12-01
Thanks I'll try that out now. The router is N so I'll try iwconfig wlan0 rate 150.

---

### Post by Davste on 2010-12-01
It simply doesn't care what rate I set it to, the command
```
sudo iwconfig rate 150
```
has absolutely no effect. iwconfig immediately after showed that the rate didn't change to 150, but stayed at 81Mb/s.

I tried setting it to lower rates, but it just won't work. I really need to find a driver for the card.... that works.

---

### Post by Davste on 2010-12-01
.....Anyone?

---

### Post by uncaspi on 2010-12-01
You could also try these options to iwconfig

sudo iwconfig wlan0 power off     

which turn off the power save mode if it's supported.

sudo iwconfig wlan0 sens -80

which determine the lowest sensitive signal from AP.

---

### Post by Davste on 2010-12-01
```
sudo iwconfig wlan0 power off 
```

seemed to do nothing, the result of iwconfig before and after remained the same, **but** I was able to access my router's homepage, but not the internet. Maybe we are finally getting a bit closer to solving this...

```
sudo iwconfig wlan0 sens -80
```

just gave me "Set failed on device wlan0 : Operation not supported."

**Update:
1 minute later, back where we started, it won't display the router's page now.
The bit rate is 108mb/s, and I can't view any site still, strange...

---

### Post by Davste on 2010-12-01
I'm getting closer to the solution:


When I type in 192.168.1.254 (the modem's IP) on the netbook, it gives me the wireless router's page ( which is very bad ). On a normal computer, it gives me the modem's page. I have a CNET wireless router and a thomson modem.

Picture this: Two computers on. Both have 192.168.1.254 typed in the address bar, and both display different pages! This is incredible! 

The one that doesn't work gives me the CNET page.

I'm very confused now, because I also installed **the same version of ubuntu, on a computer on the same network**, and it worked fine, out of the box. It's just the netbook that's giving me problems. It doesn't make much sense... I still think it could be a driver problem.

---

### Post by Davste on 2010-12-01
Route -n, on both computers, show the same thing. This is getting more confusing by the minute.

---

### Post by uncaspi on 2010-12-01
I think there is something confused with the routing. You should not use class C ip's on both modem and router. If the router gateway is 192...something the modem gateway should be 10.x.x.x something. If you can log into one of the devices, change this ip.

---

### Post by Davste on 2010-12-02
There might be, but the Cnet IP is 192.168.1.64, while the thomson IP is 192.168.1.254.
When I type in 192.168.1.254 on the computer, it actually gives me the cnet page.. wierd. :S

I am dealing with two problems at once here, the WiFi problem, and the network problem. The wifi connection drops, so I can't even constantly view the router page, (without an ethernet cable) - with the ethernet cable, **connected to the Cnet**, the internet works fine. So preferably, I'd like to get the driver working properly first here. I really wish someone could help me set up my driver...

---

### Post by Davste on 2010-12-02
Come on... Any suggestions?

I was hoping to avoid going back to a previous version of ubuntu, but it seems to be my last chance of success.

---

### Post by zenlord on 2010-12-07
I can confirm this. A friend of mine has the same chipset and reported this behavior since an upgrade somewhere early november. Before that update everything went perfectly and eversince she has to reconnect to the wireless network every few minutes...

In the messages.log I can't see anything wrong - only an entry for the CRDA, everytime she reconnects (which is no surprise, but it is not helpful)

Zl.

---

### Post by Davste on 2010-12-07
I fixed the routing problem, now when the internet disconnects, it disconnects, and that's it. I have also connected to other networks and get the same problem, so it is definitely an ubuntu-ar9285 driver problem.

The lack of replies is unbelievable though. There are so many people here who probably have the knowledge to fix this, but either didn't read this post or.... I don't know...

I also found out (but I am not sure) that if you constantly ping your gateway (in my case, go to a terminal, and type in ping 192.168.1.254) the internet seems to disconnect somewhat much much less. Read the post above, I tried stopping power saving mode. No success.

Can someone **PLEASE** tell me, for the love of all the people who have this problem, HOW TO INSTALL THE ******* DRIVER?

I don't care if it's NDISWRAPPER. I don't care if you have to modify the kernel. Hell, so long as they are understandable instructions, that's fine.

---

### Post by afv on 2010-12-19
I am having the very same problem.

Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by Thucydides411 on 2011-02-09
I have the same problem with my wireless card:
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

I can't even begin to describe how frustrating it is to have to reset the wifi connection every five minutes. Although the gnome panel icon says I'm connected to my wireless network, I have to reconnect regularly to access the Internet.

---

### Post by Davste on 2011-02-10
> **Thucydides411 said:**
> I have the same problem with my wireless card:
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

I can't even begin to describe how frustrating it is to have to reset the wifi connection every five minutes. Although the gnome panel icon says I'm connected to my wireless network, I have to reconnect regularly to access the Internet.

Yeah I agree with you :/
It's so frustrating I ended up going back to windows on my netbook. I am still waiting for a solution!

---

### Post by ben91 on 2011-02-15
think i had your same prob.. try[this]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285")

---

### Post by Oele on 2011-02-17
I had the same problem on my Asus 1201HA EEE PC. It's caused by this bug: [https://bugs.launchpad.net/linux/+bug/518818]("https://bugs.launchpad.net/linux/+bug/518818")

A workaround is posted in comment #94.

---

### Post by Thucydides411 on 2011-03-26
> **Oele said:**
> I had the same problem on my Asus 1201HA EEE PC. It's caused by this bug: [https://bugs.launchpad.net/linux/+bug/518818]("https://bugs.launchpad.net/linux/+bug/518818")

A workaround is posted in comment #94.

I have found that installing the compat drivers, as suggested in the launchpad thread, resolves this issue. The easiest way to install these drivers is through the terminal:

```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic
```

---

### Post by foutes on 2011-03-26
I have this problem as well.

For a temp fix I changed the router to G only and no more disconnects.

---

### Post by conualfy on 2011-04-14
I am having a similar problem on my Toshiba Satellite C650 with Atheros AR9285 wifi, but it only shows when the router was configured to work on bgN or N alone standard. When I only use bg connection it seems to be working.
I use Ubuntu 10.10

```
uname -r
2.6.35-28-generic
```

```
lspci -nn -s 02:00.0
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```


I ran these commands after I set the wifi to work on bg (worked ok, but slower than buggy N/bgN).

```

modinfo ath9k
filename:       /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     56EEC2C35C7C808E96B8CA9
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,led-class,ath,cfg80211,ath9k_common
vermagic:       2.6.35-28-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
```


```
lspci -vv -s 02:00.0
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Lite-On Communications Inc Device 6611
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at d4400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k
```



I am a newbie, but I'll do the steps from [here]("https://bugs.launchpad.net/linux/+bug/518818/comments/94") if necessary as I'd like to use the faster N connection.

---

### Post by conualfy on 2011-04-15
Maybe it helps others. This is what I did in the end:
- ran this ([Thucydides411]("http://ubuntuforums.org/member.php?u=361460")'s comment):

```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic
```

The N connection seems to be working, but when the router is configured to work with bgn (all 3) the connection still gets slower. I did not see it not working completely, but is was slower. I guess the negociation fails at some point and it's not using the faster standard.

I configured the router to use only N and now it's a lot faster. I don't think this is a final solution as if I have guests or devices not working on 802.11 N the wireless router is useless.

---

### Post by conualfy on 2011-05-06
Update: it seemed to be a fix, but it was not. A few minutes later the disconnecting started again (network manager shows the connection is active).

---

### Post by Davste on 2011-05-06
What I usually do is let the netbook constantly ping the gateway. It seems to stay associated and doesn't get disconnected. I'll wait for the next version of ubuntu. Maybe they come up with a fix.

---

