---
title: "Live installer says only 2.6 GB needed for install"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-04-01
The live-installer (ubiquity) displays that at least 2.6GB of disc space is required for installation so I filed a bug report during Beta1 iso-testing:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/745148)

Please report your actual installation size including SWAP. It would be best to report each partitions size related to that install.

I'm quite confident in saying that anything less than 5GB for / is a disaster looking for a place to happen, unless they intend for you to try it, hate it, and remove it :(

The replies from the devs would certainly make one wonder if they even use Ubuntu themselves :lolflag:

Here's a screenshot:

[ATTACH]187797[/ATTACH]

I think 10GB minimum is more realistic, and still a bit on the low side. The stated 2.6GB is just nuts!

---

### Post by ronparent on 2011-04-01
I agree. 2.6Gb might be sufficient for a quick look-see but would be overwhelmed in short order. I also feel that 10Gb is more realistic.

---

### Post by cariboo on 2011-04-01
That's true if you don't want to install anything else, but when I did the install alongside, it automagically created an 18GB partition for / and a 500MB partition for swap.

Hopefully the automatically create a home partition option makes it into Oneirc from Debian wheezy

---

### Post by julianb on 2011-04-01
I am using Natty on a 4gb partition - the netbook i installed on has 12gb total hard drive space (two SSDs). 

I installed apache/mysql/php, skype, dropbox, Cheese, and chromium. 

I am still at 2.9gb used out of 4gb available. 

a minimum is just that - a minimum.

all of you can recommend 10gigs but 4gb netbook hard drives really do work.

---

### Post by Starks on 2011-04-01
you need the 10gb for additional packages and updates you install. even apt-get clean won't keep up.

---

### Post by MacUntu on 2011-04-01
But apt-get purge does. The only question is: can it be installed in 2.6GB or not.

---

### Post by jerrylamos on 2011-04-01
> **MacUntu said:**
> But apt-get purge does. The only question is: can it be installed in 2.6GB or not.
I've hardly done a thing except install Unity 2D and I'm already over 2.6 GB.

No way will a linux run without at least some working space.  On my oldest smallest 18 GB hard drive Thinkpad I've got Natty and Maverick comfortably up in 5 GB each, and Lubuntu in 4 GB.  Swap is 1 GB and the rest is a shared archive.  I don't do much with the Ubuntu's except test install (Natty has got to be the absolute worst install bug history I've seen since Dapper Drake Beta!) and internet and write and such.  

And oh yes, Compiz crashes readily, frequently, and often starting in Intrepid.  Really nice cranking up System Monitor on Unity 2D and seeing no Compiz anywhere.

Depending on which pc, Natty install asks for anything from 2.4 GB to 2.7 GB.  Someone might be able to play around with the naked install in 4 GB.  A few updates will put me over 3 GB, even with no added packages.

So I'd say a "bare" install needs 4 GB but don't expect to install extra applications or games, or much in the way of documents and my mail is on Yahoo, not locally.

Jerry

---

