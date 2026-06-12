---
title: "Interface configuration"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by sorino737 on 2010-11-06
can some one help me what is the difference from GUI network configuration and command line edit of /etc/net../interf...

I'm a beginner and I was expecting to find the "interface" conf file modified after I add the new ip add in the GUI intf. It using different config file?

Thank you very much.

---

### Post by Iowan on 2010-11-06
Network Manager (the GUI) seems to have a couple of different places - depending on version. (You might check under */etc/NetworkManager*) It seems like ALT-F2 then running **gconf-editor** found it on one version...

*/etc/network/interfaces* is the older, "pre-Network Manager method - it still works, buy the way... Interfaces defined in 
*/etc/network/interfaces* are generally ignored by Netowrk Manager (unless you tell it otherwise).

---

### Post by sorino737 on 2010-11-07
thank you very much, now it's clear. With a search for Net. Manager infos I understand the thinks.

thanks again.

---

