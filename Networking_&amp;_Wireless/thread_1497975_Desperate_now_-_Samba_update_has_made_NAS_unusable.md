---
title: "Desperate now - Samba update has made NAS unusable"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by BigGeoff on 2010-05-31
Hello community, I have had a good look round the forums but cannot come up with anything quite like this and the problem prevents me from using my NAS box and stuff is starting to stack up on my main PC now...........

I have a Dell desktop running Ubuntu 9.04, a Shuttle running Mythbuntu 9.10 and a Netgear ReadyNAS Duo, all of which worked fine until this problem started. I have done nothing to any config files nor have I modified any settings from the outset, as far as I can remember I have just used everything as it came. This problem probably started a month or so back when update manager suggested a Samba update on both PC's which I accepted. I don't fire up my NAS box more than once or twice a month to back all my photos, music, video etc. so it was a while before I did (following the update) I could see the NAS and the Shuttle from the Dell but couldn't browse them I just got the error message 'Unable to mount location. Failed to retrieve share list from server' which I gather is all too common. I have searched around a bit on these forums and have tried a few things in the command line to gather information and I found  something that worried me rather a lot. From Dell:

```
geoff@geoff-dell:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.4     NAS-C7-4E-15   [NAS-C7-4E-15] [Unix] [Samba 3.0.31]
192.168.1.6     GEOFF-DELL     [	WORKGROUP     ]
192.168.1.7     USER-DESKTOP  +[WORKGROUP] [Unix] [Samba 3.4.0]

geoff@geoff-dell:~$ sudo iptables -L
[sudo] password for geoff: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

geoff@geoff-dell:~$ smbclient -L NAS-C7-4E-15
timeout connecting to 81.200.64.50:445
timeout connecting to 81.200.64.50:139
Connection to NAS-C7-4E-15 failed (Error NT_STATUS_ACCESS_DENIED)
geoff@geoff-dell:~$

```


What worried me was the timeout trying to connect to 81:200:64:50 etc. - What on earth is the system trying to connect to? I didn't find anything like this anywhere else even googling it comes up with nothing.

From the Shuttle I get more or less the same without the timeouts

```

user@user-desktop:~$ findsmb
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.4     NAS-C7-4E-15   [	WORKGROUP     ]
192.168.1.6     GEOFF-DELL    +[	WORKGROUP     ]
192.168.1.7     USER-DESKTOP   [WORKGROUP] [Unix] [Samba 3.4.0]

user@user-desktop:~$ sudo iptables -L
[sudo] password for user: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

user@user-desktop:~$ smbclient -L NAS-C7-4E-15
Enter user's password: 
Connection to NAS-C7-4E-15 failed (Error NT_STATUS_UNSUCCESSFUL)
user@user-desktop:~$ 

```

I haven't done any updates on the NAS box firmware so it can't be that and now I don't even see the shares in filemanager. What on earth is going on??? I know there are many other threads similar to this but but I am hoping that the slight difference might make this more obvious to solve.

I forgot to mention that now I don't even see the shares in filedmanager - another thing that happened all by itself!!!

Heeeellllppppp

Geoff

---

### Post by BigGeoff on 2010-05-31
OK now I feel stupid, searched for the wrong thing, anyhow came up with this:-

edit /etc/samba/smb.conf

find the line

; name resolve order = lmhosts host wins bcast

uncomment it and change to

name resolve order = lmhosts wins bcast host


This sorts it out immediately on the command line but needed a reboot before filemanager picked it up and now everything is back as it should be.

Beware of updates bringing unexpected changes............

---

