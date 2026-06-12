---
title: "FreeNX client can't connect to server"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by kranu on 2012-06-25
At the client NX NoMachine (version 3.5.0-9 on Windows 7 64-bit), the !M logo window appears, but after a few seconds that window just closes, even without showing any error message.

I have Kubuntu 12.04 64-bit with freenx-server 0.7.3.
Client is ok because works with other servers.
Solution from [https://help.ubuntu.com/community/FreeNX#Troubleshooting](https://help.ubuntu.com/community/FreeNX#Troubleshooting) didn't work.

Log:
```
Info: Display running with pid '4012' and handler '0x5036e'.

NXPROXY - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '2256'.
Session: Starting session at 'Sun Jun 24 11:52:05 2012'.
Info: Connection with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'kde'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '12000'.
Session: Session started at 'Sun Jun 24 11:52:06 2012'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Sun Jun 24 11:52:17 2012'.
Session: Session terminated at 'Sun Jun 24 11:52:17 2012'.
```

---

### Post by jwbrown on 2012-06-30
> **kranu said:**
> At the client NX NoMachine (version 3.5.0-9 on Windows 7 64-bit), the !M logo window appears, but after a few seconds that window just closes, even without showing any error message.

I have Kubuntu 12.04 64-bit with freenx-server 0.7.3.
Client is ok because works with other servers.
Solution from [https://help.ubuntu.com/community/FreeNX#Troubleshooting](https://help.ubuntu.com/community/FreeNX#Troubleshooting) didn't work.

Log:
```
Info: Display running with pid '4012' and handler '0x5036e'.

NXPROXY - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '2256'.
Session: Starting session at 'Sun Jun 24 11:52:05 2012'.
Info: Connection with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'kde'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '12000'.
Session: Session started at 'Sun Jun 24 11:52:06 2012'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Sun Jun 24 11:52:17 2012'.
Session: Session terminated at 'Sun Jun 24 11:52:17 2012'.
```


Same problem here:
Freshly inxtalled nxclient_3.5.0-7_amd64 on Ununtu 10.10 cannot connect to Kubuntu 12.04 freenx server.  I can connect to other freenx servers on my network and can connect from Kubuntu 12.04 to other freenx servers on my network.

---

