---
title: "customizing kernel 2.6.31 and building"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by karthikeyan.murali on 2010-11-15
I was trying to compile GNU linux 2.6.31 's source code to write my own protcol using experimental protocol number 253.

To start with i would llike to add a delay_interval in the udp hdr  and call it as EDP(Experimental Datagram Protocol)  .This EDP protocol  should drop the ip packets which is moved upward after delay_interval  and those which are coming before the delay_interval should be passed to  socket layer.

My Environment:
1. ubuntu lucid lynx.

Things done:
1.Source code compiled .
2.modified grub 
3.Booted on 2.6.31 

MyGoal

struct edp {                               /* Experimental Datagram Protocol */
  u_int16_t    source;                  /* Source port.                       */
  u_int16_t    dest;                    /* Destination port.                  */
  u_int16_t    len;                     /*  length. */
  u_int16_t    check;                   /* checksum.                 */
  u_int16_t   timer_delay;                   /* checksum.                 */
};

1. To add a timer using function pointer (delay_interval a field specified in udphdr  ) 

Please give your suggestions and help me in completing this task,

---

