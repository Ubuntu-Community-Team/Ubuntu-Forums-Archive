---
title: "Networking Mystery - Can't solve."
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by ghostofzuul on 2011-07-14
I have 3 computers on my home network.

2 macs
1 linux box running ubuntu 

from my macs i can access the linux box and read/write files no problems.

from my linux machine i can't even see the macs. the only thing that ever shows up is an icon for "windows network." 

when i click on the "windows network" icon sometimes it takes me to an icon called "workgroup" but when i click on that it just says failed to connect to server.

this problem is ongoing and quite vexing. Any clues would be helpful. 

thx.

---

### Post by WilcoRogers on 2011-07-14
What are you trying to ultimately achieve?

---

### Post by varelov on 2011-07-14
Create shared folder on your mac. Then from your ubuntu box (and I assume you have ubuntu linux) click Places - Connect to server and type in the ip of your mac. Before you click "Connect", from the drop down box choose "Windows Share" as connection type.
You may be prompted to install folder sharing software, go ahead and install it.
If all you wanted is some simple file sharing, this should do it.

---

### Post by ghostofzuul on 2011-07-14
the file sharing is working but only one way. 

in other words, i can access my ubuntu machine from my mac. i can transfer files from my mac to my ubuntu machine no problem. i can take files from the ubuntu machine and move them to the mac. i have file sharing and windows sharing on on the mac. so i know it's working and set up properly. when i click on the network icon on the mac i see the other 2 machines on the network, including the ubuntu machine.

the problem i'm having is from the ubuntu machine to the mac. i thought that when i open my network on the ubuntu machine i would see the other 2 machines on my network. i do not. the only thing i see is an icon for windows network. 

back when i was using jaunty, and i clicked on the network i could see the other machines and the windows network icon but i couldn't connect to them. since upgrading to 10.4 i can't even see the 2 machines. 

i have tried to ftp into my mac from the ubuntu machine and that doesn't seem to work either.

also. these are hardwired network connections not wi-fi.

---

### Post by varelov on 2011-07-14
In other words, file sharing works both ways? Like Ubuntu < - > Macs? But you want to browse their directory structure via network the way you browse your local computer's structure?
For that to happen, you'll have to mark some higher level directory on Ubuntu and Macs for sharing and to somehow enable that sharing to apply recursively (to other subfolders within the tree).

---

### Post by capscrew on 2011-07-14
> **varelov said:**
> In other words, file sharing works both ways? Like Ubuntu < - > Macs? But you want to browse their directory structure via network the way you browse your local computer's structure?
For that to happen, you'll have to mark some higher level directory on Ubuntu and Macs for sharing and to somehow enable that sharing to apply recursively (to other subfolders within the tree).

Usually when you are able to connect to a share via IP address but can't "browse" you have a name services problem.  Browsing SMB shares always requires either:[LIST]
[*]A working hostname that is converted to a NetBIOS name and broadcast on the LAN
[*]A NetBIOS name that is able to at the least broadcast on the LAN
[/LIST]

---

