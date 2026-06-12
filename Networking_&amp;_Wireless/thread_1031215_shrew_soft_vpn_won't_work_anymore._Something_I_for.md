---
title: "shrew soft vpn won't work anymore. Something I forgot?"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by svaens on 2009-01-05
Hi guys, 

I've been recommended to use shrew soft vpn to connecto the my office at work..  
I got it working once before. That was when i had gutsy installed. 
I realized ike vpn had been included in the repositories in Hardy, so i temporarily added the appropriate repositories to my /etc/apt/souces.list. 
Installed the thing using apt, and it was running. 

Great!

Since then, i've installed Hardy itself (fresh install) and now tried to re-install shrew soft vpn again. 

Installs ok. GUI starts up ok, daemon appears to be running. 

But i don't get anywhere much when connecting. 

Here is the output from the gui:

config loaded for site 'office.astraia.com.2'
attached to key daemon ...
peer configured
iskamp proposal configured
esp proposal configured
ipcomp proposal configured
client configured
local id configured
remote id configured
pre-shared key configured
bringing up tunnel ...
virtual network device configured
virtual network device enabled
tunnel enabled
gateway not responding
tunnel disabled
detached from key daemon ...



Anyone got any idea what my problem might be? It is not just on this one computer. I tried installing it also on another, (Fresh Hardy) and i have the same problem there. And this is in the same network conditions as it was before when it worked without problems. 
Oh, and, incidentally, when i run windows under VirtualBox, and run shrew soft ike client there, I have no problems. 

I would be very grateful if someone could help me work this out! Even to the point of writing up a howto, so no one else has this problem again.

---

### Post by svaens on 2009-01-06
Well... it can't be firewall getting in the way.. because by default there ain't none on Ubuntu. 

Is there extra configurations I need? 
How can I find out how the shrew soft client available on the Ubuntu repositories was compiled?? I have read that for NAT support, it needs to be compiled differently than the default. Perhaps this is it?

---

### Post by svaens on 2009-01-07
Any idea what the error report (in the first post) actually means?

---

### Post by svaens on 2009-01-10
well, i know it is not an authentication error. 
I tried sticking a new mutual authentication key in, (in the authentication tab). 
And, as soon as I try to connect with the wrong key, i get an authentication error. 

So, it seems to be actually connecting to the server. But still don't get any luck. 

tunnel enabled
gateway not responding
tunnel disabled
detached from key daemon ...

Doesn't anyone else use this application besides myself?

---

### Post by svaens on 2009-01-14
hmm.. ok.. i thought it might be because my home intranet was using the same ip address as the work one which I was trying to connect to (i.e. 192.168.1.1) ... so i changed mine to (192.168.2.1) ... 
But that didn't help me. Still no go. 

hmmm... .what else could be the problem...

---

### Post by Iowan on 2009-01-14
I'm still quite low on the learning curve for VPN (only on page 64 of the OpenVPN book). From a generic networking perspective, it appears that "gateway not responding" could be a problem.  Offhand, I couldn't say on which end the gateway has failed (my guess would be near side - dunno if far side would be called a gateway.) Showing more of my ignorance - I presume you have a routable address for a target somewhere (the 192.168.x.x is in the private range).  Hope I haven't muddied the water too much.

---

### Post by svaens on 2009-01-14
hehe, thanks for the reply!
Don't worry. You can't muddy the waters for me any more than they are already!

But to answer your question: "I presume you have a routable address for a target somewhere"  

yes, definitely have a routable address. The 192.168 addresses I listed were simply the internal intranet addresses of my home, and work. Which (according to guys I spoke to at work about it) shouldn't clash. That my router should be on a different subnet than the work internal router.... 
(or something...... see .... very muddy).

---

### Post by svaens on 2009-03-12
To close this, and let all you other suffering people know how to fix it:

Firstly, I think i was correct in saying that this HAD worked in gutsy. 
What changed since then? 
Kernel changes!

And now you need to modify your sysctl.conf file

modify

net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

to 

net.ipv4.conf.default.rp_filter=0
net.ipv4.conf.all.rp_filter=0

restart your network interfaces ( i think, i just did a lazy reboot)
and it will (should) work again. 

Got this information from the shrew soft mailing list. It worked for me.

---

### Post by svaens on 2009-04-24
Hi all, 

I'm running jaunty now. 

The same fix doesn't fix the same problem now. 
While on Hardy i was finally able to use shrew soft, 
once again, with the upgrade to a new kernel, there has been further change. 
And I have no idea what the hell to do to get it working again. 
The configuration change which enabled the VPN communication in Hardy, does NOT work for jaunty.

anyone got any ideas this time?

---

