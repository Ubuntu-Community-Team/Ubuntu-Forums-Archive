---
title: "Two simultaneous wired conncetions at the same time"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by Irsmuncast on 2009-01-10
Hello, I have the following issue:

I would like to use two separate network connections to two different ISPs. I have two NICs, each with the network configuration of the respective ISP - one NIC supports 1Gbps the other 100Mbps. Both networks are wired.
The purpose of making this is that one ISP provides access to resources that are visible only to its users, while the other provides faster Internet speed.
Also, I would like to set a browser and a download manager to use only the connection to that private resource, while all other software (including other browsers and download managers) to use the faster network through the other NIC. And also, I would like to use the full speed capacities of each network without any connection between them, merging the network traffic, etc. Also - no possibility for the two networks to see each other.

I have read a lot of similar topics for doing that under Win XP, but I still have not found an appropriate solution to match all the requirements described above.

The only solution that seems possible to work (both in XP and Ubuntu but I still have not tried it) is to add static routes to the routing tables but the problem is that the private resources I need to access are on different internal IPs of type 10.x.x.xxx and found through a search engine that is also private for the ISP. Also, there are different permission rules for different subfolders on these IPs.
For example, you search for a file named "openoffice3.0.exe" and the search engine returns results on several internal addresses  some of which are of type 10.x.x.xxx/Shared/SubfolderName/openoffice3.0.exe,
and permission is given only to that subfolder, not the parent folder.

In my opinion, all this means that if I use the static route solution, I should manually add a static route for each result of each separate search as I do not know the location of the file in advance which could be a very time consuming task. Also I wonder what would happen if the other ISP also uses addresses of type 10.x.x.xxx on its internal network.

Yet, I have completely no idea how to make certain software use one NIC and other use the other NIC.

Does anyone know all that could be achieved under Ubuntu and how? (I would also appreciate if anyone knows how to achieve it on XP but after reading lots of related topics in carious software forums I have not found a solution, most of the people say that XP cannot be configured to that and will automatically use one connection and ignore the other)

Thank you very much in advance!

---

