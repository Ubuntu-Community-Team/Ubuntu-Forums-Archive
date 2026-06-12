---
title: "Network overview needed"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by ianp5a on 2010-01-02
On 9.10 I'm looking for a way to get an overview of the network that I am connected to. This is because I want to get access to my NAS and Windows PCs attached.
After searching I thought that Network Manager is the tool for this, but it just seems to show my wireless and Ethernet connections and not the network itself. Maybe I'm doing it wrong? Is there another tool for this? I'm hoping to find a diagram or tree showing the router and other devices on the network. Do I need to install a new tool?

Thanks

Ubuntu 9.10 Gnome
NAS: Western Digital My Book 1Tb
Router: Fritz Box 7050
PC connection: Wireless (status OK)

---

### Post by peepingtom on 2010-01-02
Hi,

in terminal, run ```
sudo smbtree
```
This will show all SMB/CIFS shares on your network.
For other types of network scanning, try using "nmap".

---

### Post by ianp5a on 2010-01-03
Thanks. Success!
Since running those commands the NAS and the other PCs show up in the file manager under "network" which is what I really wanted, as I can now browse their contents by navigating in the tree. 

Do I have to run those commands again if there are more devices appearing on the network or is there a way to automatically show new devices as soon as they are connected, as in Windows 7? It would be sufficient to have a "refresh" command on the "Network" place under "Places".

---

### Post by ianp5a on 2010-01-17
Why do the Network Devices not show up in the File Manager without using those commands?
And is there a way to make them show up directly in the File Manager? (Without using a terminal)

---

### Post by ianp5a on 2011-01-07
After a Hard disk crash I install ubuntu (10.10) completely new and I encountered this same problem again. Other computers and my NAS on the netwerk were not accessible in Nautilus under the "Network" An error message unable to connect appears.

This thread seems to know the problem, along with possible solutions.
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

However my problem was solved for me like this:
1) I repeatedly attempt to connect to the NAS and fail. 
2) My daughter came home and switched her PC on.
3) I make a another attempt. Success! Both the NAS and her PC are now visible!
She might have also woken the NAS from it's sleep mode which ubuntu might not have done.

Is there a better way?

---

