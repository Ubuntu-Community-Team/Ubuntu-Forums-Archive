---
title: "Rhythmbox doesn't autodetect or save DAAP host"
date: 2008-05-29
forum: Multimedia Software
---

### Post by Morcroft on 2008-05-29
I have a Maxtor shared storage drive set up with its "iTunes" server switched on. This seems to be a fairly standard DAAP implementation: ie. iTunes connects to it from an XP box. 
I added the DAAP plugin to Hardy's Rhythmbox and when I select the "Connect to DAAP share" option and type in the name of the Maxtor then it appears under "Shared" and allows the (mp3 music) content to be browsed and played exactly as I want. So far so good.

The problem is that I really need the network shared storage to appear automatically every time Rhythmbox opens - this computer is intended for a non-technical (7 year old) user and typing in a network host every time she wants to play music is just going to set off a sulk! 

So - either I need Rhythmbox to autodetect the DAAP share or I need to be able to save it in some way. I've googled till I'm crosseyed and tinkered with Avahi but I'm stumped. 
Why doesn't this work, and can anyone think of a workaround?

Thanks

---

### Post by skgu67 on 2008-11-20
I've got the exact same issue (except for an 8 year-old boy vs. a 7-year old girl).

Did you ever figure it out?

---

### Post by Morcroft on 2009-01-23
'Fraid not. Gave up in the end: the pc I gave her was too underpowered to play Club Penguin so she inherited my wife's laptop. Don't get me started on trying to get Windows Media Player 11 to connect to the aforesaid DAAP host!

Cheers
MD.

---

### Post by Martijn van Es on 2009-10-24
Rhythmbox shouldn't need any config except for the DAAP mysic sharing plugin.
mt-daapd works over port 3689 (udp/tcp) you should have that port accepted on all firewalls (firefly server PC and all clients)
Then mt-daapd relies on avahi to broadcast it's presence. Make sure avahi is running (sudo /etc/init.d/avahi-daemon restart) and on the server and clients port 5353 (udp/tcp) must be accepted.
If all that is OK the share should pop up in your rhythmbox sidepane,

Hope this helps!

---

### Post by Kprojekt on 2009-11-30
The problem is not getting the DAAP to work, as the OP said, it works if he left-clicks the side pane and selcts connect to DAAP, and enters the IP of the DAAP server. What Rhythmboxx is not doing, however is Automatically discovering the DAAP on AVHI, and loading the shared library on startup, without entering the IP each time Rhythmbox is started. I'm having this same problem, and would like for Rhythmboxx to have some setting that would connect and show shared library as its default library. 

Should I submit this as a bug?

---

### Post by doas777 on 2009-11-30
my rhythm box picks up my firefly server automatically. not sure what to tell you. may be Maxtor's implementation.

---

