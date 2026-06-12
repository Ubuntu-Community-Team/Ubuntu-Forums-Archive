---
title: "Assign application to IPv6 tunnel?"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by poo706 on 2010-05-24
I've set up a Freenet6 IPv6 tunnel in 10.04 with gw6c and it seems to work great.  I'm trying to access an IPv6 Usenet server.  If I use Sabnzb+ with port 119, I can connect just fine (I assume because it's using Firefox, which also cooperates with the tunnel).  I'm not a fan of Sabnzb+, however, I'd rather use Alt.Binz under Wine.  Alt.Binz works just fine in Wine, but it seems as though it isn't using the tunnel.  In Windows, I have to run this command:

netsh interface portproxy add v4tov6 listenport=1120 connectaddress=reader.ipv6.xsnews.nl connectport=119

Then I setup Alt.Binz to use server 127.0.0.1 and port 1120.  How would I go about pulling this off in Ubuntu?  Thanks.

[poo]

---

### Post by poo706 on 2010-05-24
Found the answer to my own question!  Install 6tunnel from the repos and then run:

6tunnel 1120 reader.ipv6.xsnews.nl 119

Alt.Binz and Hellanzb are both now properly using the tunnel!  Alt.Binz is really slow over x11vnc compared to Hellanzb over SSH, so I think I'll ditch Alt.Binz for the most part.  But I needed that 6tunnel command regardless.

[poo]

---

