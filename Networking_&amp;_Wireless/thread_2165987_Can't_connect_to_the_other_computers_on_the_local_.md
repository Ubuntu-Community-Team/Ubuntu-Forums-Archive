---
title: "Can't connect to the other computers on the local network"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by rashidmostafa on 2013-08-07
I am running Ubuntu 12.04.  I am connected to my network by a netgear router with an ethernet cable. There is one other Ubuntu 12.04 computer connected to the router with ethernet, and up to four laptops using wireless connections.  The Internet is connected to the router by an ethernet cable from an ADSL modem.  All the machines can see each other, but the Ubuntu ones cannot connect to each other's shares. The Ubuntu machines can access the mac laptop's shared folders. The windows7 laptop can see the Ubuntu machine's shared folders and access the files.  I also have a wireless HP printer that works without problems.

Ateempts to connect to the other Ubuntu machine gives me the error "Failed to retrieve share list from server".

smbtree gives me:[INDENT][COLOR=#000080]WORKGROUP
    \\USER-PC                
    \\PHOEBE-PRECISIO        phoebe-Precision-WorkStation-490 server (Samba, 
    \\BUZZY2                 Buzzy2 server (Samba, Ubuntu)
        \\BUZZY2\Videos4            
        \\BUZZY2\Documents          
        \\BUZZY2\MFC-8820D          Brother MFC-8820D
        \\BUZZY2\WirelessHP         n
        \\BUZZY2\Videos             
        \\BUZZY2\PicturesR          
        \\BUZZY2\Brother-MFC-8220    Brother MFC-8220
        \\BUZZY2\IPC$               IPC Service (Buzzy2 server (Samba, Ubuntu))
        \\BUZZY2\Writing            
        \\BUZZY2\print$             Printer Drivers[/COLOR]
[/INDENT]
 The first computer is a laptop.  The next is the other Ubuntu computer and Buzzy2 is my machine.  The 5 folders that are shared were shared using the GUI.

What are the first steps in diagnosing my problem?

Best wishes

Rashid.):P
My first post.

---

### Post by Morbius1 on 2013-08-07
I'm just on my way out but if the only problem is the two Ubuntu machines  [COLOR=#000080]( PHOEBE-PRECISIO        and BUZZY2[/COLOR] ) seeing each other remember that one Linux box can access another Linux box in a way a Windows box cannot ( unless you do something to the windows box ):

In a terminal from buzzy2 run:
```
nautilus smb://phoebe-precisio.local
```
In a terminal from phoebe-precisio run:
```
nautilus smb://buzzy2.local
```
If that works then once nautilus opens up to that location you can bookmark it so it sort  of looks like a "mapped drive" does in Windows.

***Note***: You have to have avahi running on both systems:
```
sudo service avahi-daemon start
```
And you have to have port 5353/udp open if you have done anything with a firewall on your install.

---

### Post by rashidmostafa on 2013-08-07
Many, many thanks.  That sorted it out a treat.  Really appreciate your taking the time to help.:D

Best wishes

Rashid

---

