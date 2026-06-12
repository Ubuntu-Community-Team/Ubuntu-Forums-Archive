---
title: "Direct connect - can't find answers"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by ed-koala on 2009-05-27
I've looked all over and cannot find simple, step by step instructions on how to direct connect 2 PCs using a crossover cable. Both PCs run Jaunty.

I've tried everything I've found but I must be missing a step somewhere. All I want to do is transfer files from one PC to the other, no internet required.

Can someone please tell me how, step by step, so I can "see" the files on both machines and move them back and forth?

Thanks

---

### Post by Boondoklife on 2009-05-27
What steps have you taken so far?

Basicly you need to do the following.

[LIST=1]
[*]Power both boxes on
[*]configure them to have a static ip
[*]plug in the network cable
[*]try to ping the other box.
[/LIST]

---

### Post by ed-koala on 2009-05-27
I did that and pinged successfully, but how do I "see" and transfer the files?  File browser doesn't show the other PC (or I don't know where to look)

---

### Post by Boondoklife on 2009-05-27
are they both linux boxes, if so then if you are trying to do the browse pc's like windows, you will need to install and configure samba on both.

if one is windows then just use the network option under places to connect to the windows box, but you will need to make sure you have given it permission to connect on the windows side.

---

### Post by ed-koala on 2009-05-27
Both run Ubuntu Jaunty.  I installed Samba thru Synaptic on both machines (took some cable switching for internet access).

No Samba shows up anywhere to configure.  How to config Samba?  And then what?  You'd think this would be a lot easier.

---

### Post by timcredible on 2009-05-27
go to places->home folder, and right-click on the folder you want to share and choose 'sharing options'.  if your system doesn't have the packages, it'll prompt you to install them (if you have an internet connection).  no configuration of samba necessary.

then, to find that shared folder from the other computer, go places->network, and your first pc should be there.

as for crossover cable, buy one from wherever, a couple dollars, plug ends into the 2 pcs, and go to the network icon, right-click on it, go to edit connections, and give one pc the ip address of 1.1.1.1 with subnet mask of 255.0.0.0 and give the other one 1.1.1.2 with same mask, and away you go.

---

### Post by ed-koala on 2009-05-27
Thank you, got it working. Had to make a network connection using local connect, but finally, got what I need.  You're a lifesaver!!

---

