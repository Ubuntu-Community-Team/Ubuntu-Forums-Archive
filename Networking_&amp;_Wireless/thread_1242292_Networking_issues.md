---
title: "Networking issues"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by Suncoaster on 2009-08-17
Afternoon all,

I am still trying to find my way around Ubuntu. My home network consists of a AMD64 machine running 64 bit 9.04, a Eeepc 1000HE netbook running 9.04 remix and an Intel machine running XP.

The XP machine connects via wireless and everything works fine, it connects to the net via the modem/router and can access the printer connected to the AMD64 machine and file sharing via Samba works between XP and the AMD64, but the Netbook is not visible on the wireless network but it is visible via ETH0. All three machines have had the smb.conf edited to change the workgroup to MSHOME.

The netbook connects to the Internet via the modem/router but not to any other machine on the network, it will however connect to the printer via Samba.

So my question is what do I need to do to have the netbook connect to the other machines via the wireless connection the same as the XP machine does.

Sorry if this sounds confusing, but I have tried everything within my limited Ubuntu knowledge.:confused:

---

### Post by Brandon Williams on 2009-08-17
Please be more specific about what you mean when you say that the netbook will not connect to any other machine on the network. It sounds like it will connect just fine to the amd64 machine, since it can access the printer connected to that machine via samba. What other services are you trying to use in order to verify connectivity?

---

### Post by Suncoaster on 2009-08-17
The major issue for access is file sharing.  Any attempt to access a file on any other machine on the network results in a "**Unable to mount location[B]**[/B]  Failed to retrieve share list from server" message.  All three machines appear in a browse list when I click on "Network" in Nautilus, but I cannot access any of the shares that are setup.

---

### Post by cgb on 2009-08-17
Apparently others have had some issues with file sharing in jaunty as well per the below thread.  Have you tried opening nautilus and entering the IP address to browse such as with the below code and does it give you an error doing it this way?

```
smb://"IP_of_file_server"
```

[http://ubuntuforums.org/showthread.php?t=1082148&page=3](http://ubuntuforums.org/showthread.php?t=1082148&page=3)

---

### Post by superprash2003 on 2009-08-17
yea , the smb://x.x.x.x worked for me ..

---

### Post by cgb on 2009-08-17
Then it sounds like you are having a DNS issue with the Wireless connection.  Not entirely sure on what exactly the problem is since the wired connection does not have this issue but a workaround would be to add the DNS information manually to your hosts file.  You will need to edit /etc/hosts and add the ip/hostname to the list.  example code below.

```
192.168.1.20 myserver
```

---

### Post by Suncoaster on 2009-08-18
> **cgb said:**
> Then it sounds like you are having a DNS issue with the Wireless connection.  Not entirely sure on what exactly the problem is since the wired connection does not have this issue but a workaround would be to add the DNS information manually to your hosts file.  You will need to edit /etc/hosts and add the ip/hostname to the list.  example code below.

```
192.168.1.20 myserver
```

I assumed you meant that I add all three of my machines to the hosts file on each machine.  That helped with the Eeepc via the wireless connection.   but it has made my desktop worse as it cannot even browse itself via the network.  The smb.conf file is identical on the two Unbuntu machines, so I guess I will keep searching the forums for a solution.  Thanks for your help

---

### Post by arch0njw on 2009-08-18
Have you tried using smb://*machinename*.local ...?  I had to start using the .local suffix to get name resolution to happen.  That works for me under KDE.

---

### Post by Suncoaster on 2009-08-20
> **arch0njw said:**
> Have you tried using smb://*machinename*.local ...?  I had to start using the .local suffix to get name resolution to happen.  That works for me under KDE.

Sorry for the late response, but I have been away for a couple of days.  I tried that but it did not work for me.

---

