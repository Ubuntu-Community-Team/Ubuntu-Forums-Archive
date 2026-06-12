---
title: "cisco vpnclient profile cant be read"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by jaxxm on 2009-02-28
hi all i get this error after installing the cisco client in ubuntu 8.10.

:~# vpnclient connect tt-ip-guruz
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:35 UTC 2009 i686
Config file directory: /etc/opt/cisco-vpnclient

The profile specified could not be read.


I installed the pcf file in the /etc/opt/cisco-vpnclient/Profiles directory and checked if it had the right permissions. As you can see I haven't got the .pcf after the profile. I have to use the command line version 'cos I'm using Iburst and the network manager does not see the interface(well not the one in 8.10 at least). the client does start up fine.

Could any one help me please.



goddit

i was putting it in the /opt/cisco-vpnclient/Profiles not in the /etc/opt/cisco-vpnclient/Profiles as I said above. Helps to try to explain to someone what to do while doing it.

---

