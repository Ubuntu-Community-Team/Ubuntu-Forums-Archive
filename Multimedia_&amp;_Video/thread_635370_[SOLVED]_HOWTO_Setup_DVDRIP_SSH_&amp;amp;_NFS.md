---
title: "[SOLVED] HOWTO: Setup DVD::RIP SSH &amp;amp; NFS"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by Son of Silas on 2007-12-08
being a complete Linux noob, I found setting up a DVD::RIP cluster a complete nightmare following the online instructions, so I cobbled this together based on my fumblings today that resulted in a working cluster.

Simple DVD:RIP cluster setup with 2 PCs A 'trancode server' that does most of the front end stuff, and a 'transcode client' that does some number crunching remotely.

In this example:
The transcode server has an ip address of 192.168.1.9
The transcode client has an ip address of 192.168.1.2


1. Install SSH server On the transcode client
	sudo apt-get install ssh

2. On the transcode server generate a key pair
	ssh-keygen

Follow its instructions but press enter if you are asked for a password!

3. Copy the contents of id_rsa.pub on the transcode server to a file called ~/.ssh/authorized_keys on the transcode client

4. Test ssh from the transcode server to the transcode client by typing (on the server)
	ssh 192.168.1.2

5. Install nfs on the trancode server
	sudo aptitude -P install nfs-kernel-server nfs-common portmap

When configuring portmap do NOT bind loopback. If you do you can either edit /etc/default/portmap by hand or run:

	sudo dpkg-reconfigure portmap

If you have edited the file by hand you can restart portmap via:

	sudo /etc/init.d/portmap restart

6. Share the Directory on the transcode Server by editing the exports file
	sudo gedit /etc/exports

	Add a line like this:  /home/silas/dvdripdata 192.168.1.1/24(rw,no_root_squash,async)

7. After making changes to /etc/export make the share take effect by typing
	sudo exportfs -a

8. Create a directory on the transcode client 
	sudo mkdir ~/transcode

9. Edit the fstab file to mount the server share at boot time
	gksudo gedit /etc/fstab

Add a line like this, changing the directory details as necessary:

	192.168.1.9:/home/silas/dvdrip-data	/home/silas/transcode nfs rsize=8192,wsize=8192,timeo=14,intr

10. After you have saved fstab, restart portmap and nfs-common
	sudo /etc/init.d/portmap restart
	sudo /etc/init.d/nfs-common restart


11. Test it works by typing
	sudo mount ~/transcode

12. Setup Transcode server cluster as per _[online instructions.](http://www2.exit1.org/dvdrip/doc/cluster.cipp)_ from here on its straight forward.

One thing worth noting. DVD::RIP doesn't allow IP address or node names that contain hyphens such as remote-computer, so edit the hosts file to create an alias such as remotecomputer on the transcode server:

	sudo gedit /etc/hosts
	Add 192.168.1.9	remotecomputer

refer to remote-computer in the DVD::RIP GUI as remotecomputer (or whatever yours is called, this is just an example)

---

### Post by whomever21 on 2007-12-28
One problem I ran into was getting dvdrip to connect to my node via ssh. I was able to ssh through the terminal without any hangups, but dvdrip failed each time. I found a thread on a German forum ([http://www.linuxforen.de/forums/showthread.php?t=241323]("http://www.linuxforen.de/forums/showthread.php?t=241323")) but in case you're having the same problem in English, here's the solution:

Change the timeout from 5 to 10 in /usr/share/perl5/Video/DVDRip/Cluster/Node.pm. Make sure you restart dvdrip-master after that change, restart dvdrip and attempt the connection again. 

Good luck!

---

### Post by adpsimpson on 2008-06-19
Thanks for this - very useful guide.

Just one note - you need to install nfs-common and portmap on both the server AND client node machines. Other than that, perfect :)

---

