---
title: "WindowsXP can't access Ubuntu 9.04 shares"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by 1915flyer on 2009-05-28
I have set up a shared folder in my Ubuntu home directory which Windows cannot access. Windows sees the computer when I view the workgroup computers but says the network path was not found and the Ubuntu computer does not show up in My Network Places.

A 2nd Ubuntu computer also cannot access shared folders on this computer.

Ubuntu can access and transfer files to and from the shared folders on the XP computer with no trouble.

I have:

1. Installed Firestarter, allowed incoming connections from 192.168.1.0/24 and enabled Samba (SMB) service ports 137-139, 445 for everyone.

2. Edited smb.conf to change my workgroup to my windows workgroup (HOMEOFFICE)

3. Enabled sharing on a folder in my /home/user directory (/home/user/Public). Allowing other users to changes my files in that folder would not "stick" until I used sharing-admin. This still did not allow access.

What else do I need to do?

---

### Post by dmizer on 2009-05-28
For what reason did you install Firestarter? What version of Ubuntu are you using?

---

### Post by 1915flyer on 2009-05-28
Jaunty Jackalope 9.04.

I installed firestarter because another thread indicated that it was necessary to network.

Well, rather that they had trouble networking until they installed it and opened the ports, etc.

---

### Post by dmizer on 2009-05-28
Please provide a link to that thread, it may give me some insite into what the problem is.

---

### Post by 1915flyer on 2009-05-28
I can't find the specific thread right now.

If I stop the firewall (firestarter), I am able to connect. I didn't see this happen before. The Outbound policy is blank so far, Permissive by default.

How do I set firestarter to allow local connections, or do I have to simply remove it?

Thanks for the help.

---

### Post by dmizer on 2009-05-28
Well, if you're connected to a router, you already have a firewall. Unless you have some special routing needs like internet connection sharing, there's certainly no need for Firestarter.

---

### Post by 1915flyer on 2009-05-28
OK. I do have the router firewall set up.

 What do I have to do to return the firewall to the original condition? Remove the policies, quit, and uninstall Firestarter?

Many, many thanks for the help.

---

### Post by dmizer on 2009-05-28
Open a terminal and type:
```
sudo aptitude purge firestarter
```

To be sure that everything is back to default, run this command:
```
sudo iptables -L
```

It should look like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

---

