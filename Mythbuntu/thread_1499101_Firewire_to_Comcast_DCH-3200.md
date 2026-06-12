---
title: "Firewire to Comcast DCH-3200"
date: 2010-06-01
forum: Mythbuntu
---

### Post by bawilson2 on 2010-06-01
I'm trying to setup a secondary backend for my mythtv server.  I'm using Mythbuntu 10.4 and not having much luck.  I've tried following the guide here:  [http://www.mythtv.org/wiki/FireWire](http://www.mythtv.org/wiki/FireWire) but it hasn't been successful.  I think that the port on my STB might be disabled because I can't get the plugreport to show a node.  Here's a few outputs.  I just wanted to get a second opinion before I went to comcast to see if they'd enable the port for me.

```
$ lsmod|grep 1394
dv1394                 15339  0 
raw1394                22271  0 
ohci1394               27238  1 dv1394
ieee1394               81213  3 dv1394,raw1394,ohci1394

```

```
$ plugreport 
Host Adapter 0
==============

Node 0 GUID 0x00110666455579ea
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

```

I have the STB turned on to a local channel so if it is going to work I believe this should be a working state.  Any suggestions?

---

### Post by bawilson2 on 2010-06-04
Anybody had a similar problem?

---

### Post by ozite on 2010-06-20
I have the same Comcast box and was considering trying to connect using firewire.

Did you ever fix this problem?

---

