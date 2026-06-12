---
title: "Network management"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by raphaelsaldanha on 2012-04-04
Hi!

I need to rebuild the network where I work. Currently we have a Dell PowerEdge SC 440 with OpenSuse running as a file server, and ten machines with Windows on the router (wireless).

The guy who installed the OpenSuse on the server disappeared some years ago ):P , the HD is running out of memory, and isn't detecting any of the monitors we have (it was working with old CRT that we don't have more).

I need reconfigure this server, probably with Ubuntu to run as a domain and file server., adopt some backup procedures etc. I was thinking too about to buy a NAS... 

As you can see, I'm a little lost here. So I'm asking for some advice and good references about network configurations and management.

Thanks in advance!

---

### Post by na5h on 2012-04-04
The [Ubuntu Server Guide]("https://help.ubuntu.com/11.10/serverguide/C/index.html") might be a good place to start...

---

### Post by lukeiamyourfather on 2012-04-04
This is a great resource that will cover pretty much anything you need for setting up a Linux server. There's newer versions depending on what version of Ubuntu you install.

[https://help.ubuntu.com/10.04/serverguide/C/](https://help.ubuntu.com/10.04/serverguide/C/)

Something to consider about the Dell server is the age. Being more than five years old a lot of components are probably on their last leg (especially the hard disks). Be sure to perform regular backups.

Buying a NAS is an option but you'll probably pay more for equivalent capacity and performance compared to buying or building a server. A NAS is also less flexible than building or buying a server since most have proprietary software and limited features. Good luck with the project.

EDIT: na5h beat me to the Ubuntu Server Guide.

---

### Post by raphaelsaldanha on 2012-04-04
Hi! Thanks for the reply! I would take a good look on the guide.

I started to use Ubuntu for 6 months ago and I'm loving it! I plan to migrate all the office some day... but one step after other. First, I would like to re-configure the network.

The main goal of the network is have a file and print server. But, as the office is growing, I think a domain server to login will be desirable. And there will be a filial opening, so we will have to had access to some files over Internet.  And we are planning to host some web services in the future. Can I, and is secure, to have all these services in one single server?

Our server is indeed very old. Probably, no one had ever logged in the server for three or four years ago. The backups are current being made over the network (not direct on the server) on a external HD, on a very unprofessional way.

I'm have notified the administration several times about the gravity of the problem and the bomb we have, but they were waiting the server catch on fire to pay some attention I think... But there is now a signal to pay attention to this, and some budget too. I would like to contract some expert, but I think we will not have enough budget to this. So, here I go again...

It is attached the current structure diagram, and the project I hda in mind. Considering what was said about NAS, what will be the best solution?

---

