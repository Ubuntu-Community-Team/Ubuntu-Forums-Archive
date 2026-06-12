---
title: "OpenVPN Working in Terminal but not with NetworkManager"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by finito on 2011-04-28
Well Title says it all.

Another thing is I have to do sudo openvpn conf.opvn for the command to work in Terminal.

Unprivileged attempts get a permission denied

```
Thu Apr 28 23:18:51 2011 Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Thu Apr 28 23:18:51 2011 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Thu Apr 28 23:18:51 2011 Cannot allocate TUN/TAP dev dynamically
Thu Apr 28 23:18:51 2011 Exiting

```

But run with sudo it connects.

I think this is why NetworkManager is also not working.

The Difference is that Network Manager shows Connected but I lose all connectivity when I connect via NetworkManager.

I read a few threads that seem to indicate this is known issue but I was unable to find a direct answer.

Peace.

---

### Post by finito on 2011-04-29
I know it's been only 10 Hours and I am supposed to wait 24hours before bumping a post.

I just wanted to add that I have another machine LinuxMint9 and it works perfect I set it up a while ago so I don't remeber if I had to do something to make it work.

Any response on the matter would be awesome, even a point in the right direction is cool.

Peace.

---

### Post by finito on 2011-05-03
bump

---

### Post by finito on 2011-05-05
bump

---

### Post by doc_fr on 2011-05-05
Hi, i actually do have the same problem, whether it is on a standard install or in a VirtualBox VM, wich leads me to think it is a network-manager problem.
After some research, resolv.conf seems correctly altered, although the routing table is completely messed up.
I tried to renew the addressing with a dhclient launch, but no success, since it simply ignore the openvpn ip settings and go to the standard connection, therefore no traffic goes through the tun adapter.
Iptables is allowing everything, so it's not an iptable problem either.
And no, i absolutely don't want any traffic to go through my local public ip, i need it to go through the vpn ip, so balancing part of the traffic with the options in advanced routing config is not an option.

This problem is also not only related to 11.04, i had the same problem on the previous version of ubuntu, 10.10.

I have seen many posts about this problem, but nothing seems to advance in resolving this problem.

Ubuntu is supposed to work out of the box on such feature, even if you actually have to install the network-manager-openvpn-plugin to have access to this kind of vpn, and having to launch a terminal client to actually establish successfully an openvn connection is not so user-friendly as canonical says this new version is really intended to be for linux newcomers ...

---

### Post by finito on 2011-05-05
doc_fr it works flawlessly on LinuxMint9.

I want to know why it doesn't work on 10.10

Peace.

---

### Post by doc_fr on 2011-05-05
I also tried the same thing with Fedora 14, wich use the same networking tools, network-manager with openvpn plugin under gnome.
They actually have the same problem, and still no concrete answer on their side either.
Finito, I'll need to give a try to linuxmint, to see what they do since you seems to be saying they don't have this problem.
Basicaly, check the routing table table, and resolv.conf, also give a look to the iptable settings, just to check nothing special in there.
So far, on both Fedora and Ubuntu (14 for fedora, 11.04 and 10.10 for ubuntu), the routing table seems to be affected, i unfortunately have no time to look at the behaviour of he network manager plugin, but it would be really interresting to know what is changing between linux mint and fedora and ubuntu on that special part of the network.

On some french forums, they tried to use with success older version of the network-manager, probably need to give a look to the maintainer of the package to know what they are doing ...

But implementing a known bugged version of the network-manager without trying to actually correct it on such a major version of Ubuntu, disappoint me a little bit to be honest, i hear more and more good about linux Mint, i will give it a try.

---

### Post by finito on 2011-05-05
I treid LinuxMint10 Same Problem. Since Mint is based on Ubuntu I think this problem was carried over from Ubuntu 10.

Mint9 was the most stable one I have tried to date, but I don't feel like downgrading to 9 just for OpenVPN.

It works fine with Terminal and I usually need it more on my Mint9 Machine anyway.

I thought there may be an actual solution since the bug is well known.

I will try to keep this thread alive until I get an answer.

Peace

---

### Post by jonnybignote on 2011-08-10
I had a number of tries with this in a few Ubuntu versions with no luck.  I'm settled on 10.04 though for now and I came across a post suggesting to uncheck 'Available to all users' at the bottom of the VPN configuration window.  Since doing that, it's been rock solid for me although it currently prompts for password and I haven't looked into the right thing to plug into sudoers.

Thought I'd drop that by just in case it helped...

---

