---
title: "New router.....no shares"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by motorcity909 on 2010-03-07
A few months ago on these here forums I was given some help in setting up Samba shares from my Ubuntu desktop to my sons' WinXP laptops.
 
 This involved replacing the Firestarter firewall manager with UFW and adding this code into a file to configure the firewall:-
 
```
sudo iptables -L 
 sudo ufw allow proto udp from 192.168.0.2/26 to any port 137 
 sudo ufw allow proto udp from 192.168.0.2/26 to any port 138 
 sudo ufw allow proto tcp from 192.168.0.2/26 to any port 139 
 sudo ufw allow proto tcp from 192.168.0.2/26 to any port 445

``` 

This worked in as much as the two WinXP laptops could successfully access the Ubuntu share but if I wanted to access a WinXP shared folder on my Ubuntu desktop I had to disable the firewall first, access the shared Windows folder from Places>Network, re-enable the firewall, then copy any files across from the Windows machine.
 
This was acceptable as I rarely had to access files on the WinXP laptops (quicker just to grab a memory stick for those files) and it was more important for my sons' to access my shared Music folder.
 
I've recently changed my router to an N wireless compatible model, in anticipation of a new laptop with N wireless.
 
All the computers (and our Wii) connect to the internet without any problems, both wired and wireless.
 
However the Samba shares can no longer be accessed on the WinXP machines unless I disable the UFW firewall first.
 
I'm wondering if I need to change that UFW firewall configuration and would appreciate any help.  
 
I've noticed the new router's IP range is 192.168.1.**2** to 192.168.1.**254**, which I *think* is a wider range than the old router.  I may talking rubbish there! ;)
 
(As an aside - My ISP doesn't offer static IP addresses for home use and I'd rather not go down the whole dynamic DNS route either.)
 
I hope this question makes sense.  Many many thanks as always
 Dave

---

### Post by bernied on 2010-03-07
Is there a typo in the address ranges here:
> **motorcity909 said:**
> ```
sudo iptables -L 
 sudo ufw allow proto udp from 192.168.**0**.2/26 to any port 137 

``` 

or here:
> **motorcity909 said:**
> I've noticed the new router's IP range is 192.168.**1**.2 to 192.168.**1**.254

??

Is your new router using a different address range than is configured for the firewall - ie. 192.168.0.* vs 192.168.1.* ?

If that's the case you just need to adjust either the router or the server, so that they match again.

Personally I don't use firewalls on linux machines behind my home router. I just set up the firewall in the router to only let in the traffic I want, and configure the linux machine so only the things I want served are served. The only reason you should need a firewall inside your own LAN would be if you had both trusted and untrusted machines on it.

---

### Post by motorcity909 on 2010-03-07
Hi bernied

No typos - see attached screengrab of the firewall gui and the router.

I haven't changed anything on the router - that's what was there the day I plugged it in.

I agree I need to make them match, so how do I change the firewall settings?

As for your second point, am I safe enough just using the router firewall?  All the machines on the network are trusted.

Thanks
Dave

---

### Post by motorcity909 on 2010-03-11
Is there anybody out there?

---

### Post by dmizer on 2010-03-14
Are you absolutely positive you need a firewall? If not (and you probably don't), I suggest simply uninstalling it. You'll have a much better computing experience without it.

From the 6th link in my sig:
> Firewalls block samba browsing. If you're sharing files over samba, that probably means you're on a LAN with only indirect (usually via a firewalled gateway/router) access to the Internet. This means that you probably don't need a firewall at all. If you think you DO need a firewall, you should really think about how wise it is to poke holes in it to facilitate samba file sharing.

Since you indicate you already have a router, a local software firewall is redundant unless the traffic on your own LAN is untrusted (eg, your router is a public WIFI hotspot).

---

### Post by motorcity909 on 2010-03-14
Hi Dmizer

Thank you so much for taking a look at this for me.

My router does indeed have it's own firewall and also WPA2 security enabled and all the machines on the network are trusted (two son's XP laptops and a Nintendo Wii).  

I will therefore disable the firewall to allow for easier sharing between the three machines.

Thanks again for helping me with this.

Dave

---

### Post by CharlesA on 2010-03-14
I know you've got the problem fixed, but I was wondering why there was a 26 bit netmask instead of the usual 24 bit class-C netmask in the firewall settings in the OP.

---

### Post by motorcity909 on 2010-03-14
Er...sorry, can't help you on that.

I copied those firewall exceptions from Dmizer's 'How To Fix Windows shares' [here]("http://ubuntuforums.org/showthread.php?t=1169149") - see problem 4.

Maybe someone else can chip in here....?

Dave

---

### Post by CharlesA on 2010-03-14
Ah ok. I checked that thread and it listed /24 for the netmask. *shrugs*

I must have mine set up differently, since the only port I have open is 445.

---

