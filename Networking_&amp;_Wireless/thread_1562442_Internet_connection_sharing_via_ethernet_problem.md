---
title: "Internet connection sharing via ethernet problem"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by jacksonpollack on 2010-08-27
I am attempting to share my laptop's internet connection (received via wireless) with a laptop that has no wireless connection. I do not have access to the router itself (it's in my land lady's appartment) so this is the only way I can connect the second laptop to the internet.
So:
Wireless signal -> my laptop -> ethernet cable -> laptop #2

I found this guide, and it seems to say things are very easy these days (I'm running Lucid, and am using a crossover cable):
[http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/](http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/)

My problem is that when I connect the second laptop (which runs Karmic, if that matters), my laptop displays the message:
Wired network - Connection Established
Then, three seconds later: Wired network - Disconnected

And the notifications just pop up back and forth every few seconds. The second laptop eventually stops trying to connect.

Has anyone tried to do something similiar? I've found a few things written here and there, but they are for older versions of Ubuntu. Any help would be appreciated, thanks.

---

### Post by Iowan on 2010-08-27
Are you using Network Manager?
Are you Using static address(es)?

---

### Post by jacksonpollack on 2010-08-27
Yes, network manager. I tired the method described in the link I provided above. I'm not sure about the static address bit, as I left everything else as the default. I certainly didn't set up any static address beforehand.

---

### Post by Iowan on 2010-08-27
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page?

---

### Post by jacksonpollack on 2010-08-27
I did see that page. I was hoping that maybe someone had had the same problem as I did using the simple GUI method listed there (which is the same as the link I provided). I suppose I'll try the complex method when I get some free time, though since I don't understand what's actually being changed in some of the steps, I'm wary that I'll mess something up and be unable to change it back. I guess I'll see. Thanks for your suggestions so far.

---

### Post by jacksonpollack on 2010-08-27
Well, I gave up the complex methods and just downloaded firestarter from the repos.
Then set up my eth0 connection's IPv4 settings to manual (Address: 192.168.0.1, Netmask: 255.255.255.0). Then the other computer's as (Address: 192.168.0.2, 255.255.255.0, Gateway: 192.168.0.1, DNS servers: 192.168.1.254 [that last # was listed in /etc/resolv.conf]).

With firestarter running it all works like a charm. It should probably be easier, but oh well.

---

### Post by skywatcher on 2010-10-19
Hi everyone, I hope that there is an expert out there with enough patience to give me some advice.

My scenario is this: I have two laptops. Laptop A runs on Ubuntu 10.04, laptop B runs on Ubuntu 9.10. I have the following connected to laptop A: printers and a 3G USB modem for internet and email.

I use laptop B for everyday work because I have a large LCD monitor connected to it, which makes it easy on the eyes. I have successfully set up an ethernet connection between the two, and I can share files and printers.

Good so far. Now I would like to have access to the internet and email on laptop B as well. I don't want to spend money on a router or a switch. How do I go about this? I have searched and searched and found many conflicting explanations as well as some very impatient replies.

Can someone help here, please?

Thanks

---

