---
title: "unable to access linux machines in network"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by gaurav sontakke on 2009-09-01
Hi All 
                            I have installed Ubuntu 9.04 on 3 computers I already have one opensuse 11 machine and one fedora 10 machine and some windows machines.
                              I am able to access my files from windows to ubuntu but I am unable to access opensuse or fedora to my ubuntu and vice versa..
               It even not shows these machine in my network,
And whenever I try to access by issuing command 

        sftp://ip 

It gives me error 

           Access was denied 


What should be the problem???

                        Thanking You



Regards
Gaurav Sontakke

---

### Post by gaurav sontakke on 2009-09-07
any help will be appreciated ...

         Thanking You in advance..








Regards
GS

---

### Post by uncle-c on 2009-09-08
Gaurav,

Can you ping to either suse / fedora machines from xp and ubuntu ?

---

### Post by red_michael on 2009-09-08
I've exactly the same problem. I can ping all my machines

---

### Post by uncle-c on 2009-09-08
Have you guys checked to see if machines are protected by a firewall and that it may be blocking traffic through port 22 , the sftp port ?

---

### Post by red_michael on 2009-09-08
> **uncle-c said:**
> Have you guys checked to see if machines are protected by a firewall and that it may be blocking traffic through port 22 , the sftp port ?

Well I don't have issues with sftp or ssh but only with samba. I don't have any firewall installed.

---

### Post by jamest09 on 2009-09-08
> **gaurav sontakke said:**
> Hi All 
                            I have installed Ubuntu 9.04 on 3 computers I already have one opensuse 11 machine and one fedora 10 machine and some windows machines.
                              I am able to access my files from windows to ubuntu but I am unable to access opensuse or fedora to my ubuntu and vice versa..
               It even not shows these machine in my network,
And whenever I try to access by issuing command 

        **sftp://ip **

It gives me error 

           Access was denied 


What should be the problem???

                        Thanking You



Regards
Gaurav Sontakke


Try 
sftp://user@ip.add.ress

---

