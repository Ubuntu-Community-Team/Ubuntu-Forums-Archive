---
title: "Accessing MAC header from a network packet"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by stormshadow on 2009-03-20
I am trying to access and obtain the destination MAC address of a captured network packet. I am using the following kernel module which uses netfilter hooks to process the packets.

```
#define __KERNEL__
#define MODULE
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/netfilter.h>
#include <linux/netfilter_ipv4.h>
static struct nf_hook_ops netfilter_ops_in; /* NF_IP_PRE_ROUTING */
/* Function prototype in <linux/netfilter> */
unsigned int main_hook(unsigned int hooknum,  
                  struct sk_buff **skb,
                  const struct net_device *in,
                  const struct net_device *out,
                  int (*okfn)(struct sk_buff*))
{
struct sk_buff* sk;
sk = (*skb);

unsigned char* rawp;
rawp = sk->mac.raw; //Accessing the MAC Header
return NF_ACCEPT;
}
int init_module()
{
        netfilter_ops_in.hook                   =       main_hook;
        netfilter_ops_in.pf                     =       PF_INET;
        netfilter_ops_in.hooknum                =       NF_IP_PRE_ROUTING;
        netfilter_ops_in.priority               =       NF_IP_PRI_FIRST;
      

        nf_register_hook(&netfilter_ops_in); /* register NF_IP_PRE_ROUTING hook */
      
return 0;
}
void cleanup_module()
{
nf_unregister_hook(&netfilter_ops_in); /*unregister NF_IP_PRE_ROUTING hook*/
}

```

When I compile this I get and error saying that the 'struct sk_buff' has no member called 'mac'. I need the mac header in order to obtain the destination mac address of an incoming packet.

Can anyone suggest what is wrong here ?

---

