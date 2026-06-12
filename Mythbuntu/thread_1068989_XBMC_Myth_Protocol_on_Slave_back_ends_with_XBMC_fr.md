---
title: "XBMC Myth Protocol on Slave back ends with XBMC front end on both Master and Slave."
date: 2009-02-13
forum: Mythbuntu
---

### Post by rodercot on 2009-02-13
So here is my situation,

I have My Master backend and XBMC running on 192.168.1.132, everything works as well as It should I guess. 

Mythbox script works as well on above.

Setup Slave machine at 192.168.1.190 with XBMC as the frontend. Setup Mythbackend and Frontend first as secondary backend and I am making sure that works and it does, other than I cannot WATCH the recordings I schedule on the Master back end. 

The secondary machine is configured as 127.0.0.1 in Myth backend setup for the slave machine and it is connecting to the database at 192.168.1.132 and that is fine I can watch live tv from Myth on the slave machine.

NOW How do I setup the protocol for this OR mythbox because currently it will not connect to 127.0.0.1 I get no guide or livetv data if I change to 192.168.1.190 I get no guide but I can see the recordings (but they will not play) and I can see Live tv (but with no icons) and I can watch live tv. If I change to 192.168.132 of course I get liveTV data, Guide Data, and I see the recordings from the default directory only and not from the livetv but they will not play and the major problem here is no watching of live tv but what the protocol does do is tries to launch the live tv channel say discovery I can see activity like it is going to start then does not but I still have activity going on, then if I hit the button again to view the same live tv channel it will then start but will not stop and if I go and check status on the Master Back end, both of my TUNERS 3 and 4 are tied up watching live tv and I have to reboot the slave machine to get it to stop and release the tuners.

**_And finally I get no live tv after resuming from Standby in any way shape or form unless I reboot the machine again._**

Any Advice. Same issues using the protocol or the mythbox script.

Dave

---

### Post by fld on 2009-03-05
well, the thing sounding wrong is using 127.0.0.1 instead of 192.168...
the next one is...your setup!? It's not clear why you use 2 backends, using just one would probably make things much more simple, but you don't give much details about that. I'm planning something similar although on just one machine, so I would be interested in your (software) setup. What exactly did you use to install?

---

### Post by rodercot on 2009-03-05
Yes I fixed that local host problem, it turns out that xbmc needs to see an actual host NAME in the hosts files on each machine. 

 My setup I did not think was that unique but here goes.

 I have two bell rcvrs one in the living room and another in the bedroom. Thus creating the need for a Master b/e and a Slave b/e each a machine has a tuner in it well there is also an hvr-1250 in the master doing local OTA hd I get about four channels currently but I have not played with antenna placament at all. 

 I have all the cards configured on the master b/e and the two pvr-150 are sharing the express vu source and each machine has a /var/lib/mythtv/recordings directory although I mainly use that for livetv on the slave machine and point all recording to the master. 
  
 the 2nd rcvr and 2nd card in the bedroom was the need to create a slave backend. I hope to configure a new master b/e in the spring and move all the rcvr,s and the new box to the rack in the basement with the media server and that will eliminate all of this. 

 Finally to fix all this I now load up the mythfrontend and use it for livetv and recordings and then has an xbmc launcher that resides as another button on the myth frontend main menu screen when I am done with xbmc I just choose exit and I am back at the mythtv main menu again. I have also a Suspend system button to the main page on each machine which powers down the systems with pm-suspend and also powers down the tv's and stereo automagically the WAF loves it.

 Rgds,

 Dave

---

