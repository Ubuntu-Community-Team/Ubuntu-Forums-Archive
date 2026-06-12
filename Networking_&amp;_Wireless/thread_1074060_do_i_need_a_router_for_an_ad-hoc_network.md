---
title: "do i need a router for an ad-hoc network?"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by zander1013 on 2009-02-18
hi,

there was a thread that discussed some issues close to this but i don't think it really addressed this question directly.

basically do i need a router for an ad-hoc network so that i can ssh between the machines?

i am trying to setup ssh via wifi on a cluster of laptops using hadoop. i have put the following lines into /etc/hosts...

# /etc/hosts (for master (node0) and slave (node1))
192.168.0.1	node0
192.168.0.2	node1
#end hadoop section

...

for simplicity i am getting the cluster started with just a pair of nodes. and i will scale up when i am satisfied that everything is working on these two.

this seems to work okay when i ssh between the machines on my home wlan.

i am satisfied i got the nodes to work as a multinode cluster.

however i want the cluster to be portable with a minimum of gear to haul around to make it work.

my plan is to use mobile broadband to connect the cluster to the web via the gsm modem in node0 and att wireless broadband service. i want to dedicate the wifi cards in the units to just passing messages/data related to their function as a cluster. to this end i have elected to setup an ad-hoc network between the machines that will be exclusive to them.

the problem now is that due to a "bug" in hadoop i have to reformat the datanodes on all machines everytime i add a node or move the cluster to a different wlan. i hope to workaround this by just having a static ad-hoc type wifi network between the nodes in the cluster dedicated to the service of the cluster.

can i do this without a router?

what is the best way to proceed?

please advise.

zander

---

