---
title: "shell script to access computers via ssh?"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by helstreak on 2009-05-29
I have 3 computers.  1 computer is the master, the other 2 are for jobs.  I do not have job management software on them so what I am wondering is if it is possible to write a shell script that will access the 2 job computers and tell them what to do?  The 2 computers can be accessed via ssh but a password is needed.  Can you supply the password through the shell script?

I guess what I would like to do in pseudocode is:

script:
    ssh compute-node-1
    password-for compute-node-1
    compute-node-1 start some job and run

    ssh compute-node-2
    password-for compute-node-2
    compute-node-2 start some job and run

I don't want to download and job management software, I'm just curious if it could be done from a script :)

Thank you :)

---

