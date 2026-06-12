---
title: "How can I stop my local IP address from changing?"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by snkngshps on 2008-12-06
I have a few computers on a local wireless network. We've set up folder sharing between the computers and occasionally I use the port forwarding feature on my router to access my home computer through my work computer via VNC. The problem is, after a week or two our local IP addresses change and I have reset up the port forwarding and our folder sharing.

Unfortunately I'm more ignorant when it comes to networking than I'd like to be. I don't know if this is something my ISP does, or my router does, or Ubuntu does, but how can I make our computers keep the same local IP? We use a linksys wireless router by the way. Thank you.

---

### Post by lovelyvik293 on 2008-12-06
I think u got the IP address by the DHCP and you can change to the manual mode where your IP is not changed by DHCP and remains same.):P

---

### Post by snkngshps on 2008-12-06
Ok, I'm still pretty new to messing with any of this. On my router's admin page there is an option to disable the local DHCP server. Is that all I need to do, or will I have to manually configure IP addresses for each of my machines after that?

---

### Post by lovelyvik293 on 2008-12-06
Don't disable the DHCP just go manually do in each computer because even when you disable the DHCP you have to go manually give the IP to each machine.

---

### Post by superprash2003 on 2008-12-07
which ubuntu version do you have ? post ifconfig output of theubuntu machine

---

### Post by lisati on 2008-12-07
I think it's probably easier to (a) keep DHCP switched on (on both your router and the machine(s) that connect(s) to the router), and (b) assign a specific IP address with a MAC address on your router. Details will depend on the specific router.....

---

### Post by razy60 on 2008-12-07
in some routers you can assign the IP address on a more permanent basis by reserving the ip to the mac address on others its called leasing an address. the settings have to be made in the router.


Raz

---

### Post by Dr Small on 2008-12-07
A sample static IP address on Ubuntu with the device ath0:
```
iface ath0 inet static
address 192.168.0.14
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid default
```

Just edit the values to match your router (gateway, netmask) and set your own static IP there. Add that to /etc/network/interfaces and comment out the other entries that are not referring to "lo", and restart networking:
```
sudo /etc/init.d/networking restart
```

---

### Post by TeXtonyx on 2008-12-07
I have a question about this. I thought you had to pay a little
extra to the ISP to obtain a fixed IP address from them, otherwise
they rotate them dynamically. Is that just a wrong notion?

---

### Post by snkngshps on 2008-12-07
> **superprash2003 said:**
> which ubuntu version do you have ? post ifconfig output of theubuntu machine


I'm running Ibex