### Post by svaens on 2009-04-25
ahh... found it. 
There is yet another filter configuration in jaunty that didn't seem to exist in Hardy. I missed that. 
from this file:

 /etc/sysctl.d/10-network-security.conf 

I set to zero the values of the configurations:
net.ipv4.conf.default.rp_filter=0
net.ipv4.conf.all.rp_filter=0

I re-read the original mailing list, and realized there were more that the original fix finder had found on the kernel he was troubleshooting on. 

original (must more informative):

[http://lists.shrew.net/mailman/htdig/vpn-help/2008-November/001827.html](http://lists.shrew.net/mailman/htdig/vpn-help/2008-November/001827.html)

---

### Post by Eerms on 2010-03-26
Just had the same problem and changing the values in /etc/sysctl.d/10-network-security.conf to 0 did the trick.

A question - can this compromise the security of my Ubuntu 9.10 box?

---

### Post by svaens on 2011-10-20
Once again, after upgrade to 11.10, shrew soft vpn doesn't work (even with above fixes).

If anyone has the solution to this, please post it here!
And when/if I find it, i'll do the same.

There is actually a bug report on the matter:
[https://bugs.launchpad.net/ubuntu/+source/ike/+bug/860208](https://bugs.launchpad.net/ubuntu/+source/ike/+bug/860208)

config loaded for site 'XXXX'
attached to key daemon ...
peer configured
iskamp proposal configured
esp proposal configured
ipcomp proposal configured
client configured
local id configured
remote id configured
pre-shared key configured
bringing up tunnel ...
negotiation timout occurred
tunnel disabled
detached from key daemon ...

---

### Post by Michael Biddle on 2011-10-21
Same problem here on 11.10. :/

---

### Post by Borts on 2011-11-04
I have the same problem, again 11.10, but I've been thinking.. what if I try Win version under Wine? I wonder if that helps.

---

### Post by enmansarl on 2011-11-10
Hi,

I have been able to use Shrew Soft VPN v2.2.0 picked from their web site and compiled it and I was able to make the VPN working, where it was failing using the compiled binaries from Ubuntu 11 (v2.1.7).

You will need to follow the instructions in the v2.2.0 package to compile the ike binaries and to install them on your system, and you will just need to copy the iked script in the /etc/init.d directory. Then, start the iked daemon, and run ikea.

Best regards,
Enman SARL

---

### Post by AN@S on 2012-01-03
I've found a fix, you just have to uninstall version 2.1.7 and install older version 2.1.5 and it works (tested on 11.10). More details here: [http://lists.shrew.net/pipermail/vpn-help/2011-October/004053.html](http://lists.shrew.net/pipermail/vpn-help/2011-October/004053.html)

:D

---

### Post by schneil on 2012-03-01
> **enmansarl said:**
> Hi,

I have been able to use Shrew Soft VPN v2.2.0 picked from their web site and compiled it and I was able to make the VPN working, where it was failing using the compiled binaries from Ubuntu 11 (v2.1.7).

You will need to follow the instructions in the v2.2.0 package to compile the ike binaries and to install them on your system, and you will just need to copy the iked script in the /etc/init.d directory. Then, start the iked daemon, and run ikea.

Best regards,
Enman SARL

I'd like to compile the 2.2 version, but when I type 
"cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DQTGUI=YES -DETCDIR=/etc -DNATT=YES"

It gets stuck on 
"CMake Error at CMakeLists.txt:211 (message):
  Unable to locate openssl crypto include files"

Can anyone help me?

---

### Post by deb8torGG on 2012-05-13
> **AN@S said:**
> I've found a fix, you just have to uninstall version 2.1.7 and install older version 2.1.5 and it works (tested on 11.10). More details here: [http://lists.shrew.net/pipermail/vpn-help/2011-October/004053.html](http://lists.shrew.net/pipermail/vpn-help/2011-October/004053.html)

:D
I have just installed (Fresh) Precise 12.04 and installed the Shrew Soft Ver 2.1.7 and give that a try with no luck.  Still etting the "negotiation timout occurred" message

I removed 2.1.7 and instaled the older version of the VPN manage 2.1.5 and I still get the same message.  Can anyone shed some light on this at all.  I looked at the Launchpad site for the bug progress and from what I could gather the updated newer version of 2.1.7 was suppose to solve the issue but it doesn't seem to have for me.

I have checked VPN connectivity to my fritzbox from a VM(running XP)using Shrewsoft 2.1.7 and although I have problems pinging **any device** on the remote network I can get it to connect everytime.

Has anyone been able to get this sorted or is anyone else getting this problem??

---

### Post by deb8torGG on 2012-05-20
bump

---

