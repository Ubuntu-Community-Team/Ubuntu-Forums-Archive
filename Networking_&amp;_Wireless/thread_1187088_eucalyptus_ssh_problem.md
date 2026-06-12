---
title: "eucalyptus ssh problem"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by neavin on 2009-06-14
hi,
i am using eucalyptus to create a private cloud. i am trying to add a node using:

#euca_conf -addnode <remote ip address>

the output that i get is:

/var/lib/eucalyptus
First, please run the following commands on '10.0.152.54':

sudo apt-get install eucalyptus-nc
sudo tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEArtqwLoiNIq4FgDpgkjweZa x8vXyVN8xSPkDZCSyopylElch2fPIPLSw41G4FHp8Vt+UXCC6R QNksk/b/HMHVVRo5OYdC4Yc6wTcXZgsAGT2Q2Zi5yMIoUfXZeYbX55Ljxr 7SME7ipDUtAR6pTwFq0m60PbMg76RNIFEcYLaoCQuZ71rpRnsM PmZjcZZLlah/yHTFpuIQfaSuTaVSkNrmYQNjUvUfFtNzC9rQ7dv1mDuKKntKLa XWfrCTZ9AZLa3pUgAYKa4irnKEdEgaW/m+5pwlkov9Ibt9ny4j9Q9DVUK28MHbupo8AveL4hvlLD4ElFVe lmvF3QmYOZaBAC+dJw== eucalyptus@neavin-laptop
EOT

hit return to continue

Enter passphrase for key '/var/lib/eucalyptus/.ssh/authorized_keys': 
Enter passphrase for key '/var/lib/eucalyptus/.ssh/authorized_keys': 
Enter passphrase for key '/var/lib/eucalyptus/.ssh/authorized_keys': 
[EMAIL="eucalyptus@10.0.152.54"]eucalyptus@10.0.152.54[/EMAIL]'s password: 
Permission denied, please try again.
[EMAIL="eucalyptus@10.0.152.54"]eucalyptus@10.0.152.54[/EMAIL]'s password: 
Permission denied, please try again.
[EMAIL="eucalyptus@10.0.152.54"]eucalyptus@10.0.152.54[/EMAIL]'s password: 
Permission denied (publickey,password).
lost connection
ERROR: could not syncronize keys, check authorized_keys on 10.0.152.54, then run this command again.

the key is present in the remote computers .ssh/authorized_keys file.
the passkey entered is

ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEArtqwLoiNIq4FgDpgkjweZa x8vXyVN8xSPkDZCSyopylElch2fPIPLSw41G4FHp8Vt+UXCC6R QNksk/b/HMHVVRo5OYdC4Yc6wTcXZgsAGT2Q2Zi5yMIoUfXZeYbX55Ljxr 7SME7ipDUtAR6pTwFq0m60PbMg76RNIFEcYLaoCQuZ71rpRnsM PmZjcZZLlah/yHTFpuIQfaSuTaVSkNrmYQNjUvUfFtNzC9rQ7dv1mDuKKntKLa XWfrCTZ9AZLa3pUgAYKa4irnKEdEgaW/m+5pwlkov9Ibt9ny4j9Q9DVUK28MHbupo8AveL4hvlLD4ElFVe lmvF3QmYOZaBAC+dJw==



 the password entered was the root password of the remote computer. in spite of this, permission is denied.

is there any problem with the procedure that i have followed while setting up the ssh 
Do i need to set any passwords at the remote machine.

/etc/hosts at the remote machine @ 10.0.152.54 has :
127.0.0.1    localhost
127.0.1.1    bhavna-laptop
10.0.152.54     bhavna-eu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts 


Please help!!!.

Thanks.

---

