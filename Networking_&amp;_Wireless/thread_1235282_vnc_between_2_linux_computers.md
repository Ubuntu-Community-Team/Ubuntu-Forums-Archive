---
title: "vnc between 2 linux computers"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by oneiric on 2009-08-08
is it possible to have remote desktop between two linux computers, without using vncviewer, or any GUI interfaces?  

I am running matlab on the linux server, which is a part of some subnet.. the subnet is accessible through another linux box... which is the only computer on the network to be exposed to outside world.. this linux box is called gonzo and the one which is the matlab server is called nuke. ...

i access the gonzo machine from home using ssh, and from gonzo ssh into nuke... but i need to run the matlab GUI remotely from home because I don't know how to operate matlab from the command line... i can't install vncviewer on gonzo, so how do I do it?  is this possible ??

---

### Post by 80aless on 2009-10-22
I do not think I understand your "but i need to run the matlab GUI remotely from home because I don't know how to operate matlab from the command line"
I think you cannot use matlab from command line, ie from the terminal after a ssh connection. 


how do you use Matlab in Gonzo? or you mean that you run Matlab in Gonzo while using the Nuke server for the Matlab License?

---

### Post by briwood on 2009-10-22
Look into "port forwarding".  What you want to do is setup port forwarding on gonzo.  You configure gonzo so that any connection to 10022 (or port of your choice) should be forwarded to a specific port on nuke.  I think Openssh allows you to set up port forwarding rules.  

hth

---

