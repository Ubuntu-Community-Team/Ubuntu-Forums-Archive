---
title: "How do I use firewire STB? and partition question"
date: 2008-06-05
forum: Mythbuntu
---

### Post by Saxomophone on 2008-06-05
I have mythbuntu installed, but I'm completely lost on how to get it to use the firewire connection from my set top box. I referred to the  [_[COLOR="Blue"]mythtv_firewire page[/COLOR]_]("https://help.ubuntu.com/community/MythTV_Firewire"), but it's incomplete for 8.04.

Can anyone help me?

Also, I put the mount point of my 500 gb hdd as /myth
How do I change the default location for saving files to that drive?


Here's the output of mythprime
> 1 devices detected.  checking avc subtypes...
0 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...


---

### Post by Saxomophone on 2008-06-06
bump

---

### Post by tgm4883 on 2008-06-06
A lot of work has gone into the firewire for 8.04.  I bet you will find lots of useful info here [http://ubuntuforums.org/showthread.php?t=738782](http://ubuntuforums.org/showthread.php?t=738782)

As for your storage.  You will need to go into mythtv-setup and change your storage directory (option 6)

---

### Post by Saxomophone on 2008-06-06
Okay,

I've read that thread already, and it didn't provide anything to tell me how to fix this, but thank you for the response. mythprime keeps failing.
> $ mythprime
1 devices detected.  checking avc subtypes...
0 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...
0 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...
0 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
Priming Errors encountered: 0 stbs primed, 0 stbs failed to prime, 0 non-stbs ignored and 0 ghost nodes skipped on 2 ports in 3 runs.

---

### Post by Saxomophone on 2008-06-06
Okay,

So I started following the directions for the old way to configure firewire.

plugreport returns this 
> Host Adapter 0
==============

Node 0 GUID 0x0d60410600044b03
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x001ceade98f00000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
	channel=1, data_rate=1, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

Host Adapter 1
==============

Node 0 GUID 0x00023c002105736c
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR


Which unless I'm mistaken means port 0, node 1, correct?


When trying port 0 node 1 in firewire tester, everything fails.

What does this mean? Is there anything I can do? If I can't use firewire, what's my next best solution?

---

