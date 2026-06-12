---
title: "SSH Password Denied"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by thirdmusketeer on 2009-12-26
Hi Guys

I am dumbfounded why SSH server on one machine is giving the message
Permission denied, please try again.
Checkout the following. 

```


user1@machineA:~$ ssh localhost -l root
root@localhost's password: 
root@machineA:~# exit 
logout
Connection to localhost closed.
user1@machineA:~$ ssh localhost
user1@localhost's password: 
Permission denied, please try again.
user1@localhost's password: 


```




On machineA I can't get users login using ssh but on machineB I have no problem with users logging in using ssh. The passwords are correct as users can login using the console on machineA. The ssh server seems to be working properly because root can log in using ssh.
(I know its not recommended but in my setup its not a problem as there are no connections to the internet from outside)

I have verified that there is no difference between sshd_config on both machines. Both machines are also having identical passwd files.

What other places might have differences? MachineA is a fresh 9.04 install and I installed openssh-server.

Thanks

---

### Post by thirdmusketeer on 2009-12-26
After significant amount of hair loss, I figured out the problem. I had a suspicion that the problem was a minor one yet it eluded me.

I had to completely reinstall and this time I was able to pinpoint when the functionality broke.

Turned out that the new machine didn't have the shell "tcsh" which was the default shell for all the users. Once tcsh was installed everything worked out.

---

