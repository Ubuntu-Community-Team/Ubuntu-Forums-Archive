---
title: "Wireless keeps on disconnecting"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by annec on 2009-06-18
Hi!

I am having some connection problems on ubuntu 9.04 and I am a newbie on Linux.

I tried cross referencing my problem with other posts but could not find my answer. 

**Thanks in advance for the help!**

Here it goes:

- **Network works** because it does under Windows
- **Network is recognized by Ubuntu**. I tried iwconfig and saw it, but I don't know how to interpret the iwconfig any more than that...
- I do have access to the internet but every 1 second to ten minutes the **connection fails intempestively** and it keeps requiring me confirmation of my authentification codes 
- It **worked perfectly yesterday**! Natural question you would ask: what did I change since? I connected using ethernet at work but changed back the parameters (proxy) so I don't think that is it. Else I changed some stuff on the Power Management, but I really don't see how it could be linked. Basically that's it. I can't remember doing anything more than that that would lead to this problem. 

I hope you can help and if so, I would be very grateful!

---

### Post by annec on 2009-06-18
Ok I think I found part of the problem, but not the solution! It seems to be related with _Azureus_.

When Azureus works, connection goes on and off, and Azureus I think tries to manage it. There is this weird unending text appearing on the terminal (part of it only is quoted here) each time it disconnects:

*******************************************************************************

DEBUG::Fri Jun 19 02:22:13 CEST 2009::com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager::addNewOutboundRequests::242:
  ConnectDisconnectManager::address exception: full=/88.174.129.130:30632, hostname=88.174.129.130, port=30632, unresolved=false, full_sub=88.174.129.130/88.174.129.130, host_address=88.174.129.130
 channel=java.nio.channels.SocketChannel[closed], socket=Socket[unconnected], local_address=0.0.0.0/0.0.0.0, local_port=-1, remote_address=<null>, remote_port=0
    TCPConnectionManager::mainLoop::212,TCPConnectionManager::access$900::46,TCPConnectionManager$5::runSupport::202,AEThread::run::71
java.net.SocketException: Network is unreachable
    at sun.nio.ch.Net.connect(Native Method)
    at sun.nio.ch.SocketChannelImpl.connect(SocketChannelImpl.java:525)
    at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.addNewRequest(TCPConnectionManager.java:311)
    at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.addNewOutboundRequests(TCPConnectionManager.java:242)
    at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.mainLoop(TCPConnectionManager.java:212)
    at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager.access$900(TCPConnectionManager.java:46)
    at com.aelitis.azureus.core.networkmanager.impl.tcp.TCPConnectionManager$5.runSupport(TCPConnectionManager.java:202)
    at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:71)

*******************************************************************************

I don't get a word of it, but do you think there might be an interference here? Maybe a port problem of some sort? When Azureus is off, it seems to go back to normal...

Thanks!

---

### Post by annec on 2009-06-18
Changing the settings of _Azureus_ to unlimited download and unlimited upload solved the problem. Don't ask me why! :)
NB: _Deluge_ got me the exact same disconnection problem when I tried it a few minutes ago. I really do not understand what is going on! If you still have some answers, I would be grateful.

---

