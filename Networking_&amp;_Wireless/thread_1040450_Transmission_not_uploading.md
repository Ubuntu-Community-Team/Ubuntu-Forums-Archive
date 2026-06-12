---
title: "Transmission not uploading?"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by -mbs- on 2009-01-15
Hello.

I'm a Ubuntu user, and I have a problem. Can't remember when it started, just that it began. It is a matter of transmission would not upload, it comes for that matter, of deluge - When I try in Windows Vista (with the same computer - uTorrent) it would upload!

Firestarter, I have tried to turn off, but it did not help. Router I have also tried to default, nothing will help

Can not really come up with more information. Do not know if I just reinstall Ubuntu?

Regards. 
mbs

---

### Post by -mbs- on 2009-01-19
No one that can help me :( ?

---

### Post by BardSeed on 2009-04-22
I'm having the same issue and it's a problem because private torrent sites require you to keep a good ratio.

---

### Post by SilverDrake11 on 2009-05-01
Someone help! Yea, im also having the same problem. I got my ports open and everything fully configured on transmission. The downloading works but I cannot seed, its always zero. I'm running a fresh install of jaunty 64bit.

---

### Post by crysys on 2009-05-08
Same problem here.  I have multiple rules on my wired router opening all ports needed for bit torrent and transmission listening port.  This all worked in Intrepid.  Now with a clean install of Jaunty I cannot seed anything and transmission lists the listening port only occasionally as open and then comes back as closed again shortly thereafter.  I've been banging my head at this all night and it is starting to give me a headache.

An online port scan shows the listening port as open, but bt port range(6881-6969) is closed.

---

### Post by s7dhansh on 2010-08-01
I had similar troubles, but my port was closed. Did a ufw allow <port> to cruise through. The topic is quite old and probably the problem had been solved. But just wanted to share.

---

### Post by kryptic_mind on 2011-01-03
Anyone have any luck in solving this problem. It persists for me.

---

### Post by ulkas on 2011-01-09
bump, the same problem here. after few months of use my transmission has stoped seeding, although it shows me that i'm connected to peers but no upload traffic at all.
runing ubuntu 10.04

---

### Post by Rollinson on 2011-01-24
Same problem here - I think I've tried everything, but maybe if I give more details a good response will materialize. 

Background info: running Ubuntu 9.04. UPnP is selected both at the router level and at Transmission. I have made exceptions in ufw for 51413 and 51415 (see below). I can download fine (get great speeds!) but no uploading. This despite my formerly being able to upload with ease prior to Christmas (it seems to have stopped working sometime while I was on vacation). I can also download/upload quite fine on a Windows 7 machine attached to the same wireless router using uTorrent. (Although even here there are some hints of potential problems - while I generally get the green check mark saying the network is fine,  running the setup wizard that checks for bandwith/network tools doesn't always work - just did it now and I get two red X's, with the Network box giving the message: "Neither NAT-PMP nor UPnP is enabled"...which is wrong, since they are and I've getting high upload speeds in the background.)I have also tested this with other torrent programs in Ubuntu (kTorrent and uTorrent through Wine - and I get similar problems). 

I originally had the Ubuntu machine on DHCP but set up a Static IP (which is working for Internet use). I also forwarded port 51415 at the router level (Netgear WND3700; created a TCP/UDP forwarding rule) but Transmission says it is closed (I originally tried 51413 but it also failed). As I've mentioned I made exceptions for both ports in ufw. (I originally had Firestarter installed, but not running, but I've since taken that off and only have ufw up).  If I do a port scan of my router address using Network Tools neither comes up, although a port in the 491xx range does. Likewise, if I use canyouseeme.org it says it cannot (connection times out). 

Per another thread [[http://ubuntuforums.org/showthread.php?t=893863&highlight=transmission+forward+port]](http://ubuntuforums.org/showthread.php?t=893863&highlight=transmission+forward+port]), I ran sudo netstat --tcp --listening --programs and it appears to list 51415 port as in a state of LISTEN. When I follow the advice of growing needs in that thread and go through Network Tools->Netstat it also says that 51515 is listening, although with an incoming IP of 0.0.0.0. 

I also tried removing the Transmission folder as recommended in that thread, but both the 51413 and -15 ports are reported as closed when tested. 


Are there any other potential solutions? What else can I check? What else could be problematic? Thanks for any help proffered!

---

### Post by Rollinson on 2011-01-24
Ok, so there is one more thing to try: restart your router after you set up the port forward/static ip option. just did it and now the port is open and transmission is working. I'd suggest that to anybody who is having difficulties with their port forward/static ip.

---

### Post by subjucha on 2011-03-22
I have the same issue. Transmission doesn't upload but it download perfectly. KTorrent on the same system starts massive upload just after starting the program, as far as I have nearby 350 torrents. I know surely that here isn't any blocking rules on the router of my office network. I have tested various combinations of parameters. I have upgraded Ubuntu 10.10. Deluge doesn't upload too.

_**UPDATE:**_

Sorry, I was mistaken, my router doesn't allow unstablished  incoming connections, except on port 22. So, I've configured Transmission on 22 port and it works, uploads well. But I don't understand why KTorrent can upload on closed ports?

---

