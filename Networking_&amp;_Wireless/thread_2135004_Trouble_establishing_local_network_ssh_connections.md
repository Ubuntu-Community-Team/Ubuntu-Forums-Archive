---
title: "Trouble establishing local network ssh connections"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by kdoherty on 2013-04-12
I have 2 machines on a LAN in which I would like to share some files when the need arises via ssh.  I have previously had the sftp working between the two machines using password authentication.  Now my troubles began,  I wanted to disable the password authentication on both and rely on public/private key authentication.
  The steps I had taken failed, and to be quite honest I relied on a few different sources for information to which may have caused some conflict in the process.  Without me trying to recall the steps in which I had taken to achieve my failed attempt, I do wish to remove any information /configuration on both machines, and try another attempt at the ssh configuration.  My problem lies in that I am not sure if or how to remove my existing keys , and what sshd and ssh files I should edit /remove, as well as should I create new key sets (home/me/.ssh/id_rsa   home/me/.ssh/id_rsa.pub) on both machines for my next attempt.
Your input is much appreciated!

---

### Post by sev1 on 2013-04-13
1.) Remove your keypairs from both machines:    ~/.ssh/id_rsa       ~/.ssh/id_rsa.pub 

2.) Clear the contents (fingerprints) of the known_hosts file for both machines ~/.ssh/known_hosts

3.) Make a backup of the sshd_config file prior to altering it

That will get you back to a place where you can generate new keypairs. To simplify things for yourself starting out, think of one machine as the server and the other as the host.

I didn't read through it in depth, but this tutorial appears relatively up-to-date:
[URL="https://www.digitalocean.com/community/articles/how-to-set-up-ssh-keys--2"]
https://www.digitalocean.com/community/articles/how-to-set-up-ssh-keys--2[/URL]
 
You didn't mention the version of Ubuntu this is for, unless I missed it.

---

### Post by kdoherty on 2013-04-13
sev1, thank you for your help.  One machine is running xubuntu 12.04 the other running ubuntu 12.04.

The information you have provided is what I was looking for.  However, I feel I have another issue that is causing my woes  I was looking through some log files and came across some permissions problems within  /etc and its contents.   example :  0777 etc/ssh '//ssh_host_rsa_key' are too open.   

I believe I have made a fatal error in using the chmod  command at an earlier date.  It looks like I did a chmod -R 777 to the whole /etc.  This is causing ssh to ignore my keys.  Probably the most efficient way for me to proceed is to reinstall the os on this borked machine, and then use your advice while setting up the new connection.

---

### Post by kdoherty on 2013-04-20
Just an update, after reinstalling ubuntu 12.04 on my machine in which I hosed the /etc permissions.  The machine is now able to accept ssh connections from the xubuntu machine.  However the reverse is not yet working.

---

