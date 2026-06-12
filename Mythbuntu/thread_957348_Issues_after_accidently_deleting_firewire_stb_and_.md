---
title: "Issues after accidently deleting firewire stb and re-installing it"
date: 2008-10-24
forum: Mythbuntu
---

### Post by codered867 on 2008-10-24
So yesterday I decided to try and install a tuner card onto my mythbox. Everything went ok until I tried to clean up my install and get rid of some old devices I had on there, accidentally deleting all of my devices and having to add them again. First of all I had the firewire from my STB working great and the reason I wanted to add a tuner card was so that I could watch/record more then one thing at a time. Now when I added the STB via firewire again it seems that it is not registering correctly. The GUID does not auto fill as it did when I set it up the first time and when I look at the logs it says ERROR: no valid capture cards are defined in the database. The STB is a motorola 3200 with RCN cable. Is there some step that I am forgetting, I have re-read the wiki article on this and did not find anything that stood out.

Thanks in advance for any advice,
-Chris

---

### Post by thalon on 2008-10-24
Is this the wiki you're talking about:

[http://www.mythtv.org/wiki/index.php/FireWire](http://www.mythtv.org/wiki/index.php/FireWire)

What are the results of running plugreport and "dmesg | grep ieee1394"?  (see [http://www.mail-archive.com/mythtv-users@mythtv.org/msg09771.html](http://www.mail-archive.com/mythtv-users@mythtv.org/msg09771.html))

---

### Post by codered867 on 2008-10-24
Im referring to this one [https://help.ubuntu.com/community/MythTV_Firewire](https://help.ubuntu.com/community/MythTV_Firewire).
 
Plugreport:
```
Host Adapter 0
==============

Node 0 GUID 0x001e8c000168d83d
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x002180fffedd3f5d
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
	channel=62, data_rate=1, overhead_id=0, payload=376
iMPR n_plugs=0, data_rate=2
```

dmesg | grep ieee1394:

```
[    6.684454] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c000168d83d]
[    6.692457] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[002180fffedd3f5d]
[    9.191445] ieee1394: raw1394: /dev/raw1394 device initialized

```

---

