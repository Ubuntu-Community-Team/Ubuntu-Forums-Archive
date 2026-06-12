---
title: "IP Addresses for Backend Behind Router"
date: 2007-10-27
forum: Mythbuntu
---

### Post by spivak.d on 2007-10-27
Hi all,

I'm using Mythbuntu under Gutsy and have gotten my desktop computer functional as a backend and a laptop of mine functional as a frontend; however, this is using the 192.168.1.101 IP address of my router (i.e. internal address). I'm wondering if anyone is familiar with what steps I would need to take to be able to access my backend (which is behind a Linksys router) from my frontend (which would not be behind the router; maybe on a wireless access point at Starbucks, for example). 

Any ideas? :)

---

### Post by napsilan on 2007-10-27
You need to enable remote connections in mythtv-setup on the backend (also note which port it uses), and then set up port forwarding in your router for that port to your backend.

---

### Post by spivak.d on 2007-10-27
Alright. So, as an example, an ifconfig command on my MythTV backend gives me the 192.168.1.100 IP that the router gives it (yet a website scan tells me my IP is something like 62.125.x.x). In that case, which IP do I set as the server IP on the MythTV backend (i.e. the IP given to my computer by the router or the external IP)? Also, it is as simple as just port forwarding the MythTV port from my router to my computer (in this case, 6543)? No server set up necessary or anything?

---

