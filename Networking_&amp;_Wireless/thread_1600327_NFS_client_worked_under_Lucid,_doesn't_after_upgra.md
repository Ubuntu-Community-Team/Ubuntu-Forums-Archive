---
title: "NFS client worked under Lucid, doesn't after upgrade to Maverick"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by greybeard95a on 2010-10-18
Hi all,

I had a working NFS setup under Lucid Lynx (10.04).  It has not worked since I upgraded to Maverick Meerkat (10.10).  One server is a Debian Lenny system and that hasn't changed.  The other server (actually my old laptop) was also upgraded from Lucid to Maverick.

Now, when I attempt to mount a NFS share, it simply hangs and I eventually hit CTRL/C.  There is no information about this in any of the logs that I can find.  Here are the relevant lines from /etc/fstab:

atlanta:/home				/mnt/atlanta/home nfs	  rw,noauto,rsize=8192,wsize=8192 0  0
192.168.1.2:/home			/mnt/graton/home nfs	  rw,noauto,rsize=8192,wsize=8192 0  0

As near as I can tell, when others have asked about this, they've gotten defensive responses that amount to a denial that anything is wrong.  Sorry, but something is wrong.

Now, can anyone help?

Thanks!

---

### Post by amauk on 2010-10-19
how long are you leaving the mount command before you kill it?

Mount will timeout if it can't mount something
and it's possible that nothing is in your logs because you're killing the process

Unfortunately, without any logs / error msgs, we're left guessing as to the real issue

---

### Post by SeijiSensei on 2010-10-19
Are you sure the hostname "atlanta" resolves correctly on the client machine?  Since it's "unqualified" you'd need a "search" or "domain" directive in /etc/resolv.conf to add the domain part, or you need an entry for it in /etc/hosts.

---

### Post by greybeard95a on 2010-10-26
Hi all,

'atlanta' is in /etc/hosts:

n4rky root /home/benfell # cat /etc/hosts
192.168.1.4	n4rky	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	n4rky	localhost6.localdomain6	localhost6
127.0.1.1	n4rky
10.8.0.1	atlanta.parts-unknown.org	atlanta
10.8.0.1	[www.parts-unknown.org](www.parts-unknown.org)		www
74.207.225.79	parts-unknown.org
10.8.0.1	mail.parts-unknown.org		mail

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

It runs over OpenVPN and I am able to use the connection for everything else normally.

I've been waiting several seconds before killing it.  NFS mounts happened instantly previously.  But I let it run this time and got:

n4rky benfell /home/benfell % sudo mount /mnt/atlanta/home 
mount.nfs: Connection timed out

And still nothing appears in any of the logs I know to look at (messages, syslog, kern)

---

### Post by aidans on 2010-11-12
I filed [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/674729](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/674729) for this.

It's clearly horked in Maverick.

---

### Post by greybeard95a on 2010-11-12
Thanks!  I'm surprised this could have gotten by.  I was assuming there was some undocumented configuration change that needed to be made.

---

