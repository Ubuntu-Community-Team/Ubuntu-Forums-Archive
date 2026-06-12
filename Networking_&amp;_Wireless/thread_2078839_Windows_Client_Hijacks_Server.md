---
title: "Windows Client Hijacks Server"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by Qwirty on 2012-10-31
This is an old problem but despite much time on Google reading about people who have had the problem I have not found a confirmed solution yet. I am hoping the members have some suggestions.

One of my client computers used to be on a Windows workgroup network. Initially my new network with an Ubuntu desktop server worked fine but recently I cannot view the shared directory on the server from the client computer. Viewing Windows reports I find the following message:
"The master browser has received a server announcement from the computer Ubuntu Server that believes that it is the master browser for the domain on transport NetBT_Tcpip_{598AB28E-FA8C-44EA-BEE8-35FA791B82E8}.The master browser is stopping or an election is being forced."

Apparently the client computer is taking over as Master Browser from the Server computer. In the past this has been a well-known problem but I cannot find a solution from the Web or the Microsoft support pages.

Client computer runs W7 Ultimate and Server runs Ubuntu 12.10 with Samba. Registry entries on the client say "IsDomainMaster=false". All the client computers on the system can connect to the Internet through the server but the clients cannot view the server shared directory.

Does anybody know how to put the client computer in its rightful place (under the Ubuntu machine ;);)).

---

