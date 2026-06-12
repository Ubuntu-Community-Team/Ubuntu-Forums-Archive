---
title: "SSH Primer : How to instal SSH w/ Public Keys (for rookies)"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by mike_abc on 2010-10-10
I thought I'd share this with all users that are trying to link computers thru SSH. After 24 hours of googling, I finally managed to make my SSH w/ RSA Public Keys work. I am quite new to Ubuntu (6 months of sporadical use), although I'm pretty old in IT.

SSH w/ (RSA) Public Keys is one of the safest methods of connecting two (or more) Linux  machines, as long as the private keys used in the process are kept safe. This  is similar to saying "No thief will ever enter your house as long as  you keep your key safe" - since the Unix house has pretty good reinforced doors and windows. 

My scenario postulates that the systems are in physical proximity and you exchange the public key via a stick (a very safe way to do it).

So here it is.

0. On client and server
----------------------------------

Install ssh client & server on both systems (Google on how to do it).


A. On client - generate RSA keys (public & private) 
---------------------------------------------------------------- 
 
Open a terminal window and issue the following commands: 
 
mkdir ~/.ssh 
chmod 700 ~/.ssh 
ssh-keygen -t rsa -b 4096 

Note: The -b 4096 option will generate strong RSA keys.

 
B. On client - copy RSA_public_key from client to stick 
--------------------------------------------------------- 
 
The key is located in ~/.ssh (i.e. /home/<username>/.ssh), which is a hidden directory. 
You can use Nautilus's option** View/Show hidden files** to get to it.
Copy file** id_rsa.pub** from the above directory to your stick. 
 
 
C. On server - register public_key of client 
---------------------------------------------- 
 
Copy the RSA_public_key from the stick to the server. To do so,  
copy the RSA_public_key to ~/.ssh and issue the command: 
 
cat id_rsa.pub >> authorized_keys 

where **~** refers to the user's directory on the server that you'll want to impersonate.

Make sure you have the proper permissions for the files & directories: 
 
chmod go-w ~/ 
chmod 700 ~/.ssh 
chmod 600 ~/.ssh/authorized_keys 

Also, check in the **sshd_config** file (etc/ssh/sshd_config) that the
AuthorizedKeysFile option actually points to your authorized_keys file. 

 
D. On server - check sshd is running 
------------------------------------------------ 
 
Issue command: 
 
sudo netstat -natp | grep sshd 
 
or 
 
telnet <servername> <port> 

If not working, start sshd, by issuing something like **service ssh start** (Google for the "best" 
command). 

 
E. Connect to server 
---------------------------- 

Try to connect:
 
[B]ssh <username@server>
[/B]
Note: In all the above, <username> on client is not (necessarily) <username> on the server.
When you connect to the server using SSH, you use the keys on the local system to impersonate 
a user on the server, so <username@server> should ALWAYS refer to a user on the server.

 
F. Further reading
------------------------

To know what the options for ssh_config and sshd_config, look them up in the manual.
Do this by typing m**an ssh_config**, or **man sshd_config**. You'll find some very useful info there.

A working SSH connection can then be used from within Nautilus, with rsync, with Krusader etc. etc.

---

