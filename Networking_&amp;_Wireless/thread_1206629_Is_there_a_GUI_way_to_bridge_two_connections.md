---
title: "Is there a GUI way to bridge two connections"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by tunyawat on 2009-07-07
Hi, I want to to bridge two connections together, one is from NIC (et0) and another one is from wireless receiver (wl0). I'm quite scared to do things terminally. Is there a program (GUI) for this?

---

### Post by sadohert on 2009-07-07
Pretty sure the answer is no.  I've been hunting around to see if the network-manager gui and how it administers my network interfaces will play nicely with a bridge setup.  On my last Gusty install I basically had to remove network-manager and setup the bridge manually to make it work.  I can see this coming eventually, but have no idea when.

---

### Post by rootless on 2009-11-11
Sorry to revive an old thread- but I'd like to agree with this. There needs to be a GUI way of doing this- not that I don't know my way around the terminal, but nm-applet is a fragile piece of garbage. The script way of doing this seems rather hackish and the applet is liable to break if you look at it the wrong way.

/rant over.

---

### Post by kornphlake on 2009-11-11
Firestarter will let you bridge connections, select which interface you want to be LAN and which you want to be WAN then check the box that says something about connection sharing.

---

### Post by dmizer on 2009-11-11
> **kornphlake said:**
> Firestarter will let you bridge connections, select which interface you want to be LAN and which you want to be WAN then check the box that says something about connection sharing.

Firestarter causes more problems than it solves. This is not a good solution.

---

### Post by kornphlake on 2009-11-12
> **dmizer said:**
> Firestarter causes more problems than it solves. This is not a good solution.

Do you care to elaborate as to what kind of problems firestarter causes?  I don't have a lot of experience with firestarter or ubuntu, but given my limited exposure firestarter seems to do what it's advertised to do.

---

### Post by squidmaster on 2009-11-12
If you're using 9.04/.10 then you can just use the built in network manager. I bridged connection from my wireless to xbox with just a check box.

---

### Post by Kushkah on 2009-11-12
> **squidmaster said:**
> If you're using 9.04/.10 then you can just use the built in network manager. I bridged connection from my wireless to xbox with just a check box.

I'm trying to get my xbox360 to connect to my wireless network through my laptop.  In windows I can just select the two and hit bridge, but so far I've tried to bridge my wireless wlan0 to my wired eth0 both with bridge-utils and the settings in network manager (Running 9.10) and neither worked.  Am I missing anything?

---

### Post by squidmaster on 2009-11-13
Realllly simple! Let me upload some pictures

---

### Post by squidmaster on 2009-11-13
[IMG]http://i24.photobucket.com/albums/c31/kakor/Screenshot-NetworkConnections.png[/IMG]
[IMG]http://i24.photobucket.com/albums/c31/kakor/Screenshot-EditingAuto5hr00m5.png[/IMG]

I believe that it uses two different "user profiles" for the connections. Anyway, it started working when I did this.

---

### Post by dmizer on 2009-11-13
> **kornphlake said:**
> Do you care to elaborate as to what kind of problems firestarter causes?  I don't have a lot of experience with firestarter or ubuntu, but given my limited exposure firestarter seems to do what it's advertised to do.

Firestarter is overly restrictive by default. If you need network services, you have to specifically open all the necessary ports. For a firewall configuration, the LAN side of things should be fairly open and unrestrictive but that's certainly not the case here. Simple things like printer sharing and file sharing are rendered useless by Firestarter unless you really know how to configure it well.

Also, Firestarter is not supported in Ubuntu which means that you're relying on the Ubuntu community for updates. Plus it has a conflict with Network-Manager: [https://help.ubuntu.com/community/Firestarter#Troubleshooting](https://help.ubuntu.com/community/Firestarter#Troubleshooting)

Finally, most people don't realize that Firestarter is simply a front end for IPtables, which means that even if Firestarter is not running, your firewall IS active. This fact alone causes more headaches than I care to recall.

---

### Post by Krause on 2009-11-13
I agree, there needs to be a GUI way to do this.

I have set up LACP teams on Ubuntu before, and the network manager needs to be uninstalled since it wants to control the setting file, erasing any manual changes you make.

The actual software support is part of linux, network manager doesnt need to do anything except add options to set it through network manager itself, essentially doing the same thing that typing it in manually would do. Making it slightly easier to configure and eliminate the need to remove network manager if you want to aggregate ports.

---

### Post by Throbbing Gristle on 2009-12-22
> **dmizer said:**
> Firestarter is overly restrictive by default. If you need network services, you have to specifically open all the necessary ports. For a firewall configuration, the LAN side of things should be fairly open and unrestrictive but that's certainly not the case here. Simple things like printer sharing and file sharing are rendered useless by Firestarter unless you really know how to configure it well.

Also, Firestarter is not supported in Ubuntu which means that you're relying on the Ubuntu community for updates. Plus it has a conflict with Network-Manager: [https://help.ubuntu.com/community/Firestarter#Troubleshooting](https://help.ubuntu.com/community/Firestarter#Troubleshooting)

Finally, most people don't realize that Firestarter is simply a front end for IPtables, which means that even if Firestarter is not running, your firewall IS active. This fact alone causes more headaches than I care to recall.

I am a new member long time reader. My 904 version has firestarter in the add and remove menu? Ubuntu must ave officially started supporting this app? As for stumbling onto this thread. I was studying bridging too independent connections.

---

### Post by dmizer on 2009-12-23
> **Throbbing Gristle said:**
> I am a new member long time reader. My 904 version has firestarter in the add and remove menu? Ubuntu must ave officially started supporting this app? As for stumbling onto this thread. I was studying bridging too independent connections.
It's possible you have some alternative repositories enabled? Either way, even if Firestarter is part of the Ubuntu core, I would highly recommend avoiding it.

Besides, I believe bridging is now supported by Network Manager.

---

### Post by adnan-kamili on 2011-08-17
[SIZE=3][B]At last we have a GUI network bridge creator for linux/ubuntu "Network Bridge". I thought such an application is must for linux so i thought of writing one myself.
  You can dowload it from sourceforge.net[/B][/SIZE]
[SIZE=2][COLOR=black]"http://sourceforge.net/projects/bridger/files/Network%20Bridge/download"
  Enable the executable permission of the file and
make sure you run it using "sudo" else it won't work.
The new advanced version will come soon, completely rewritten and using IPC 
[/COLOR][/SIZE]

---

### Post by dmizer on 2011-08-18
> **adnan-kamili said:**
> At last we have a GUI network bridge creator for linux/ubuntu

Network manager has been able to do this for several releases now.

Closing this very old thread due to outdated and no longer valid information.

Thank you.

---