```
joshua@SNKNGSHPS:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:277199 (277.1 KB)  TX bytes:277199 (277.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:82:56:37  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe82:5637/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6936459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6769528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3573922945 (3.5 GB)  TX bytes:1019547196 (1.0 GB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-82-56-37-36-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by Dr Small on 2008-12-07
> **TeXtonyx said:**
> I have a question about this. I thought you had to pay a little
extra to the ISP to obtain a fixed IP address from them, otherwise
they rotate them dynamically. Is that just a wrong notion?
That's for the internet connection. We are talking about LAN (local area network) IP addresses.

@snkngshps: How are you connected to your network? Wireless or Ethernet?

---

### Post by snkngshps on 2008-12-07
> **Dr Small said:**
> That's for the internet connection. We are talking about LAN (local area network) IP addresses.

@snkngshps: How are you connected to your network? Wireless or Ethernet?

Wirelessly. I saw your post before but I was still slightly confused. You may have to dumb it down a bit for me ;)

---

### Post by superprash2003 on 2008-12-08
you could edit your /etc/network/interfaces file manually and set static ip [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by tarps87 on 2008-12-08
> **snkngshps said:**
> access my home computer through my work computer via VNC. The problem is, after a week or two our local IP addresses change and I have reset up the port forwarding and our folder sharing.

Do you mean the IP of each machine or you 'external' IP (the one you type in at work to connect)?
Most routers will allow you to set IPs, I would expect this of a router that allows configurable port forwarding. Ideally you would want to keep using DHCP and assign IP address based on the machines mac.
This is how I have set my router up, all the file shares/servers, the printer and so some of the desktops have a fixed IPs. The laptops and any other devices that connect are assigned a 'random' address.

I don't know what model you have but page 16 may help:
[linksys manual]("http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fpdf&blobheadervalue2=inline%3B+filename%3DWRT150N_ug.pdf&blobkey=id&blobtable=MungoBlobs&blobwhere=1193768812096&ssbinary=true&lid=1218384378B05")

Edit: meant page 16 (DHCP reservation)

---

### Post by snkngshps on 2008-12-08
> **tarps87 said:**
> Do you mean the IP of each machine or you 'external' IP (the one you type in at work to connect)?
Most routers will allow you to set IPs, I would expect this of a router that allows configurable port forwarding. Ideally you would want to keep using DHCP and assign IP address based on the machines mac.
This is how I have set my router up, all the file shares/servers, the printer and so some of the desktops have a fixed IPs. The laptops and any other devices that connect are assigned a 'random' address.

I don't know what model you have but page 16 may help:
[linksys manual]("http://www.linksys.com/servlet/Satellite?blobcol=urldata&blobheadername1=Content-Type&blobheadername2=Content-Disposition&blobheadervalue1=application%2Fpdf&blobheadervalue2=inline%3B+filename%3DWRT150N_ug.pdf&blobkey=id&blobtable=MungoBlobs&blobwhere=1193768812096&ssbinary=true&lid=1218384378B05")

Edit: meant page 16 (DHCP reservation)

It's the local IP that changes, not the external, but since I have the port forwarding on my router set to my computer's local IP when my local IP changes, I can no longer access my computer. I'll take a look at that guide though. All I really want is to create a permanent, local IP address so I don't have to constantly reset my bookmarks and everything.

---

### Post by snkngshps on 2008-12-08
> **superprash2003 said:**
> you could edit your /etc/network/interfaces file manually and set static ip [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

This looks to be exactly what I'm looking for! I'm at work right now but I'm going to give this a shot when I get home.

Edit: This might be a pain to ask, but can anyone look at the iconfig information I posted earlier and help me with what I should be putting in, relevant to this guide. I understand most of it but the only part this is confusing me is the eth0. I'm thinking this will be different for me, but I don't want to mess anything up.

---

### Post by Dr Small on 2008-12-08
> **snkngshps said:**
> This looks to be exactly what I'm looking for! I'm at work right now but I'm going to give this a shot when I get home.

Edit: This might be a pain to ask, but can anyone look at the iconfig information I posted earlier and help me with what I should be putting in, relevant to this guide. I understand most of it but the only part this is confusing me is the eth0. I'm thinking this will be different for me, but I don't want to mess anything up.
Just replace eth0 with wlan0, as that looks like your interface from the ifconfig output.

---

### Post by snkngshps on 2008-12-08
> **Dr Small said:**
> Just replace eth0 with wlan0, as that looks like your interface from the ifconfig output.

I'm running into a problem with step 4 of the guide. My interfaces file only has the following 2 lines in it:

```
auto lo
iface lo inet loopback

```

The guide says to replace the line "iface eth0 inet dhcp" but I don't have that line at all.

---

### Post by tarps87 on 2008-12-09
Adding the following lines to the end of the file should work

iface wlan0 inet static
address *ipadd*
netmask *mask*
gateway *gateway*

---

### Post by noBananas on 2008-12-09
> **TeXtonyx said:**
> I have a question about this. I thought you had to pay a little
extra to the ISP to obtain a fixed IP address from them, otherwise
they rotate them dynamically. Is that just a wrong notion?
It depends on your ISP. If you're just talking about home service, you may have a static IP address. Best way is to find out your *external* IP address and monitor it over time. If you use a home router, you must use your router interface to see the external IP. I've had the same external IP address for years from my ISP without paying any extra charge. 

The original poster's question was about setting up a static IP address for the *internal* IP, not the *external* one. I trust you understand the difference.

---

### Post by confusedstingray on 2008-12-09
just an idea depending on the router you can make you life easier by setting the dchp part on the router, under the lease area should have opinion that the lease never expires. and the router will give the computers login in the same ip as long as the router's power stay on it ill remember it in ram.

---

### Post by snkngshps on 2008-12-09
> **tarps87 said:**
> Adding the following lines to the end of the file should work

iface wlan0 inet static
address *ipadd*
netmask *mask*
gateway *gateway*

Ok I really feel like I'm beating a dead horse but I just want to make sure I'm not messing anything up. At the end of the tutorial it says to do this:

[I]Step 6 : Now Back in your terminal type sudo /etc/init.d/networking restart
Step 7 : Then type sudo ifdown eth0
Step 8 : Then type sudo ifup eth0[/I]

In the example they used the were working with eth0 but I'm working with wlan0 so I should change set 7 and 8 to say wlan0 instead correct? I tried doing that but I got an error for each command. My connection is still working so I know I didn't mess anything up, but I want to make sure I did properly set up the static IP. Here is my output:

```
joshua@SNKNGSHPS:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
SIOCDELRT: No such process
                                                                         [ OK ]
joshua@SNKNGSHPS:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
joshua@SNKNGSHPS:~$ sudo ifuo wlan0
sudo: ifuo: command not found
joshua@SNKNGSHPS:~$ sudo ifup wlan0
SIOCSIFNETMASK: Invalid argument
Failed to bring up wlan0.

```

---

### Post by tarps87 on 2008-12-10
Does this behave the same without the lines in?

---

### Post by superprash2003 on 2008-12-10
post output of /etc/network/interfaces file

---

