---
title: "[SOLVED] firewire_tester errors"
date: 2008-04-01
forum: Mythbuntu
---

### Post by mantisboxer on 2008-04-01
Before getting roasted, I wanted to note that I have been trying to follow the Firewire step by step guide first and have searched this and many other forums for assistance.

I am trying to connect to a Motorola DCT3416. When I do the diagnostics it shows active ports and connections to my machine. I can make it come and go by plugging/unplugging the cable.

Ran plugreport and got the following:

```
Node 0 GUID 0x44a104080804a144     **<- this seems to change every time i run plugreport, is that **normal?
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=0, data_rate=1, overhead_id=0, payload=376
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x474fc00023709081  **<- this ones stays the same ?!?**
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR
```

Good so far? Is it normal for the GUID to change everytime one runs plugreport?


Downloaded and compiled firewire_tester.c per Myth Firewire Community page. When I run it, I get the following:

```
Action: Test P2P connection 10 times, node 0, channel 0
P2P: Testing...libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
iec61883_cmp_create_p2p_output failed
P2P: Testing...libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to get the oPCR[0] plug for node 0.
iec61883_cmp_create_p2p_output failed
P2P: Testing...libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to get the oPCR[0] plug for node 0.
iec61883_cmp_create_p2p_output failed
P2P: Testing...libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
iec61883_cmp_create_p2p_output failed
P2P: Testing...libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
iec61883_cmp_create_p2p_output failed
```


DOHH!! I get similar errors when trying to test via broadcast or using test-mpeg2. What am I doing wrong? As far as I can tell, my cable box has active 1394 ports and it shows my PC connect and disconnect in the diagnostic screens. Please help the noob!!

---

### Post by volkswagner on 2008-04-01
Have you tried broadcast.  Those results look as if you are not connected to node 0.  If the system saw a device there it would say something like below.

```
P2P: receiving packets... FAILED
```


Be sure not to  hot plug the cable.  Shutdown the pc and cable box prior to changing ports.

You can also try to reset the bus
```

firewire_tester -R -n 0 
```

The above is for node zero.  Run plugreport again to verify you are in fact on node zero.

You said you are going though the setup.  If you have not completed it and performed a reboot you will need to run the following until you set udev rules and permissions.

 > Plugctl

To explain what the switch's do for plugctl, -n will allow you to specify your node and -p will allow you to specify your host adapter. If you are using host adapter 0 then there is no need to use the -p switch. Gaining information to use with plugctl is done by using plugreport.

For the most reliable FireWire operation, use Point2Point/p2p. By default your n_p2p_connections will be set to '0'. This mode presented unreliable operation with dct6200's for recording and watching. Set p2p to 1.
[edit]
Single STB (Set-Top Box) setup

plugctl -n 1 "oPCR[0].n_p2p_connections=1"

This will allow setting it so you maintain a stable connection by setting the Point2Point "Active". 

---

### Post by mantisboxer on 2008-04-02
Volkswagner,

Thanks for your reply. I was stumped by this one but I figured out that I was following the guides correctly. My problem was a bad cable!! Apparently it was good enough to transmit small amounts of data involved in executing plugreport, but during the test, it crapped out. I have settled on broadcast, which seems to be the best option for the Motorola STBs.

Thanks everyone for reading!!

---

