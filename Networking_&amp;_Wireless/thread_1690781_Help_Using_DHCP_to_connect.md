---
title: "Help Using DHCP to connect"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by utleymu on 2011-02-18
Hello everyone, so I just installed ubuntu for the first time, and I am not very familiar with everything yet but i am trying to connect to my university's wireless network and can't seem to figure it out.  These are the directions they provide for linux users:
Use **linuxconf**             
[LIST]
[*]Start **linuxconf**, go to **Basic Host Information**                     under **Networking** and **Client Tasks**.
[*]Click **Adapter 1**, and select **DHCP**.
[*]Click **OK** and **Apply Changes**.
[*]Finally, reboot
[/LIST]
I tried running linuxconf from the terminal but no such command exists, is there a similar one for ubuntu?  Thanks for any help

---

### Post by Sean Moran on 2011-02-19
> **utleymu said:**
> Hello everyone, so I just installed ubuntu for the first time, and I am not very familiar with everything yet but i am trying to connect to my university's wireless network and can't seem to figure it out.  These are the directions they provide for linux users:
Use **linuxconf**             
[LIST]
[*]Start **linuxconf**, go to **Basic Host Information**                     under **Networking** and **Client Tasks**.
[*]Click **Adapter 1**, and select **DHCP**.
[*]Click **OK** and **Apply Changes**.
[*]Finally, reboot
[/LIST]
I tried running linuxconf from the terminal but no such command exists, is there a similar one for ubuntu?  Thanks for any help
I reckon you can use the GUI menu and goto SYSTEM -> Preferences -> Network Connections, which will open a dialog box with five tabs, the second one being Wireless.  

Select the Wireless tab.
Click on _A_dd 

First, fill in the details for Wireless, then goto the third tab: IPv4 Settings.  That should already show your Method: as Automatic (DHCP).

Hopefully, because I'm not sure on the GUI version of linuxconf, that will set things the same way.  Sorry that nobody with more expertise than I have can sort this one out.

---

