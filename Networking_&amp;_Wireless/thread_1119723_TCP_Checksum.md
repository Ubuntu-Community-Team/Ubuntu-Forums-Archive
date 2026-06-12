---
title: "TCP Checksum"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by sarannmr on 2009-04-08
I have a netfilter hook that changes some of the contents of the tcp header for all packets that fall in NF_IP_FORWARD category. Before passing on the packet, I need to of course calculate the TCP and IP checksums again, but I am unable to get the TCP checksums right.
Here are a few of the things i tried.
tcph->check = tcp_v4_check(len, iph->saddr, iph->daddr,
csum_partial((char *)tcph,
tcph->doff << 2,
skb->csum));

tcph->check = csum_tcpudp_magic(iph->saddr, iph->daddr,tlen, iph->protocol,skb_ch ecksum(skb, skb_transport_offset(skb), tlen, 0));
(I found these being used in other places within the kernel )

I'd really appreciate it if someone can tell me how I could do a TCP checksum.
( IP checksumming works just fine using ip_fast_sum )

---

