---
title: "insserv: command not found and /etc/sysconfig directory in ubuntu"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by mhfida on 2013-06-17
Hi, 
I am trying to install and run EtherCAT masters program but I am facing some problems

There is a complete manual explaining how to install and run the program first it says in the instructions after installing the program the manual says

"If the EtherCAT master shall be run as a service4 (see section 7.4), the init scriptand the sysconfig file (or the systemd service file, respectively) have to be copied (or
linked) to the appropriate locations. The below example is suitable for SUSE Linux.
It may vary for other distributions"


# cd /opt/etherlab
# cp etc/sysconfig/ethercat /etc/sysconfig/
# ln -s etc/init.d/ethercat /etc/init.d/
# insserv ethercat

My first problem is that I am using ubuntu and i cannot find /etc/sysconfig directory and what i searched on internet I came to know that this directory is not available in ubuntu so I copied this ethercat file to /etc/network directory but I am not sure if that is correct can someone help me out with this 

Second problem I am facing is that after executing the first three commands ( I used # cp etc/sysconfig/ethercat /etc/network/ ) when I try to run 
# insserv ethercat 
it gives an error 
insserv: command not found

please can someone help me with this 
thanks in advance

---

