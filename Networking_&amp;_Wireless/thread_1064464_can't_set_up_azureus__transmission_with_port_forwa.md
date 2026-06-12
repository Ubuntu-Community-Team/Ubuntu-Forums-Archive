---
title: "can't set up azureus / transmission with port forwarding"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by vajorie on 2009-02-08
I don't quite understand what I'm doing wrong here... I tried it with transmission, didn't work, so I installed azureus and still no go. 

here's the problem. I told azureus to use port 51413 (the one transmission was using - I tried others too). then I told my router to do port forward on port 51413. the router is a westell given by verizon (portforwarding.com didn't help). I didn't set up iptables in the PC (no firewall on PC). 

then I told azureus to test the port and it times out. while azureus is testing, my router's log have no entries, but at times, it shows me random ports being blocked, none of them being 51413. Here's an example (port was set as 51413, router has port forwarding for it)
```

Time 	        Direction 	     Rule/Reason 	Details
Feb 8 20:49:50 	In: br0 -> Out: ppp0 	Blocked 	
Src IP: x.x.x.x 	Port: 35452
Dest IP: x.x.x.x 	Port: 2710
Proto: TCP 	Len: 60
Feb 8 20:49:44 	In: br0 -> Out: ppp0 	Blocked 	
Src IP: x.x.x.x 	Port: 35452
Dest IP: x.x.x.x 	Port: 2710
Proto: TCP 	Len: 60
Feb 8 20:49:41 	In: br0 -> Out: ppp0 	Blocked 	
Src IP: x.x.x.x 	Port: 35452
Dest IP: x.x.x.x 	Port: 2710
Proto: TCP 	Len: 60 

```

The rules on my router looks like this:
```

Entry	Protocol	Global Port(s)	Local Port(s)
1	both	           51413	51413
2	both              51413	 
3	both	 	                51413

```

is my PC confused about which port is which one??? wut

---

### Post by vajorie on 2009-02-09
bump

---

