---
title: "Netgear Stora: Access from Linux?"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by EchoBeach on 2010-09-11
I have a Netgear Stora that I've been using with Windows for a while now.
Does anyone know what I need to do to be able to access it from my Ubuntu installation, please?
Echo

---

### Post by MaindotC on 2010-09-11
You can start [here](http://is.gd/f6ivI).  The 1st result talks about Ubuntu.

---

### Post by EchoBeach on 2010-09-28
Thanks strAlan.
I searched again and found [this]("http://forum1.netgear.com/showpost.php?p=252659&postcount=5").
```
id

[take note of your current uid and gid]

sudo mkdir /mnt/stora/FamilyLibray
sudo mount -t cifs -o  nounix,uid=YOUR_UID,gid=YOUR_GID,file_mode=0777,dir_mode=0777,username=YOUR_STORA_LOGIN,password=YOUR_STORA_PASSWORD //YOUR_STORA_IP_ADDRESS/FamilyLibrary /mnt/stora/FamilyLibrary
```
All I need to do know is to work out how I move the username/password parameters into a file in my home folder - instead of having them on the command line - as in the format for fstab:```
//hipservlocation /mountpoint cifs credentials=/YOUR_HOME_FOLDER/.smbcredentials,noperm 0 0
```The other related problem is that the stora doesn't always have the same IP address.
Thanks
Echo

---

### Post by JLNemisis on 2012-05-01
> **EchoBeach said:**
> Thanks strAlan.
I searched again and found [this]("http://forum1.netgear.com/showpost.php?p=252659&postcount=5").
```
id
 
[take note of your current uid and gid]
 
sudo mkdir /mnt/stora/FamilyLibray
sudo mount -t cifs -o  nounix,uid=YOUR_UID,gid=YOUR_GID,file_mode=0777,dir_mode=0777,username=YOUR_STORA_LOGIN,password=YOUR_STORA_PASSWORD //YOUR_STORA_IP_ADDRESS/FamilyLibrary /mnt/stora/FamilyLibrary
```All I need to do know is to work out how I move the username/password parameters into a file in my home folder - instead of having them on the command line - as in the format for fstab:```
//hipservlocation /mountpoint cifs credentials=/YOUR_HOME_FOLDER/.smbcredentials,noperm 0 0
```The other related problem is that the stora doesn't always have the same IP address.
Thanks
Echo
 
 
You've probably found a solution, but I felt a answer to the changing IP address for your stora was needed to help people who are searching for that answer.
 
The ip address for the stora is set by your router.
Log into the routers control panel and set it to serve DHCP.
Then it is just a matter of assigning your stora a IP.
Most routers I have come across want a MAC address to accomplish this.
That information will never change, unless you physically change your stora.
The MAC address for the stora is located on the sticker on the bottom of the stora.
You'll also have your Serial Number, Model Number, and a Product Key (unlocks windows software)
Once you have set your stora with a static IP on your router you will also need to set that same ip in the stora set up.
 
VIA Windows: 

Assuming you have a dual boot system or an available windows os on your network.
Start the stora application, sign in. you will need administrator account rights.
browse to **Settings**. expand **LAN Connection**,
The first item is "Obtain IP Address Automatically" set to **NO**.
The next item is **Server IP Address **enter the IP address you chose in your router set up. [SIZE=1](IE**:** **192.168.1.25** )[/SIZE]
The next item is **Server Netmask** Most users will use **Netmask.24(255.255.255.0) **(this is a drop menu item)
The next item is **Gateway **enter the ***IP address*** for your router. (IE: **192.168.1.1** )
The next item is **DNS Server 1 **leave this blank or **Do Not change the information.**
The next item is **DNS Server 2** leave this blank.
 
VIA WebAccess: [ http://www.mystora.com/]("http://www.mystora.com/")

This method works with Windows, Linux, Mac, Android devices. (from anywhere with anything)
Browsers I have tested this with: FF 12, IE9 (have yet to try from kindle fire)
This will give you the same options as the windows application included on the setup disk.
You will need [Adobe Flash Player 10]("http://www.adobe.com/devnet/flashplayer.html") or better.

However, If you are connecting through the web and your IP keeps changing.
That is because you have a dynamic IP set by your internet provider and the address will
tend to change about every 24 hours depending on how often you restart your connection. 
Most providers will offer a Static or "Fixed" ip for a small monthly fee. 
[SIZE=1](they really work hard to maintain it, kinda like the fee to keep your name *out* of the phone-book)[/SIZE]

---

