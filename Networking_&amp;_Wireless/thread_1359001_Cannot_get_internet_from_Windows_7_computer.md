---
title: "Cannot get internet from Windows 7 computer"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by valzi on 2009-12-19
Hey everybody.

Here's my situation:

1. I am getting wireless internet on my Win 7 laptop.
2. I have a Ubuntu 9.10 desktop connected to the Win 7 laptop by ethernet.
3. Both computers claim to see a wired network.
4. I cannot get internet on the Ubuntu laptop.
5. Neither computer can access the other's shares, though I have installed Samba on Ubuntu.
6. I cannot permanently physically connect the desktop to the router the wireless internet is coming from. I have temporarily tried this, however. Doing so allows me to use the internet and share folders.

Here are my questions:
1. How do I get internet to Ubuntu desktop computer?
2. How do I share files between the two computers?

Thanks in advance for the help!

-Valzi

---

### Post by valzi on 2009-12-20
Bump. Need any more info?

-Valzi

---

### Post by Iowan on 2009-12-20
Can you **ping** one computer from the other? Have you tried connecting the machines with crossover cable (or a hub/switch/router)?

---

### Post by valzi on 2009-12-20
Yes, I've tried connecting through a switch. As far as I can tell, there is no difference.

My wired connection method is "Shared to other computers."

My Ubuntu machine can ping my Windows 7 machine, but my Windows 7 machine cannot ping my Ubuntu machine.

After a reboot this morning, my Ubuntu machine is able to access Windows 7 folders through Samba. (My Windows 7 machine obviously cannot see Ubuntu folders, since it cannot ping the machine.) That's great in that I can share files now, but what I really want is to get my Ubuntu machine access to my internet connection.

---

### Post by valzi on 2009-12-20
New development:

Now, when I plug in the ethernet cord that goes from my Win 7 pc to my Ubuntu pc, the internet quits working on even my laptop. I think my computer is confused about using more than one network at time, perhaps?

---

### Post by Iowan on 2009-12-20
I presume you tried **ping** by name AND address. Is there a firewall on the Ubuntu machine that may be blocking pings?

---

### Post by valzi on 2009-12-20
Yes, I've attempted ping by ip address and by computer name. Both only work when pinging the Win 7 machine from the Ubuntu machine.

I did not install a firewall on Ubuntu and do not see an automatic firewall either, so no, there appears to be no firewall on it. Also, the Win 7 firewall is disabled.

---

### Post by jamesisin on 2009-12-20
Maybe I misunderstand, but are you trying to use your Windows 7 machine as a gateway for your Ubuntu machine to access the Internet?  If so, that must be enabled in Windows and your Windows machine will need two nics (one for incoming and one for outgoing).  I guess I'm a little unclear why you would want to set things up in this unusual fashion.

---

### Post by valzi on 2009-12-20
Yes, you are describing the situation correctly. This is the map of what I am attempting:

desktop Ubuntu ---> laptop Windows 7 -----> wireless router ====> internet

The reason I am doing this is because the windows 7 machine has a wireless card and the Ubuntu machine does not. Thus, this is the only map available to me.

```
If so, that must be enabled in Windows and your Windows machine will need two nics (one for incoming and one for outgoing).
```

I don't understand what you mean here. If you're referring to enabling internet sharing on my ethernet port using my wireless internet, I've done that. However, when I plug in the ethernet cord, rather than sharing the internet, it simply disables my internet on my Windows 7 computer.

As far as the 2 nics stuff goes, I have no idea what you're talking about yet. If you could explain in more depth, I would be grateful.

-Valzi

---

### Post by zaphod777 on 2009-12-20
You need to check that there are no power options in Win7 that disable the Wireless when the NIC is connected I know a lot of the pre installed Manufacturer software will do that. I know Dell would disable the NIC if you weren't connected to the AC adapter. Also check in the Bios for this setting under power management.

Furthermore you need to use a crossover cable to connect a PC directly to a PC.

The rule of thumb is similar devices need a crossover cable to connect each other.

