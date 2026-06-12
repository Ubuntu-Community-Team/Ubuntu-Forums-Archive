---
title: "Please help me to set up VPN connection"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by m4lte on 2010-03-19
**SOLVED. Actually, all I had to do was to specify my user name in the VPN settings :)**

Hi there!
I want to set up a VPN connection to my university's network. Unfortunately, they only provide support for Windows and Mac, so I have to figure it out myself.

I installed the packages for PPTP, VPNC, OpenConnect as described here and rebooted.
[http://ubuntuforums.org/showthread.php?p=8261958#post8261958](http://ubuntuforums.org/showthread.php?p=8261958#post8261958)

Then I opened the network manager and tried importing a .pcf file that my university provides together with a cisco vpn client for windows. I posted the content of that file below.

However, when I try to import the .pcf file I get the following message:
[I]TCP tunneling not supported
The VPN settings file 'RU VPN-service.pcf' specifies that VPN traffic should be tunneled through TCP which is currently not supported in the vpnc software.
The connection can still be created, with TCP tunneling disabled, however it may not work as expected[/I]

When I try enabling the VPN connection I'm asked for an authentication password. I'm actually not sure what that means, because for my log in to the university network I should require both a user name and a password. Anyway, putting in my password I just get a message that the connection failed.

Does this mean that I won't be able to set up a VPN connection from linux or do I just use the wrong settings? I have absolutely no experience with VPN. So any help or hints would be great.
Thanks for your help!


This is the content of the .pcf file coming with the cisco client for windows:
```
[main]
Description=
Host=vpn.ru.nl
AuthType=1
GroupName=radius
GroupPwd=
enc_GroupPwd=B3C017...(very long passphrase)
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPPhonebook=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=1
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0

```

---

### Post by javajesse on 2010-05-12
Did you ever get this working.  I am having the exact same issue with Lucid even though I set the user name

---

