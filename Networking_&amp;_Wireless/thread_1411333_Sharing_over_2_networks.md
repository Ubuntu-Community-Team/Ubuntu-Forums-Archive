---
title: "Sharing over 2 networks"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by gtcardwhere on 2010-02-19
Hi guys, I am new to linux and I just installed linux on an older unused computer. I want to use this computer as a fileserver. I have a Dell PERC/5 in this, running a raid 5 array that is currently storing everything. I want to make the contents of this array available to my network, however I am not sure if what I want to do is possible.

My current wifi network has 3 main computers, the linux mint desktop, a windows 7 box, a windows xp laptop, plus miscellaneous devices like smartphones and PDAs. My windows 7 box is my primary computer.

This is what I am trying to do: 

1. I want to connect my windows 7 desktop to my linux desktop via gigabit ethernet crossover cable. I want these 2 computers to have a wide bandwidth link because I want high-speed access to the raid array inside the linux box. I need to have write permission for my windows 7 box--I want to be able to use the array as if it were a "local" disk.

2. Both my windows 7 and my linux computer also have wireless NICs, and are connected to my home's wireless network. I want the raid array to be available to my wireless network as well. However, I do not want any devices connecting to the array via wifi to have write access, only read.

Basically, I want my main Windows 7 computer to be able to use the raid array inside my linux box as if it were a locally stored hard drive, through the direct computer to computer gigabit ethernet connection. I also want the array to be accessible wirelessly to all my other devices, but I do not want any wireless device to change the contents of the array. Therefore, both my windows computer and my linux computer will be on 2 networks, the wifi network, as well as a private LAN with just the 2 computers. Is this scenario possible to setup with Ubuntu?

---

### Post by gtcardwhere on 2010-02-20
I have successfully done this, and I will reply to this post for documentation purposes, in case someone comes across the same problem. I used Linux Mint 8.

I used my gigabit patch cable to setup a direct connect LAN between my windows 7 and linux desktops. Both had IP's assigned manually (192.168.2.1, 192.168.2.2 - Subnets at 255.255.255.0 - no gateways, no DNS). The biggest problem I had for this was determining which port is eth0 and which one is eth1 on my linux box, because I am using an eVGA 780i SLI motherboard, with dual gigabit ports. Apparently, eth0 is the port that is "on top", the upper port, when the motherboard is installed to my case.

On the linux machine, I used samba to setup the shares. Right clicked the folders I wanted to share, and went to Properties>Permission (not Sharing Options). Permission gives more refined controls. By default, the folder has 3 sets of sharing permissions, Owner, Group, Others. I created a dummy account for my Windows 7 PC, and put it in the same group as my linux box's account and gave that group read and write access. The Others group had Access Only permission.

On my PC, I added a network drive (right click when inside My Computer window), and used \\192.168.2.2\(shared folder name) as the address. Clicking this link will ask me to login, and I login with the dummy account I created earlier. Doing this gave me full access to the folder; I am able to read, write, delete, and create files in this folder, through the gigabit connection. I transferred 7GB of files in about 2 minutes, limited by my raid1 array's write speeds. 

Both of these desktops also have wireless NICs, configured as normal (DHCP) to connect to my wifi router, which connects to the internet. Both of these computers can get online, but have a 1 gigabit connection with each other. My laptap, also using wifi, can connect to my linux box through the wifi router, using a guest account (smbguest) to access to share. My laptop can read from the share, but cannot modify it in any way (can't delete, can't change, can't create), which is exactly what I wanted. 

So, to recap: manual gigabit IP assignments, DHCP wifi. Share access is defined through permissions on the linux box. Just make sure that the path used to connect to this share on the windows pc is the IP for the gigabit connection and not the wifi IP. Doing this will ensure that access to the share from the PC will go through the gigabit connection and not the significantly slower wifi connection. Because I created the network share in my PC, I am able to use the shares as if they were locally stored disks. 

This is my scenario. My windows 7 PC is using an Intel SSD, and as all SSD's go, they do have a limited number of write cycles they can sustain before they become unwriteable. With 8GB of ram in this computer, I disabled the pagefile as well as set my default download directory to the network share on the linux box. This should help cut down the writes. Another reason I am doing this is because my linux box is setup next to my TV, hooked up directly to it to use it as a display. It is also running XBMC and Transmission. My linux box is left on 24/7, since it has a corsair low wattage PSU (400w), uses a Celeron 430 (conroe 1.8ghz), and a low profile 0dBA (passively cooled) Radeon HD 4350; the computer uses up very little power, is whisper quiet, and fairly easy to keep cool due to the slower components. In other words, perfect as a HTPC, but expanded to play the role of a server as well with the redundancy raid 5 offers. Access to this machine is done through VNC on all my other computers, as well as the XBMC application for Android on my phone, which allows me to browse the entire raid 5 array's media on my phone, and have it playback on my TV directly from the phone. 

All in all, I am really pleased with what Linux has to offer, because I am able to do so much without paying for a license fee to use the OS.

---

