---
title: "Ad hoc troubles"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by htpw16 on 2009-05-25
Hello all, 

I am a networking newbie so bare with me here. I have two Ubuntu laptops and several hardware nodes that I perform my testing on. The nodes form a ad hoc network that I can associate with using one of my laptops flawlessly. My other laptop for some reason cannot connect to the network unless the working laptop does or it will connect for a brief time, less than a minute, then I suddenly cannot access the other devices (i.e. no route to host). 

The network manager shows that I am connected to the network but I cannot access the other devices. I have the settings on both laptops identical in the network manager. It is really strange since when I run iwlist scanning on the non working laptop I can see the ad hoc network but the ssid is <hidden>. Whereas in the working laptop it sees the ad hoc name.

I did some packet sniffing and obviously the troubled laptop does not receive anything from the ad hoc network. Could it be that the Cell address gets changed somehow on the troubled laptop or something?

Any help would be great,

Thanks.

---

### Post by htpw16 on 2009-05-25
Any suggestions?

---

### Post by superprash2003 on 2009-05-26
are you trying to connect more than 2 machines to an adhoc network?? if so , its not possible , an adhoc network is only between 2 machines.. if your trying to access shares , firstly check if both machines are able to ping each other..

---

### Post by htpw16 on 2009-05-26
The troubled laptop cannot ping anyone (host unreachable). I am not trying to connect two machines per say, just trying to associate the machine with the network so that it can also be discovered and used for forwarding info etc... (mesh network). I am just so at loss since one laptop works and the other doesn't with identical configurations.

---

