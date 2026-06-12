---
title: "Disabling IPv6"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by cryptodan on 2009-08-24
I tried the following ipv6.disable=1 and I get the following:

Unknown boot option `ipv6.disable=1': ignoring


Any other way to disable IPv6?

---

### Post by Bucky Ball on 2009-08-24
In Firefox, in the address bar type:

about:config

You will get a warning about voiding your warranty. Then search for:

network.dns.disable.IPV6
(a search for simply 'ipv6' will turn it up)

Right click where it says 'false' and toggle to 'true'.

Done.

Also, you should just be able to comment out ('#') any IPV6 references in the appropriate files.

---

### Post by tad1073 on 2009-08-24
> **cryptodan said:**
> I tried the following ipv6.disable=1 and I get the following:

Unknown boot option `ipv6.disable=1': ignoring


Any other way to disable IPv6?

ipv6 is no longer modular, to disable it you would have to rebuild your kernel.

---

### Post by cryptodan on 2009-08-24
I am talking about globally not via Firefox.

As in no IPv6 what so ever in the kernel loading up.

I wished that the kernel writers would disable that and allow it to be enabled via apt-get.

> **tad1073 said:**
> ipv6 is no longer modular, to disable it you would have to rebuild your kernel.

Why did they make it part of the Kernel to begin with.  I am still using IPv4 and my networking equipment uses IPv4 and there is no need for my server to have ipv6 enabled in the kernel.  I wished the kernel writers would stop enabling ipv6 by default its rather annoying and rather pointless when your computer is behind a router with a subnet of 192.168.0.0/16 available and at your disposal.  It should be an option when you are doing apt-get and it downloads the kernel, and asks you "Would you like to enable IPv6?" Yes or No.

---

### Post by Bucky Ball on 2009-08-24
Firefox is the major culprit for using it. You will notice a fractionally better speed possibly and yes, I realise you are ideally looking to not start it at boot. :)

---

### Post by cryptodan on 2009-08-24
It takes me like 15 seconds to log in to my server via SSH with IPv6 enabled.

---

### Post by dmizer on 2009-08-24
> **cryptodan said:**
> It takes me like 15 seconds to log in to my server via SSH with IPv6 enabled.

Here's the bug: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218)

---

### Post by dmizer on 2009-08-24
A bit more research indicates that this may fix your problem:

```
echo 1 >/proc/sys/net/ipv6/conf/all/disable_ipv6
```

You'll have to do that from a root prompt. To get a root prompt, just type:
```
sudo -i
```

---

### Post by cryptodan on 2009-08-24
> **dmizer said:**
> Here's the bug: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/313218)

Its no bug its an issue with IPv6 being automatically enabled by default which is pointless.  I know its the future, but I shouldn't have it forced down my throat.  With Windows I just uncheck a box stating I don't want IPv6 and that is it.

This slowness is also evident in Fedora 5.

> **dmizer said:**
> A bit more research indicates that this may fix your problem:

```
echo 1 >/proc/sys/net/ipv6/conf/all/disable_ipv6
```

You'll have to do that from a root prompt. To get a root prompt, just type:
```
sudo -i
```

That does not work, I tried and it defaulted back to normal after a reboot.

They need to disable IPv6 in all kernels and make it optional for those of us who want to use IPv4.  

Or someone needs to compile an IPv4 only kernel and call it *-ipv4-only.

---

### Post by dmizer on 2009-08-24
> **cryptodan said:**
> That does not work, I tried and it defaulted back to normal after a reboot.

