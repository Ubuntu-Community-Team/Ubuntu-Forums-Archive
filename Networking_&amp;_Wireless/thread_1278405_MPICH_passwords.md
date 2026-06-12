---
title: "MPICH passwords"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by ndyguy on 2009-09-29
I'm having an issue finishing the install on mpich-bin.  It installed, I can run a sample program, but if I have n processes, the shell asks me n-1 times for my password.  Is this normal, or is there a way to turn this off?  Here's a sample:
```

ndyguy@computer:~/Desktop$ mpirun -np 4 a.out
ndyguy@localhost's password: 
ndyguy@localhost's password: 
ndyguy@localhost's password: 
Hi there from 0 of 4
Hi there from 3 of 4
Hi there from 2 of 4
Hi there from 1 of 4
ndyguy@computer:~/Desktop$

```

---

