---
title: "Explorer 4250 won't prime"
date: 2008-03-27
forum: Mythbuntu
---

### Post by dsbw on 2008-03-27
All right. I've followed every speck of info in the firewire how-to.

And I think I have it set up right. The problem is that my box (SA Explorer 4250HDC) seems to go to sleep if I don't use it for a while.

The last two times this happened, while I was fiddling around with it, it woke up and everything worked. But now it seems to be asleep for good. (And I don't know what caused it to wake up before, so I don't know if something I did woke it up or if it something else happened to cause the change.)

I'm truly stumped: I've been using plugreport (which has returned info), firewire_tester (which always fails), test_mpeg2 (which always gets a zero-length file) and just now I've checked out gscanbus (which IDs the SA device).

But nothing seems to be doing the trick. I've tried plugging the firewire in  either port and tried different nodes and ports to no avail.

Any ideas?

---

### Post by yfed on 2008-09-24
I have the same exact problem, please help! STB SA4250HD

```
Host Adapter 0
==============

Node 0 GUID 0x344fc00007d73901
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Host Adapter 1
==============

Node 0 GUID 0xff1106005471afd6
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x001bd72015220000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
	channel=1, data_rate=1, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

```

firewire_tester
```
$ sudo ./firewire_tester -p -P 1 -n 1 -r 5
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Failed

```

mythprime 0.69a.beta
```
$ ./mythprime
UNKNOWN STB

Please email the Vendor and Model ID along with
the model number of your STB to: major.idiot@gmail.com

Please run scanfw again with the -f option to force a channel changer for your STB


```

Don't know what to do at this point :confused:

---

### Post by majoridiot on 2008-09-26
> **yfed said:**
> 
```
$ ./mythprime
UNKNOWN STB

Please email the Vendor and Model ID along with
the model number of your STB to: major.idiot@gmail.com

Please run scanfw again with the -f option to force a channel changer for your STB


```

Don't know what to do at this point :confused:

maybe i'm an idiot, but i think [b]"Please email the Vendor and Model ID along with
the model number of your STB to: [email]major.idiot@gmail.com[/email][/b] is kind of a clue? ;)

run it with ```
$ ./mythprime -v
``` (verbose mode) which will output the model number and vendor id.

then, mail the three pieces of info the error message requests and before you 
know it, new source will be posted which includes *your* stb info... and which will 
probably help others, too.

---

