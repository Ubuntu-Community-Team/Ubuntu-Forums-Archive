---
title: "Network disconnecting"
date: 2009-06-14
forum: Mythbuntu
---

### Post by Billsputters on 2009-06-14
We suffer frequent power outages here and although the Myth box is protected by a UPS, the network router is not, due to it's different location.

In pre Myth days, it wasn't a problem if the network went down, but as it it now, the front end can't see the backend, even though they are physically on the same machine, and Mythweb won't work. So I have to manually connect the wireless connection on the BE. Sooner or later this is going to happen overnight before a recording is scheduled and it will therefore just not happen.

Is there any way of telling the wireless connection to automatically or at least retry every minute or so until connection is re-established. The only way I can think of is a small cron job that runs, pings the router and if unsuccessful, try to reconnect.

---

### Post by klc5555 on 2009-06-15
> **Billsputters said:**
> We suffer frequent power outages here and although the Myth box is protected by a UPS, the network router is not, due to it's different location.

In pre Myth days, it wasn't a problem if the network went down, but as it it now, the front end can't see the backend, even though they are physically on the same machine ... 


How is it that the localhost frontend doesn't see the localhost (master/solitary) backend when the network is out? This is something of a mystery for me. 

If you have the backend set up on a standard static IP address, then the frontend should be set up also on that same static address; the presence of the router (or the rest of the network in general) is irrelevant unless the machine needs to contact something else on the network, which it doesn't do just for simple recording. 

If the local frontend for some reason is set up for localhost 127.0.0.1 and can't find the backend on a real ip address, then this should either be changed in the frontend setup, or a line should be added in the /etc/hosts file. 

Or am I missing something here?

---

