---
title: "Unable to connect to anything using FreeNX"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by klemencic on 2008-12-31
I have just downloaded and installed FreeNX (client, node and server) but I am unable to obtain a connection to any other machine
I tried connecting to testdrive.nomachine.com and this times out with the  following error
NX> 203 NXSSH running with pid: 9247
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options

I then tried 127.0.0.1 and the connection terminates with
NXPROXY - Version 3.3.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '9257'.
Session: Starting session at 'Wed Dec 31 16:14:28 2008'.
Info: Connection with remote proxy completed.
Info: Using MODEM link parameters 256/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-3' with session 'gnome'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 9/9.
Info: Using bandwidth limit of 256k bits per second.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '11002'.
Session: Session started at 'Wed Dec 31 16:14:28 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 1/4096K.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Terminating session at 'Wed Dec 31 16:14:38 2008'.
Session: Session terminated at 'Wed Dec 31 16:14:38 2008'.

When I try to connect to the Ubuntu  box with the NX server installed from a windows machine I receive
NX> 203 NXSSH running with pid: 1872

NX> 285 Enabling check on switch command

NX> 285 Enabling skip of SSH config files

NX> 285 Setting the preferred NX options

NX> 200 Connected to address: 202.168.119.157 on port: 22

ssh_exchange_identification: Connection closed by remote host

One strange thing I have noticed is that at a command prompt, if I type nxserver --version I receive a command not found error, same with node and client

Can someone please help to resolve this problem

---

