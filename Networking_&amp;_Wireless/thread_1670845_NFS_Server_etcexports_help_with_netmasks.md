---
title: "NFS Server: /etc/exports: help with netmasks"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by frafu on 2011-01-19
Hi, 

I have a NFS server running Ubuntu lucid sever edition in my private network.

I want the following: 

- The machines whose ip ends with a number between 1 and 15 should have rw access to the server.

- The machines whose ip ends with a number between 16 and 31 should not have access to the server.

- The machines whose ip ends with a number greater than 31 should have ro access to the server.

Is it possible to achieve it with netmasks in the exports file of the NFS server? I suppose that it should have an entry like this: 

```

/media/Share 192.168.1.0/255.255.255.YYY(rw,no_root_squash,no_subtree_check) 192.168.1.0/255.255.255.ZZZ(ro,all_squash)

```

I suppose that YYY should be 15 as it covers the numbers 1 to 15 in binary format. (The pool of rw client machines)

But I am not sure what number to set for ZZZ. (the pool with the ro client machines) Should I set it to 223 (255-32=223)? Would 223 not also include the rw client machines as 223 in binary format is 11011111 and thus the bits covering 1 to 15 in binary format are also included!?

Thanks in advance for any suggestion or explanation.

---

### Post by frafu on 2011-01-19
The following is not what I was looking for, but it allows me at least to give rw accesto specific clients and only ro access to the rest:

```

/media/Share 192.168.1.3(rw,no_root_squash,no_subtree_check) 192.168.1.0/24(ro,all_squash)

```

I am aware that 192.168.1.3 is also included in 192.168.1.0/24, but it seems to work.  

Thus, I wonder whether the options of clients given by their exact ip have priority to the options of the same client given in a mask. 

Could anybody please confirm that it is a lecit behaviour and not any side effect of some bug?

Thanks in advance.

---

### Post by frafu on 2011-01-19
The following is not what I was looking for, but it allows me at least to give rw accesto specific clients and only ro access to the rest:

```

/media/Share 192.168.1.3(rw,no_root_squash,no_subtree_check) 192.168.1.0/24(ro,all_squash)

```

I am aware that 192.168.1.3 is also included in 192.168.1.0/24, but it seems to work.  

Thus, I wonder whether the options of clients given by their exact ip have priority to the options of the same client given in a mask. 

Could anybody please confirm that it is a lecit behaviour and not any side effect of some bug?

Thanks in advance.

---

### Post by frafu on 2011-01-19
The following is not what I was looking for, but it allows me at least to give rw accesto specific clients and only ro access to the rest:

```

/media/Share 192.168.1.3(rw,no_root_squash,no_subtree_check) 192.168.1.0/24(ro,all_squash)

```

I am aware that 192.168.1.3 is also included in 192.168.1.0/24, but it seems to work.  

Thus, I wonder whether the options of clients given by their exact ip have priority to the options of the same client given in a mask. 

Could anybody please confirm that it is a lecit behaviour and not any side effect of some bug?

Thanks in advance.

---

### Post by frafu on 2011-01-19
The following is not what I was looking for, but it allows me at least to give rw accesto specific clients and only ro access to the rest:

```

/media/Share 192.168.1.3(rw,no_root_squash,no_subtree_check) 192.168.1.0/24(ro,all_squash)

```

I am aware that 192.168.1.3 is also included in 192.168.1.0/24, but it seems to work.  

Thus, I wonder whether the options of clients given by their exact ip have priority to the options of the same client given in a mask. 

Could anybody please confirm that it is a lecit behaviour and not any side effect of some bug?

Thanks in advance.

---

### Post by frafu on 2011-01-19
The following is not what I was looking for, but it allows me at least to give rw accesto specific clients and only ro access to the rest:

```

/media/Share 192.168.1.3(rw,no_root_squash,no_subtree_check) 192.168.1.0/24(ro,all_squash)

```

I am aware that 192.168.1.3 is also included in 192.168.1.0/24, but it seems to work.  

Thus, I wonder whether the options of clients given by their exact ip have priority to the options of the same client given in a mask. 

Could anybody please confirm that it is a lecit behaviour and not any side effect of some bug?

Thanks in advance.

---

### Post by gmargo on 2011-01-19
It's possible, and slightly easier if you relax your first requirement to include addresses from .0 instead of .1.

Here's a table of address/cidr and the associated IP ranges.  With this reference it should be easy to craft your /etc/exports line.  You can see that 0-15 is one group, 16-31 is another group, and then 32-255 takes three groups.

```

192.168.1.0/28                  192.168.1.0   - 192.168.1.15
192.168.1.16/28                 192.168.1.16  - 192.168.1.31
192.168.1.32/27                 192.168.1.32  - 192.168.1.63
192.168.1.64/26                 192.168.1.64  - 192.168.1.127
192.168.1.128/25                192.168.1.128 - 192.168.1.255

```I generated these on the command line using the **ipcalc(1)** and **sipcalc(1)** tools.

---

### Post by frafu on 2011-01-20
First of all, sorry for my multiple postings above. The browser kept telling me that there was an error or seemed to hang; so I kept sending the message. 

@gmargo

Thanks for your reply. I have a question regarding your solution about the base and broadcast ips:

I read that for a /24 mask, xxx.xxx.xxx.255 is the broadcast ip of the subnet. Does this mean that in your solution, the ips ending with 15, 31, 63, 127, 255 are all broadcast ips? 

Moreover, and probably more important: can I use these broadcast ips for client machines or do I have to configure my router to not assign these ips per dhcp to machines? 

And what about the base ips ending with 0, 16, 32, 64, 128? Can I use these for client machines? 

Cheers, 

Francesco.

---

### Post by gmargo on 2011-01-20
The appropriate IP address for broadcast is entirely determined by the configuration of your network interface.  So for this network interface the config is 192.168.1.0/24 (aka 192.168.1.0/255.255.255.0) and so broadcast is 192.168.1.255.

Using other masks in /etc/exports only affects the NFS server - you're effectively building a permissions lookup table for the NFS server.  Anything you put in /etc/exports will not "pollute" the network interface configuration. So the entire address range (or from .1 to .254 anyway) can be safely used for host addresses.

---

### Post by frafu on 2011-01-20
Thanks gmargo for your help and explanations.  :-)

For others that might be interested, here is the line that I am now using in /etc/exports:

```

/media/Share 192.168.1.0/28(rw,no_root_squash) 192.168.1.32/27(ro,all_squash) 192.168.1.64/26(ro,all_squash) 192.168.1.128/25(ro,all_squash)

```

In other words: 
192.168.1.0   - 192.168.1.15: rw access
192.168.1.16  - 192.168.1.31: no access
192.168.1.32  - 192.168.1.255: only ro access

Cheers, 

Francesco

---

