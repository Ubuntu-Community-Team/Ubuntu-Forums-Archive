---
title: "Cannot view Windows Shared Folders"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by kanagaraj.rk on 2009-08-20
Dear Friends,

I have ubuntu Jaunty Jackalope(9.04) installed in my Two Desktop Systems. Both Have Internet Connections through other 8 windows Machines are connected Through a Router.

My question is My system 1 is showing the windows shared folders and i can access them but i cant access those from my System 2. it shows the error Message "UNABLE TO MOUNT LOCATION -  Failed to retrieve share list from server". But both has all the same things common.

---

### Post by pedro_orange on 2009-08-20
> **kanagaraj.rk said:**
> Dear Friends,

I have ubuntu Jaunty Jackalope(9.04) installed in my Two Desktop Systems. Both Have Internet Connections through other 8 windows Machines are connected Through a Router.

My question is My system 1 is showing the windows shared folders and i can access them but i cant access those from my System 2. it shows the error Message "UNABLE TO MOUNT LOCATION -  Failed to retrieve share list from server". But both has all the same things common.

Sorry but you've not explained your problem very well.

If you're having trouble getting stuff from a Windows Share to an Ubuntu machine, have you installed samba? 

```
sudo apt-get install samba
```

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Are all your machines within the same subnet? Are the addresses all reachable with ping? What happens when you open a file browser and type \\IPADDRESS\ ? Can you get to the machine in question?

---

### Post by dmizer on 2009-08-20
You don't have to configure a samba server just to view shares on Windows computers.

The error "UNABLE TO MOUNT LOCATION - Failed to retrieve share list from server" is almost always related to a firewall problem either on the Ubuntu comptuer or on the Windows machine.

For more information, please see the 6th link in my sig.

---

