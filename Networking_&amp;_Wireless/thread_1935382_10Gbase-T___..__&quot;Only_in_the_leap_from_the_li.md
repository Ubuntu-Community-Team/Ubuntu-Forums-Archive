---
title: "10Gbase-T   ..  &quot;Only in the leap from the lion's head will he prove his worth.&quot;"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by Phoenixxl on 2012-03-04
I am contemplating running iscsi over 10gbase-T on 4 of my computers.(home usage)

The only affordable cards I see available are those solarflare ones : [http://www.solarflare.com/Mid-Range-10GbE-Adapters](http://www.solarflare.com/Mid-Range-10GbE-Adapters)  .

A switch being out of the question -cough- I am looking at putting 2 of those SFN5161T dual port models in my primary file server , then connecting a second file server to that one , then connecting workstations to the other ports all 4 using the SFN5151T single port models.

The computer with the 2 dual port nics would be running on a 4 core 2011 socket based pc with 16 GB of mem running ubuntu server.

Now .. before I go and rape my bank account  for the sake of my hobby I am wondering about the following :



-I know we can expect some price drops in those 10Gbase-T cards in the next months/years .. But I'd be really disappointed if they end up at 1/10th of the price by christmas .. On the other hand , I've been looking at these things for years now so I am getting impatient.. Should I wait just a tad bit longer?.. I wonder..

-Are the standards set in stone for those types of nics by now ?... Am I running the risk , even today , I'm going to be buying hardware that will be incompatible with standards coming out in the near future...

- what kind of latency and bandwidth can I expect if I bridge the 4 interfaces in the 2 cards , when transferring packets from 1 workstation to another , or from the workstation to the secondary  file server. I expect these cards to have some degree of offloading , but I have yet to see them work in the flesh so to speak. Should I expect a difference in latency when packets go from port 1 to port 2 on the same nic , than going from one port to the other on a different nic .. or would everything go through the system/driver anyway .. I can't find any independent benchmarks on those things , which isn't surprising ..

-Drivers for these cards seem to be available from the vendor , I somewhat expect them to be present in ubuntu in some way or another.. or am I just deluding myself here..
[https://support.solarflare.com/index.php?view=categories&amp;id=165&amp;option=com_cognidox&amp;Itemid=2](https://support.solarflare.com/index.php?view=categories&amp;id=165&amp;option=com_cognidox&amp;Itemid=2)

-Do any of you have any hands on experience with these cards in particular or cards of those speeds from other vendors or fiber models (I am really reluctant to buy anything fiber for home usage ) ? I've read about overheating problems as well , have any of you experienced that? (an extra radiator is quickly installed , it would be nice to know before I fry one) 

-Any thoughts about this are welcome as well.

Extra info : My setup now is what I have described here (except it's 1gb and using a switch), but only 1 workstation boots from iscsi , the rest still have harddisks . Internet , ssh , kvm are running on a second network.


Thank you in advance for any reply.

[SIZE="1"]You have been hit by WALL OF TEXT inflicting 50 points of mental damage.[/SIZE]

---

### Post by TheR on 2012-03-21
You got to have a lot of money. What kind of bussines are you doing at home that you need that kind of bandwidth.

Shortly. I haven't seen a lot of 10base-T switches (none really) but most of 10G switches are north of 10k US$ for 16+ ports. You can get by with HP Procurve xyz, 6 ports 10Base-CX4 for 3-4k$. Thats cheapest you can get. And the price hasn't changed for two years (I can tell, because I configured KVM virtualization with iscsi at my job two years ago).

At Colfax direct you can get Mellanox 8 port Infiniband switch for 1750$. That is cheapest that I have seen. But I heard that Infiniband is hard to configure.

So probably the cheapest solution is still bonding 4 port Ethernet 1Gb cards together on a cheap 1Gb switch. That way you get cheap 4Gb network.

What kind of drives are you planning to use in iscsi server. You got to raid0 2-4 SSDs or quite a lot HDDs to get 1GB/s speed, which would saturate 10gB Ethernet.

I think that network latency is 100-1000 times lower than hd drive seek time.

by
TheR

---

