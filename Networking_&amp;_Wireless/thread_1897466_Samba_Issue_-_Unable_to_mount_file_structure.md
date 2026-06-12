---
title: "Samba Issue - Unable to mount file structure"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by aaronfletcher on 2011-12-19
Im new here, and new to linux so please don't judge me too harshly!

I've spent quite a few hours trying to get this to work but it seems like I'm bashing my head against the wall.

I have a Desktop "ServerStation" and a new shiney netbook "RemoteStation" both running Ubuntu 11.10

I have successfully set up a share between the Serverstation and the RemoteStation so that the RemoteStation can read / write to the directories located on Serverstation. However I cannot seem to get ServerStation to read anything located on RemoteStation. Both have static IPs of 192.168.0.254 for ServerStation and 192.168.0.253 for RemoteStation

This is the ServerStation smb.conf which everything seems to be working fine - [http://pastebin.com/fxeLXwCK]("http://pastebin.com/fxeLXwCK")

The problem lies when I browse to RemoteStation from ServerStation. I have set up smb.conf to share one Folder for testing and it first says "Opening "RemoteStation" then proceeds to error with **Unable to mount Location - Failed to retrieve share list from server.**

This is the RemoteStation smb.conf which seems to be at error -[http://pastebin.com/1d2eQQW9]("http://pastebin.com/1d2eQQW9") 

_**Thing I've Done**_

** Workgroups the same ** - Check

**Checking Firewall status** - Same for both Computers

**aaron@ServerStation:~$ sudo iptables -L -n**
[sudo] password for aaron: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

**smbtree without password**

On ServerStation -[http://pastebin.com/twWeFaNZ]("http://pastebin.com/twWeFaNZ") (Note: Error NT_STATUS_UNSUCCESSFUL)

On RemoteStation - [http://pastebin.com/8us1uGmv]("http://pastebin.com/8us1uGmv") (Note: Lack of Error NT_STATUS_UNSUCCESSFUl)

**Nauutilis** via - Go / Location

From ServerStation - smb://192.168.0.253 yeilds access to the Remotestation (Intersting!)

**Netbios Name** is under 15 chars so I don't think its an issue.

If I can clarify it any more please do ask and I will try! Sorry if the language is bad as English isn't a first language I'm afraid. 

TLDR: I can connect to the Big Desktop PC through Samba on Ubuntu from my laptop, cannot connect to Laptop through Big Desktop PC through Samba on Ubuntu.


Thanks for any help you can give me

---

### Post by Morbius1 on 2011-12-19
As a general practice, unless you have some other mechanism in place, I would recommend you either add or modify the "name resolve order" to place the only by default working mechanism first in smb.conf on all your machines:
```
name resolve order = bcast host lmhosts wins
```Restart samba on both machines:
```
sudo service smbd restart
sudo service nmbd restart
```Wait about 5 minutes and then run smbtree again to see if the error went away.

---

### Post by aaronfletcher on 2011-12-19
Fully functioning now. Thank  you so much for your time.

:D

---

