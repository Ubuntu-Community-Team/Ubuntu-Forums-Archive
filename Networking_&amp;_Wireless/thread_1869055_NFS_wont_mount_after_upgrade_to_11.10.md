---
title: "NFS wont mount after upgrade to 11.10"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by john_duff on 2011-10-25
Hi Forum

                                I updated to Oneiric a few days ago and my nfs shares will  not connect. They always have before, with Natty on this and other computers  on my network.

  The error message is:
  mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd. 
mount.nfs: an incorrect mount option was specified 

So i did a clean install to 11.10, copying in the fstab etc that worked on  Natty on this box, but get the same error as i did after the upgrade.

No auto mount on boot, and  when i do for example sudo mount /nas/mydocs i get the same error.

  Have tried adding -o nolock to the fstab with no success

  fstab has lines like this, all working before upgrade, and still working on the other machines on the network running Natty
192.168.6.15:/johnsstore /home/john/nas/mydocs nfs rw,auto 

If i do sudo start statd i get:
start: Job is already running: statd 

     rpcinfo gives:
program version netid     address                service    owner 
    100000    4    tcp6      ::.0.111               portmapper superuser 
    100000    3    tcp6      ::.0.111               portmapper superuser     
100000    4    udp6      ::.0.111               portmapper superuser     
100000    3    udp6      ::.0.111               portmapper superuser     
100000    4    tcp       0.0.0.0.0.111          portmapper superuser 
    100000    3    tcp       0.0.0.0.0.111          portmapper superuser 
    100000    2    tcp       0.0.0.0.0.111          portmapper superuser     
100000    4    udp       0.0.0.0.0.111          portmapper superuser     
100000    3    udp       0.0.0.0.0.111          portmapper superuser 
    100000    2    udp       0.0.0.0.0.111          portmapper superuser     
100000    4    local     /run/rpcbind.sock      portmapper superuser 
    100000    3    local     /run/rpcbind.sock      portmapper superuser 
    100024    1    udp       0.0.0.0.138.56         status     114     
100024    1    tcp       0.0.0.0.228.44         status     114     
100024    1    udp6      ::.236.85              status     114     
100024    1    tcp6      ::.142.26              status     114       

Have tried all the possible fixes i can find via forums and google with no luck.
Any ideas folks? Return to Natty?

---

### Post by robertmaynord on 2011-11-01
Same problem here, with no solution.  I reinstalled 11.04 and it works fine.

---

### Post by nickbnf on 2011-11-01
I am having the same problem and am trying to get to the bottom of it now.

So a question for the two of you: what is your KDC (and NFS) server running?

I am connecting to a Debian lenny server (running both KDC and NFS).

---

### Post by ene_dene on 2011-11-03
Same problem here. It will not mount at startup, but if I go to directory where it should be mounted and exit the directory then it does get mounted. I've tried this in Xubuntu and Kubuntu, but not in Ubuntu, but I guess you guys have.
```
sudo mount -a 
```
Also works without errors.
Mine was not an upgrade but a fresh install.

---

