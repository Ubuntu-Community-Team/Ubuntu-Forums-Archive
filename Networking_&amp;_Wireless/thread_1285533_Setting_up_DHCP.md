---
title: "Setting up DHCP"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by AllRadioisDead on 2009-10-07
Hi, I run several different boxes in my house, but I can never get the mino-iso to work because the DHCP in my router is not configured. My network consists of a Bell Canada Speedstream modem, and a Linksys WRT54GS router. On the routers configuration page, DHCP is off. I do not know how to configure it, can someone help me get it set up? Thanks a bunch.

---

### Post by ermeyers on 2009-10-07
Login to your router, and go to DHCP setup.  Turn DHCP service on.  Look at the DHCP address range being provided.  If you need to assign a specific "static" address to something, then get its MAC address and fill it in with the IP to the lower box.  It fairly simple, and works well.

---

### Post by AllRadioisDead on 2009-10-14
Hey, sorry I haven't replied, I've been a bit busy and haven't had time to get back into this. When I enable it, the default starting IP is **192.168.2.100**.
I don't believe I need to assign a static IP, so where can I go from here? The mini-iso still can't connect to my network. Thanks!

---

### Post by AllRadioisDead on 2009-10-14
Bump!

---

### Post by oldfred on 2009-10-15
If you go to a terminal on a device you are connecting to do: 
ifconfig
You should get a list showing lo and eth0 or eth1. The eth port if it is the first device and is set up for DHCP should get your 192.168.2.100.

If not go back to system preference network connections and add a connection.

---

### Post by AllRadioisDead on 2009-10-15
Hi, I forgot to mention this is a wireless connection so I'm using wlan0.
Since I am currently unable to do a netinstall, I have xubuntu on my laptop right now. I have noticed that when I enable DHCP, I can connect to the network but I am unable to access the internet.

---

### Post by AllRadioisDead on 2009-10-15
Edit: Sorry for the double post, here is the output of ifconfig with DHCP disabled on xubuntu.
```

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:16:c9:fd  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe16:c9fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104856739 (104.8 MB)  TX bytes:7266642 (7.2 MB)


```

---

### Post by oldfred on 2009-10-15
For my linksys I did not have to do anything but plug it into the cable modem. Did you check the linksys tab status. Status should show your connection.
The instructions say you may have to enter Host and or Domain Names. I did not have to, and status shows no Host and automatically set up Domain name.
Under wireless I did have to get security and passwords to match before it worked. But if you are on the local network that should be ok.

---

### Post by AllRadioisDead on 2009-10-15
Hi, thanks for the reply.
I should mention that I don't know much about this, so please bear with me as my knowledge is limited. This is not my internet, it's my parents. I'm just a student up to no good :)
The modem has its own status page, and it gives me my IP address, Subnet mask, 2 DNS server addresses, the modem IP and the mac address. 
When I turn DHCP on, my status page has 3 tabs. The first is "Router" and contains:
```


Login Type:           **Automatic Configuration - DHCP**                                                         
IP Address:           **0.0.0.0**                                            
          

Subnet Mask:           **0.0.0.0**                       
Default Gateway:           **0.0.0.0**
```In "Local network" I have:
```


MAC Address:            **00:18:F8:D6:EC:47**                        
                                        
IP Address: [B]192.168.2.12
[/B]Subnet Mask: **255.255.255.0**

DHCP Server: [B]Enable

[/B]Start IP Address:[B] 192.168.2.100

[/B]End IP Address: **192.168.2.149 **           

```Then the third is "wireless" with the ssid and DHCP status (On).

---

### Post by gmjs on 2009-10-15
Strange.  Usually a simple 'enable' of the DHCP feature on the router is enough.  Is there any chance you could test the machine running the mini-iso cd on the wired network, rather than wirelessly; just to confirm that the DHCP server is running correctly?

Failing that, perhaps disabling the static IP address on another PC on the network (Linux or Windows) and requesting a lease to see if a DHCP offer is received is easier?

---

### Post by AllRadioisDead on 2009-10-15
Hang on, I just realized my laptops wireless card was not supported until kernel 2.6.26, so I'm going to download the latest image and try again. I believe my mini-iso is from 8.10, I'll report back if it works. Right now testing on a wired network is not an option because the only cable is being used.

---

