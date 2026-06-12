---
title: "Good router for torrents?"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by Pithikos on 2011-10-28
I have had a Netgear WRT614 for about 2 years and when I have many torrents open I will not be able to browse at all!! I took now the decision after setting up rtorrent on my server to get a better router.

What do you recommend? Also I was wondering since I already have this crappy Netgear which is wireless maybe it would be cheaper to buy a router with only wire ports? Can I then connect the wireless on top of it? What should I pay attention to?

Many questions I know but I would be greatful :grin:

---

### Post by satanselbow on 2011-10-28
A different router will not make much difference - you might do better limiting your upload speed in your torrent client so you are not maxing out and bottlenecking you connection.

If you are using all your bandwidth for torrents both up and down you are not leaving yourself any room to surf as well ;)

Limiting your upload speed is crucial if you want to surf and seed ;) about 50-60% total upwidth for torrents should leave you enough to play with.

---

### Post by aloogobi on 2011-10-28
> **Pithikos said:**
> 

What do you recommend? Also I was wondering since I already have this crappy Netgear which is wireless maybe it would be cheaper to buy a router with only wire ports? Can I then connect the wireless on top of it? What should I pay attention to?



Your netgear wireless router has already got ports for ethernet cables. Buying a router with no wireless capability and adding a router to it won't make a difference. Your issue is that your torrents are eating up all your available bandwidth. You're only real option, as mentioned above, is to limit the download rate.

---

### Post by dargaud on 2011-10-28
There also the fact that some cheap-*** router fill up their routing table quickly when using P2P apps, and then are unable to route anything new. I don't know if this is the case of your router. A firmware upgrade may fix it. A periodic reboot of the modem will solve it. Buying a recent router will help as well.

---

### Post by Pithikos on 2011-10-29
> **satanselbow said:**
> A different router will not make much difference - you might do better limiting your upload speed in your torrent client so you are not maxing out and bottlenecking you connection.

If you are using all your bandwidth for torrents both up and down you are not leaving yourself any room to surf as well ;)

Limiting your upload speed is crucial if you want to surf and seed ;) about 50-60% total upwidth for torrents should leave you enough to play with.

It's not the bandwidth. I have a 10/10Mbit connection and I might be downloading at just 90-200Kbps or uploading at 60Kbps and still get long hangs. I have also limited my global connections to a very small number but same problem. Rebooting the router does solve the problem but just temporarily. :(

---

### Post by Lars Noodén on 2011-10-29
> **satanselbow said:**
> If you are using all your bandwidth for torrents both up and down you are not leaving yourself any room to surf as well ;)

You could set up some kind of [queuing](http://manpages.ubuntu.com/manpages/oneiric/en/man8/tc.8.html) on the router to have torrent traffic go through only if there isn't any web traffic.  I haven't tried that sort of thing yet on Linux but it was easy to set up in PF on OpenBSD.

---

