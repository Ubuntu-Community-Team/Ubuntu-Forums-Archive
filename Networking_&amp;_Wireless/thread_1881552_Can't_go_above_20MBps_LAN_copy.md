---
title: "Can't go above 20MBps LAN copy"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by catsrules on 2011-11-15
I can't get anything to copy over LAN to break the 20MBps mark, on my home network. Beside windows to windows, I get 70-50MBps all of the time using windows to windows.

I have tried Ubuntu 10.10, 11.4 and 11.10, all have the same problem
It may not just related to ubuntu because I install freenas and it suffered the same problem
I am using mainly SAMBA, (I come from a windows back ground so SAMBA is what I am comfortable with.) 
I have also tried SFTP between ubuntu and a windows box using WinSCP client and  got only 3MBps, (Had to copy 50GB over that, it took forever :))

It seams to be universal and not just related to one box, I have install Ubuntu on several different PCs as well as in virtual environments, and have never broken the 20MBps mark.

I have copied to and from between 
Ubuntu to Ubuntu, 
Ubuntu to windows
windows to Ubuntu
Ubuntu to freenas 
windows to freenas
The files I copied where large single file videos disk images virtual harddrives. I was useing the default Ubuntu GUI to copy.

The link speeds is 1000mbps on all of my boxes.
All of my computers are hardwired in to a netgear gsm7224 l2 managed gigabit switch.
I am using a Untangle router are my router and DHPC, DNS server.


Any ideas what is going on here.

---

### Post by bkratz on 2011-11-15
Are your cables capable of the rates you desire?  You are noting rates in MBps where if you check the following you will see there are limits to speed with cables such as cat5 and cat5e.

[http://ezinearticles.com/?Cat-5,-5E,-6,-and-6A-Cables---Distance-and-Speed-Limitations&id=1237951](http://ezinearticles.com/?Cat-5,-5E,-6,-and-6A-Cables---Distance-and-Speed-Limitations&id=1237951)

Where they are rating cat5 at 100mbps at 100 meters only (that is in mega bits/second not mega bytes/second as your ratings seem to indicate).

---

### Post by catsrules on 2011-11-15
Thanks for the quick response!! 
My cables are Cat5e, and well under 100 meters (around 50-35 feet)
I am measuring my speeds in mega bytes because that is the units Ubuntu's and windows 7's copy GUI measures them.  
All of my connections are gigabit (125 mega byes), and I am only getting 160mega bites (20mega bytes), well under 1000 mega bits (125MB) 

I know 1000mb and 125MB are more theoretical speeds but I should be getting more then 20MBps. And I get 70-50MBps all of the time between windows to windows, that is using the same hardware and network.

---

