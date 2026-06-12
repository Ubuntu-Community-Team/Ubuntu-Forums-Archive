---
title: "Network Manager recoonect script 8.10 hardy"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by xoroz on 2009-03-26
Problem:
My script to reload NetworkManager (if internet conection is lost) fails because it cannot get the "GetSecrets" even if I run crontab as root

CRONTAB:
#*/5 * * * * /home/felix/Scripts/testnet.sh

testnet.sh: 
#!/bin/bash
#Script to test internet connection and restart Network Manager if it fails.
ping -c 2 -w 3 google.com || /etc/init.d/NetworkManager restart


Error Msg:
Mar 24 20:55:10 SYSMENGO NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.NetworkManagerSettings.Connection.Secrets" member "GetSecrets" error name "(unset)" destination "org.freedesktop.NetworkManagerUserSettings"). 

Related Bug:
[https://bugzilla.redhat.com/show_bug.cgi?id=487722](https://bugzilla.redhat.com/show_bug.cgi?id=487722)

Files:
NetworkManagerInfo.conf
nm-user-settings.conf


Automatic Keyring, is that the solution?

---

