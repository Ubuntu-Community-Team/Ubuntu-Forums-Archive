---
title: "SSH connection refused"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by dzaletnev on 2009-12-07
I try to run an application (OpenFOAM 1.6) in parallel (openmpi 1.3.3) on two nodes - Head node (openSuSE 11.1 x64) and Slave node (Ubuntu 9.10 x64). I've got a message on the Head node that SSH connection to server - Slave node at port 22 refused. So I'm interested how to disable firewall for one of the NIC's in Ubuntu 9.10 x64. And what methods are applicable in my case.

---

### Post by diablo75 on 2009-12-07
> **dzaletnev said:**
> I try to run an application (OpenFOAM 1.6) in parallel (openmpi 1.3.3) on two nodes - Head node (openSuSE 11.1 x64) and Slave node (Ubuntu 9.10 x64). I've got a message on the Head node that SSH connection to server - Slave node at port 22 refused. So I'm interested how to disable firewall for one of the NIC's in Ubuntu 9.10 x64. And what methods are applicable in my case.

If I understand correctly, the SuSE is the server and your Ubuntu client is attempting to connect to it.  By default, local outbound traffic on port 22 is not blocked, so Ubuntu should be able to connect to the SuSE system, providing that SuSE isn't blocking inbound traffic on that port.

---

