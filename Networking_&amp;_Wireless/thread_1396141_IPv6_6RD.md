---
title: "IPv6 6RD"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by 100man on 2010-02-01
Hi everyone,

I wasn't sure where to post this question (networking or upgrade/install).

I've been looking into playing around with 6rd IPv6 in IPv4 tunneling in the latest kernel 2.6.33-rc6 .  I went ahead and installed it on my Jaunty machine.  The install went fine but when I try to setup the 6rd tunnel using the following from: [http://www.ripe.net/ripe/meetings/ripe-58/content/presentations/ipv6-free.pdf](http://www.ripe.net/ripe/meetings/ripe-58/content/presentations/ipv6-free.pdf)

# ip addr add 212.27.58.6/30 dev eth2
# ip route add default via 212.27.58.5 dev eth2
# ip link set dev eth2 up

# ip -6 addr add 2a01:e00:1:2::2/126 dev eth3
# ip -6 route add default via 2a01:e00:1:2::1 dev eth3
# ip link set dev eth3 up

# ip addr add 192.88.99.201/32 dev dummy0
# ip link set dev dummy0 up
# ip tunnel add sit1 mode sit local 192.88.99.201 \
6rd_prefix 2a01:e30::/28 ttl 64  <--------------------Fails on keyword 6rd_prefix 

# ip -6 addr add 2a01:e00:1:2::2/126 dev sit1
# ip -6 route add 2a01:0e30::/28 via 2a01:e00:1:2::1 dev sit1
# ip link set dev sit1 up

It fails on the 6rd_prefix keyword most likely because the ip command has no idea what that is.

