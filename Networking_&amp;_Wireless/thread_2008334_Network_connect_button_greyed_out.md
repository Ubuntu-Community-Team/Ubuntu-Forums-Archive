---
title: "Network connect button greyed out"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by 54woody3 on 2012-06-22
I have been using 12.04 for about a month. I have two primary locations for wireless connection, work and home. Both have worked perfectly until Wednesday
of this week. My work connection is the issue. It works in Windows 7(dual boot), but no more in ubuntu. When it ques me for the password to access the wireless, I type in the password, but it takes three more "characters"(keystrokes) for the connect button to go from greyed out to black, but by then the password is wrong. I have deleted the connection, tried to reestablish the connection, re-booted all to no avail. I'm scratch'n my head on this one. Any help would be appreciated.

The connect button also goes from greyed out to black with 5 digits in case this is important.

---

### Post by praseodym on 2012-06-22
Using e.g. WPA2-AES encryption you need at least 8 characters

---

### Post by 54woody3 on 2012-06-22
The password is 10 characters, as in the Windows 7 install which works...

---

### Post by praseodym on 2012-06-22
Try it via

> gksu nm-connection-editor

---

### Post by andyp6 on 2012-06-22
Any success on this, I have the same problem even after downloading a new 12.04 xubuntu live cd. Exactly the same issue

---

### Post by 54woody3 on 2012-06-22
I don't seem to have connection editor installed, I will try it over the weekend, where I have a good connection, and test on Monday back here at work.

---

### Post by 54woody3 on 2012-06-23
My mistake, the connection editor is installed if it is the gui that  comes up when "gksu nm-connection-editor" is run in terminal. The best I  can tell, as I can't open the file with any program that I have,  connection editor changes the file, but the problem persists as I tried  this also on Friday. Is there a program that I can edit the file created  by the name of the network (ATTXXXXX) in etc/NetworkManager/system-connections? or is there an other problem?

---

### Post by 54woody3 on 2012-06-23
> **andyp6 said:**
> Any success on this, I have the same problem even after downloading a new 12.04 xubuntu live cd. Exactly the same issue

I have a Toshiba Laptop P205d-s7438. Just in case it may be a hardware related issue, what machine are you running?

---

### Post by steeldriver on 2012-06-23
> **54woody3 said:**
> Is there a program that I can edit the file created  by the name of the network (ATTXXXXX) in etc/NetworkManager/system-connections? or is there an other problem?

afaik it's just a plain text file (at least it was in 11.10) - but you need root permissions to read it so as not to expose your wireless credentials

```
sudo cat /etc/NetworkManager/system-connections/ATTXXXXX
```in fact if you think there's something corrupted in it you can just delete it altogether (sudo rm) or move/rename it (sudo mv - safer, in case you do need to get it back) and let network-manager try to establish a default connection using DHCP

---

### Post by 54woody3 on 2012-06-23
> **steeldriver said:**
> afaik it's just a plain text file (at least it was in 11.10) - but you need root permissions to read it so as not to expose your wireless credentials

```
sudo cat /etc/NetworkManager/system-connections/ATTXXXXX
```in fact if you think there's something corrupted in it you can just delete it altogether (sudo rm) or move/rename it (sudo mv - safer, in case you do need to get it back) and let network-manager try to establish a default connection using DHCP

idk, it seems to me that the program would check the password with the one that I put in it. The issue seems that somewhere it adds three keystrokes and then I can't use the connection. I have deleted and re-established the connection numerous times to end up in the same place. I guess I could check that theroy by deleting the home connection, and trying to re-esablish it. I will try that later, but right now I need the connection. Thanks!!

---

### Post by 54woody3 on 2012-06-24
The home connection is removed and reconnected without issue....???

---

### Post by 54woody3 on 2012-06-25
With the Airport mode on, I deleted the network, but when I re-connect things have not changed...  :(

---

