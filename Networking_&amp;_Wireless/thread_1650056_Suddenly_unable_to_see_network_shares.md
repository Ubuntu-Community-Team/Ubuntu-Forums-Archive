---
title: "Suddenly unable to see network shares"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Stormwalker302 on 2010-12-21
Hi, I am a relatively new Ubuntu user.  I have three computers on the network, one is using Windows Vista, one is in an office room using Ubuntu 10.10, and one is in the living room using Ubuntu 10.10.  All three computers have folders shared, and were all three reading files just fine with one another for a couple of months.  To share the folders, I just right clicked on them, selected sharing options, and checked the boxes for "share this folder" and "guest access".   Both Ubuntu computers have samba installed and configured so the Vista computer can see their shares.  Tonight, the Ubuntu computer in the living room stopped being able to see the other computers under places -> network.  The other Ubuntu computer and Vista computer can still see each other's shares just fine.  I also created a test share folder with a file in it on the living room Ubuntu computer, and it can be seen by the other Ubuntu computer.  I can ping the computer in the living room, and the computer in the living room can ping the other two computers.  I set a static IP address on the Ubuntu computer in the living room to rule out an IP address conflict.

Due to my inexperience with Ubuntu, I'm not quite sure where to go from here.  Under network, if I go to "go -> location..." I'm not quite sure what to type in there to find other computers.  Under places -> network, the only thing that comes up on the Ubuntu computer in the living room is it's own shares.

I tried using the search feature, but was unable to come up with anything resembling my particular problem within a reasonable amount of time.  I apologise if this has been asked before.  If anyone here can provide any assistance, it would be greatly appreciated.  Thank you.

---

### Post by Stormwalker302 on 2010-12-22
I was able to figure out how to access the shared folders on the ubuntu computer in the office room.  I went to places -> network, then selected "go -> location" on the menu options, then on the browse bar, typed in smb://computername/sharedfolder where "computername" is the name of the ubuntu computer in the office, and "sharedfolder" is the shared folder on that computer that I want to access.  It's still not showing up in "network" under places like it did before, but I have a way to access the shares now.

---

