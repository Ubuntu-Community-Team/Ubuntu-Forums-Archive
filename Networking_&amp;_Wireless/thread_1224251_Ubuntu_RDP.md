---
title: "Ubuntu RDP"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by DariusZelvys on 2009-07-27
Hi, i'm in desperate need of help. Imagine 2 networks. connected through the vpn connection. 192.168.111.254 and 192.168.110.254. There is one win2003 server on 111.254 network. Every user on those 2 networks connects to that server through RDP and copies data. Now's the problem. If a user with ubuntu desktop from network connects to 111.254 networks and copies more than 200 lines from excel file for example, paste function in OpenOffice fails. If it's 100 lines, then it works like a charm. If the same computer does this operation on 111.254 network, it works flawlessly with any amount of data. Even with 50000 lines. The same computer goes back to 110.254 network and the copy size drops to 200 maximum. I tried to recplicate the same situation with winxp computer, and everything is working good even with very large amount of data. I can copy 50000 lines using winxp on network 110.254 from network 111.254, but can't do the same operation using ubuntu system. Any ideas?

---

### Post by The Cog on 2009-07-27
It sounds like an MTU problem on the VPN. Try this:
Figure out which interface the VPN is by looking at the output from the command **ifconfig**. It's probably something like tun0. Use that interface in this command:
**sudo ifconfig tun0 mtu 1300**
and see if that makes any difference.

---

### Post by DariusZelvys on 2009-07-27
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:79:03:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:69:7c:6f:d9  
          inet addr:192.168.110.116  Bcast:192.168.110.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe7c:6fd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43576 errors:0 dropped:0 overruns:0 frame:7505
          TX packets:26724 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21677892 (21.6 MB)  TX bytes:5289065 (5.2 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:422681 (422.6 KB)  TX bytes:422681 (422.6 KB)



thats my ifconfig

---

### Post by DariusZelvys on 2009-07-27
> **The Cog said:**
> It sounds like an MTU problem on the VPN. Try this:
Figure out which interface the VPN is by looking at the output from the command **ifconfig**. It's probably something like tun0. Use that interface in this command:
**sudo ifconfig tun0 mtu 1300**
and see if that makes any difference.
Tried eth0 instead of tun0, didn't help
actually tried to set every interface to 1300 and it didn't help
any other ideas?

---

### Post by The Cog on 2009-07-27
None, I'm afraid. I suppose you could try 1200 but I don't see any point in trying to go lower than that.

Looking at man rdesktop, there are a couple of options you could try (in desperation).

rdesktop -4 hostname
rdesktop -5 hostname
rdesktop -z hostname
rdesktop -P hostname

---

### Post by DariusZelvys on 2009-07-28
any other ideas? nothing helps

---

### Post by dmizer on 2009-07-28
What kind of VPN connection are you using? Since your ifconfig does not show a TAP or TUN device, this indicates that you are either not connected via VPN or are using a different method for connecting.

---

### Post by DariusZelvys on 2009-07-28
Thats' definetly VPN, it's just not through tunnells. It's a direct VPN connection, between 2 routers that are provided by my internet provider

---

### Post by dmizer on 2009-07-28
> **DariusZelvys said:**
> Thats' definetly VPN, it's just not through tunnells. It's a direct VPN connection, between 2 routers that are provided by my internet provider

Then you may have to look at the MTU settings in the router.

---

### Post by DariusZelvys on 2009-07-28
I'll have to ask my provider for that... but i thought that linux works with networks better than windows, how come windows work flawlessly in this situation i still dont understand

---

### Post by dmizer on 2009-07-28
Your network seems to be working fine. Your problem seems to be with file sizes. Frankly, I'm out of my league here because I've just recently started to experiment with VPN so I'm hardly an authority. I was just trying to expand on the suggestion offered by The Cog.

How are you accessing the cross network shares?

---

### Post by DariusZelvys on 2009-07-28
network shares work perfectly for example i can copy a 100mb file with a normal speed,

---

### Post by DariusZelvys on 2009-07-28
Another thing. Through the VNC everything's working well

---

### Post by DariusZelvys on 2009-07-29
sad moment.. 50 pc's of ubuntu will have to be reinstalled to windows because of this problem. VPN has nothing to do with it... cause VNC works... i think it's software related problem...

---

### Post by dmizer on 2009-07-29
> **DariusZelvys said:**
> sad moment.. 50 pc's of ubuntu will have to be reinstalled to windows because of this problem. VPN has nothing to do with it... cause VNC works... i think it's software related problem...

Well, I was going to point you at the Open Office Samba fix in my CIFS tutorial (2nd link in my sig), but you seemed to think that it was not Samba related. And, since I don't know how you're mounting your shares, I'm not sure if it would be of any help or not.

Just because you can copy files fine doesn't mean that there isn't still a problem with Samba, or how you've mounted your shares. Open Office is notoriously picky about how it interacts with Samba.

If you are mounting your shares via Places > Connect to server, you'll find reduced performance, and this could result in the symptoms you're experiencing.

---

### Post by DariusZelvys on 2009-07-29
I doubt it's samba... 
I can open even any text document on windows2003 server copy 20000 lines from notepad for example, go back to ubuntu, open any editor, try to paste it, and it will fail if i'n not on the same network, where the server is. 
Somehow it drops buffer synchro between windows buffer and ubuntu buffer. I'm desperate.. 
All we wanna do is connect with RDP to the server, copy info, go back to ubuntu and paste it. :(

---

### Post by dmizer on 2009-07-29
Okay, so what RDP software are you using, and have you tried any alternatives?

---

### Post by DariusZelvys on 2009-07-30
I've tried all the available RDP clients, the best results i could get were with grdc 0.60
results of other clients were similar, but grdc works a bit quicker.
Still trying to figure out that copy problem. Please help me

---

### Post by dmizer on 2009-07-30
Perhaps this is a problem or limit in the Gnome clipboard ... or lack thereof? Try a different clipboard manager: [http://tombuntu.com/index.php/2008/10/22/enhance-your-clipboard-with-a-clipboard-manager/](http://tombuntu.com/index.php/2008/10/22/enhance-your-clipboard-with-a-clipboard-manager/)

Edit ->
Also, here is a development thread for Grdc: [http://ubuntuforums.org/showthread.php?t=1021138](http://ubuntuforums.org/showthread.php?t=1021138) you could try giving some feedback there and see if the dev has any ideas.

---

### Post by DariusZelvys on 2009-07-30
Tried various clipboard managers... didn't help

---

### Post by DariusZelvys on 2009-07-30
Idea:
it's not a memory issue. After braistorming this problem with my friend we came up to solution that if it was memory issue then it would paste some data, now it doesn't have a single line in clipboard. It seems like it timeouts before it can synchronize with ubuntu clipboard. How can i change the time settings for synchronizing/copying data from rdp?

---

### Post by DariusZelvys on 2009-07-30
bump

---

### Post by dmizer on 2009-07-30
> **DariusZelvys said:**
> bump

As I suggested before, I strongly recommend that you discuss this mater directly with the developers of grdc either in the thread I linked earlier or here: [http://sourceforge.net/projects/grdc/](http://sourceforge.net/projects/grdc/)

---

