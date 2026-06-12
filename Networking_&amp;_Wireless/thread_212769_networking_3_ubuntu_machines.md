---
title: "networking 3 ubuntu machines"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by closeyourwindows on 2006-07-10
this should be a no brainer, but I cant seem to see the other computers on the network.  here is what I have.  2 desktops and one laptop at work, all with ubuntu 6.06 installed.  I can ping all machines from any machine here.  however I can not seem to be able to share files or printers here because I dont know how to find them.  when I go to menu > places > network servers, all that I see is a sama share that does work and I dont use often.  lets forget about that one.   
I also have vncviewer installed and would like to be able to RDP into one of them both from within the network and also from home.  by the way I am using a linksys wireless router wrt54g to connect the 3 computers at work.  2 wired and one wireless.  

first, how can I see the other computers in the network?
second:  vncviewer, I assume the syntax is vncviewer <ip address> or <hostname>.  any help is appreciated.

---

### Post by apjone on 2006-07-10
put an etry in your host for them eg

127.0.0.1       localhost localhost.localdomain
192.168.1.2     host1     host1.domain
192.168.1.3     host2     host2.domain
192.168.1.4     host3     host3.domain
192.168.1.1     router1   router1.domain

---

### Post by dasyar613 on 2006-07-10
Since I am trying to accomplish the same thing, and I am new to this, some hand holding is required. Could you be a little more specific as to where and how that info gets to where it is supposed to go. Some of us have been spoiled by MS.
Thanks

---

### Post by closeyourwindows on 2006-07-10
well that did not seem to work, but a valiant attempt.  all I am really trying to do is peer to peer and I see other unanswered posts as well.  surely there is someone that has successfully configured a peer to peer network in ubuntu.  

and the vnc, I do not have any experience with this so I could really use somehelp in getting this going.  I did what I found in some of the other posts, like configure the remote users, allow user to access system remotly with a graphic interface.  however that is not the problem, it is the syntax and the ports to allow vnc.

---

### Post by scxtt on 2006-07-10
you've got 2 easy, viable options w/ your 3 ubuntu boxes ... SSH and NFS ... neither are hard to setup/use - just install some packages ... if you're interested, i can walk you through it ...

as for VNC, i use SSH to start the vncserver (host) and vncviewer (client) to connect to it ...

---

### Post by krpnm on 2006-07-10
You need to:

1.  apt-get install the NFS packages.
2.  Create or modify your /etc/exports file.
3.  Modify your /etc/fstab file.
4.  Modify your /etc/hosts file.
5.  If your are using a firewall on each machine such as firestarter you need to set a rule allowing each machine on the internal network to access the other machines.

---