connecting older switches to each other require a crossover cable but newer ones will cross it automaticly. However PC to OC still require it.

---

### Post by valzi on 2009-12-20
re: zaphod777:

1. I don't seem to have any power options disabling my wireless card. I installed everything myself after formatting the hard drive and don't use any third-party networking software.

2. I'll check in the bios tonight, but can't at the moment.

3. I can connect two modern Windows 7 machines to each other without a crossover cable. However, the Ubuntu machine in this setup is an older machine, so maybe that's the problem. I'm running the ethernet through a Linksys 10/100 8-port Workgroup Switch (EZXS88W.) I don't know anything about this crossover stuff - is it doing the same thing as a crossover cable?

re: jamesisin:

Do I really need another network card to share my internet?

-Valzi

---

### Post by zaphod777 on 2009-12-20
In the network manager on the Windows 7 machine it will show weather it is disabled or not. Newer machines may automaticly cross over the connection but if the older machine probably won't. 

However it should work just fine when connected to the switch.

A crossover cable is a network cable that has the transmit and send lines crossed for directly connecting to machines without a switch.

[http://en.wikipedia.org/wiki/Crossover_cable](http://en.wikipedia.org/wiki/Crossover_cable)

---

### Post by valzi on 2009-12-21
Okay, checked everything. It's not disabled in the network manager or in the BIOS.

This seems to suggest the problem is a configuration one, right?

---

### Post by zaphod777 on 2009-12-21
yes but I still think you need a crossover cable or use a small switch.

Okay I need a few details that you already provided but just to get it all clear.

1. does this configuration work with both machines connected to a switch?
2. The internet connection has been shared on the Windows7 machine right?
3. What IP do both machines get?
4. can you ping the machines from each other?

---

### Post by valzi on 2009-12-21
1. I've been using a switch but cannot share internet.
2. The Windows 7 machine is showing the internet from the wireless adapter being shared via the ethernet adapter. 
3. What do you mean by which ip do they "get"? I'll give you the external ip that each is sending to the ethernet network in a minute. Is that what you're looking for?
4. Only the Ubuntu machine can ping the Windows machine. The Windows machine cannot ping the Ubuntu machine.

---

### Post by valzi on 2009-12-21
Windows 7 IPv4 Address: 10.42.43.10
Ubuntu IPv4 Broadcast Address: 10.42.43.255

Ubuntu can ping 10.42.43.10
Windows 7 cannot ping 10.42.43.255

When I plug in the ethernet cable with this configuration, Windows 7 loses the ability to go to websites, but downloads and instant messaging still work.

---

### Post by zaphod777 on 2009-12-21
Okay I think I see the problem here. It is actually quite a simple one.

you Win7 machine should have 2 Interfaces one with the public ip assigned by your ISP the other one will turn on DHCP and use a private IP scheme of 192.168.0.x you Win7 machine will get an ip of x.x.x.1 and ubuntu machine will get .2. The Ubuntu machine should be set to DHCP.

10.42.43.255 is a reserved ip address for bradcast. ON you ubuntu machine do a ifconfig to see its assigned ip.

also check dns settings in ubuntu they should be set to automatic.

On your Win 7 machine do an ipconfig /all

might want to take a look here:
[http://discussions.virtualdr.com/archive/index.php/t-237754.html](http://discussions.virtualdr.com/archive/index.php/t-237754.html)

---

### Post by valzi on 2009-12-22
> **zaphod777 said:**
> 
you Win7 machine should have 2 Interfaces one with the public ip assigned by your ISP the other one will turn on DHCP and use a private IP scheme of 192.168.0.x you Win7 machine will get an ip of x.x.x.1 and ubuntu machine will get .2. The Ubuntu machine should be set to DHCP.

also check dns settings in ubuntu they should be set to automatic.

I'm not really sure what the solution you're proposing is. I probably missed something. I'm going to list everything I did after reading your post now.

I changed my Ubuntu machine from link-local only to DHCP, which allows my win 7 laptop to remain connected to the internet when the ethernet cable is plugged in. However, it also prevents any signs of connectivity to the Ubuntu machine, including the Windows 7 share I had access to before.

When I choose "Automatic (DHCP)," the "DNS servers" box is greyed out, so I assume it is set to automatic, correct?

This is what seems relevant from ipconfig /all and ifconfig when the machines are physically connected by the ethernet cord:

```
Win 7:
Ethernet adapter Local Area Connection:

   Description . . . . . . . . . . . : Marvell Yukon 88E8071 PCI-E Gigabit Ether
net Controller
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 10.42.43.10(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 10.42.43.1
   DHCP Server . . . . . . . . . . . : 10.42.43.1

Wireless LAN adapter Wireless Network Connection:

   Description . . . . . . . . . . . : Intel(R) WiFi Link 5100 AGN
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.0.3(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   DHCP Server . . . . . . . . . . . : 192.168.0.1

Ubuntu:
eth0
inet addr:10.42.43.1
Bcast: 10.42.43.255

```

---

### Post by zaphod777 on 2009-12-22
okay i see the problem you are sharing your eathernet and broadcasting through the wireless adapter. You might need a usb nic to share but it  might be easier to buy a cheap router.

For this to work you need to have one nic 
connected to the wan and the other connected the lan.  Basicly your pc becomes a router. 

You might be able to run vm with t virtual nics on the same nic and run it all through a switch.

Personally I would buy a cheap router.

So it should go 

internet -> NIC1 (10.42.43.10)-> Win7 -> NIC2 (192.168.0.3) -> Ubuntu (192.168.0.4)

---

### Post by valzi on 2009-12-22
So you're saying I need a router that *receives* wireless and *sends* ethernet, right?

Internet ==> Wireless router in building --> my new router ==> Ubuntu

-- is wireless and == is ethernet

This leaves Windows 7 out of it altogether since my Win 7 machine already connects to the current wireless router.

Do you have a suggestion for a good cheap router of this sort?

---

### Post by valzi on 2009-12-22
Nevermind, I just didn't understand your diagram, since your network cards look like separate devices.

I might just get a USB wifi adapter or a wifi card for the desktop, since using my laptop as a router seems impossible.

---

### Post by zaphod777 on 2009-12-22
Okay I misunderstood why you were doing it this way it think where you went wrong is you shared your eathernet connection not the wireless connection.

Anyway what you can probably do is get a wireless game adapter they have wireless on one end then go to eathernet. then plug that into the WAN port on a router.

---

### Post by jamesisin on 2009-12-23
> **valzi said:**
> Yes, you are describing the situation correctly. 

The reason I am doing this is because the windows 7 machine has a wireless card and the Ubuntu machine does not. Thus, this is the only map available to me.

If you're referring to enabling internet sharing on my ethernet port using my wireless internet, I've done that. However, when I plug in the ethernet cord, rather than sharing the internet, it simply disables my internet on my Windows 7 computer.




You need one network connection device (NIC) for connecting the two machines together and a second NIC for connecting to the Internet.  (It may be possible to do both using one wireless card but never mind that for now.)  If your Windows machine has an ethernet port AND a wireless card you have two NIC's.

As mentioned (by zaphod777), you will need to use a cross over cable to connect two machines directly through ethernet.  You may alternatively use a hub (or a router or a switch but it sounds like you have neither) and regular cables.

My first recommendation would be to connect your Ubu machine directly to your wireless router (doesn't it have any ports?) via ethernet.  But if you must connect to the wireless through the Windows machine you will have to enable network connection sharing.

[http://www.windowsreference.com/windows-vista/step-by-step-internet-connection-sharing-ics-setup-in-vista/](http://www.windowsreference.com/windows-vista/step-by-step-internet-connection-sharing-ics-setup-in-vista/)

These instructions ought to be the same (or close enough) for Windows 7.

As to disabling your wireless when a cable is attached, you should be able to tell your system to keep the wireless running (off the top of my head I would start with what comes in the right-click menu of the wireless network icon in your system tray) but it could be very specific to your wireless software.

Hope that gets you a little closer.

---

### Post by jamesisin on 2009-12-23
> **valzi said:**
> ```
Win 7:
Ethernet adapter Local Area Connection:

   Description . . . . . . . . . . . : Marvell Yukon 88E8071 PCI-E Gigabit Ether
net Controller
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 10.42.43.10(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 10.42.43.1
   DHCP Server . . . . . . . . . . . : 10.42.43.1

Wireless LAN adapter Wireless Network Connection:

   Description . . . . . . . . . . . : Intel(R) WiFi Link 5100 AGN
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.0.3(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   DHCP Server . . . . . . . . . . . : 192.168.0.1

Ubuntu:
eth0
inet addr:10.42.43.1
Bcast: 10.42.43.255

```

This is not going to work.  The Gateway listed for your Ubu machine (not shown above) needs to be the IP address of your ethernet controller on the Windows machine ("IPv4 Address. . . . . . . . . . . : 10.42.43.10(Preferred)".

Your Ubu machine can have any IP address except the gateway address and the IP address of the Windows 7 wireless connection ("IPv4 Address. . . . . . . . . . . : 192.168.0.3(Preferred)".

Make your life simple and use 10.42.43.99 or something like that.  It ought to do this automatically through DHCP if enabled properly though.  Set up as it is above it appears that your Windows machine is trying to use your Ubu machine as its gateway (exactly backwards).

Confused yet?

---

### Post by jamesisin on 2009-12-23
If you want to set up a manual connection for this machine (and there are advantages to doing so), right-click on the network icon in the notification area (Ubuntu) and choose "Edit Connections...".

Click the Add button and choose Manual from the IPv4 Settings tab's Method dropdown.  Then click that Add button and enter an IP address (use the one from my previous post) Netmask (say 255.255.255.0) and a Gateway (see previous post).  Hit enter or the number won't get saved.  Name it something special and click OK.

This will allow you to use the eth0 connection in other locations while reserving this new manual configuration for your odd set up.

Sorry to dump all this on you at once but I've not been around lately and I wouldn't want you to feel neglected.

---

### Post by valzi on 2009-12-23
jamesisin: Regarding your questions:

1. I'm using a switch
2. Our wireless router is out of range for an ethernet cord from this computer. Besides, I don't think my roommate would appreciate the long cord running into his office from the hallway.

I tried the manual setup as you described and now both computers can ping each other! Thanks. Internet sharing is not working, however. Also, shared network locations are not working (I have SAMBA set up and sharing works when I'm plugged into the router.)

Windows 7 is set to share the wireless internet services with the ethernet network.

Poking around a bit until you suggest something... Let me know if you need any info to continue.

---

### Post by jamesisin on 2009-12-23
> **valzi said:**
> If you're referring to enabling internet sharing on my ethernet port using my wireless internet, I've done that.


I could be mistaken but I should think you would want to enable sharing on the wired port where you are attaching the other machine.

---

### Post by valzi on 2009-12-27
> **jamesisin said:**
> I could be mistaken but I should think you would want to enable sharing on the wired port where you are attaching the other machine.

Which is what I just said I did, actually. I may have phrased it confusingly. Anyway, that doesn't work, so I'm waiting on my Wireless USB adapter to arrive in the mail.

---

### Post by jamesisin on 2009-12-27
Oops.  Ok.

So, you are getting a wireless card for your Ubu machine then?  I think that's your strongest alternative anyway.

---

### Post by valzi on 2009-12-27
Not an *actual* card, but a wireless USB adapter. It's essentially an external card. Here's an example of one: [http://www.belkin.com/IWCatProductPage.process?Product_Id=179211](http://www.belkin.com/IWCatProductPage.process?Product_Id=179211)

My friend happened to have an extra one he's mailing me. Seems like that should solve the problem.

---

### Post by jamesisin on 2009-12-28
Internal or external, giving that Ubu machine a wireless adapter all its own would be your best solution.

---

### Post by SeaJayEmm on 2009-12-29
If this has not been solved yet, you have to bridge your wireless connection with your LAN connection on the Windows machine.

---

