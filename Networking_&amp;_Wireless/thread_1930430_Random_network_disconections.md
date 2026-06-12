---
title: "Random network disconections"
date: 2012-02-23
forum: Networking &amp; Wireless
---

### Post by bleavitt on 2012-02-23
Hello All,

So I have a server that I placed in CoLocation. The server is running Citrix Xen, and the Virtual Machine is running Ubuntu 10.10 server 64bit.

I discovered the issue while playing Minecraft. I would randomly get disconnected, and when I tried to connect to my webserver it would also time out.

I logged into the virtual machines console and the server was responding properly from the command line. I ran bwm-ng and at around the time I get disconnected from Minecraft all network traffic suddenly dies.

I am not sure how to properly troubleshoot this issue. I have another system running on the server that I am able to keep a continuous network connection alive with.

I am installing some network monitoring tools to try and see if the connection is dropped at any regular rate, possibly connecting with a service, but as of now I am lost. I have disabled Minecraft, but the issue still persists.

If anyone has any ideas on what to try, places to investigate, or even potential solutions it would be greatly appreciated.

---

