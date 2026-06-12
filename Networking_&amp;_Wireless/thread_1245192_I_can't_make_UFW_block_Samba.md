---
title: "I can't make UFW block Samba"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by swerdna on 2009-08-20
Hi I've got Ubuntu 9.04 running.

I have Samba on a LAN of mixed Suse, Ubuntu & windows machines, all sharing files. On th Ubuntu machine I have turned off all traffic through UFW (or so I thought).

"sudo ufw status" shows the following: "status active" and displays no rules. 

If I check by displaying GUFW I see:
[LIST]
[*]deny incoming traffic
[*]the color of the shield is green
[*]there's a tick in "firewall enabled"
[/LIST]

I take that to mean that all incoming traffic is denied.

But if I open Nautilus I can see all computers on the LAN and I can drill down in all of them to the shares on the computers.

Have I broken UFW somewhere or do I need to set something else to really block incoming traffic? Or is Samba special in that it isn't blocked in the catch-all: "deny incoming traffic"?

What am I missing

Thanks
swerdna

---

### Post by dmizer on 2009-08-20
You should be able to tell more about the rules that UFW has in place by looking at the output of:
```
sudo iptables -L
```

I'm a bit confused though, you say that you open Nautilus. Are you opening Nautilus on the Ubuntu machine or on the Suse machine? I believe that localhost will always be allowed even if incoming traffic is denied.

---

### Post by swerdna on 2009-08-20
Thanks for the reply.
> Are you opening Nautilus on the Ubuntu machine or on the Suse machine
The short answer is "both". Here's the long answer:

On the Suse machine I can drill down to the share but not into it -- which is some protection if not perfect. But it occurred to me while I was sleeping last night (it 0630 here now) that this "seeing" the share from the Suse machine might not be real. It might be an artifice of the nmb cache on the Suse machine. (I've done a lot of experiments -- there's cache memory aplenty).

So I created a new share on Ubuntu that Suse hadn't seen before -- and I can see that share from Suse too, though I can't drill down into it. So the "seeing" of shares while the Ubuntu firewall is up is indeed real, not a cache artifice. That's security issue #1.

Now to the second issue, that of the shares on Ubuntu while the firewall is up. I can write to those when UFW is up when I log onto Ubuntu as any user. I had thought that UFW would prevent network access to Samba shares on Ubuntu. This means that the Network Interface on the Ubuntu machine has "trusted" status by default -- or is not in the "external" zone and thus is not properly firewalled. Is there a way to have UFW prevent network access to the Ubuntu shares from all machines, even its own machine? That's security issue #2.

It's obvious from my confusion in the last thread of mine that you kindly answered (where I had the rules backwards -- I'm still analysing that) -- it's obvious that I've got a long way to go to be fully conversant with UFW -- but I'll get there in the end.

Maybe I just have to live with your diagnosis that localhost is providing the access to the Ubuntu shares. It's just that I'm not used to that in Suse. But I can live with it if that's a limitation of UFW. It's pretty good otherwise.

---

