---
title: "Nortel VPN Client 3.6.1 no longer compiles after upgrade to 9.10"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by bdudek on 2009-11-10
Hello,

Is anyone else having a problem with the Nortel VPN software compiling after the 9.10 upgrade? I am getting the errors below and don't know how to fix them as I am not a developer. Is there anyone that can help me with this?

bdudek@bruce:~/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6$ sudo make
cd src && make all
make[1]: Entering directory `/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src'
cd k2.6 && make
make[2]: Entering directory `/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6'
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.o
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:142: error: ‘readq’ redeclared as different kind of symbol
/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/io.h:56: note: previous definition of ‘readq’ was here
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c: In function ‘nl_ip_rcv’:
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:553: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c: In function ‘nl_skb_dup’:
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:696: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:696: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c: In function ‘nl_skb_hdr_copy’:
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:730: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:730: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c: In function ‘nl_send_skb’:
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:813: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:814: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:815: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:817: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:820: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c: In function ‘update_inner_route’:
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:850: error: ‘struct sk_buff’ has no member named ‘dst’
/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.c:851: error: ‘struct sk_buff’ has no member named ‘dst’
make[4]: *** [/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6/linux_wrapper.o] Error 1
make[3]: *** [_module_/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bdudek/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6/src'
make: *** [all] Error 2
bdudek@bruce:~/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6$ uname -a
Linux bruce 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
bdudek@bruce:~/Software/Nortel/Version-3.6.1/cvc_linux-gcc3-3.6$ 

Bruce Dudek

---

### Post by oreomike on 2010-01-16
same problem with VPN Client 3.5...

```
 CC [M]  src/k2.6/linux_wrapper.o
src/k2.6/linux_wrapper.c: In function ‘ip_route_output’:
src/k2.6/linux_wrapper.c:129: error: too few arguments to function ‘ip_route_output_key’
src/k2.6/linux_wrapper.c: At top level:
src/k2.6/linux_wrapper.c:133: error: ‘readq’ redeclared as different kind of symbol
/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/io.h:51: note: previous definition of ‘readq’ was here
src/k2.6/linux_wrapper.c: In function ‘register_nl_netfilter’:
src/k2.6/linux_wrapper.c:267: error: ‘NF_IP_LOCAL_IN’ undeclared (first use in this function)
src/k2.6/linux_wrapper.c:267: error: (Each undeclared identifier is reported only once
src/k2.6/linux_wrapper.c:267: error: for each function it appears in.)
src/k2.6/linux_wrapper.c:274: error: ‘NF_IP_LOCAL_OUT’ undeclared (first use in this function)
src/k2.6/linux_wrapper.c: In function ‘nl_ip_rcv’:
src/k2.6/linux_wrapper.c:524: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c: At top level:
src/k2.6/linux_wrapper.c:560: error: conflicting types for ‘dev_name’
include/linux/device.h:422: note: previous definition of ‘dev_name’ was here
src/k2.6/linux_wrapper.c: In function ‘nl_skb_dup’:
src/k2.6/linux_wrapper.c:654: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c:654: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c: In function ‘nl_skb_hdr_copy’:
src/k2.6/linux_wrapper.c:688: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c:688: error: ‘struct sk_buff’ has no member named ‘dst’
/home/mike/vpn/src/k2.6/linux_wrapper.c: In function ‘nl_send_skb’:
src/k2.6/linux_wrapper.c:757: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c:758: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c:759: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c:761: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c:764: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c: In function ‘nl_data_len’:
src/k2.6/linux_wrapper.c:785: error: invalid operands to binary - (have ‘sk_buff_data_t’ and ‘unsigned char *’)
src/k2.6/linux_wrapper.c: In function ‘update_inner_route’:
src/k2.6/linux_wrapper.c:791: error: ‘struct sk_buff’ has no member named ‘dst’
src/k2.6/linux_wrapper.c:792: error: ‘struct sk_buff’ has no member named ‘dst’

```

---

### Post by Gibby13 on 2010-03-16
Anyone get this working yet?

---

### Post by gmoore777 on 2010-06-29
I also cannot get the 3.6 version working on 64-bit LucidLynx.
(Aside: on the apani website, I only see 3.6. I do not see any reference to 3.6.1)

I was able to get past the compile problems with some edits to the source code (that I'm sure are logically wrong), but during the
linking step I get:
    ld: Relocatable linking with relocations from format elf32-i386
    (.../cvc_linux-gcc3-3.6/src/k2.6/../libmishim-2.6.a(linux_int_26.o))
    to format elf64-x86-64 (.../cvc_linux-gcc3-3.6/src/k2.6/mishim.o)
    is not supported

So my newly compiled 64-bit .o's cannot be linked with other
32-bit Apani-supplied objects. (understandable)

and if I force the compile to be 32 bit, the compilation fails
with:
    error: code model kernel not supported in the 32 bit mode

So, the Apani software is only 32-bit. I don't see a 64-bit
version to choose from, from their download evaluation site.
So, it looks impossible to get the 32-bit Apani 3.6 compiled
and working on a 64-bit system.
But maybe you others on 32-bit LucidLynx can get a bit further.

Here were my edits to linux_wrapper.c

142c142
< DECLARE_WAIT_QUEUE_HEAD(readq);
---
> // DECLARE_WAIT_QUEUE_HEAD(readq);
553c553
<   if (skb->dst == NULL)
---
>   if (skb->_skb_dst == NULL)
696c696
<     new_skb->dst = dst_clone(skb->dst);
---
>     new_skb->_skb_dst = dst_clone(skb->_skb_dst);
730c730
<   skb_to->dst = skb_from->dst;
---
>   skb_to->_skb_dst = skb_from->_skb_dst;
813,815c813,815
<     if (skb->dst != NULL);
<       dst_release(skb->dst);
<     skb->dst = &rt->u.dst;
---
>     if (skb->_skb_dst != NULL);
>       dst_release(skb->_skb_dst);
>     skb->_skb_dst = &rt->u.dst;
817c817
<     if (skb->dst)
---
>     if (skb->_skb_dst)
820c820
<       skb->dst->output(skb);
---
>      //  skb->_skb_dst->output(&skb);
822c822
<       skb->dst->output(&skb);
---
>       // skb->_skb_dst->output(&skb);
841c841
< int nl_data_len (struct sk_buff *skb)
---
> unsigned int nl_data_len (struct sk_buff *skb)
843c843,847
<   return (skb->tail - skb->data);
---
>   return ((unsigned char *)skb->tail - skb->data);
>
850,851c854,855
<   dst_release(skb->dst);
<   skb->dst = NULL;
---
>   dst_release(skb->_skb_dst);
>   skb->_skb_dst = NULL;

I wouldn't be surprised during runtime, that this crashes,
since the edits may not make sense, although they satisfy the
compiler.

---

### Post by oreomike on 2010-06-29
This sounds like a good enough reason to downgrade to 32bit.  It is the only thing that is keeping me from booting into Linux.  now only if I could return my Windows 7 disc for a refund...

---

