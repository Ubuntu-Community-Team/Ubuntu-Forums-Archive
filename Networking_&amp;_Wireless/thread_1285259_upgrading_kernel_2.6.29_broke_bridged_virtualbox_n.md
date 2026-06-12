---
title: "upgrading kernel 2.6.29 broke bridged virtualbox network adapter"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by lieberb on 2009-10-07
I'm running Ubuntu 9.04 64bit, with VirtualBox running WinXP as a guest. I run a development server (mongrel) locally, and connect to it from inside the VM. The VM is configured with a Bridged Adapter, and so can hit my dev server through [http://192.168.1.175:3000](http://192.168.1.175:3000) (or similar)

This all worked fine, EXCEPT - my environment doesn't support IPv6, whick 9.04 has hard-coded for some reason, so I upgraded to kernel 2.6.29 and used the ipv6.disable=1 option in the boot grub. This fixed my IPv6 problem, with no side affects other than:

Now, from within my virtual machine, I can hit the dev server, I see logs rolling showing that they received a request. I can even see the browser get redirected to a login page as it should. But it will never load. Since there is obviously traffic coming both ways, I'm not sure how to better describe the problem, other than it just hangs.

In order to narrow down the cause, I've booted back to 2.6.28: problem fixed.
I've can hit my server within the network from another computer without problem.
I can hit the server from another virtualbox machine that uses NAT instead of bridged.

So, its narrowed down to kernel 2.6.29, virtualBoxes running Bridged adapter. 

I know this is a one-off scenerio, but I would appreciate any insight people might have.

Thanks,

-Ben

---

### Post by tomthumb99 on 2009-10-07
Thanks for the post and help on disabling ipv6. I ran into some corruption and had to run "apt-get upgrade", I have come to find the worst possible command in this os; my IP broke, my nvidia drivers broke, it upgraded my grup...all bad things.  

Why would they hard code Ipv6 into the kernel in 9.04?  I had it under 8.04  setup as a restricted module in the past, it was a nice solution. 

I have no need for IP6, my home network is only four PCs.  With all the stability/quality issues with this OS why do they play with stuff that works.  My old router work fine, no need for a new one!

With sharp folks running this Rail Road, uncle Bill and  Win7 has nothing to worry about.

---

### Post by lieberb on 2009-10-13
Looks like this has been fixed in VirtualBox 3.0.8 :guitar:

---

