---
title: "mythbuntu 8.10 firewire problems"
date: 2009-01-26
forum: Mythbuntu
---

### Post by jeremystaples on 2009-01-26
I apologize in advance if I ask any stupid questions.  I've searched high and low for answer to this one without any luck, so I'm finally posting.

I can't get mythprime to work (haven't even begun to setup firewire as a capture source).  I'm running mythbuntu 8.10 with an SA4250HDC stb (comcast).

plugreport shows:

```
Host Adapter 0
==============

Node 0 GUID 0x001e8c0001854ad7
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x001cea9887220000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
    channel=6, data_rate=2, overhead_id=12, payload=146
iMPR n_plugs=0, data_rate=2
```

When I run mythprime (ver. 0.69h) it is able to detect and power on my stb and change channels (using either firewire port), but fails testing p2p connection:

```
mythprime .69h beta

Acquiring firewire handle... OK.
1 port(s) found

Acquiring handle on port 0... 1 devices detected.
Skipping empty node 0
STB Vendor ID: 0x1cea Model ID: 0x10cc, Scientific Atlanta Model SA4250HDC

(Using channel changer #4)

1 STB(s) found:
-------------
STB 1: port=0, node=1, p2p=1, changer=4, GUID=0x001cea9887220000

Priming STB 1:
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1

connection unstable, resetting firewire bus... firewire bus reset
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Failed.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1

connection unstable, resetting firewire bus... firewire bus reset
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Failed.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1

connection unstable, resetting firewire bus... firewire bus reset
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... FAILED.
Disconnecting P2P connection on node 1, channel 1
Failed.
Priming Errors encountered: 0 stbs primed, 1 stbs failed to prime, 0 non-stbs ignored and 1 empty nodes skipped on 1 ports in 3 runs.
```

The failure is very quick as well.  What else should I be trying?  If the firewire ports on my stb were disabled would mythprime be able to power on the box and change channels?

---

### Post by theophile on 2009-01-26
Are you sure the STB is tuned to a known-clear channel? Mythprime won't be able to establish a connection unless there is data to receive. Try one of the HD network TV stations like NBC (for example).

Also, try one of the "manual" methods for establishing a p2p conection with the STB. I have an SA3250HD also with a very stable firewire connection and I never could get mythprime to work for me.

---

### Post by jeremystaples on 2009-01-26
Yeah, I am running mythprime -v -c 5 -f 4 and mythprime is successfully changing the channel on the stb to channel 5, which is Standard Def unencrypted.  Does it have to be High Def?  I am planning on recording High def, of course.

I tried configuring firewire as a capture source in myth-backend and linking it with schedulesdirect, but trying to open live tv from mythfrontend kicks me back out to the menu.

Is it possible for the firewire port on my stb to be disabled and still be able to change channels with mythprime?

---

### Post by jeremystaples on 2009-01-26
I just tried an unencrypted HD channel and mythprime and firewire_tester both work on p2p tests.  So, that must have been.  I knew there had to be some simple answer.  Thanks theophile!

---

