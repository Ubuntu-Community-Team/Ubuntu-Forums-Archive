---
title: "SAMBA Priunter inconsistancies"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by LordOrange on 2011-04-26
I've been having trouble getting my printer to be recognized over the network. I'm running ubuntu 11.04 beta 2 using a Samsung printer connected via USB. I'm not able to find it on any other computer on the network (ubuntu 10.10, windows 7 or Mac). In the SAMBA configuration file i've set browseable under the printing section to yes and saved and restarted a number of times, yet i still can't find the printer and when i run the testparam comand for the config file, it keeps returnign that browseable is set to no. My dad's been tearing his hair out at this and as always the bad mood spreads to everyone else. Please can some one help?

---

### Post by uncaspi on 2011-04-26
Use cups. Open a browser window and type localhost:631 in the address bar to get into the cups GUI. Add the printer and see examples in the GUI what you should use to add a samba printer. I think its  smb://servername/sharename allows everybody to print. If you google smb: printer you could search for it.

---