I looked at the 2.6.33-rc6 kernel source and matched it up with all the changes found in this patch:
[http://patchwork.ozlabs.org/patch/34121/](http://patchwork.ozlabs.org/patch/34121/)

These files were OK:
[FONT=monospace]
[/FONT]include/linux/if_tunnel.h [FONT=monospace]
[/FONT]include/net/ipip.h       [FONT=monospace]
[/FONT]net/ipv6/Kconfig         [FONT=monospace]

But I couldn't find this one at all in my usr/src directory 

[/FONT]net/ipv6/sit.c    

The kernel was obtained from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Any ideas?  Is the pre-compiled mainline kernel the same as the kernel found on kernel.org?

Thanks for looking.

---

### Post by sylware on 2010-02-24
Your IAP must be Free (in France). I don't know if other IAPs around the globe are following Free tracks.
Since I have now a custom ADSL2+ modem and my IAP is Free, I would like to configure manually 6rd for some computers on my domestic LAN (FTTH will have native IPv6).

---

### Post by sanderj on 2010-02-28
According to [http://lxr.linux.no/#linux+v2.6.33/net/ipv6/Kconfig#L173](http://lxr.linux.no/#linux+v2.6.33/net/ipv6/Kconfig#L173) , 6rd defaults to 'n' (No).

I don't know if the Ubuntu maintainers have changed that to get 6rd into the Ubuntu kernel.

So, maybe you have to recompile yourself...

Apart from that, I guess you will need 6rd tunnel provider ...

---

### Post by digitalsushi on 2010-03-09
6rd extends 6to4 to allow for native v6 prefixes.  This is so that an ISP can trust its packets will come back.  ISP-A is terrified ISP-B's 6to4 relay will drop packets going through ISP-B meant for ISP-A, but such is the nature of anycast routing.  ISPs arent so interested in this hope-for-the-best model and so 6rd allows everyone to have a unique prefix, eliminating the need to trust that your competitor will follow the spec and respect foreign packets.  Anyways, the nice thing is that 6to4 is just a special case of 6rd, and 6to4 blindly forwards packets for everyone, so we can just use the 6to4 relay servers to test our spiffy new 6rd capabilities in linux.

You must patch your userland tools to access the 6rd features in the newer kernels.  Get the patch Alexandre Cassen wrote at [http://patchwork.ozlabs.org/patch/41255/](http://patchwork.ozlabs.org/patch/41255/) and patch it against the iproute2-2.6.31 package.  Mine patched cleanly.  Rebuild it and install it.  You'll now have access to the 6rd features in the kernel.

It took me a while to realize that sit0 has some magical linux properties, so just skip over it to sit1, which works fine.  If someone wants to explain why sit0 is magic, you'd be my hero.

```
ip tunnel add sit1 mode sit ttl 64 remote any local $wan_ipv4_address
ip link set dev sit1 up
ip tunnel 6rd dev sit1 6rd-prefix 2002::/16
ip -6 route add default via ::192.88.99.1 dev sit1 metric 1
```

I'm announcing this prefix on my lan as 2002:$wan_ipv4_address_in_hex:0::/64.  Packets definitely go through the regular 6to4 relay into a native v6 host elsewhere.

BTW, Comcast is going to beta this this year.  It's all over the news.  They have a beta list you can sign up on.  *crosses fingers*

---

### Post by sanderj on 2010-03-09
> **digitalsushi said:**
> 
<snip>

You must patch your userland tools to access the 6rd features in the newer kernels.  Get the patch Alexandre Cassen wrote at [http://patchwork.ozlabs.org/patch/41255/](http://patchwork.ozlabs.org/patch/41255/) and patch it against the iproute2-2.6.31 package.  Mine patched cleanly.  Rebuild it and install it.  You'll now have access to the 6rd features in the kernel.


AFAIK, you need Linux kernel 2.6.33, don't you? Furthermore, I believe 6rd is "default=n", so you need to recompile with 6rd in it.

So, have you done the above? On Ubuntu?


> **digitalsushi said:**
> 
It took me a while to realize that sit0 has some magical linux properties, so just skip over it to sit1, which works fine.  If someone wants to explain why sit0 is magic, you'd be my hero.



sit0 used to be a normal tunnel, which I used for 6over4. That changed a few years ago, and then you had to use sit1.

Maybe this is a pointer, as "sit0" is mentioned on it's own:

[http://lxr.linux.no/#linux+v2.6.33/net/ipv6/sit.c#L1175](http://lxr.linux.no/#linux+v2.6.33/net/ipv6/sit.c#L1175)

And now I read IPv6 guru Jeroen Massar saying "Using sit0/sit1 interfaces is deprecated and it looks a lot like you have a lot of weird things in your routing tables."

---

### Post by digitalsushi on 2010-03-10
> **sanderj said:**
> AFAIK, you need Linux kernel 2.6.33, don't you? Furthermore, I believe 6rd is "default=n", so you need to recompile with 6rd in it.

So, have you done the above? On Ubuntu?

Yup.  But the patch for 6rd applies against the iproute2 for 2.6.31.  So 2.6.33 kernel, 2.6.31 iproute2.  It works great.  I didn't use ubuntu's kernel.  I just grabbed a vanilla one from kernel.org.

> 

sit0 used to be a normal tunnel, which I used for 6over4. That changed a few years ago, and then you had to use sit1.

Maybe this is a pointer, as "sit0" is mentioned on it's own:

[http://lxr.linux.no/#linux+v2.6.33/net/ipv6/sit.c#L1175](http://lxr.linux.no/#linux+v2.6.33/net/ipv6/sit.c#L1175)

And now I read IPv6 guru Jeroen Massar saying "Using sit0/sit1 interfaces is deprecated and it looks a lot like you have a lot of weird things in your routing tables."He's usually incredibly terse but also almost always correct.  Still, my config works, so sit1 works, for now anyways.

---

### Post by digitalsushi on 2010-03-12
Actually, the patch works great against the earlier version of the pre-spec, but [http://tools.ietf.org/html/draft-ietf-softwire-ipv6-6rd-07](http://tools.ietf.org/html/draft-ietf-softwire-ipv6-6rd-07) has added the ability to compress the first n bits of the v4 wan address.  The patch does not currently support this.  It's all experimental though so things will catch up when they catch up.

---

