---
title: "Transmission won't download torrents"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by vitorsouza on 2009-02-03
I'm pretty sure my problem isn't Ubuntu-related, but if anyone could help I'd appreciate it.

I have a DSL connection at home, my provider lent me a adsl modem + wireless router and I can download torrents fine here.

My friend, though, has another provider and he's got a D-Link DSL-504T modem/router connected to a Linksys WRT54G wireless router from where he gets the wireless signal and connects from anywhere in his house. At his house, Transmission won't download any torrents.

Under Preferences > Peers > Listening Port, Transmission says the port is open. It even gets as far as listing some available peers, but in the Details of the torrent, in the Peers tab, the Status column is always something weird like "|?". And nothing is downloaded or uploaded.

We tried configuring Port Forwarding as shown here:

[http://portforward.com/english/routers/port_forwarding/Dlink/DSL-504T/BitTorrent.htm](http://portforward.com/english/routers/port_forwarding/Dlink/DSL-504T/BitTorrent.htm)

But that didn't help. We checked the configured port (51413) under [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and it was open.

We ruled out the Linksys wireless router because we connected with an ethernet cable directly to the D-Link router and the problem persisted.

As I'm writing this, I'm ruling out the 51413 port thing, because at his house Tranmission said it was open, at my house it says it's closed... So I guess that has nothing to do with the ability to download...

Networking really isn't my area, so any experts have any tips for me here? Anything I can try to better diagnose the problem?

Thanks in advance for any response.

Vítor Souza

---

### Post by icheyne on 2009-02-04
What about trying Vuze or Deluge?

---

### Post by vitorsouza on 2009-02-04
> **icheyne said:**
> What about trying Vuze or Deluge?

So you think it might be Transmission's fault? I'll try other torrent clients then and report back once I do. Thanks!

Vítor

---

