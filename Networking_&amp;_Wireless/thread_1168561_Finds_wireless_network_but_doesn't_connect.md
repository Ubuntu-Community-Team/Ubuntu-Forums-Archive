---
title: "Finds wireless network but doesn't connect"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by rbubamara on 2009-05-24
Hi everyone, 

I'm a newbie using dual-boot with Windows XP and Ubuntu 9.04. 
The only reason I don't change 100% to Ubuntu is because, for some reason, I can't connect to the wireless network. I'm living in an University Hall of Residence and using the public Wi-Fi, which has a very weak and insecure signal, but I can connect it with Windows.
In Ubuntu, it detects the network (although I have to click in "connect to hidden networks") but I doesn't connect. The ethernet wired network works perfeclty though. 

Anyone could help me with this?

Thanks!

---

### Post by RedSingularity on 2009-05-26
Is it hidden in windows as well?

---

### Post by superprash2003 on 2009-05-26
do you see any error?? post output of** iwconfig** and **ifconfig** when you try connecting..

---

### Post by rbubamara on 2009-05-30
No it's not hidden in Windows and I don't think it shows any error, it just tries to connect and then this "Wireless disconnected" message appears. :(

---

### Post by RedSingularity on 2009-05-30
Its not hidden if you can see it in windows.  Did you look in System>Admin>Software sources?  You may be able to activate it there.

Oh and post "lspci" from your terminal.

---

### Post by Falconhead on 2009-05-30
Hi fellow linux ubuntu users, (new ubuntu user v9.04)
Wireless network is found, my network is broadcast WPA2-personal, unable to connect just keeps asking for WPA2 Key.  

04:04.0 Network controller: RaLink RT2800 802.11n PCI

ra0       Link encap:Ethernet  HWaddr (populated) 
          inet6 addr: fe80::208:54ff:fe8d:7278/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:41972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8991857 (8.9 MB)  TX bytes:0 (0.0 B)
          Interrupt:17 

description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: ra0
       version: 00
       serial: (same as above)
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless

Any help would be great I have no idea what the issue is, I am familiar using to Red Hat and running wired connections. This is a head first dive into Linux for me. 

Router: DIR-655
Mobo: BioStar P4M900-M4
PCI adaptor 802.11n Wireless ENLWI-N

---

### Post by smalldog on 2009-05-30
> **Falconhead said:**
> Hi fellow linux ubuntu users, (new ubuntu user v9.04)
Wireless network is found, my network is broadcast WPA2-personal, unable to connect just keeps asking for WPA2 Key.  

04:04.0 Network controller: RaLink RT2800 802.11n PCI

ra0       Link encap:Ethernet  HWaddr (populated) 
          inet6 addr: fe80::208:54ff:fe8d:7278/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:41972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8991857 (8.9 MB)  TX bytes:0 (0.0 B)
          Interrupt:17 

description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: ra0
       version: 00
       serial: (same as above)
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless

Any help would be great I have no idea what the issue is, I am familiar using to Red Hat and running wired connections. This is a head first dive into Linux for me. 

Router: DIR-655
Mobo: BioStar P4M900-M4
PCI adaptor 802.11n Wireless ENLWI-N

Are you using network-manager? Do you ever try other connection manager? Try it. However, you must know how to manually bring your network interface up, otherwise the new connection manager application might force you remove the old one - that make you no network connection anymore. Goodluck

---

### Post by Falconhead on 2009-05-31
I did use the GUI network manager and named the connection ra0 mimic-ing eth0 settings. I even went as far as naming it Auto ra0 like the manager did eth0. I am not sure what command you are referring too.  Could you elaborate more on the command?

---

### Post by juky on 2009-05-31
Hi Falconhead,

I had a similar issue with my home wireless connection. I have a Fujitsu-Siemens notebook with Intel wireless adapter, which works flawlessly in XP and previously in Hardy Heron 8.04. In Jaunty Jackalope 9.04 it was not the case.

With network-manager I could see my WEP protected network, edit settings etc, but no luck, either with DHCP or manual configuration. Also, I have tried manual network configuration found on this forum, but no luck all the way. In both cases, it says "connected", but when I try to ping my router, I get "Destination host unreachable" message from my adapter. And for what I know, it is a known bug in 9.04 release, you can find this information on the internet.

Now the connection works for me, and here is what I have done:

Installed "WICD" via "System-Administration-Synaptic Package Manager". It is a GUI interface package which replaces network-manager. "WICD" installation will automatically uninstall default "network-manager".

After installing, you can start it from "Applications-Internet-Wicd Network Manager". Everything displayed there is pretty much self-explained, you can see it in attached screen-shot.

Anyhow, still minor issue, I cannot connect if I set-up static IP address, it works only with dynamic (DHCP) address, but until permanent fix it is a good solution.


Hope it will work for you also this way.

Good luck,
juky

---

### Post by Falconhead on 2009-06-01
Thanks Juky I will google that and give it a try sometime this week.

---

### Post by The Jinx on 2009-06-01
Hi,

I have the exact same problem as the OP, rbubamara, I am running the Dell LPIA version of 8.04 on my Dell Mini 9 and although I can see my wireless connection I cannot connect to it. I tried disabling all my security and disabling the MAC filtering and I still have no luck. Can anyone please give me some directions on what to do. Or what I should post so someone may help me out.

PS: I have not check to see if I can get online with the netbook on Windows 

Thank You,
Jinx

---

### Post by The Jinx on 2009-06-02
bump?

---

### Post by juky on 2009-06-02
The Jinx, try the soulution on the bottom of the page 1 which I have provided. It worked for me.

---

