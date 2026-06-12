---
title: "Reach Ubuntu Live from Win7"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Formicula on 2010-04-24
Hi,

i tried to reach a PC that runs with 9.04 live-CD from Win 7.

Found some hints in .ch like:

"I had the same Problem with 7 Home Premium. Simply go to registry:

HKLM\SYSTEM\CurrentControlSet\Control\Lsa

and create the key:

LmCompatibilityLevel

Type DWORD , Value  "2" and if this dont work take "1". 
Default seems to be  "3" on Win7
The meaning of the values...
([http://blog.t-error.ch/article/1027/mit_…ares_zugreifen/]("http://www.ubuntu-forum.de/index.php?page=ExternalLink&url=http%3A%2F%2Fblog.t-error.ch%2Farticle%2F1027%2Fmit_windows_7_auf_samba-shares_zugreifen%2F"))   ".

I tried this because theres no ’secpol.msc /s’ on Windows 7 home premium.
But it didnt work for me.

Win7 home premium does not find the Ubuntu PCs.

In the other direction it works fine with:

HKLM\System\CCS\Services\LanmanWorkstation\Parameters

DWORD DomainCompatibilityMode = 1

DWORD DNSNameResolutionRequired = 0



HKLM\System\CCS\Services\Netlogon\Parameters

DWORD RequireSignOrSeal = 0

DWORD RequireStrongKey = 0


Any idea?

---

### Post by P4man on 2010-04-24
windows isnt going to see the ubuntu pc, unless that has samba installed and is sharing something. On a livecd its doing neither.

---

### Post by mick222 on 2010-04-24
windows should see your machine don't use the homegroup share a folder on your ubuntu machine and look under the network tab in the side panel of computer in win7.I spent all night trying to get homedroup working in windows7.

---

### Post by Formicula on 2010-04-25
Sorry, I cant find it from win7 home premium.

Even the installed Ubuntu 8.04 Samba doesnt appear (Not the live-CD).

And, sorry again: I dont know how to configure smb.conf. Heres one script that once
worked with XP connectet to 8.04 (this machine) with a crossover cable and two LAN-Cards. The 8.04 had the address 192.168.0.30.

```

[global]
workgroup = WORKGROUP
netbios name = IRGENDWAS
security = share
interfaces = 192.168.0.30/255.255.255.0
bind interfaces only = Yes

wins support = no
[data]
comment = Data
path = /home/thomas
force group = users
read only = No
guest ok = Yes
force create mode = 0777
force directory mode = 0777

available = yes
browsable = yes
public = yes
writable = yes
[media]
comment = Data
path = /media/cdrom
force group = users
read only = No
guest ok = Yes
force create mode = 0777
force directory mode = 0777
available = no
browsable = no
public = no
writable = no

```But now theres a router in between. smb.conf seems like to complete the annual tax declaration to me ; ) The documentations are so different. Writing normal programs or
scripts is much easyer.

At all I think you can load the complete samba, smbfs,... and smb.conf into RAM mostly during a live session. Mount the ntfs and check the live session hard drive for virusses
from win7 through WLAN f.e. Am I so wrong, doing this ecercise?

---

### Post by P4man on 2010-04-25
Do the ubuntu machines see each other (or other windows machines see each other?) Ive heard about issues with windows 7 network discovery, and one thing that is often suggested is going in to the network properties and disable IPv6 (on windows). Since its easy to try, I thought Id suggest it.

---

### Post by Formicula on 2010-05-02
Sorry, Its my weekend problem. To connect the 3 Ubuntu machines I use FTP (with login)
locally and worldwide. The Windows machines recognize each other, even it may need a little patience.
But I think u cant change the network properties in Win7 + home

---

