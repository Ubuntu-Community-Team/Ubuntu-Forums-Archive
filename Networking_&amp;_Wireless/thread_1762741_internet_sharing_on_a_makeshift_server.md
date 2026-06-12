---
title: "internet sharing on a makeshift server"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by srs008 on 2011-05-19
okay. i'm trying to rig up my machine as a household server, i had it sharing internet to my other computers via a wifi router. (machine is a desktop and i have no wifi cards for it)
then i installed java, squid and SAMBA. since then the other machines can't detect internet. java is screwy. i've updated it and it reduces the screen scramble. but squid is what has me. it seems to stop ubuntu telling my windows machines (win 7, and win xp) that there is internet available. intrestingly i can play multiplayer games on the windows machines with a ip address. (ip address of a mate. connected and ran ok.) 

system specs
ubuntu 11? (i know it updated from 10 a few weeks ago)
internet - DODO mobile broadband (piggybacks on yes optus australia)
wifi- via router connected to eth0

so someone know how to either 
1. get ubuntu to state it's sharing internet again.
or
2. turn mobile broadband off for 5-10 secs, re-enable, then connect to a mobile broadband called DODO automatically when internet drops out (a script perhaps?) 

thanks

---

### Post by srs008 on 2011-05-20
okay, got the internet sharing going again (windows 7 tampered with router settings)
but anyone know good solution for my DODO mobile broadband, it disconnects every so often, and it don't auto re-connect.
to re connect i have to (i think it's unity desktop) click the network tab (top left of screen)
click disable mobile broadband, re-enable it. connect.
if i do anything else it just goes (GSM DISCONNECTED) within half second

any ideas?
SCRIPTS?

---

### Post by srs008 on 2011-05-21
HELLO???

by the way, the DODO thing ain't linux. even under windows, different machines, still disconnects from time to time. i'm after some sort of auto-reconnect solution to re-load it when it goes down.

because it's a server of sorts, it shares the DODO conection via a router to connected computers. so when internet drops out, my other machines lose internet. sometimes during downloads.

any help??????

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
Why even use network-manager for a server?

Network managers slow, crappy and takes up a fair chunk of resources.

Just configure the mobile internet through config files (google it).

That way, you should at least have a stable connection :)

---

