---
title: "problem with the network connection gui"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by gixpaulie on 2009-10-14
hi all
 
 
im having a problem with the network connection gui , anything i enter into it saves but doesnt save in the interfaces file and when trying to edit the info in the gui it doesnt work properly either, deleting say the gateway box goes blank but the apply button greys out but when entering 0.0.0.0 it goes back to what it was before when i first saved it. If i edit the interfaces file directly when opening the gui again nothing comes up as i edited in the intefaces file, now it gone to the point where theres no nic connections showing up to the wired box part even though i do ifconfig and they show up :confused::confused::confused::confused::confused::confused::confused:
 
is this a bug ? or any help will be great
 
many thanks

---

### Post by chili555 on 2009-10-14
It's not a bug. It is assumed that either the gui, Network Manager, will control your interfaces...*OR*...you will control them manually in */etc/network/interfaces*, but not both. The amateur shade-tree mind-reader in me surmises you are trying to set up a static IP address. Yes? No?

---

### Post by sir_cheats_a_lot on 2009-10-14
What version of Ubuntu are you using? it may or may not be a known issue.  not that i'd know or anything.. i'm still on Hardy(8.04)..but someone else might.  my best guess would be run: "gksu/sudo(i forget which) network-admin"  in the terminal and see what it does when you re-enter the info.  good luck.

---

### Post by TiredBird on 2009-10-14
> **gixpaulie said:**
> ...im having a problem with the network connection gui...
I assume you are talking about network manager or something like that. I've been having trouble with it for years. Same thing you're describing. I have never been able to get it save my settings. It always acts like its never seen me before. I've looked for documentation and can't find that either. Anyway, I gave up on it. Can't figure out why anybody uses it.

I have begun using 'wicd' and couldn't be more pleased. It seems to work the way I think. Handles hard-wire and wireless, dhcp and static, and all kinds of encryption. Most of all its user friendly. It may not have any documentation either but who needs it. It works like it should. 

To install it you may have to add a software repository unless you are using 9.04, which I think has it in the ubuntu repository. If it isn't already there, a Google search on 'wicd' should give you all the information you need.

BTW: installing wicd with also uninstall network-manager but it never bothered me. I was glad to see it gone.

---

### Post by gixpaulie on 2009-10-15
> **chili555 said:**
> It's not a bug. It is assumed that either the gui, Network Manager, will control your interfaces...*OR*...you will control them manually in */etc/network/interfaces*, but not both. The amateur shade-tree mind-reader in me surmises you are trying to set up a static IP address. Yes? No?
 
 
Hi thanks for all your replies,
 
yeh i was trying to set a static ip but it seem that the network connection gui doesnt work properly as once i set the ip i wanted along with the netmask and gateway then i go back into it and edit it for example, i cant even edit it either, so i ended up just editing the interaces file which was a dam site alot easier then trying to get the nc gui to work , where does the gui save the settings because when i did save the info and open the interfaces and it wasnt saved. Im having problem with the wireles now i set info correctly and it dont work as a static ip ,it work with the gateway 0.0.0.0 and when i entered my gateway it dont work even same as above i try to edit it and it wont edit 
 
 
 
thanks

---

### Post by TiredBird on 2009-10-15
> **TiredBird said:**
> I have begun using 'wicd' and couldn't be more pleased. It seems to work the way I think. Handles hard-wire and wireless, dhcp and static, and all kinds of encryption.
I guess this got lost among all my bad-mouthing of network-manager.

---