Try this then: [http://ubuntuforums.org/showpost.php?p=7270740&postcount=6](http://ubuntuforums.org/showpost.php?p=7270740&postcount=6)

I used to have crappy networking equipment which didn't work well with ipv6, so I feel your pain. IPv6 works fine on my new equipment so it's not a problem anymore and I can't test these solutions. However, I am aware that a problem exists, so I'm interested in finding a solution.

That may not work anyway. Here's another possible solution (I think it's basically installing a precompiled IPv4 only kernel): [http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

### Post by cryptodan on 2009-08-24
> **dmizer said:**
> Try this then: [http://ubuntuforums.org/showpost.php?p=7270740&postcount=6](http://ubuntuforums.org/showpost.php?p=7270740&postcount=6)

I used to have crappy networking equipment which didn't work well with ipv6, so I feel your pain. IPv6 works fine on my new equipment so it's not a problem anymore and I can't test these solutions. However, I am aware that a problem exists, so I'm interested in finding a solution.

That may not work anyway. Here's another possible solution (I think it's basically installing a precompiled IPv4 only kernel): [http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

My Router/Modem is the Actiontec MI424WR and its relatively new.

The solution would be to disable IPv6 in the kernel and the kernel creaters stop forcing it down our throats.  I can only see IPv6 in corporate environments and not in homes.  Whatever happened to "CHOICE"?

I will try the above.

---

### Post by dmizer on 2009-08-24
> **cryptodan said:**
> My Router/Modem is the Actiontec MI424WR and its relatively new.

In my case, the problem was with my networking equipment (it was new too, just crappy). Your problem may be with your service provider. IPv6 issues can happen at multiple levels of networking.

Plenty of people have voiced their opinion on this (including me), and the fact is that it's in the kernel and it's there to stay. The bug report indicates that a fix has been released, if you have the latest kernel and you're still experiencing problems it might help if you posted in the bug report.

---

### Post by cryptodan on 2009-08-24
> **dmizer said:**
> In my case, the problem was with my networking equipment (it was new too, just crappy). Your problem may be with your service provider. IPv6 issues can happen at multiple levels of networking.

Plenty of people have voiced their opinion on this (including me), and the fact is that it's in the kernel and it's there to stay. The bug report indicates that a fix has been released, if you have the latest kernel and you're still experiencing problems it might help if you posted in the bug report.

This has nothing to do with my ISP, it has everything to do via LAN.  My ISP doesnt even belong in the picture as I am using a switch on my lan.  My server is 2 feet from me.  I can kick it if I wanted too.

root@capricorn:/etc# uname -a
Linux capricorn 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

root@capricorn:/etc# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:b3:8c:00:c0
inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::202:b3ff:fe8c:c0/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:128553 errors:0 dropped:0 overruns:0 frame:0
TX packets:71266 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:14557423 (14.5 MB)  TX bytes:15505716 (15.5 MB)

---

### Post by dmizer on 2009-08-24
If it's on your local network, and your servers are Linux, then your problem probably isn't IPv6.

Are you accessing your SSH server via IP or host name? If host name, do you have a local DNS server, and is your Ubuntu client correctly configured to use the local DNS server?

I recognize that IPv6 in the kernel is a problem. It was a problem for me, now it's not, but I do know that there are many network problems that can show the same symptoms as IPv6 routing issues.

---

### Post by cryptodan on 2009-08-24
> **dmizer said:**
> If it's on your local network, and your servers are Linux, then your problem probably isn't IPv6.

Are you accessing your SSH server via IP or host name? If host name, do you have a local DNS server, and is your Ubuntu client correctly configured to use the local DNS server?

I recognize that IPv6 in the kernel is a problem. It was a problem for me, now it's not, but I do know that there are many network problems that can show the same symptoms as IPv6 routing issues.

I access all my servers via IP address, as they are all statically assigned.

This problem is also evident with WinSCP as well.  My client is properly configured.

---

### Post by dmizer on 2009-08-24
If you're accessing your SSH servers via an IPv4 address, how is it that IPv6 can be considered a problem?

---

### Post by cryptodan on 2009-08-24
> **dmizer said:**
> If you're accessing your SSH servers via an IPv4 address, how is it that IPv6 can be considered a problem?

All I know is when I had it disabled on a FreeBSD, Fedora, and another Ubuntu box logging in was quite instant and not nearly as slow as it is with IPv6 enabled by default.  

This is the system that I use for my server: [http://www.cryptodan.net/sys/index.php?disp=dynamic](http://www.cryptodan.net/sys/index.php?disp=dynamic)

---

### Post by dmizer on 2009-08-24
Well, if you're accessing the machine directly by IPv4, then IPv6 is never going to enter the picture. IPv6 would only be a possible problem if you're trying to connect using a hostname, and usually only a problem on the WAN rather than the LAN.

There are several discussons regarding slow SSH login prompts. Have you tried any of those possible solutions? Take a look here: [http://ubuntuforums.org/showthread.php?t=361262](http://ubuntuforums.org/showthread.php?t=361262)

Why is IPv6 a problem at all? Because Ubuntu is trying to query an IPv6 host when either networking equipment or ISPs aren't handling it correctly. When you have an IPv6 problem, you get slow DNS resolution times because you have to wait for the IPv6 DNS query to timeout before it rolls over to IPv4.

---

### Post by cryptodan on 2009-08-24
> **dmizer said:**
> Well, if you're accessing the machine directly by IPv4, then IPv6 is never going to enter the picture. IPv6 would only be a possible problem if you're trying to connect using a hostname, and usually only a problem on the WAN rather than the LAN.

There are several discussons regarding slow SSH login prompts. Have you tried any of those possible solutions? Take a look here: [http://ubuntuforums.org/showthread.php?t=361262](http://ubuntuforums.org/showthread.php?t=361262)


Why is it faster when I disable IPv6 completely?

---

### Post by dmizer on 2009-08-25
> **cryptodan said:**
> Why is it faster when I disable IPv6 completely?

Well, by all means ... if disabling IPv6 fixes your problem, install the IPv4 kernel as outlined a few posts up.

But the IPv6 problem is related to DNS, not the IP stack.

---

### Post by cryptodan on 2009-08-25
I would like to apologize to everyone for my shear ignorance, and state that:

UseDNS no

Solved my issue.

But I am still baffled that with disabling IPv6 the issue went away.

---

### Post by dmizer on 2009-08-25
> **cryptodan said:**
> UseDNS no

Solved my issue.

That's fantastic!

---

