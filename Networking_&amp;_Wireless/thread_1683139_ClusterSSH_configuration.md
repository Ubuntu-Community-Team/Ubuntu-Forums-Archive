---
title: "ClusterSSH configuration"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by Linuxson25 on 2011-02-07
Hi

I have recently set up a network of 21 computers running Edubuntu 10.10
I use iTalc to communicate with the pcs and also to shutdown all of them at once.
The only problem I have, is it doesn't start up again with iTalc...
So I switched to ClusterSSH. Only problem I have now is that everytime I run cssh, I need to manually add IP addresses of all the pc's, before I can start issuing commands.
Is there a config file or something I can populate with all the IP addresses so that it starts up with all of them already added? And while we are at it, the command to start up a computer on the network?

Thanx

---

### Post by rchille on 2011-04-22
I found this post looking for same info. There should be a couple of configs in /etc/clusters and /~/.csshrc that should do what we are after. 

I just haven't figured out how from the rather scant documentation (I didn't even have a /etc/clusters file)

Did you get anywhere with this?

---

### Post by rchille on 2011-04-22
Ug! 5 mins later I find the solution from:

**(Warning: Scary SSL Self-signed Cert ahead)**
[https://wiki.zealnetworks.com/tiki-index.php?page=Cluster+SSH+-+CSSH]("https://wiki.zealnetworks.com/tiki-index.php?page=Cluster+SSH+-+CSSH")


The short answer:
1) Create /etc/clusters if you don't have it

2) Add a cluster a line at a time:
   cluster_name user1@host1 host2 user3@host3

3) edit /home/[you]/.csshrc
   Change: extra_cluster_file=
   To: extra_cluster_file=/etc/clusters

4) Try: cssh cluster_name and you should be good

I hope this helps! :D

---

