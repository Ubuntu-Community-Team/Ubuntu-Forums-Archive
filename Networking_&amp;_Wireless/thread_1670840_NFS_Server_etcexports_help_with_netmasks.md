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

If it possible to achieve it with netmasks in the exports file of the NFS server? I suppose that it should have an entry like this: 

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

