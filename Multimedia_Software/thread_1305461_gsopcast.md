---
title: "gsopcast"
date: 2009-10-29
forum: Multimedia Software
---

### Post by u_kapaley256 on 2009-10-29
Hi,
I worked a lot towards getting sopcast running on my system but it wont budge

I suspect its because i dont have a sopcast id but the site wont come up

I have sp-sc and sp-sc-auth in /usr/bin
I have gsopcast installed 
gsopcast doesnt seem to fetch the channels 
and if i enter a url in the box it keeps looping from "connecting" to "0%........peers=0" to "restart monitoring"

I used ./sp-sc-auth sop://broker.sopcast.com:3912/57700 3908 8908 

which gave me this :-
detect MTU=4c4
Connection=11	Connection=11
i=0   51
ipExternal:245ab14a  Internal:4401a8c0  portLocal:38188    portExternal1:38188    External2:38188  linkType:51
tm4.sopserv.com proto=17
adv=193
TD1=411172-4294556124:  1256870692:193:2739830203
tm1.sopserv.com proto=17
adv=935
TD1=411172-4294556124:  1256870693:935:2739830461
Average difference=411172
411172
411172
3dbedaf0 28ba0b0d
Not valid ID
54c22859 1dfff897
sop://broker.sopcast.com:3912/99
system channelID=99
detect MTU=4c4
localaddr:	c0a80144:25923, externaladdr:4ab15a24:25923
channel ID=57700
tk:00000000 00000000
streamID=e164
STOP QUIT
retv = 0
	spsc_cleanup_sysch
sopch2_schedule_sc_misc_sysch retv=0
CHLST blockSize=0
2740241837:2740241634
detect MTU=4c4
ADRESS = 252498d3
Start cache thread.
hook_broker_connect:msgType=2
reason=1
SO_QUIT
retv = -104
	spsc_cleanup



any suggestions ??

---

### Post by u_kapaley256 on 2009-10-29
i do have libstdc++.so.5

root@udayan:/usr/bin# !219
locate libstdc++.so.5
/usr/lib/libstdc++.so.5
/usr/lib/libstdc++.so.5.0.7

---

### Post by donotbugme on 2009-10-30
[Here]("http://www.sourceslist.eu/installare-software-tramite-repository/installare-sopcast-player-0-3-0-su-ubuntu-karmic-koala-9-10-in-pochi-click/") you can find sopcast-player for Ubuntu Karmic Koala 9.10. :popcorn:

---

### Post by u_kapaley256 on 2009-10-30
I am running hardy heron and one of the so dependencies are messing up with a version problem.

If someone can look at the output and tell me whats wrong it will be great

Thanks

---

